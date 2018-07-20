---
title: Déployer le modèle R et l’utiliser dans SQL (procédure pas à pas) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a5d8b7ac8bd36a6ce76b895b2dde4a07f5ea96
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085351"
---
# <a name="deploy-the-r-model-and-use-it-in-sql"></a>Déployer le modèle R et l’utiliser dans SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans cette leçon, vous utilisez vos modèles R dans un environnement de production, en appelant un modèle formé à partir d’une procédure stockée. Vous pouvez ensuite appeler la procédure stockée à partir de R ou n’importe quel langage de programmation d’application qui prend en charge [!INCLUDE[tsql](../../includes/tsql-md.md)] (par exemple, c#, Java, Python, etc.), pour utiliser le modèle pour élaborer des prédictions sur de nouvelles observations.

Cet exemple montre les deux manières courantes d’utiliser un modèle de notation :

- **Mode de notation par lots** est utilisé lorsque vous avez besoin créer plusieurs prédictions très rapides, en passant une instance SQL de requête ou de table en tant qu’entrée. Une table de résultats est retournée, que vous pouvez insérer directement dans une table ou écrire dans un fichier.

- **Mode d’évaluation individuelle** est utilisé lorsque vous avez besoin créer des prédictions une à la fois. Vous transmettez un ensemble de valeurs individuelles à la procédure stockée. Les valeurs correspondent aux fonctionnalités dans le modèle, le modèle utilise pour créer une prédiction, ou génèrent un autre résultat tel qu’une valeur de probabilité. Vous pouvez ensuite retourner cette valeur à l’application, ou l’utilisateur.

## <a name="batch-scoring"></a>Notation par lot

Une procédure stockée pour la notation par lot a été créée quand vous avez exécuté le script PowerShell. Cette procédure stockée, *PredictTipBatchMode*, effectue les opérations suivantes :

- Elle obtient un jeu de données d’entrée sous la forme d’une requête SQL.
- Elle appelle le modèle de régression logistique formé que vous avez enregistré à la leçon précédente.
- Prédit la probabilité que le pilote Obtient les info-bulle différente de zéro

1. Prenez une minute pour vérifier le script pour la procédure stockée, *PredictTipBatchMode*. Il illustre plusieurs aspects de la façon dont un modèle peut être mis en œuvre à l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].
  
    ```tsql
    CREATE PROCEDURE [dbo].[PredictTipBatchMode]
    @input nvarchar(max)
    AS
    BEGIN
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  FROM nyc_taxi_models);
      EXEC sp_execute_external_script @language = N'R',
         @script = N'
           mod <- unserialize(as.raw(model));
           print(summary(mod))
           OutputDataSet<-rxPredict(modelObject = mod,
             data = InputDataSet,
             outData = NULL,
             predVarNames = "Score", type = "response",
             writeModelVars = FALSE, overwrite = TRUE);
           str(OutputDataSet)
           print(OutputDataSet)',
      @input_data_1 = @input,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

    + Vous utilisez une instruction SELECT pour appeler le modèle stocké à partir d’une table SQL. Le modèle est récupéré à partir de la table en tant que **varbinary (max)** données, stockées dans la variable SQL  _\@lmodel2_et passée comme paramètre *mod* au système procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + Les données utilisées comme entrées pour la notation est définie comme une requête SQL et stockée sous forme de chaîne dans la variable SQL  _\@d’entrée_. Comme les données sont récupérées à partir de la base de données, il est stocké dans une trame de données appelée *InputDataSet*, qui est simplement le nom par défaut pour les données d’entrée pour le [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) procédure ; vous pouvez définir un autre nom de variable si nécessaire en utilisant le paramètre   *_\@input_data_1_name_*.

    + Pour générer les scores, la procédure stockée appelle la fonction `rxPredict` à partir de la bibliothèque **RevoScaleR** .

    + La valeur de retour, *Score*, est la probabilité, compte tenu du modèle, ce pilote Obtient une info-bulle. Si vous le souhaitez, vous pouvez facilement appliquer une sorte de filtre aux valeurs retournées pour classer les valeurs de retour dans des « tip » et « aucun pourboire ».  Par exemple, une probabilité de moins de 0,5 signifie qu'une info-bulle est peu probable.
  
2.  Pour appeler la procédure stockée en mode batch, vous définissez la requête requise en tant qu’entrée à la procédure stockée. Voici la requête SQL. Vous pouvez l’exécuter dans SSMS pour vérifier qu’elle fonctionne.

    ```SQL
    SELECT TOP 10
      a.passenger_count AS passenger_count,
      a.trip_time_in_secs AS trip_time_in_secs,
      a.trip_distance AS trip_distance,
      a.dropoff_datetime AS dropoff_datetime,
      dbo.fnCalculateDistance( pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance
      FROM 
        (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude 
        FROM nyctaxi_sample)a 
      LEFT OUTER JOIN
      ( SELECT medallion, hack_license, pickup_datetime
      FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b
      ON a.medallion=b.medallion
      AND a.hack_license=b.hack_license
      AND a.pickup_datetime=b.pickup_datetime
      WHERE b.medallion is null
    ```

3. Utilisez ce code R pour créer la chaîne d’entrée à partir de la requête SQL :

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @inquery = ", input, sep="");
    ```

4. Pour exécuter la procédure stockée à partir de R, appelez le **sqlQuery** méthode de la **RODBC** empaqueter et utiliser la connexion SQL `conn` que vous avez défini précédemment :

    ```R
    sqlQuery (conn, q);
    ```

    Si vous obtenez une erreur ODBC, vérifiez la syntaxe de requête, et si vous êtes le nombre approprié de guillemets. 
    
    Si vous obtenez une erreur d’autorisations, assurez-vous que la connexion a la possibilité d’exécuter la procédure stockée.

## <a name="single-row-scoring"></a>Ligne unique de score

Lorsque vous appelez le modèle pour la prédiction sur une ligne par ligne de base, vous passez un ensemble de valeurs qui représentent des fonctionnalités pour chaque cas. Ensuite, la procédure stockée retourne une prédiction unique ou une probabilité. 

La procédure stockée *PredictTipSingleMode* illustre cette approche. Il prend comme plusieurs paramètres représentant les valeurs de fonctionnalité (par exemple, selon la distance nombre et le voyage de passagers) d’entrée, évalue ces fonctionnalités à l’aide du modèle R stocké et renvoie la probabilité d’info-bulle.

1. Si la procédure stockée *PredictTipSingleMode* n’a été créé par le script PowerShell initial, vous pouvez exécuter l’instruction Transact-SQL suivante pour la créer maintenant.

    ```tsql
    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0,
    @trip_distance float = 0,
    @trip_time_in_secs int = 0,
    @pickup_latitude float = 0,
    @pickup_longitude float = 0,
    @dropoff_latitude float = 0,
    @dropoff_longitude float = 0
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs, @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)'
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);

      EXEC sp_execute_external_script @language = N'R',  @script = N'
            mod <- unserialize(as.raw(model));
            print(summary(mod))
            OutputDataSet<-rxPredict(
              modelObject = mod,
              data = InputDataSet,
              outData = NULL,
              predVarNames = "Score",
              type = "response",
              writeModelVars = FALSE,
              overwrite = TRUE);
            str(OutputDataSet)
            print(OutputDataSet)
            ',
      @input_data_1 = @inquery,
      @params = N'
      -- passthrough columns
      @model varbinary(max) ,
      @passenger_count int ,
      @trip_distance float ,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      -- mapped variables
      @model = @lmodel2 ,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance ,
      @trip_time_in_secs=@trip_time_in_secs ,
      @pickup_latitude=@pickup_latitude ,
      @pickup_longitude=@pickup_longitude ,
      @dropoff_latitude=@dropoff_latitude ,
      @dropoff_longitude=@dropoff_longitude
      WITH RESULT SETS ((Score float));
    END
    ```

2. Dans SQL Server Management Studio, vous pouvez utiliser la [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** procédure (ou **EXECUTE**) pour appeler la procédure stockée et passer les entrées requises. Par exemple, essayez d’exécuter cette instruction dans Management Studio :

    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    Les valeurs transmises ici sont, respectivement, pour les variables _passagers\_nombre_, _trip_distance_, _voyage\_temps\_dans\_secondes_, _pickup\_latitude_, _pickup\_longitude_, _arrivée\_latitude_, et _arrivée\_longitude_.

3. Pour exécuter ce même appel à partir de code R, vous définissez simplement une variable R qui contient l’appel de procédure stockée complet, similaire à celle-ci :

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    Les valeurs transmises ici sont, respectivement, pour les variables _passagers\_nombre_, _voyage\_distance_, _voyage\_temps\_dans\_secondes_, _pickup\_latitude_, _pickup\_longitude_, _arrivée\_ Latitude_, et _arrivée\_longitude_.

4. Appelez `sqlQuery` (à partir de la **RODBC** package) et passez la chaîne de connexion, ainsi que la variable de chaîne contenant l’appel de procédure stockée.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > Outils R pour Visual Studio (RTVS) fournit une intégration étroite avec SQL Server et R. Consultez cet article pour plus d’exemples d’utilisation de RODBC avec une connexion SQL Server : [fonctionne avec SQL Server et R](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="summary"></a>Résumé

Maintenant que vous avez appris à travailler avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données et conserver des modèles R formés pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il devrait être relativement facile de créer de nouveaux modèles basés sur ce jeu de données. Par exemple, vous pouvez essayer de créer ces modèles supplémentaires :

- Un modèle de régression qui prédit le montant du pourboire

- Un modèle de classification multiclasse qui prédit si l’info-bulle est grande, moyenne ou petite

Nous vous recommandons également de consulter certains de ces exemples et ressources supplémentaires :

+ [Scénarios de science des données et modèles de solutions](data-science-scenarios-and-solution-templates.md)

+ [Analytique avancée en base de données](sqldev-in-database-r-for-sql-developers.md)

+ [Microsoft R - Plongée dans l’analyse des données](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)

+ [Ressources supplémentaires](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)

## <a name="previous-lesson"></a>Leçon précédente

[Créer un modèle R et l’enregistrer dans SQL Server](walkthrough-build-and-save-the-model.md)

## <a name="next-steps"></a>Étapes suivantes

[Didacticiels de SQL Server R](sql-server-r-tutorials.md)

[Comment créer une procédure stockée à l’aide de sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)
