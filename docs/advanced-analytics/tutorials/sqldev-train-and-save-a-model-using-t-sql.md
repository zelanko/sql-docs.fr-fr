---
title: Leçon 3 former et enregistrer un modèle à l’aide de R et de T-SQL
description: Didacticiel expliquant comment former, sérialiser et enregistrer un modèle R à l’aide de SQL Server procédures stockées et de fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f23f4c350855b71a3633587bb3c092988fe89fef
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715333"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Leçon 3 : Former et enregistrer un modèle à l’aide de T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article fait partie d’un didacticiel pour les développeurs SQL sur l’utilisation de R dans SQL Server.

Dans cette leçon, vous allez apprendre à effectuer l’apprentissage d’un modèle de Machine Learning à l’aide de R. Vous allez effectuer l’apprentissage du modèle à l’aide des fonctionnalités de données que vous avez créées au cours de la leçon précédente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puis enregistrer le modèle formé dans une table. Dans ce cas, les packages R sont déjà installés avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], donc tout peut être effectué à partir de SQL.

## <a name="create-the-stored-procedure"></a>Créer la procédure stockée

Lors de l’appel de R à partir de T-SQL, vous utilisez la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Toutefois, pour les processus que vous répétez souvent, tels que la reformation d’un modèle, il est plus facile d’encapsuler l’appel à sp_execute_exernal_script dans une autre procédure stockée.

1. Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une nouvelle fenêtre de **requête** .

2. Exécutez l’instruction suivante pour créer la procédure stockée **RxTrainLogitModel**. Cette procédure stockée définit les données d’entrée et utilise **rxLogit** à partir de RevoScaleR pour créer un modèle de régression logistique.

    ```sql
    CREATE PROCEDURE [dbo].[RxTrainLogitModel] (@trained_model varbinary(max) OUTPUT)
    
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,
        pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
        from nyctaxi_sample
        tablesample (70 percent) repeatable (98052)
    '
    
      EXEC sp_execute_external_script @language = N'R',
                                      @script = N'
    ## Create model
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)
    summary(logitObj)
    
    ## Serialize model 
    trained_model <- as.raw(serialize(logitObj, NULL));
    ',
      @input_data_1 = @inquery,
      @params = N'@trained_model varbinary(max) OUTPUT',
      @trained_model = @trained_model OUTPUT; 
    END
    GO
    ```

    - Pour vous assurer que certaines données sont conservées pour tester le modèle, 70% des données sont sélectionnées aléatoirement dans la table de données de taxis à des fins de formation.

    - La requête SELECT utilise la fonction scalaire personnalisée *fnCalculateDistance* pour calculer la distance directe entre les points de prise en charge et de dépose. Les résultats de la requête sont stockés dans la variable d’entrée R par `InputDataset`défaut,.
  
    - Le script R appelle la fonction **rxLogit** , qui est l’une des fonctions R améliorées incluses [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]dans, pour créer le modèle de régression logistique.
  
        La variable binaire _tipped_ est utilisée comme *étiquette* ou colonne de résultat, et le modèle est adapté à l’aide de ces colonnes de caractéristiques :  _passenger_count_, _trip_distance_, _trip_time_in_secs_et _direct_distance_.
  
    - Le modèle formé, enregistré dans la variable `logitObj`R, est sérialisé et retourné en tant que paramètre de sortie.

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>Former et déployer le modèle R à l’aide de la procédure stockée

Étant donné que la procédure stockée contient déjà une définition des données d’entrée, vous n’avez pas besoin de fournir une requête d’entrée.

1. Pour effectuer l’apprentissage et le déploiement du modèle R, appelez la procédure stockée et insérez-la dans la table de base de données _nyc_taxi_models_, afin de pouvoir l’utiliser pour de futures prédictions:

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. Regardez la fenêtre **messages** de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour les messages qui seraient dirigés vers le flux **stdout** de R, par exemple ce message: 

    «Message (s) STDOUT à partir du script externe: Lignes lues: 1193025, nombre total de lignes traitées: 1193025, durée totale du segment: 0,093 secondes»

    Vous pouvez également voir des messages spécifiques à la fonction individuelle `rxLogit`,, en affichant les variables et les métriques de test générées dans le cadre de la création du modèle.

3.  Une fois l’instruction terminée, ouvrez la table *nyc_taxi_models*. Le traitement des données et l’ajustement du modèle peuvent prendre un certain temps.

    Vous pouvez voir qu’une nouvelle ligne a été ajoutée, qui contient le modèle sérialisé dans le _modèle_ de colonne et le nom de modèle **RxTrainLogit_model** dans le _nom_de la colonne.

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

À l’étape suivante, vous allez utiliser le modèle formé pour générer des prédictions.

## <a name="next-lesson"></a>Leçon suivante

[Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle R dans une procédure stockée](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 2 : Créer des fonctionnalités de données à l’aide des fonctions R et T-SQL](..//tutorials/sqldev-create-data-features-using-t-sql.md)

