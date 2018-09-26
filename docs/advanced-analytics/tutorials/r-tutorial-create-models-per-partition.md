---
title: Didacticiel sur la création, formation et évaluation des modèles en fonction de partition dans R (SQL Server Machine Learning Services) | Microsoft Docs
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: tutorial
ms.author: heidist
author: HeidiSteen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 51fd17b10ed2fde9d8412c6c47f868458edf7d5c
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715297"
---
# <a name="tutorial-create-partition-based-models-in-r-on-sql-server"></a>Didacticiel : Créer des modèles basés sur une partition dans R sur SQL Server
[!INCLUDE[appliesto-ssvnex-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dans SQL Server 2019, en fonction de partition de modélisation est la possibilité de créer et former des modèles sur des données partitionnées. Pour les données stratifiées segmente naturellement dans un schéma de donnée de classification - tel que les régions géographiques, date et heure, âge ou sexe - vous pouvez exécuter les script sur l’ensemble de données, avec la possibilité de modéliser, former et noter sur les partitions qui restent intactes sur toutes ces opérations. 

En fonction de partition de modélisation est activée via deux nouveaux paramètres sur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql):

+ **input_data_1_partition_by_columns**, qui spécifie une colonne à la partition par.
+ **input_data_1_order_by_columns** spécifie les colonnes à la clause order by. 

Dans ce didacticiel, découvrez basé sur partition de modélisation à l’aide des données taxi NYC classiques et un script R. La colonne de partition est la méthode de paiement.

> [!div class="checklist"]
> * Partition basée sur une colonne payment_type. Valeurs dans ces données de segment de colonne, une seule partition pour chaque type de paiement.
> * Créer et former des modèles sur chaque partition et stocker les objets dans la base de données.
> * Prédire la probabilité des résultats de l’info-bulle sur chaque modèle de partition, à l’aide d’exemples de données réservés à cet effet.

## <a name="prerequisites"></a>Prérequis
 
Pour suivre ce didacticiel, vous devez disposer des éléments suivants :

+ Instance du moteur de base de données SQL Server 2019 avec Machine Learning Services et la fonctionnalité R
+ Exemples de données
+ Un outil pour l’exécution de requête T-SQL, tels que SQL Server Management Studio

### <a name="system-resources"></a>Ressources système

Le jeu de données est volumineux et les opérations d’apprentissage sont gourmandes en ressources. Si possible, utilisez un système ayant au moins 8 Go de RAM. Ou bien, vous pouvez utiliser les petits jeux de données à contourner les contraintes de ressources. Instructions pour réduire le jeu de données sont en ligne. 

### <a name="sql-server-database-engine-with-machine-learning-services"></a>Moteur de base de données SQL Server avec Machine Learning Services

2019 CTP de SQL Server 2.0 ou version ultérieur, avec Machine Learning Services installé et configuré, est requis. Vous pouvez vérifier la version du serveur dans Management Studio en exécutant `SELECT @@Version` comme une requête T-SQL. Sortie doit être « Microsoft SQL Server 2019 (CTP 2.0) - 15.0.x ».

### <a name="r-packages"></a>Packages R

Ce didacticiel utilise R installé avec les Services Machine Learning. Vous pouvez vérifier l’installation de R en renvoyant une liste correctement mise en forme de tous les packages R sont actuellement installés avec votre instance du moteur de base de données :

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

### <a name="tools-for-query-execution"></a>Outils pour l’exécution des requêtes

Vous pouvez [télécharger et installer SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms), ou utilisez n’importe quel outil qui se connecte à une base de données relationnelle et exécute le script T-SQL. Assurez-vous que vous pouvez vous connecter à une instance du moteur de base de données qui a des Services Machine Learning.

### <a name="sample-data"></a>Exemples de données

Les données proviennent du [NYC Taxi et Limousines Commission](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml) jeu de données public. 

+ Téléchargez le [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak ) fichier de sauvegarde de base de données et restaurez-la sur l’instance du moteur de base de données.

Le nom de fichier de base de données doit être **NYCTaxi_sample** si vous souhaitez exécuter les scripts suivants sans modification.

## <a name="connect-to-the-database"></a>Se connecter à la base de données

Démarrez Management Studio et connectez-vous à l’instance du moteur de base de données. Dans l’Explorateur d’objets, vérifiez le [NYCTaxi_Sample de base de données](sqldev-download-the-sample-data.md) existe. 

## <a name="create-calculatedistance"></a>Créer CalculateDistance

La base de données de démonstration est fourni avec une fonction scalaire pour le calcul de distance, mais notre procédure stockée de fonctionne mieux avec une fonction table. Exécutez le script suivant pour créer le **CalculateDistance** fonction utilisée dans le [étape d’apprentissage](#training-step) par la suite.

Pour confirmer la fonction a été créée, examinez les fonctions \Programmability\Functions\Table-valued sous le **NYCTaxi_Sample** base de données dans l’Explorateur d’objets.

```sql
USE NYCTaxi_sample
GO

SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE FUNCTION [dbo].[CalculateDistance] (
    @Lat1 FLOAT
    ,@Long1 FLOAT
    ,@Lat2 FLOAT
    ,@Long2 FLOAT
    )
    -- User-defined function calculates the direct distance between two geographical coordinates.
RETURNS TABLE
AS
RETURN

SELECT COALESCE(3958.75 * ATAN(SQRT(1 - POWER(t.distance, 2)) / nullif(t.distance, 0)), 0) AS direct_distance
FROM (
    VALUES (CAST((SIN(@Lat1 / 57.2958) * SIN(@Lat2 / 57.2958)) + (COS(@Lat1 / 57.2958) * COS(@Lat2 / 57.2958) * COS((@Long2 / 57.2958) - (@Long1 / 57.2958))) AS DECIMAL(28, 10)))
    ) AS t(distance)
GO
 ```

## <a name="define-a-procedure-for-creating-and-training-per-partition-models"></a>Définir une procédure de création et l’apprentissage des modèles par partition

Ce didacticiel inclut dans un wrapper de script R dans une procédure stockée. Dans cette étape, vous créez une procédure stockée qui utilise R pour créer un jeu de données d’entrée, de générer un modèle de classification pour prévoir les résultats de l’info-bulle, puis stocke le modèle dans la base de données.

Parmi les entrées de paramètre utilisées par ce script, vous verrez **input_data_1_partition_by_columns** et **input_data_1_order_by_columns**. Rappelez-vous que ces paramètres sont le mécanisme par lequel partitionnée modélisation se produit. Les paramètres sont passés en tant qu’entrées pour [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) pour traiter les partitions avec le script externe exécutant une fois pour chaque partition. 

Pour cette procédure stockée, [utiliser le parallélisme](#parallel) pour raccourcir les délais de saisie semi-automatique.

Après avoir exécuté ce script, vous devez voir **train_rxLogIt_per_partition** dans les procédures \Programmability\Stored sous le **NYCTaxi_Sample** base de données dans l’Explorateur d’objets. Vous devriez également voir une nouvelle table utilisée pour stocker des modèles : **dbo.nyctaxi_models**.

```sql
USE NYCTaxi_Sample
GO

CREATE
    OR

ALTER PROCEDURE [dbo].[train_rxLogIt_per_partition] (@input_query NVARCHAR(max))
AS
BEGIN
    DECLARE @start DATETIME2 = SYSDATETIME()
        ,@model_generation_duration FLOAT
        ,@model VARBINARY(max)
        ,@instance_name NVARCHAR(100) = @@SERVERNAME
        ,@database_name NVARCHAR(128) = db_name();

    EXEC sp_execute_external_script @language = N'R'
        ,@script = 
        N'
    
    # Make sure InputDataSet is not empty. In parallel mode, if one thread gets zero data, an error occurs
    if (nrow(InputDataSet) > 0) {
    # Define the connection string
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    
    # build classification model to predict a tip outcome
    duration <- system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet))[3];

    # First, serialize a model to and put it into a database table
    modelbin <- as.raw(serialize(logitObj, NULL));

    # Create the data source. To reduce data size, add rowsPerRead=500000 to cut the dataset by half.
    ds <- RxOdbcData(table="ml_models", connectionString=connStr);

    # Store the model in the database
    model_name <- paste0("nyctaxi.", InputDataSet[1,]$payment_type);
    
    rxWriteObject(ds, model_name, modelbin, version = "v1",
    keyName = "model_name", valueName = "model_object", versionName = "model_version", overwrite = TRUE, serialize = FALSE);
    } 
    
    '
        ,@input_data_1 = @input_query
        ,@input_data_1_partition_by_columns = N'payment_type'
        ,@input_data_1_order_by_columns = N'passenger_count'
        ,@parallel = 1
        ,@params = N'@instance_name nvarchar(100), @database_name nvarchar(128)'
        ,@instance_name = @instance_name
        ,@database_name = @database_name
    WITH RESULT SETS NONE
END;
GO
```

<a name="parallel"></a>

### <a name="parallel-execution"></a>Exécution parallèle

Notez que le [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) incluent des entrées  **@parallel= 1**, utilisé pour permettre un traitement parallèle. Contrairement aux versions antérieures, dans SQL Server 2019, paramètre  **@parallel= 1** fournit une indication plus forte à l’optimiseur de requête, rendre l’exécution en parallèle un résultat beaucoup plus probable.

Par défaut, l’optimiseur de requête a tendance à fonctionner sous  **@parallel= 1** sur les tables ayant des lignes plus de 256, mais si vous pouvez gérer cela explicitement en définissant  **@parallel= 1** comme indiqué dans cette script.

> [!Tip]
> Pour workoads de formation, vous pouvez utiliser **@parallel** avec n’importe quel script arbitraire de formation, même ceux qui utilisent des algorithmes de non-Microsoft-rx. En règle générale, uniquement des algorithmes RevoScaleR (avec le préfixe rx) offrent le parallélisme dans les scénarios de formation dans SQL Server. Mais avec le nouveau paramètre, vous pouvez paralléliser un script qui appelle des fonctions, y compris les fonctions R open source, qui ne sont pas spécifiquement conçues avec cette fonctionnalité. Cela fonctionne, car les partitions ont une affinité à des threads spécifiques, afin que toutes les opérations appelées dans un script exécutent sur une base par partition, sur le thread donné.

<a name="training-step"></a>

## <a name="run-the-procedure-and-train-the-model"></a>Exécuter la procédure et l’apprentissage du modèle

Dans cette section, le script effectue l’apprentissage du modèle que vous avez créé et enregistré à l’étape précédente. Les exemples suivants illustrent deux approches pour l’apprentissage votre modèle : à l’aide d’un ensemble de données ou des données partielles. 

Attendre cette étape pour prendre un certain temps. L’apprentissage est exigeant en ressources, en prenant le nombre de minutes pour terminer. Si les ressources système, en particulier la mémoire, sont insuffisantes pour la charge, utiliser un sous-ensemble des données. Le deuxième exemple fournit la syntaxe.

```sql
--Example 1: train on entire dataset
EXEC train_rxLogIt_per_partition N'
SELECT payment_type, tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance
  FROM dbo.nyctaxi_sample CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d
';
GO
```

```sql
--Example 2: Train on 20 percent of the dataset to expedite processing.
EXEC train_rxLogIt_per_partition N'
  SELECT tipped, payment_type, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance
  FROM dbo.nyctaxi_sample TABLESAMPLE (20 PERCENT) REPEATABLE (98074)
  CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d
';
GO
```

> [!NOTE]
> Si d’autres charges de travail sont en cours d’exécution, vous pouvez ajouter `OPTION(MAXDOP 2)` à l’instruction SELECT si vous souhaitez limiter le traitement de requête à seulement 2 cœurs.

## <a name="check-results"></a>Résultats de la vérification

Le résultat de la table de modèles doit être cinq modèles différents, selon les cinq partitions segmentées par les types de paiement de cinq. Modèles se trouvent dans le **ml_models** source de données.

```sql
SELECT *
FROM ml_models
```
 
## <a name="define-a-procedure-for-predicting-outcomes"></a>Définir une procédure pour prévoir les résultats

Vous pouvez utiliser les mêmes paramètres pour calculer les scores. L’exemple suivant contient un script R qui évalue à l’aide du modèle approprié pour la partition, qu'il est en cours de traitement.

Comme auparavant, créer une procédure stockée pour encapsuler votre code R.

```sql
USE NYCTaxi_Sample
GO

-- Stored procedure that scores per partition. 
-- Depending on the partition being processed, a model specific to that partition will be used
CREATE
    OR

ALTER PROCEDURE [dbo].[predict_per_partition]
AS
BEGIN
    DECLARE @predict_duration FLOAT
        ,@instance_name NVARCHAR(100) = @@SERVERNAME
        ,@database_name NVARCHAR(128) = db_name()
        ,@input_query NVARCHAR(max);

    SET @input_query = 'SELECT tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance, payment_type
                          FROM dbo.nyctaxi_sample TABLESAMPLE (1 PERCENT) REPEATABLE (98074)
                          CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d'

    EXEC sp_execute_external_script @language = N'R'
        ,@script = 
        N'
    
    if (nrow(InputDataSet) > 0) {

    #Get the partition that is currently being processed
    current_partition <- InputDataSet[1,]$payment_type;

    #Create the SQL query to select the right model
    query_getModel <- paste0("select model_object from ml_models where model_name = ", "''", "nyctaxi.",InputDataSet[1,]$payment_type,"''", ";")
    

    # Define the connection string
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
        
    #Define data source to use for getting the model
    ds <- RxOdbcData(sqlQuery = query_getModel, connectionString = connStr)

    # Load the model
    modelbin <- rxReadObject(ds, deserialize = FALSE)
    # unserialize model
    logitObj <- unserialize(modelbin);

    # predict tipped or not based on model
    predictions <- rxPredict(logitObj, data = InputDataSet, overwrite = TRUE, type = "response", writeModelVars = TRUE
        , extraVarsToWrite = c("payment_type"));        
    OutputDataSet <- predictions
    
    } else {
        OutputDataSet <- data.frame(integer(), InputDataSet[,]);        
    }
    '
        ,@input_data_1 = @input_query
        ,@parallel = 1
        ,@input_data_1_partition_by_columns = N'payment_type'
        ,@params = N'@instance_name nvarchar(100), @database_name nvarchar(128)'
        ,@instance_name = @instance_name
        ,@database_name = @database_name
    WITH RESULT SETS((
                tipped_Pred INT
                ,payment_type VARCHAR(5)
                ,tipped INT
                ,passenger_count INT
                ,trip_distance FLOAT
                ,trip_time_in_secs INT
                ,direct_distance FLOAT
                ));
END;
GO
```

## <a name="create-a-table-to-store-predictions"></a>Créer une table pour stocker des prédictions

```sql
CREATE TABLE prediction_results (
    tipped_Pred INT
    ,payment_type VARCHAR(5)
    ,tipped INT
    ,passenger_count INT
    ,trip_distance FLOAT
    ,trip_time_in_secs INT
    ,direct_distance FLOAT
    );

TRUNCATE TABLE prediction_results
GO
```

## <a name="run-the-procedure-and-save-predictions"></a>Exécuter la procédure et enregistrer des prédictions

```sql
INSERT INTO prediction_results (
    tipped_Pred
    ,payment_type
    ,tipped
    ,passenger_count
    ,trip_distance
    ,trip_time_in_secs
    ,direct_distance
    )
EXECUTE [predict_per_partition]
GO
```

## <a name="view-predictions"></a>Prédictions de vue

Étant donné que les prédictions sont stockées, vous pouvez exécuter une requête simple pour retourner un jeu de résultats.

```sql
SELECT *
FROM prediction_results;
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez utilisé [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) d’itérer les opérations sur les données partitionnées. Avant pour examiner l’appel de scripts externes dans les procédures stockées et à l’aide des fonctions RevoScaleR, passez au tutoriel suivant.

> [!div class="nextstepaction"]
> [procédure pas à pas pour R et SQL Server](walkthrough-data-science-end-to-end-walkthrough.md)

<!--
## Old intro

**(Not for production workloads)**

One of the more common approaches for executing R or Python code on SQL data is providing script as an input parameter to the [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) stored procedure. In this CTP release, SQL Server 2019 adds new parameters to `sp_execute_external_script` to process partitions with the external script executing once for every partition:

| Parameter | Usage |
|-----------|-------|
| **input_data_1_partition_by_columns** | Specifies which columns to partition by. |
| **input_data_1_order_by_columns** | Specifies which columns to order by.  |

Partitions are an organizational mechanism for stratified data that naturally segments into a given classification scheme. Common examples include partitioning by geographic region, by date and time, by age or gender, and so forth. Given the existence of partitioned data, you might want to execute script over the entire data set, with the ability to model, train, and score partitions that remain intact over all these operations. Calling `sp_execute_external_script` with the new parameters allows you to do just that.

You can run this operation in parallel by combining `partition_by` with `@parallel`. If the input query can be parallelized, set `@parallel=1` as part of your arguments to `sp_execute_external_script`. By default, the query optimizer operates under `@parallel=1` on tables having more than 256 rows.

When the scenario is training, one advantage is that any arbitrary training script, even those using non-Microsoft-rx algorithms, can be parallelized by also using the @parallel parameter. Typically, you would have to use RevoScaleR algorithms (with the rx prefix) to obtain parallelism in training scenarios in SQL Server. But with the new parameter, you can parallelize a script that calls functions not specifically engineered with that capability.
-->
