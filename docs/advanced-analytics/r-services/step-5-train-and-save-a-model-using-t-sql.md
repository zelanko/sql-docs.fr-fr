---
title: "&#201;tape 5 : Former et enregistrer un mod&#232;le &#224; l’aide de T-SQL (Didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
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
  - "TSQL"
ms.assetid: 3282e8ed-b515-4ed5-8543-fcef68629a92
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# &#201;tape 5 : Former et enregistrer un mod&#232;le &#224; l’aide de T-SQL (Didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es)
Dans cette étape, vous allez apprendre à former un modèle d’apprentissage automatique à l’aide de R. Les packages R étant déjà installés avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vous pouvez appeler l’algorithme à partir d’une procédure stockée. Vous allez former le modèle avec les caractéristiques de données que vous venez de créer, puis enregistrer le modèle formé dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Création d’un modèle R à l’aide de procédures stockées  
Tous les appels au runtime R installé avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sont effectués à l’aide de la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Toutefois, si vous devez reformer un modèle, il est probablement plus facile d’encapsuler l’appel à sp_execute_exernal_script dans une autre procédure stockée.  
  
Dans cette section, vous allez créer une procédure stockée qui peut être utilisée pour générer un modèle en utilisant les données que vous venez de préparer. Cette procédure stockée définit les données d’entrée et utilise un package R pour créer un modèle de régression logistique.  
  
#### Pour créer la procédure stockée  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une nouvelle fenêtre de requête et exécutez l’instruction suivante pour créer la procédure stockée _TrainTipPredictionModel_.  
  
    La procédure stockée contenant déjà une définition des données d’entrée, vous n’avez pas besoin de fournir de requête d’entrée.  
  
    ```  
    CREATE PROCEDURE [dbo].[TrainTipPredictionModel]  
  
    AS  
    BEGIN  
      DECLARE @inquery nvarchar(max) = N'  
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,   
        pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance  
        from nyctaxi_sample  
        tablesample (70 percent) repeatable (98052)  
    '  
      -- Insert the trained model into a database table  
      INSERT INTO nyc_taxi_models  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
  
    ## Create model  
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)  
    summary(logitObj)  
  
    ## Serialize model and put it in data frame  
    trained_model <- data.frame(model=as.raw(serialize(logitObj, NULL)));  
    ',  
                                      @input_data_1 = @inquery,  
                                      @output_data_1_name = N'trained_model'  
      ;  
  
    END  
    GO  
  
    ```  
  
    Cette procédure stockée exécute ces activités dans le cadre de la formation du modèle :  
  
    -   Pour que des données soient disponibles pour tester le modèle, 70 % des données sont sélectionnées aléatoirement à partir de la table de données sur les taxis.  
  
    -   La requête SELECT utilise la fonction scalaire personnalisée _fnCalculateDistance_ pour calculer la distance directe entre les points de prise en charge et de dépose.  Les résultats de la requête sont stockés dans la variable d’entrée R par défaut, `InputDataset`.  
  
    -   Le script R appelle la fonction `rxLogit`, qui est une des fonctions R améliorées incluses avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], pour créer le modèle de régression logistique.  
  
        La variable binaire _tipped_ est utilisée comme *étiquette* ou colonne de résultat, et le modèle est adapté à l’aide de ces colonnes de caractéristiques : _passenger_count_, _trip_distance_, _trip_time_in_secs_ et _direct_distance_.  
  
    -   Le modèle formé, enregistré dans la variable R `logitObj`, est sérialisé et placé dans une trame de données destinée à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette sortie est insérée dans la table de base de données _nyc_taxi_models_, afin que vous puissiez l’utiliser pour des prédictions.  
  
2.  Exécutez l’instruction pour créer la procédure stockée.  
  
#### Pour créer le modèle R à l’aide de la procédure stockée  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], exécutez cette instruction.  
  
    ```  
    EXEC TrainTipPredictionModel  
    ```  
  
    Le traitement des données et l’ajustement du modèle peuvent prendre un certain temps. Les messages éventuellement redirigés vers le flux **stdout** de R sont affichés dans la fenêtre **Messages** de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Par exemple :  
  
  
*Message(s) STDOUT provenant du script externe : Lignes lues : 1193025, Total de lignes traitées : 1193025, Durée totale du segment : 0.093 secondes*       
  
Des segments successifs de données sont lus et traités. Vous pouvez également voir des messages spécifiques à la fonction en question, `rxLogit`, qui indique la variable et les métriques de test.  
  
2.  Ouvrez la table *nyc_taxi_models*. Vous pouvez voir qu’une nouvelle ligne a été ajoutée, avec le modèle sérialisé dans la colonne _model_.  
  
  
  
*model*  
*0x580A00000002000302020....*  
  
À l’étape suivante, vous allez utiliser le modèle formé pour créer des prédictions.  
  
## Étape suivante  
[Étape 6 : Rendre le modèle opérationnel](../../advanced-analytics/r-services/step-6-operationalize-the-model-in-database-advanced-analytics-tutorial.md)  
  
## Étape précédente  
[Étape 4 : Créer des caractéristiques de données à l’aide de T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## Voir aussi  
[Analytique avancée en base de données pour les développeurs SQL &#40;Didacticiel&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
