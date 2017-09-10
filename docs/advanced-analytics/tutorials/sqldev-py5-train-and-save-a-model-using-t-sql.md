---
title: "Étape 5 : former et enregistrer un modèle à l’aide de T-SQL | Microsoft Docs"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- python-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 80a47819dfbb2e96162a49730e0dcf0b1b340f07
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="step-5-train-and-save-a-model-using-t-sql"></a>Étape 5 : L’apprentissage et enregistrez un modèle à l’aide de T-SQL

Dans cette étape, vous apprenez former un modèle d’apprentissage à l’aide des packages Python **scikit-en savoir plus** et **revoscalepy**. Ces bibliothèques Python sont déjà installés avec SQL Server Machine Learning Services, afin de pouvoir charger les modules et appeler les fonctions nécessaires à partir d’une procédure stockée. Vous allez former le modèle avec les caractéristiques de données que vous venez de créer, puis enregistrer le modèle formé dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Fractionner les exemples de données en jeux d’apprentissage et jeux de test

1. Exécutez les commandes T-SQL suivantes pour créer une procédure stockée qui divise les données dans le nyctaxi\_exemple de table en deux parties : nyctaxi\_exemple\_d’apprentissage et nyctaxi\_exemple\_test.

    ```SQL
    CREATE PROCEDURE [dbo].[TrainTestSplit] (@pct int)
    AS
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_training
    SELECT * into nyctaxi_sample_training FROM nyctaxi_sample WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) < @pct
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_testing
    SELECT * into nyctaxi_sample_testing FROM nyctaxi_sample
    WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) > @pct
    GO
    ```

2. Exécutez la procédure stockée et tapez un entier qui représente le pourcentage de données alloués au jeu d’apprentissage. Par exemple, l’instruction suivante affecte à 60 % des données au jeu d’apprentissage. Apprentissage et de test les données sont stockées dans deux tables distinctes.

    ```SQL
    EXEC TrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model-using-scikit-learn"></a>Générer un modèle de régression logistique à l’aide de scikit-en savoir plus

Dans cette section, vous créez une procédure stockée qui peut être utilisée pour effectuer l’apprentissage d’un modèle en utilisant les données d’apprentissage que vous venez de préparer. Cette procédure stockée définit les données d’entrée et utilise un **scikit-en savoir plus** fonction pour former un modèle de régression logistique. Vous appelez le runtime Python qui est installé avec SQL Server à l’aide de la procédure stockée système, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Pour faciliter le former à nouveau le modèle, vous pouvez encapsuler l’appel à sp_execute_exernal_script dans une autre procédure stockée et passer les nouvelles données d’apprentissage en tant que paramètre. Cette section vous guidera tout au long de ce processus.

1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une nouvelle **requête** fenêtre et exécutez l’instruction suivante pour créer la procédure stockée _TrainTipPredictionModelSciKitPy_.  Notez que la procédure stockée contient une définition des données d’entrée, vous n’avez pas besoin de fournir une requête d’entrée.

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelSciKitPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelSciKitPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
      EXEC sp_execute_external_script
      @language = N'Python',
      @script = N'
      import numpy
      import pickle
      import pandas
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

2. Exécutez ce qui suit les instructions SQL pour insérer le modèle formé dans la table nyc\_taxi_models.

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelSciKitPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Le traitement des données et l’ajustement du modèle peuvent prendre quelques minutes. Les messages qui sont redirigés vers Python **stdout** flux sont affichés dans le **Messages** fenêtre de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Exemple :

    *Messages STDOUT du script externe :*
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Ouvrez la table *nyc\_taxi_models*. Vous pouvez voir qu’une nouvelle ligne a été ajoutée, avec le modèle sérialisé dans la colonne _model_.

    *linear_model* *0x800363736B6C6561726E2E6C696E6561...*

## <a name="build-a-logistic-model-using-the-revoscalepy-package"></a>Créez un modèle logistique avec la _revoscalepy_ package

À présent, créez une autre procédure stockée qui utilise le nouveau **revoscalepy** package pour former un modèle de régression logistique. Le **revoscalepy** package Python contient des objets, transformation et algorithmes similaires à ceux fournis pour la langue de R **RevoScaleR** package. Avec cette bibliothèque, vous pouvez créer un contexte de calcul, déplacer des données entre les contextes de calcul, transforment des données et l’apprentissage des modèles prédictifs à l’aide d’algorithmes populaires tels que la régression logistique et linéaire, les arbres de décision et bien plus encore. Pour plus d’informations, consultez [What ' s revoscalepy ?](../python/what-is-revoscalepy.md)

1. Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une nouvelle **requête** fenêtre et exécutez l’instruction suivante pour créer la procédure stockée _TrainTipPredictionModelRxPy_.  Ce modèle utilise également les données d’apprentissage que vous venez de préparer. Étant donné que la procédure stockée contient déjà une définition des données d’entrée, vous n’avez pas besoin de fournir une requête d’entrée.

    ```SQL
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
    import pandas
    from revoscalepy.functions.RxLogit import rx_logit_ex
    
    ## Create a logistic regression model using rx_logit_ex function from revoscalepy package
    logitObj = rx_logit_ex("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
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

    Cette procédure stockée effectue les étapes suivantes dans le cadre de l’apprentissage du modèle :

    - L’apprentissage d’un modèle de régression logistique à l’aide de package de revoscalepy sur nyctaxi\_exemple\_données d’apprentissage.
    - La requête SELECT utilise la fonction scalaire personnalisée _fnCalculateDistance_ pour calculer la distance directe entre les points de prise en charge et de dépose. Les résultats de la requête sont stockés dans la variable d’entrée de Python par défaut, `InputDataset`.
    - Le script Python appelle la fonction de la revoscalepy LogisticRegression, qui est incluse avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], pour créer le modèle de régression logistique.
    - La variable binaire _tipped_ est utilisée comme *étiquette* ou colonne de résultat, et le modèle est adapté à l’aide de ces colonnes de caractéristiques :  _passenger_count_, _trip_distance_, _trip_time_in_secs_et _direct_distance_.
    - Le modèle formé, contenu dans la variable de Python `logitObj`, est sérialisée et put en tant que paramètre de sortie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Que la sortie est insérée dans la table de base de données _nyc_taxi_models_, ainsi que son nom, comme une nouvelle ligne, afin que vous pouvez récupérer et l’utiliser pour les prévisions.

2. Exécutez la procédure stockée comme suit pour insérer l’objet d’un apprentissage **revoscalepy** modèle dans la table _nyc\_taxi\_modèles.

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Le traitement des données et l’ajustement du modèle peuvent prendre un certain temps. Les messages qui sont redirigés vers Python **stdout** flux sont affichés dans le **Messages** fenêtre de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Exemple :

    *Messages STDOUT du script externe :*
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Ouvrez la table *nyc_taxi_models*. Vous pouvez voir qu’une nouvelle ligne a été ajoutée, avec le modèle sérialisé dans la colonne _model_.

    *rx_model* *0x8003637265766F7363616c...*

Dans l’étape suivante, vous utilisez les modèles formés pour créer des prédictions.

## <a name="next-step"></a>Étape suivante

[Étape 6 : Rendez le modèle opérationnel.](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Étape précédente

[Étape 4 : Créer des fonctionnalités de données à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

