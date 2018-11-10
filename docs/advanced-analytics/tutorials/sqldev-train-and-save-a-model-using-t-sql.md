---
title: Leçon 3 former et enregistrer un modèle à l’aide de R et T-SQL (SQL Server Machine Learning) | Microsoft Docs
description: Didacticiel expliquant comment incorporer R dans SQL Server des procédures stockées et fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 23387a6074f0c4a1dd6b4cb675b84f7aaced2a06
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033557"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Leçon 3 : Former et enregistrer un modèle à l’aide de T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie d’un didacticiel pour les développeurs SQL sur l’utilisation de R dans SQL Server.

Dans cette leçon, vous allez apprendre à former un modèle d’apprentissage automatique à l’aide de R. Vous allez former le modèle avec les fonctionnalités de données que vous avez créé dans la leçon précédente, puis enregistrez le modèle formé dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table. Dans ce cas, les packages R sont déjà installés avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], de sorte que toutes les opérations peuvent être effectuées à partir de SQL.

## <a name="create-the-stored-procedure"></a>Créer la procédure stockée

Lors de l’appel R à partir de T-SQL, vous utilisez la procédure stockée système, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Toutefois, pour les processus que vous répétez souvent, telles que de reformer un modèle, il est plus facile d’encapsuler l’appel à sp_execute_exernal_script dans une autre procédure stockée.

1. Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une nouvelle **requête** fenêtre.

2. Exécutez l’instruction suivante pour créer la procédure stockée **RxTrainLogitModel**. Cette procédure stockée définit les données d’entrée et utilise **rxLogit** de RevoScaleR pour créer un modèle de régression logistique.

    ```SQL
    CREATE PROCEDURE [dbo].[RxTrainLogitModel]
    
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

    -Pour vous assurer que des données sont restants pour tester le modèle, 70 % des données sont sélectionnées au hasard à partir de la table de données de taxi à des fins de formation.

    - La requête SELECT utilise la fonction scalaire personnalisée *fnCalculateDistance* pour calculer la distance directe entre les points de prise en charge et de dépose. les résultats de la requête sont stockés dans la variable d’entrée R par défaut, `InputDataset`.
  
    - Le script R appelle le **rxLogit** (fonction), qui est une des fonctions R améliorées incluses avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], pour créer le modèle de régression logistique.
  
        La variable binaire _tipped_ est utilisée comme *étiquette* ou colonne de résultat, et le modèle est adapté à l’aide de ces colonnes de caractéristiques :  _passenger_count_, _trip_distance_, _trip_time_in_secs_et _direct_distance_.
  
    -   Le modèle formé, enregistré dans la variable R `logitObj`, est sérialisé et placé dans une trame de données destinée à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette sortie est insérée dans la table de base de données _nyc_taxi_models_, afin que vous puissiez l’utiliser pour des prédictions.

## <a name="generate-the-r-model-using-the-stored-procedure"></a>Générer le modèle R à l’aide de la procédure stockée

Étant donné que la procédure stockée contenant déjà une définition des données d’entrée, vous n’avez pas besoin de fournir une requête d’entrée.

1. Pour générer le modèle R, appelez la procédure stockée sans tous les autres paramètres :

    ```SQL
    EXEC RxTrainLogitModel
    ```

2. Espion le **Messages** fenêtre de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour les messages éventuellement redirigés vers de R **stdout** flux, comme ce message : 

    « Message (s) STDOUT du script externe : lignes lues : 1193025, Total des lignes traitées : 1193025, durée totale du segment : 0.093 secondes »

    Vous pouvez également voir des messages spécifiques à la fonction en question, `rxLogit`, afficher les variables et de tester les mesures générées dans le cadre de la création de modèles.

3.  Une fois l’instruction terminée, ouvrez la table *nyc_taxi_models*. Traitement des données et l’ajustement du modèle peuvent prendre un certain temps.

    Vous pouvez voir qu’une nouvelle ligne a été ajoutée, avec le modèle sérialisé dans la colonne _model_.

    ```
    model
    ------
    0x580A00000002000302020....
    ```

Dans l’étape suivante, vous utiliserez le modèle formé pour générer des prédictions.

## <a name="next-lesson"></a>Leçon suivante

[Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle R dans une procédure stockée](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 2 : Créer des fonctionnalités de données à l’aide des fonctions R et T-SQL](..//tutorials/sqldev-create-data-features-using-t-sql.md)

