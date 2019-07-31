---
title: Déployer un modèle R pour les prédictions sur SQL Server
description: Didacticiel expliquant comment déployer un modèle R sur SQL Server pour l’analyse en base de données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: b79d0bdc57ed49790874b571ccde875f45e35714
ms.sourcegitcommit: 97e94b76f9f48d161798afcf89a8c2ac0f09c584
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661295"
---
# <a name="deploy-the-r-model-and-use-it-in-sql-server-walkthrough"></a>Déployer le modèle R et l’utiliser dans SQL Server (procédure pas à pas)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans cette leçon, vous apprendrez à déployer des modèles R dans un environnement de production en appelant un modèle formé à partir d’une procédure stockée. Vous pouvez appeler la procédure stockée à partir de R ou de n’importe [!INCLUDE[tsql](../../includes/tsql-md.md)] quel langage de C#programmation d’application prenant en charge (par exemple, Java, Python, etc.) et utiliser le modèle pour faire des prédictions sur de nouvelles observations.

Cet article illustre les deux méthodes les plus courantes d’utilisation d’un modèle dans le calcul de score:

> [!div class="checklist"]
> * Le mode de calcul de **score par lot** génère plusieurs prédictions
> * Le mode de calcul de **score individuel génère des** prédictions une à la fois

## <a name="batch-scoring"></a>Notation par lot

Créer une procédure stockée, *PredictTipBatchMode*, qui génère plusieurs prédictions, en passant une requête SQL ou une table comme entrée. Une table de résultats est retournée, que vous pouvez insérer directement dans une table ou écrire dans un fichier.

- Elle obtient un jeu de données d’entrée sous la forme d’une requête SQL.
- Elle appelle le modèle de régression logistique formé que vous avez enregistré à la leçon précédente.
- Prédit la probabilité que le pilote récupère une astuce différente de zéro

1. Dans Management Studio, ouvrez une nouvelle fenêtre de requête et exécutez le script T-SQL suivant pour créer la procédure stockée PredictTipBatchMode.
  
    ```sql
    USE [NYCTaxi_Sample]
    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO

    IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PredictTipBatchMode')
    DROP PROCEDURE v
    GO

    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @input nvarchar(max)
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

    + Vous utilisez une instruction SELECT pour appeler le modèle stocké à partir d’une table SQL. Le modèle est récupéré à partir de la table en tant que données **varbinary (max)** , stockées  _\@_ dans la variable SQL lmodel2, puis passé comme paramètre *Mod* à la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + Les données utilisées comme entrées pour la notation sont définies en tant que requête SQL et stockées sous forme de chaîne dans l'  _\@entrée_de la variable SQL. À mesure que les données sont récupérées de la base de données, elles sont stockées dans une trame de données appelée *InputDataSet*, qui est simplement le nom par défaut pour les données d’entrée de la procédure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ; vous pouvez définir un autre nom de variable si nécessaire à l’aide du paramètre  *_\@input_data_1_name_* .

    + Pour générer les scores, la procédure stockée appelle la fonction rxPredict à partir de la bibliothèque **RevoScaleR** .

    + La valeur de retour, *score*, est la probabilité, étant donné le modèle, ce pilote obtient un Conseil. Si vous le souhaitez, vous pouvez facilement appliquer un filtre aux valeurs retournées pour classer les valeurs de retour dans des groupes «Tip» et «aucun Tip».  Par exemple, une probabilité inférieure à 0,5 signifie qu’une astuce est peu probable.
  
2.  Pour appeler la procédure stockée en mode batch, vous définissez la requête requise en tant qu’entrée dans la procédure stockée. Vous trouverez ci-dessous la requête SQL que vous pouvez exécuter dans SSMS pour vérifier qu’elle fonctionne.

    ```sql
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

3. Utilisez ce code R pour créer la chaîne d’entrée à partir de la requête SQL:

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @input = ", input, sep="");
    ```

4. Pour exécuter la procédure stockée à partir de R, appelez la méthode **SQLQuery** du package **RODBC** et utilisez la `conn` connexion SQL que vous avez définie précédemment:

    ```R
    sqlQuery (conn, q);
    ```

    Si vous recevez une erreur ODBC, recherchez les erreurs de syntaxe et indiquez si vous avez le nombre approprié de guillemets. 
    
    Si vous recevez une erreur d’autorisation, assurez-vous que la connexion a la possibilité d’exécuter la procédure stockée.

## <a name="single-row-scoring"></a>Notation sur une seule ligne

Le mode de calcul de score individuel génère des prédictions une à la fois, en passant un ensemble de valeurs individuelles à la procédure stockée en tant qu’entrée. Les valeurs correspondent aux fonctionnalités du modèle, que le modèle utilise pour créer une prédiction, ou générer un autre résultat comme une valeur de probabilité. Vous pouvez ensuite retourner cette valeur à l’application ou à l’utilisateur.

Lorsque vous appelez le modèle pour la prédiction ligne par ligne, vous transmettez un ensemble de valeurs qui représentent des fonctionnalités pour chaque cas individuel. La procédure stockée retourne alors une prédiction ou une probabilité unique. 

La procédure stockée *PredictTipSingleMode* illustre cette approche. Elle prend comme entrée plusieurs paramètres représentant des valeurs de caractéristiques (par exemple, le nombre de passagers et la distance du trajet), évalue ces fonctionnalités à l’aide du modèle R stocké et génère la probabilité de l’info-bulle.

1. Exécutez l’instruction Transact-SQL suivante pour créer la procédure stockée.

    ```sql
    USE [NYCTaxi_Sample]
    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO

    IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PredictTipSingleMode')
    DROP PROCEDURE v
    GO

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

2. Dans SQL Server Management Studio, vous pouvez utiliser la [!INCLUDE[tsql](../../includes/tsql-md.md)] procédure **Exec** (ou **Execute**) pour appeler la procédure stockée et lui transmettre les entrées requises. Par exemple, essayez d’exécuter cette instruction dans Management Studio:

    ```sql
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    Les valeurs transmises ici sont, respectivement, pour le nombre de _passagers\__ , le nombre de _trip_distance_, la _durée\_\_\_du trajet en secondes_, la latitude de _collecte\__ , longitude, _arrivéelatitudeet\__ _arrivéelongitude\__ . _\__

3. Pour exécuter ce même appel à partir du code R, il vous suffit de définir une variable R qui contient l’appel complet de la procédure stockée, comme celle-ci:

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    Les valeurs transmises ici sont, respectivement, pour le nombre de _passagers\__ , la _distance\_du trajet_, la _\_durée\_\_du trajet en secondes_, la _collecte\_ Latitude_, _\_longitude_, _arrivée\_Latitude_et _arrivée\_longitude_.

4. Appelez `sqlQuery` (à partir du package **RODBC** ) et transmettez la chaîne de connexion, ainsi que la variable de chaîne contenant l’appel de procédure stockée.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > Outils R pour Visual Studio (RTVS) offre une intégration parfaite avec SQL Server et R. Consultez cet article pour obtenir plus d’exemples d’utilisation de RODBC avec une connexion SQL Server: [Utilisation de SQL Server et de R](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez appris à utiliser les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données et à conserver les modèles R formés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez être relativement facile de créer des modèles basés sur ce jeu de données. Par exemple, vous pouvez essayer de créer ces modèles supplémentaires:

+ Un modèle de régression qui prédit le montant du pourboire
+ Un modèle de classification multiclasse qui prédit si le pourboire est grand, moyen ou petit

Vous pouvez également explorer ces exemples et ressources supplémentaires:

+ [Scénarios de science des données et modèles de solutions](data-science-scenarios-and-solution-templates.md)
+ [Analytique avancée en base de données](sqldev-in-database-r-for-sql-developers.md)
+ [Guides de procédures Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)
+ [Machine Learning Server des ressources supplémentaires](https://docs.microsoft.com//machine-learning-server/resources-more)
