---
title: Démarrage rapide pour créer un modèle prédictif à l’aide de R - SQL Server Machine Learning
description: Dans ce démarrage rapide, découvrez comment générer un modèle dans R à l’aide de données SQL Server pour tracer des prédictions.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: f1eaa39e5f22efbe7bea7a44ac2ce93a5e28205e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962036"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Démarrage rapide : Créer un modèle prédictif à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce démarrage rapide, vous allez apprendre à former un modèle à l’aide de R, puis enregistrez le modèle à une table dans SQL Server. Le modèle est un simple modèle linéaire généralisé (GLM) qui prédit la probabilité qu’un véhicule a été équipé d’une transmission manuelle. Vous utiliserez le `mtcars` dataset inclus avec R.

## <a name="prerequisites"></a>Prérequis

Un guide de démarrage rapide précédent, [R vérifier existe dans SQL Server](quickstart-r-verify.md), fournit des informations et des liens pour la configuration de l’environnement R requis pour ce démarrage rapide.

## <a name="create-the-source-data"></a>Créer la source de données

Dans un premier temps, créez une table pour enregistrer les données d’apprentissage.

```sql
CREATE TABLE dbo.MTCars(
    mpg decimal(10, 1) NOT NULL,
    cyl int NOT NULL,
    disp decimal(10, 1) NOT NULL,
    hp int NOT NULL,
    drat decimal(10, 2) NOT NULL,
    wt decimal(10, 3) NOT NULL,
    qsec decimal(10, 2) NOT NULL,
    vs int NOT NULL,
    am int NOT NULL,
    gear int NOT NULL,
    carb int NOT NULL
);
```

Ensuite, insérez les données de la build dans le jeu de données `mtcars`.

```SQL
INSERT INTO dbo.MTCars
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'MTCars <- mtcars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'MTCars';
```

+ Certaines personnes souhaitent utiliser des tables temporaires, mais n’oubliez pas que certains clients R déconnectent les sessions entre chaque lot.

+ Le runtime R contient de nombreux datasets de tailles diverses. Pour obtenir la liste des datasets installées avec R, tapez `library(help="datasets")` à partir d’une invite de commandes R.

## <a name="create-a-model"></a>Créer un modèle

Les données de vitesse de voiture contiennent deux colonnes, toutes deux numériques, la puissance (`hp`) et le poids (`wt`). À partir de ces données, vous allez créer un modèle linéaire généralisé (GLM) qui estime la probabilité qu’un véhicule a été équipé d’une transmission manuelle.

Pour générer le modèle, vous définissez la formule à l’intérieur de votre code R et passez les données comme paramètre d’entrée.

```sql
DROP PROCEDURE IF EXISTS generate_GLM;
GO
CREATE PROCEDURE generate_GLM
AS
BEGIN
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'carsModel <- glm(formula = am ~ hp + wt, data = MTCarsData, family = binomial);
        trained_model <- data.frame(payload = as.raw(serialize(carsModel, connection=NULL)));'
    , @input_data_1 = N'SELECT hp, wt, am FROM MTCars'
    , @input_data_1_name = N'MTCarsData'
    , @output_data_1_name = N'trained_model'
    WITH RESULT SETS ((model VARBINARY(max)));
END;
GO
```

+ Le premier argument de `glm` est la *formule* paramètre, qui définit `am` comme dépendantes de `hp + wt`.
+ Les données d’entrée sont stockées dans la variable `MTCarsData`, qui est remplie par la requête SQL. Si vous n’attribuez pas de nom spécifique à vos données d’entrée, le nom par défaut de la variable est _InputDataSet_.

## <a name="create-a-table-for-the-model"></a>Créer une table pour le modèle

Ensuite, stockez le modèle afin de reformer ou utiliser pour la prédiction. La sortie d’un package R qui crée un modèle est généralement un **objet binaire**. Par conséquent, la table où vous stockez le modèle doit contenir une colonne de **varbinary (max)** type.

```sql
CREATE TABLE GLM_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
```

## <a name="save-the-model"></a>Enregistrer le modèle

Pour enregistrer le modèle, exécutez l’instruction Transact-SQL suivante de façon à appeler la procédure stockée, à générer le modèle, puis à l’enregistrer dans une table.

```sql
INSERT INTO GLM_models(model)
EXEC generate_GLM;
```

Notez que si vous exécutez ce code une deuxième fois, vous obtenez cette erreur :

```sql
Violation of PRIMARY KEY constraint...Cannot insert duplicate key in object dbo.stopping_distance_models
```

Vous pouvez éviter cette erreur en mettant à jour le nom de chaque nouveau modèle. Par exemple, vous pouvez opter pour un nom plus descriptif en indiquant par exemple le type du modèle, le jour de sa création, etc.

```sql
UPDATE GLM_models
SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
WHERE model_name = 'default model'
```

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez un modèle, dans le dernier démarrage rapide, vous allez apprendre à générer des prédictions à partir de celui-ci et représenter graphiquement les résultats.

> [!div class="nextstepaction"]
> [Démarrage rapide : Prédire et tracer à partir du modèle](quickstart-r-predict-from-model.md)