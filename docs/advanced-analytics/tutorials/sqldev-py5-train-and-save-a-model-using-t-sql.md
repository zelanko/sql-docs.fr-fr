---
title: Former et enregistrer un modèle Python à l’aide de T-SQL
description: Didacticiel python expliquant comment former et enregistrer un modèle à l’aide de Transact-SQL sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 470d7be0e1777d029f406e183aad644359c82f13
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005995"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>Former et enregistrer un modèle Python à l’aide de T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article fait partie d’un didacticiel, [l’analytique Python en base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md). 

Dans cette étape, vous allez apprendre à former un modèle de Machine Learning à l’aide des packages python **scikit-Learn** et **revoscalepy**. Ces bibliothèques Python sont déjà installées avec SQL Server Machine Learning Services.

Vous chargez les modules et appelez les fonctions nécessaires pour créer et effectuer l’apprentissage du modèle à l’aide d’une procédure stockée SQL Server. Le modèle nécessite les fonctionnalités de données que vous avez développées dans les leçons précédentes. Enfin, vous enregistrez le modèle formé dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Fractionner les exemples de données en jeux d’apprentissage et jeux de test

1. Créez une procédure stockée appelée **PyTrainTestSplit** pour diviser les données de la table nyctaxi_sample en deux parties : nyctaxi_sample_training et nyctaxi_sample_testing. 

    Cette procédure stockée doit déjà être créée pour vous, mais vous pouvez exécuter le code suivant pour la créer :

    ```sql
    DROP PROCEDURE IF EXISTS PyTrainTestSplit;
    GO

    CREATE PROCEDURE [dbo].[PyTrainTestSplit] (@pct int)
    AS
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_training
    SELECT * into nyctaxi_sample_training FROM nyctaxi_sample WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) < @pct
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_testing
    SELECT * into nyctaxi_sample_testing FROM nyctaxi_sample
    WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) > @pct
    GO
    ```

2. Pour diviser vos données à l’aide d’un fractionnement personnalisé, exécutez la procédure stockée et tapez un entier qui représente le pourcentage de données allouées au jeu d’apprentissage. Par exemple, l’instruction suivante alloue 60% des données au jeu d’apprentissage.

    ```sql
    EXEC PyTrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Créer un modèle de régression logistique

Une fois les données préparées, vous pouvez les utiliser pour effectuer l’apprentissage d’un modèle. Pour ce faire, vous devez appeler une procédure stockée qui exécute du code Python, en prenant comme entrée la table de données d’apprentissage. Pour ce didacticiel, vous créez deux modèles, à la fois les modèles de classification binaire :

+ La procédure stockée **PyTrainScikit** crée un modèle de prédiction Tip à l’aide du package **scikit-Learn** .
+ La procédure stockée **TrainTipPredictionModelRxPy** crée un modèle de prédiction Tip à l’aide du package **revoscalepy** .

Chaque procédure stockée utilise les données d’entrée que vous fournissez pour créer et effectuer l’apprentissage d’un modèle de régression logistique. Tout le code Python est encapsulé dans la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Pour faciliter la reformation du modèle sur les nouvelles données, vous encapsulez l’appel à sp_execute_external_script dans une autre procédure stockée et transmettez les nouvelles données d’apprentissage en tant que paramètre. Cette section va vous guider tout au long de ce processus.

### <a name="pytrainscikit"></a>PyTrainScikit

1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une nouvelle fenêtre de **requête** et exécutez l’instruction suivante pour créer la procédure stockée **PyTrainScikit**.  La procédure stockée contient une définition des données d’entrée. vous n’avez donc pas besoin de fournir une requête d’entrée.

    ```sql
    DROP PROCEDURE IF EXISTS PyTrainScikit;
    GO

    CREATE PROCEDURE [dbo].[PyTrainScikit] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    from sklearn.linear_model import LogisticRegression
    
    ##Create SciKit-Learn logistic regression model
    X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
    y = numpy.ravel(InputDataSet[["tipped"]])
    
    SKLalgo = LogisticRegression()
    logitObj = SKLalgo.fit(X, y)
    
    ##Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    GO
    ```

2. Exécutez les instructions SQL suivantes pour insérer le modèle formé dans la table New-no__t-0taxi_models.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC PyTrainScikit @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Le traitement des données et l’ajustement du modèle peuvent prendre quelques minutes. Les messages qui seraient dirigés vers le flux **stdout** de Python s’affichent dans la fenêtre **messages** de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Exemple :

    *Message (s) stdout provenant du script externe :* 
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Ouvrez le tableau *no__t-1taxi_models*. Vous pouvez voir qu’une nouvelle ligne a été ajoutée, avec le modèle sérialisé dans la colonne _model_.

    *SciKit_model* *0x800363736B6C6561726E2E6C696E6561..* .

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

Cette procédure stockée utilise le nouveau package **revoscalepy** , qui est un nouveau package pour Python. Il contient des objets, des transformations et des algorithmes similaires à ceux fournis pour le package **RevoScaleR** du langage R. 

En utilisant **revoscalepy**, vous pouvez créer des contextes de calcul distants, déplacer des données entre des contextes de calcul, transformer des données et former des modèles prédictifs à l’aide d’algorithmes populaires tels que la régression logistique et linéaire, les arbres de décision, etc. Pour plus d’informations, consultez [module revoscalepy dans SQL Server](../python/ref-py-revoscalepy.md) et [référence des fonctions revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

1. Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une nouvelle fenêtre de **requête** et exécutez l’instruction suivante pour créer la procédure stockée _TrainTipPredictionModelRxPy_.  Étant donné que la procédure stockée contient déjà une définition des données d’entrée, vous n’avez pas besoin de fournir une requête d’entrée.

    ```sql
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    from revoscalepy.functions.RxLogit import rx_logit
    
    ## Create a logistic regression model using rx_logit function from revoscalepy package
    logitObj = rx_logit("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    GO
    ```

    Cette procédure stockée effectue les étapes suivantes dans le cadre de la formation du modèle :

    - La requête SELECT applique la fonction scalaire personnalisée _fnCalculateDistance_ pour calculer la distance directe entre les emplacements de sélection et de dépose. Les résultats de la requête sont stockés dans la variable d’entrée python par défaut, `InputDataset`.
    - La variable binaire _bonhommed_ est utilisée comme colonne d' *étiquette* ou de résultat, et le modèle est adapté à l’aide des colonnes de fonctionnalités suivantes : _passenger_count_, _trip_distance_, _trip_time_in_secs_et _direct_distance_.
    - Le modèle formé est sérialisé et stocké dans la variable python `logitObj`. En ajoutant le résultat du mot clé T-SQL, vous pouvez ajouter la variable en tant que sortie de la procédure stockée. À l’étape suivante, cette variable est utilisée pour insérer le code binaire du modèle dans une table de base de données _nyc_taxi_models_. Ce mécanisme facilite le stockage et la réutilisation des modèles.

2. Exécutez la procédure stockée comme suit pour insérer le modèle **revoscalepy** formé dans la table *nyc_taxi_models*.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Le traitement des données et l’ajustement du modèle peuvent prendre un certain temps. Les messages qui seraient dirigés vers le flux **stdout** de Python s’affichent dans la fenêtre **messages** de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Exemple :

    *Message (s) stdout provenant du script externe :* 
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Ouvrez la table *nyc_taxi_models*. Vous pouvez voir qu’une nouvelle ligne a été ajoutée, avec le modèle sérialisé dans la colonne _model_.

    *revoscalepy_model* *0x8003637265766F7363616c..* .

À l’étape suivante, vous utiliserez les modèles formés pour créer des prédictions.

## <a name="next-step"></a>Étape suivante

[Exécuter des prédictions à l’aide de Python Embedded dans une procédure stockée](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Étape précédente

[Créer des caractéristiques de données à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
