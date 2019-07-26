---
title: Créer des fonctionnalités de données à l’aide des fonctions R et SQL Server
description: Didacticiel expliquant comment créer des fonctionnalités de données à l’aide de fonctions de SQL Server pour l’analyse dans la base de données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: e799b1ccba38d7716f2987112573a1d2d07203cd
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68468466"
---
# <a name="create-data-features-using-r-and-sql-server-walkthrough"></a>Créer des fonctionnalités de données à l’aide de R et SQL Server (procédure pas à pas)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’ingénierie des données est un aspect important du Machine Learning. Les données doivent souvent être transformées avant de pouvoir être utilisées pour la modélisation prédictive. Si les données n’ont pas les caractéristiques dont vous avez besoin, vous pouvez les créer à partir de valeurs existantes.

Pour cette tâche de modélisation, plutôt que d’utiliser les valeurs brutes de longitude et de latitude des lieux de prise en charge et de dépose, vous souhaitez avoir la distance en miles entre les deux emplacements. Pour créer cette fonctionnalité, vous calculez la distance linéaire directe entre deux points, à l’aide de la [formule Haversine](https://en.wikipedia.org/wiki/Haversine_formula).

Au cours de cette étape, vous allez découvrir deux méthodes différentes pour créer une fonctionnalité à partir de données:

> [!div class="checklist"]
> * Utilisation d’une fonction R personnalisée
> * Utilisation d’une fonction T-SQL personnalisée dans[!INCLUDE[tsql](../../includes/tsql-md.md)]

L’objectif est de créer un nouvel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensemble de données qui comprend les colonnes d’origine, ainsi que la nouvelle fonctionnalité numérique, *direct_distance*.

## <a name="prerequisites"></a>Prérequis

Cette étape suppose une session R en cours basée sur les étapes précédentes de cette procédure pas à pas. Elle utilise les chaînes de connexion et les objets de source de données créés dans ces étapes. Les outils et les packages suivants sont utilisés pour exécuter le script.

+ RGUI. exe pour exécuter des commandes R
+ Management Studio pour exécuter T-SQL

## <a name="featurization-using-r"></a>Caractérisation à l’aide de R

Le langage R est connu pour ses bibliothèques statistiques riches et variées, mais vous devrez peut-être créer des transformations de données personnalisées.

Tout d’abord, examinons la façon dont les utilisateurs R sont habitués à: obtenir les données sur votre ordinateur portable, puis exécuter une fonction R personnalisée, *ComputeDist*, qui calcule la distance linéaire entre deux points spécifiés par les valeurs de latitude et de longitude.

1. N’oubliez pas que l’objet de source de données que vous avez créé précédemment obtient uniquement les 1000 premières lignes. Nous allons donc définir une requête qui obtient toutes les données.

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. Créez un objet de source de données à l’aide de la requête.

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) peut accepter une requête composée d’une requête SELECT valide, fournie en tant qu’argument au paramètre _SQLQuery_ ou le nom d’un objet table, fourni en tant que paramètre _table_ .
    
    - Si vous souhaitez échantillonner des données à partir d’une table, vous devez utiliser le paramètre _SQLQuery_ , définir des paramètres d’échantillonnage à l’aide de la clause T-SQL TABLESAMPLE et affecter à l’argument _ROWBUFFERING_ la valeur false.

3. Exécutez le code suivant pour créer la fonction R personnalisée. ComputeDist accepte deux paires de valeurs de latitude et de longitude, et calcule la distance linéaire entre elles, en retournant la distance en miles.

    ```R
    env <- new.env();
    env$ComputeDist <- function(pickup_long, pickup_lat, dropoff_long, dropoff_lat){
      R <- 6371/1.609344 #radius in mile
      delta_lat <- dropoff_lat - pickup_lat
      delta_long <- dropoff_long - pickup_long
      degrees_to_radians = pi/180.0
      a1 <- sin(delta_lat/2*degrees_to_radians)
      a2 <- as.numeric(a1)^2
      a3 <- cos(pickup_lat*degrees_to_radians)
      a4 <- cos(dropoff_lat*degrees_to_radians)
      a5 <- sin(delta_long/2*degrees_to_radians)
      a6 <- as.numeric(a5)^2
      a <- a2+a3*a4*a6
      c <- 2*atan2(sqrt(a),sqrt(1-a))
      d <- R*c
      return (d)
    }
    ```
  
    + La première ligne définit un nouvel environnement. En R, un environnement peut être utilisé pour encapsuler des espaces de noms dans des packages et autres. Vous pouvez utiliser la fonction `search()` pour afficher les environnements dans votre espace de travail. Pour afficher les objets dans un environnement spécifique, tapez `ls(<envname>)`.
    + Les lignes commençant par `$env.ComputeDist` contiennent le code qui définit la formule de haversine, qui calcule la *distance orthodromique* entre deux points sur une sphère.

4. Une fois la fonction définie, vous devez l’appliquer aux données pour créer une colonne de fonctionnalité, *direct_distance*. mais avant d’exécuter la transformation, définissez le contexte de calcul sur local.

    ```R
    rxSetComputeContext("local");
    ```

5. Appelez la fonction [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) pour récupérer les données d’ingénierie des fonctionnalités et appliquez `env$ComputeDist` la fonction aux données en mémoire.

    ```R
    start.time <- proc.time();
  
    changed_ds <- rxDataStep(inData = featureDataSource,
    transforms = list(direct_distance=ComputeDist(pickup_longitude,pickup_latitude, dropoff_longitude, dropoff_latitude),
    tipped = "tipped", fare_amount = "fare_amount", passenger_count = "passenger_count",
    trip_time_in_secs = "trip_time_in_secs",  trip_distance="trip_distance",
    pickup_datetime = "pickup_datetime",  dropoff_datetime = "dropoff_datetime"),
    transformEnvir = env,
    rowsPerRead=500,
    reportProgress = 3);
  
    used.time <- proc.time() - start.time;
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""));
    ```

    + La fonction rxDataStep prend en charge différentes méthodes pour modifier les données sur place. Pour plus d’informations, consultez cet article:  [Comment transformer et dégrouper des données dans votre jeu de recherche](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    Toutefois, quelques points méritent une attention particulière concernant rxDataStep: 
    
    Dans d’autres sources de données, vous pouvez utiliser les arguments *varsToKeep* et *varsToDrop*, mais ceux-ci ne sont pas pris en charge pour les sources de données SQL Server. Par conséquent, dans cet exemple, nous avons utilisé  l’argument Transforms pour spécifier les colonnes directes et les colonnes transformées. En outre, lors de l’exécution dans un contexte de calcul  SQL Server, l’argument inData peut uniquement prendre une source de données SQL Server.

    Le code précédent peut également générer un message d’avertissement lorsqu’il est exécuté sur des jeux de données plus grands. Lorsque le nombre de lignes multiplié par le nombre de colonnes créées dépasse une valeur définie (la valeur par défaut est 3 millions), rxDataStep renvoie un avertissement et le nombre de lignes dans la trame de données retournée est tronqué. Pour supprimer l’avertissement, vous pouvez modifier l’argument _maxRowsByCols_ dans la fonction rxDataStep. Toutefois, si _maxRowsByCols_ est trop volumineux, vous risquez de rencontrer des problèmes lors du chargement de la trame de données en mémoire.

7. Si vous le souhaitez, vous pouvez appeler [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) pour inspecter le schéma de la source de données transformée.

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Personnalisation à l’aide de Transact-SQL

Dans cet exercice, Découvrez comment accomplir la même tâche à l’aide de fonctions SQL plutôt que de fonctions R personnalisées. 

Basculez vers [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) ou un autre éditeur de requête pour exécuter le script T-SQL.

1. Utilisez une fonction SQL, nommée *fnCalculateDistance*. La fonction doit déjà exister dans la base de données NYCTaxi_Sample. Dans l’Explorateur d’objets, vérifiez que la fonction existe, en accédant à ce chemin d’accès: Les bases de données > NYCTaxi_Sample > programmabilité > fonctions > fonctions scalaires > dbo. fnCalculateDistance.

    Si la fonction n’existe pas, utilisez SQL Server Management Studio pour générer la fonction dans la base de données NYCTaxi_Sample.

    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function calculates the direct distance between two geographical coordinates.
    RETURNS
    AS
    BEGIN
      DECLARE @distance decimal(28, 10)
      -- Convert to radians
      SET @Lat1 = @Lat1 / 57.2958
      SET @Long1 = @Long1 / 57.2958
      SET @Lat2 = @Lat2 / 57.2958
      SET @Long2 = @Long2 / 57.2958
      -- Calculate distance
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))
      --Convert to miles
      IF @distance <> 0
      BEGIN
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);
      END
      RETURN @distance
    END
    ```

2. Dans Management Studio, dans une nouvelle fenêtre de requête, exécutez l' [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction suivante à partir de n' [!INCLUDE[tsql](../../includes/tsql-md.md)] importe quelle application qui prend en charge pour voir le fonctionnement de la fonction.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude 
    FROM nyctaxi_sample
    ```
3. Pour insérer des valeurs directement dans une nouvelle table (vous devez d’abord la créer), vous pouvez ajouter une clause **into en** spécifiant le nom de la table.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. Vous pouvez également appeler la fonction SQL à partir du code R. Revenez à l’RGUI et stockez la requête SQL caractérisation dans une variable R.

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > Cette requête a été modifiée pour obtenir un échantillon de données plus petit, afin de rendre cette procédure pas à pas plus rapide. Vous pouvez supprimer la clause TABLESAMPLE si vous souhaitez obtenir toutes les données; Toutefois, en fonction de votre environnement, il est possible qu’il ne soit pas possible de charger le DataSet complet dans R, ce qui génère une erreur.
  
5. Utilisez les lignes de code suivantes pour appeler la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] à partir de votre environnement R et l’appliquer aux données définies dans *featureEngineeringQuery*.
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
        dropoff_longitude = "numeric", dropoff_latitude = "numeric",
        passenger_count  = "numeric", trip_distance  = "numeric",
        trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  Maintenant que la nouvelle fonctionnalité est créée, appelez **rxGetVarsInfo** pour créer un résumé des données dans la table des fonctionnalités.
  
    ```R
    rxGetVarInfo(data = featureDataSource)
    ```

    **Résultats**

    ```R
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: numeric
    Var 4: trip_time_in_secs, Type: numeric
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: direct_distance, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: pickup_longitude, Type: numeric
    Var 11: dropoff_latitude, Type: numeric
    Var 12: dropoff_longitude, Type: numeric
    ```

    > [!NOTE]
    > Dans certains cas, vous pouvez recevoir une erreur semblable à celle-ci: *L’autorisation EXECUTE a été refusée sur l’objet’fnCalculateDistance'* Dans ce cas, assurez-vous que la connexion que vous utilisez dispose des autorisations nécessaires pour exécuter des scripts et créer des objets sur la base de données, et pas seulement sur l’instance.
    > Vérifiez le schéma de l’objet, fnCalculateDistance. Si l’objet a été créé par le propriétaire de la base de données et que votre connexion appartient au rôle db_datareader, vous devez accorder à la connexion des autorisations explicites pour exécuter le script.

## <a name="comparing-r-functions-and-sql-functions"></a>Comparaison des fonctions R et des fonctions SQL

Vous vous souvenez de ce morceau de code utilisé pour le code R?

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

Vous pouvez essayer de l’utiliser avec l’exemple de fonction personnalisée SQL pour voir le temps que prend la transformation de données lors de l’appel d’une fonction SQL. Essayez également de basculer les contextes de calcul avec rxSetComputeContext et comparez les minutages.

Vos horaires peuvent varier considérablement, en fonction de la vitesse de votre réseau et de votre configuration matérielle. Dans les configurations que nous avons testées [!INCLUDE[tsql](../../includes/tsql-md.md)] , l’approche de la fonction était plus rapide que l’utilisation d’une fonction R personnalisée. Par conséquent, nous utilisons la [!INCLUDE[tsql](../../includes/tsql-md.md)] fonction pour ces calculs dans les étapes suivantes.

> [!TIP]
> Très souvent, l’ingénierie des [!INCLUDE[tsql](../../includes/tsql-md.md)] caractéristiques à l’aide de sera plus rapide que R. Par exemple, T-SQL comprend des fonctions de fenêtrage et de classement rapides qui peuvent être appliquées à des calculs de science des données courants, tels que des moyennes *mobiles et des*vignettes. Choisissez la méthode la plus efficace en fonction de vos données et de vos tâches.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer un modèle R et l’enregistrer dans SQL](walkthrough-build-and-save-the-model.md)

