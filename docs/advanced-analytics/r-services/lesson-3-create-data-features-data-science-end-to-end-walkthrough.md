---
title: "Le&#231;on 3 : Cr&#233;er des caract&#233;ristiques de donn&#233;es (proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 4981d4eb-0874-4fe9-82e1-edf99890e27a
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Le&#231;on 3 : Cr&#233;er des caract&#233;ristiques de donn&#233;es (proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es)
L’ingénierie des données est un autre aspect important de l’apprentissage automatique. Souvent, les données doivent être transformées avant de pouvoir être utilisées pour la modélisation prédictive. Si les données n’ont pas les caractéristiques dont vous avez besoin, vous pouvez les créer à partir de valeurs existantes.  
  
Pour cette tâche de modélisation, plutôt que d’utiliser les valeurs brutes de longitude et de latitude des lieux de prise en charge et de dépose, vous souhaitez avoir la distance en miles entre les deux emplacements. Pour créer cette caractéristique, vous devez calculer la distance directe linéaire entre deux points à l’aide de la [formule de haversine](https://en.wikipedia.org/wiki/Haversine_formula).  
Vous allez comparer deux différentes méthodes de création d’une caractéristique à partir des données :  
  
-   Utilisation de R et de la fonction `rxDataStep`    
-   Utilisation d’une fonction personnalisée dans [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
Pour les deux méthodes, le résultat du code est un objet de source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , `featureDataSource`, qui inclut la nouvelle caractéristique numérique, `direct_distance`.  
  
## <a name="creating-features-using-r"></a>Création de caractéristiques à l’aide de R  

Le langage R est connu pour ses bibliothèques statistiques riches et variées, mais vous devrez peut-être créer des transformations de données personnalisées. 

+ Vous allez créer une fonction R, `ComputeDist`, pour calculer la distance linéaire entre deux points spécifiés par les valeurs de latitude et de longitude.  
+ Vous appellerez la fonction pour transformer les données de l’objet de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créé précédemment, puis vous les enregistrerez dans une nouvelle source de données, `featureDataSource`.  

### <a name="create-the-transformation-function"></a>Créer la fonction de transformation  
1.  Créer une fonction R personnalisée, `ComputeDist`. Celle-ci prend deux paires de valeurs de latitude et de longitude, et calcule la distance linéaire entre elles.  La fonction retourne une distance en miles.
  
    ```R  
    env <- new.env()  
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
  
    + La première ligne définit un nouvel environnement. En R, un environnement peut être utilisé pour encapsuler des espaces de noms dans des packages et autres.
    + Vous pouvez utiliser la fonction `search()` pour afficher les environnements dans votre espace de travail. Pour afficher les objets dans un environnement spécifique, tapez `ls(<envname>)`. 
    + Les lignes commençant par `$env.ComputeDistance` contiennent le code qui définit la formule de haversine, qui calcule la *distance orthodromique* entre deux points sur une sphère.  
 
  
### <a name="apply-the-transformation-function-to-data"></a>Appliquer la fonction de transformation aux données

Ayant défini la fonction, vous allez l’appliquer aux données pour créer une colonne de caractéristique, *direct_distance*.

1. Créez une source de données à utiliser à l’aide du constructeur `RxSqlServerData`.  
  
    ```R  
    featureDataSource = RxSqlServerData(table = "features",   
       colClasses = c(pickup_longitude = "numeric", 
       pickup_latitude = "numeric",   
       dropoff_longitude = "numeric", 
       dropoff_latitude = "numeric",  
       passenger_count  = "numeric", 
       trip_distance  = "numeric",  
       trip_time_in_secs  = "numeric", 
       direct_distance  = "numeric"),  
      connectionString = connStr)  
    ```  
  
3.  Appelez la fonction `rxDataStep` pour appliquer la fonction `env$ComputeDist` aux données spécifiées.  
    
    ```R  
    start.time <- proc.time()  
  
    rxDataStep(inData = inDataSource, outFile = featureDataSource,  
         overwrite = TRUE,  
         varsToKeep=c("tipped", "fare_amount", passenger_count", "trip_time_in_secs", 
            "trip_distance", "pickup_datetime", "dropoff_datetime", "pickup_longitude",
            "pickup_latitude", "dropoff_longitude", "dropoff_latitude")
         , transforms = list(direct_distance=ComputeDist(pickup_longitude, 
            pickup_latitude, dropoff_longitude, dropoff_latitude)),
            transformEnvir = env, rowsPerRead=500, reportProgress = 3)  
  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))    
    ```  
  
    + La fonction `rxDataStep` peut modifier des données sur place. Les arguments incluent un vecteur de caractère des colonnes à traverser (*varsToKeep*) et une liste qui définit les transformations.
    + Les colonnes qui sont transformées sont générées automatiquement et n’ont donc pas besoin d’être incluses dans l’argument *varsToKeep* .
    + Vous pouvez également spécifier que toutes les colonnes de la source soient incluses à l’exception des variables spécifiées, à l’aide de l’argument *varsToDrop* .  
  
4.  Enfin, appelez `rxGetVarInfo` pour inspecter le schéma de la nouvelle source de données :  
  
    ```R  
    rxGetVarInfo(data = featureDataSource)  
    ```  
  
    *Résultats*
    
    *"It takes CPU Time=0.74 seconds, Elapsed Time=35.75 seconds to generate features."*  
    *Var 1: tipped, Type: integer*   
    *Var 2: fare_amount, Type: numeric*   
    *Var 3: passenger_count, Type: numeric*   
    *Var 4: trip_time_in_secs, Type: numeric*   
    *Var 5: trip_distance, Type: numeric*   
    *Var 6: pickup_datetime, Type: character*   
    *Var 7: dropoff_datetime, Type: character*   
    *Var 8: pickup_longitude, Type: numeric*   
    *Var 9: pickup_latitude, Type: numeric*   
    *Var 10: dropoff_longitude, Type: numeric*   
    *Var 11: dropoff_latitude, Type: numeric*   
    *Var 12: direct_distance, Type: numeric*   
  
## <a name="creating-features-using-transact-sql"></a>Création de caractéristiques à l’aide de Transact-SQL  
Maintenant que vous avez vu comment créer une caractéristique à l’aide d’une fonction R, vous allez créer une fonction SQL personnalisée, `ComputeDist`, pour faire la même chose. La fonction SQL `ComputeDist` opère sur un objet de données `RxSqlServerData` existant pour créer les caractéristiques de distance à partir des valeurs de longitude et de latitude existantes.  
  
Vous allez enregistrer les résultats de la transformation dans un objet de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , `featureDataSource`, comme vous l’avez fait à l’aide de R.  
  
Très souvent, l’ingénierie des caractéristiques à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] est plus rapide qu’en R. choisissez la méthode la plus efficace en fonction de vos données et de la tâche.  

### <a name="define-the-t-sql-custom-function"></a>Définir la fonction personnalisée T-SQL
  
1.  Définir une nouvelle fonction SQL, `fnCalculateDistance`  
  
    ```tsql  
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function calculates the direct distance between two geographical coordinates.  
    RETURNS float  
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

    + Le code de cette *fonction SQL définie par l’utilisateur* a été fourni dans le cadre du script PowerShell que vous avez exécuté pour créer et configurer la base de données.  La fonction doit déjà exister dans votre base de données.  Si elle n’existe pas, utilisez SQL Server Management Studio pour générer la fonction dans la même base de données que celle où sont stockées les données de taxi.

2.  Pour voir comment la fonction se comporte, utilisez l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante à partir de toute application prenant en charge [!INCLUDE[tsql](../../includes/tsql-md.md)].   
  
    ```tsql  
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,       
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,  
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude   
    FROM nyctaxi_sample  
  
    ```  
### <a name="call-the-sql-function-from-r"></a>Appeler la fonction SQL à partir de R

1. Enregistrez l’instruction SQL qui appelle la fonction personnalisée dans une variable R.  
  
    ```R  
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,  
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,  
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude  
        FROM nyctaxi_joined_1_percent  
        tablesample (1 percent) repeatable (98052)"    
    ```  
  
    > [!TIP] Cette requête est légèrement différente de la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] utilisée précédemment. Elle a été modifiée pour obtenir un plus petit échantillon de données, afin d’accélérer cette procédure pas à pas.  
  
4.  Maintenant, utilisez les lignes de code suivantes pour appeler la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] à partir de votre environnement R et l’appliquer aux données définies dans `featureEngineeringQuery`.  
  
    ```R  
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,  
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",           
             dropoff_longitude = "numeric", dropoff_latitude = "numeric",  
             passenger_count  = "numeric", trip_distance  = "numeric",  
              trip_time_in_secs  = "numeric", direct_distance  = "numeric"),  
      connectionString = connStr)  
    ```  
  
5.  Maintenant que la nouvelle caractéristique est créée, appelez `rxGetVarsInfo` pour créer un résumé de la table des caractéristiques.  
  
    ```R  
    rxGetVarInfo(data = featureDataSource)  
    ```  
  
## <a name="comparing-r-functions-and-sql-functions"></a>Comparaison des fonctions R et des fonctions SQL

En fait, pour cette tâche particulière, l’approche faisant appel à la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] est plus rapide que la fonction R personnalisée. Vous allez donc utiliser la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] pour ces calculs lors des étapes suivantes.  

Passez à la leçon suivante pour découvrir comment créer un modèle de prédiction à l’aide de ces données et enregistrer le modèle dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 4 : Créer et enregistrer le modèle &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Leçon précédente  
[Leçon 2 : Afficher et explorer les données &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
