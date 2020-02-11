---
title: Créer des modèles basés sur une partition dans R
description: Apprenez à modéliser, à entraîner et à utiliser les données partitionnées créées dynamiquement lors de l’utilisation des fonctionnalités de modélisation basées sur les partitions de SQL Server Machine Learning.
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: tutorial
ms.author: davidph
author: dphansen
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ee5d6cbf9b1d5430e431cf04fb3b86ae7fb5743b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73726226"
---
# <a name="tutorial-create-partition-based-models-in-r-on-sql-server"></a>Tutoriel : Créer des modèles basés sur des partitions en R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans SQL Server 2019, la modélisation basée sur les partitions est la possibilité de créer et d’entraîner des modèles sur des données partitionnées. Pour les données stratifiées qui se segmentent naturellement dans un schéma de classification donné, telles que les régions géographiques, la date et l’heure, l’âge ou le sexe, vous pouvez exécuter un script sur l’ensemble du jeu de données, avec la possibilité de modéliser, d’entraîner et de noter les partitions qui restent intactes sur toutes ces opérations. 

La modélisation basée sur les partitions est activée via deux nouveaux paramètres sur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) :

+ **input_data_1_partition_by_columns**, qui indique par quelle colonne partitionner.
+ **input_data_1_order_by_columns**, qui indique par quelles colonnes trier. 

Dans ce tutoriel, découvrez la modélisation basée sur les partitions avec l’exemple de données NYC Taxi classique et le script R. La colonne de partition est le mode de paiement.

> [!div class="checklist"]
> * Les partitions sont basées sur les types de paiement (5).
> * Créez et entraînez des modèles sur chaque partition et stockez les objets dans la base de données.
> * Prédisez la probabilité des résultats des pourboires sur chaque modèle de partition à l’aide d’exemples de données réservés à cet effet.

## <a name="prerequisites"></a>Conditions préalables requises
 
Pour suivre ce tutoriel, vous devez disposer des éléments suivants :

+ Ressources système suffisantes. Le jeu de données est volumineux et les entraînements nécessitent beaucoup de ressources. Si possible, utilisez un système doté d’au moins 8 Go de RAM. Vous pouvez également utiliser des jeux de données plus petits pour contourner les contraintes de ressources. Les instructions pour réduire le jeu de données sont inline. 

+ Outil pour l’exécution de requêtes T-SQL, par exemple [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

+ [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak), que vous pouvez [télécharger et restaurer](demo-data-nyctaxi-in-sql.md) sur votre instance du moteur de base de données locale. La taille du fichier est d’environ 90 Mo.

+ Instance du moteur de base de données SQL Server 2019, avec intégration de Machine Learning Services et R.

Vérifiez la version en exécutant **`SELECT @@Version`** en tant que requête T-SQL dans un outil de requête.

Vérifiez la disponibilité des packages R en retournant une liste correctement mise en forme de tous les packages R actuellement installés avec votre instance du moteur de base de données :

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

## <a name="connect-to-the-database"></a>Se connecter à la base de données

Démarrez Management Studio et connectez-vous à l’instance du moteur de base de données. Dans l’Explorateur d’objets, vérifiez la présence de la base de données [NYCTaxi_Sample](demo-data-nyctaxi-in-sql.md). 

## <a name="create-calculatedistance"></a>Créer CalculateDistance

La base de données de démonstration est fournie avec une fonction scalaire pour le calcul de la distance, mais notre procédure stockée fonctionne mieux avec une fonction table. Exécutez le script suivant pour créer la fonction **CalculateDistance** utilisée plus tard dans l’[étape d’entraînement](#training-step).

Pour confirmer la création de la fonction, vérifiez \Programmability\Functions\Table-valued Functions sous la base de données **NYCTaxi_Sample** dans l’Explorateur d’objets.

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

## <a name="define-a-procedure-for-creating-and-training-per-partition-models"></a>Définir une procédure pour créer et entraîner des modèles par partition

Ce tutoriel inclut le script R dans une procédure stockée. Dans cette étape, vous allez créer une procédure stockée qui utilise R pour créer un jeu de données d’entrée, générer un modèle de classification pour prédire les résultats des pourboires, puis stocker le modèle dans la base de données.

Parmi les entrées de paramètre utilisées par ce script, vous verrez **input_data_1_partition_by_columns** et **input_data_1_order_by_columns**. Rappelez-vous que ces paramètres constituent le mécanisme par lequel la modélisation partitionnée se produit. Les paramètres sont passés comme entrées à [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) pour traiter les partitions avec le script externe qui s’exécute une fois pour chaque partition. 

Pour cette procédure stockée, [utilisez le parallélisme](#parallel) afin d’accélérer l’exécution.

Après avoir exécuté ce script, vous devriez voir **train_rxLogIt_per_partition** dans \Programmability\Stored Procedures sous la base de données **NYCTaxi_Sample** dans l’Explorateur d’objets. Vous devez également voir une nouvelle table utilisée pour le stockage des modèles : **dbo.nyctaxi_models**.

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

Notez que les entrées [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) incluent `@parallel=1`, utilisé pour activer le traitement parallèle. Contrairement aux versions précédentes, le paramétrage de `@parallel=1` dans SQL Server 2019 offre une meilleure indication à l’optimiseur de requête, ce qui fait de l’exécution parallèle un résultat bien plus probable.

Par défaut, l’optimiseur de requête a tendance à fonctionner sous `@parallel=1` sur des tables contenant plus de 256 lignes, mais si vous pouvez le gérer explicitement en définissant `@parallel=1` comme indiqué dans ce script.

> [!Tip]
> Pour les charges de travail d’entraînement, vous pouvez utiliser `@parallel` avec n’importe quel script d’entraînement arbitraire, même ceux qui utilisent des algorithmes non-Microsoft-rx. En règle générale, seuls les algorithmes RevoScaleR (avec le préfixe rx) offrent un parallélisme dans les scénarios d’entraînement dans SQL Server. Toutefois, avec le nouveau paramètre, vous pouvez paralléliser un script qui appelle des fonctions, dont des fonctions R open source, qui ne sont pas spécifiquement conçues avec cette fonctionnalité. Cela fonctionne parce que les partitions ont une affinité sur des threads spécifiques, de sorte que toutes les opérations appelées dans un script s’exécutent pour chaque partition, sur le `thread.`<a name="training-step"></a> donné

## <a name="run-the-procedure-and-train-the-model"></a>Exécuter la procédure et entraîner le modèle

Dans cette section, le script entraîne le modèle que vous avez créé et enregistré à l’étape précédente. Les exemples ci-dessous illustrent deux approches pour l’entraînement de votre modèle : l’utilisation d’un jeu de données entier ou de données partielles. 

Attendez-vous à ce que cette étape prenne un certain temps. L’entraînement est gourmand en ressources de calcul et prend beaucoup de minutes. Si les ressources système, en particulier la mémoire, sont insuffisantes pour la charge, utilisez un sous-ensemble des données. Le deuxième exemple fournit la syntaxe.

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
> Si vous exécutez d’autres charges de travail, vous pouvez ajouter `OPTION(MAXDOP 2)` à l’instruction SELECT si vous souhaitez limiter le traitement des requêtes à seulement 2 cœurs.

## <a name="check-results"></a>Vérifier les résultats

Le résultat de la table models doit afficher cinq modèles différents, basés sur cinq partitions segmentées par les cinq types de paiement. Les modèles se trouvent dans la source de données **ml_models**.

```sql
SELECT *
FROM ml_models
```
 
## <a name="define-a-procedure-for-predicting-outcomes"></a>Définir une procédure pour prédire les résultats

Vous pouvez utiliser les mêmes paramètres pour le scoring. L’exemple suivant contient un script R qui procède à l’évaluation à l’aide du modèle correct pour la partition qu’il traite actuellement.

Comme précédemment, créez une procédure stockée pour inclure votre code R.

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

## <a name="run-the-procedure-and-save-predictions"></a>Exécuter la procédure et enregistrer les prédictions

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

## <a name="view-predictions"></a>Afficher les prédictions

Étant donné que les prédictions sont stockées, vous pouvez exécuter une requête simple pour retourner un jeu de résultats.

```sql
SELECT *
FROM prediction_results;
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez utilisé [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) pour itérer des opérations sur des données partitionnées. Pour examiner de plus près l’appel de scripts externes dans des procédures stockées et l’utilisation de fonctions RevoScaleR, passez au tutoriel suivant.

> [!div class="nextstepaction"]
> [Procédure pas à pas pour R et SQL Server](walkthrough-data-science-end-to-end-walkthrough.md)

