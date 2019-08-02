---
title: Démarrage rapide à prédire du modèle à l’aide de R
description: Dans ce guide de démarrage rapide, Découvrez les notations à l’aide d’un modèle prédéfini dans les données R et SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4058725227deea1f6755c8e6272265ecdf91e59c
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714787"
---
# <a name="quickstart-predict-from-model-using-r-in-sql-server"></a>Démarrage rapide : Prédire du modèle à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, utilisez le modèle que vous avez créé dans le démarrage rapide précédent pour noter les prédictions par rapport aux nouvelles données. Pour effectuer un calcul de _score_ à l’aide de nouvelles données, récupérez l’un des modèles formés à partir de la table, puis appelez un nouvel ensemble de données sur lequel baser les prédictions. Le calcul de score est un terme parfois utilisé dans la science des données pour générer des prédictions, des probabilités ou d’autres valeurs en fonction de nouvelles données introduites dans un modèle formé.

## <a name="prerequisites"></a>Prérequis

Ce guide de démarrage rapide est une extension de la [création d’un modèle prédictif](quickstart-r-create-predictive-model.md).

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

À ce stade, `dbo.GLM_models` votre table peut contenir plusieurs modèles R, tous construits à l’aide de paramètres ou d’algorithmes différents, ou formés sur différents sous-ensembles de données.

Pour obtenir des prédictions basées sur un modèle spécifique, vous devez écrire un script SQL qui effectue les opérations suivantes:

1. Obtenir le modèle voulu
2. Obtenir les nouvelles données d’entrée
3. Appeler une fonction de prédiction R compatible avec ce modèle

Dans cet exemple, nous utiliserons le modèle nommé `default model`.

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

Le script ci-dessus effectue les étapes suivantes:

+ Utilisez une instruction SELECT pour obtenir un seul modèle de la table à passer comme paramètre d’entrée.

+ Après avoir récupéré le modèle de la table, appelez la fonction `unserialize` sur ce modèle.

+ Appliquez la fonction `predict` avec les arguments appropriés au modèle et fournissez les nouvelles données d’entrée.

+ Dans l’exemple, la `str` fonction est ajoutée au cours de la phase de test, pour vérifier le schéma des données retournées à partir de R. Vous pouvez supprimer l’instruction ultérieurement.

+ Les noms de colonne utilisés dans le script R ne sont pas nécessairement passés à la sortie de la procédure stockée. Nous avons ici utilisé la clause WITH RESULTs pour définir de nouveaux noms de colonnes.

**Résultats**

![Jeu de résultats pour la prédiction des properbility de transmission manuelle](./media/r-predict-am-resultset.png)

Il est également possible d’utiliser la [prédiction dans Transact-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) pour générer une valeur prédite ou un score basé sur un modèle stocké.

## <a name="next-steps"></a>Étapes suivantes

L’intégration de R avec SQL Server facilite le déploiement de solutions R à grande échelle, en exploitant les fonctionnalités les plus performantes de R et des bases de données relationnelles pour optimiser la gestion des données et accélérer le traitement analytique de R. 

Poursuivez vos connaissances sur les solutions en utilisant R avec SQL Server dans les scénarios de bout en bout créés par les équipes de développement de la science des données Microsoft et de R services.

> [!div class="nextstepaction"]
> [Didacticiels de SQL Server R](sql-server-r-tutorials.md)
