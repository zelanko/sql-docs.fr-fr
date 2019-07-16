---
title: Guide de démarrage rapide pour prédire à partir du modèle à l’aide de R - SQL Server Machine Learning
description: Dans ce démarrage rapide, obtenir des informations sur la notation à l’aide d’un modèle prédéfini dans les données R et SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 00fdcb0c8c9c535645268a0212e52eef6f7c88f6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961993"
---
# <a name="quickstart-predict-from-model-using-r-in-sql-server"></a>Démarrage rapide : Prédire à partir du modèle à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce démarrage rapide, utilisez le modèle que vous avez créé dans le Guide de démarrage rapide précédent pour noter des prédictions sur les données actualisées. Pour effectuer _notation_ à l’aide de nouvelles données, obtenir un des modèles formés à partir de la table, puis appeler un nouveau jeu de données sur lequel baser vos prévisions. Notation terme est parfois utilisé dans la science des données pour désigner la génération des prédictions, de probabilités ou d’autres valeurs selon de nouvelles données sont chargées dans un modèle formé.

## <a name="prerequisites"></a>Prérequis

Ce démarrage rapide est une extension de [créer un modèle prédictif](quickstart-r-create-predictive-model.md).

## <a name="create-the-table-of-new-data"></a>Créer la table de nouvelles données

Tout d’abord, créez une table avec de nouvelles données. 

```sql
CREATE TABLE dbo.NewMTCars(
    hp INT NOT NULL
    , wt DECIMAL(10,3) NOT NULL
    , am INT NULL
)
GO

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (110, 2.634)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (72, 3.435)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (220, 5.220)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (120, 2.800)
GO
```

## <a name="predict-manual-transmission"></a>Prédire la transmission manuelle

À ce stade, votre `dbo.GLM_models` table peut contenir plusieurs modèles R, créés avec différents paramètres ou algorithmes, ou formés sur les différents sous-ensembles de données.

Pour obtenir des prédictions basées sur un modèle spécifique, vous devez écrire un script SQL qui effectue les opérations suivantes :

1. Obtenir le modèle voulu
2. Obtenir les nouvelles données d’entrée
3. Appeler une fonction de prédiction R compatible avec ce modèle

Dans cet exemple, nous allons utiliser le modèle nommé `default model`.

```sql
DECLARE @glmmodel varbinary(max) = 
    (SELECT model FROM dbo.GLM_models WHERE model_name = 'default model');

EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(glmmodel));
            new <- data.frame(NewMTCars);
            predicted.am <- predict(current_model, new, type = "response");
            str(predicted.am);
            OutputDataSet <- cbind(new, predicted.am);
            '
    , @input_data_1 = N'SELECT hp, wt FROM dbo.NewMTCars'
    , @input_data_1_name = N'NewMTCars'
    , @params = N'@glmmodel varbinary(max)'
    , @glmmodel = @glmmodel
WITH RESULT SETS ((new_hp INT, new_wt DECIMAL(10,3), predicted_am DECIMAL(10,3)));
```

Le script ci-dessus effectue les étapes suivantes :

+ Utilisez une instruction SELECT pour obtenir un seul modèle de la table à passer comme paramètre d’entrée.

+ Après avoir récupéré le modèle de la table, appelez la fonction `unserialize` sur ce modèle.

+ Appliquez la fonction `predict` avec les arguments appropriés au modèle et fournissez les nouvelles données d’entrée.

+ Dans l’exemple, le `str` fonction est ajoutée au cours de la phase de test, de vérifier le schéma de données est retournés à partir de R. Vous pouvez supprimer l’instruction ultérieurement.

+ Les noms de colonne utilisés dans le script R ne sont pas nécessairement transmises à la sortie de la procédure stockée. Ici, nous avons utilisé la clause WITH RESULTS pour définir des nouveaux noms de colonnes.

**Résultats**

![Jeu de résultats de prédiction properbility de transmission manuelle](./media/r-predict-am-resultset.png)

Il est également possible d’utiliser le [PREDICT dans Transact-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) pour générer une valeur prédite ou un score basé sur un modèle stocké.

## <a name="next-steps"></a>Étapes suivantes

L’intégration de R avec SQL Server facilite le déploiement de solutions R à grande échelle, en exploitant les fonctionnalités les plus performantes de R et des bases de données relationnelles pour optimiser la gestion des données et accélérer le traitement analytique de R. 

Continuer à découvrir des solutions à l’aide de R avec SQL Server dans des scénarios de bout en bout créés par les équipes de développement Microsoft Data Science et R Services.

> [!div class="nextstepaction"]
> [Didacticiels de SQL Server R](sql-server-r-tutorials.md)
