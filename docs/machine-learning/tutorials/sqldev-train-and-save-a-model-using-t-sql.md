---
title: "Tutoriel R + T-SQL : Effectuer l'apprentissage du modèle"
description: Ce tutoriel explique comment entraîner, sérialiser et enregistrer un modèle R à l’aide des procédures stockées SQL Server et des fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ada26cbf8091b7e7b29e22378be5aa5f2b880314
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725234"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Leçon 3 : Entraîner et enregistrer un modèle à l’aide de T-SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Cet article fait partie d’un tutoriel pour développeurs SQL expliquant comment utiliser le langage R dans SQL Server.

Dans cette leçon, vous découvrirez comment entraîner un modèle Machine Learning à l’aide d’un script R. Vous entraînerez le modèle à l’aide des fonctionnalités de données que vous avez créées au cours de la leçon précédente, puis vous enregistrerez le modèle formé dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ici, vous pouvez tout effectuer à partir de SQL, car les packages R sont déjà installés avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

## <a name="create-the-stored-procedure"></a>Créer la procédure stockée

Lorsque vous appelez R à partir de T-SQL, vous utilisez la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Toutefois, si les processus sont souvent répétés, notamment pour entraîner à nouveau un modèle, il est plus facile d’encapsuler l’appel à sp_execute_exernal_script dans une autre procédure stockée.

1. Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une nouvelle fenêtre de **requête**.

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

    - Pour que des données soient disponibles pour le test du modèle, 70 % des données sont sélectionnées aléatoirement à des fins d’entraînement à partir de la table de données sur les taxis.

    - La requête SELECT utilise la fonction scalaire personnalisée *fnCalculateDistance* pour calculer la distance directe entre les points de prise en charge et de dépose. Les résultats de la requête sont stockés dans la variable d’entrée R par défaut, `InputDataset`.
  
    - Le script R appelle la fonction **rxLogit**, qui est l’une des fonctions R améliorées incluses avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], pour créer le modèle de régression logistique.
  
        La variable binaire _tipped_ est utilisée comme *étiquette* ou colonne de résultat, et le modèle est adapté à l’aide de ces colonnes de caractéristiques :  _passenger_count_, _trip_distance_, _trip_time_in_secs_et _direct_distance_.
  
    - Le modèle entraîné (enregistré dans la variable R `logitObj`) est sérialisé et retourné en tant que paramètre de sortie.

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>Entraîner et déployer le modèle R à l’aide de la procédure stockée

Étant donné que la procédure stockée contient déjà une définition des données d’entrée, vous n’avez pas besoin de fournir de requête d’entrée.

1. Pour entraîner et déployer le modèle R, appelez la procédure stockée et insérez-la dans la table de base de données _nyc_taxi_models_ afin de pouvoir l’utiliser pour de futures prédictions :

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. Consultez la fenêtre **Messages** de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour voir les messages éventuellement redirigés vers le flux **stdout** de R. Par exemple : 

    « Message(s) STDOUT provenant du script externe : Lignes lues : 1193025, Nombre total de lignes traitées : 1193025, durée totale de la segmentation : 0,093 seconde »

    Vous pouvez également voir des messages spécifiques à la fonction en question (`rxLogit`) indiquant la variable et les métriques de test générées lors de la création de modèle.

3.  Une fois l’instruction terminée, ouvrez la table *nyc_taxi_models*. Le traitement des données et l’ajustement du modèle peuvent prendre un certain temps.

    Vous pouvez voir qu’une nouvelle ligne a été ajoutée et que celle-ci contient le modèle sérialisé dans la colonne _model_ ainsi que le nom de modèle **RxTrainLogit_model** dans la colonne _name_.

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

À l’étape suivante, vous allez utiliser le modèle entraîné pour générer des prédictions.

## <a name="next-lesson"></a>Leçon suivante

[Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle R dans une procédure stockée](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 2 : Créer des fonctionnalités de données à l’aide de fonctions R et T-SQL](..//tutorials/sqldev-create-data-features-using-t-sql.md)

