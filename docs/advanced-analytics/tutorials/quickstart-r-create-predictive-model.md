---
title: Démarrage rapide pour créer un modèle prédictif à l’aide de R
description: Dans ce guide de démarrage rapide, Découvrez comment créer un modèle dans R à l’aide de SQL Server données pour tracer des prédictions.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 7de37b16c04cf2f972e36c11ba5dfb53721e6094
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469434"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Démarrage rapide : Créer un modèle prédictif à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous allez apprendre à former un modèle à l’aide de R, puis à enregistrer le modèle dans une table dans SQL Server. Le modèle est un modèle GLM (simple Generalized Linear) qui prédit la probabilité qu’un véhicule ait été équipé d’une transmission manuelle. Vous utiliserez le `mtcars` jeu de données fourni avec R.

## <a name="prerequisites"></a>Prérequis

Un démarrage rapide précédent, [Vérifiez que R existe dans SQL Server](quickstart-r-verify.md), fournit des informations et des liens pour configurer l’environnement r requis pour ce guide de démarrage rapide.

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

Ensuite, insérez les données de la build dans le `mtcars`jeu de données.

```SQL
INSERT INTO dbo.MTCars
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'MTCars <- mtcars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'MTCars';
```

+ Certaines personnes aiment utiliser des tables temporaires, mais sachez que certains clients R déconnectent les sessions entre les lots.

+ Le runtime R contient de nombreux datasets de tailles diverses. Pour obtenir la liste des datasets installées avec R, tapez `library(help="datasets")` à partir d’une invite de commandes R.

## <a name="create-a-model"></a>Créer un modèle

Les données de vitesse de la voiture contiennent deux colonnes, numériques,`hp`puissance () et`wt`poids (). À partir de ces données, vous allez créer un modèle GLM (generalize Linear model) qui estime la probabilité qu’un véhicule ait été équipé d’une transmission manuelle.

Pour générer le modèle, vous définissez la formule à l’intérieur de votre code R et vous transmettez les données en tant que paramètre d’entrée.

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

+ Le premier argument de `glm` est le paramètre de *formule* , qui `am` définit comme dépendant `hp + wt`de.
+ Les données d’entrée sont stockées dans la variable `MTCarsData`, qui est remplie par la requête SQL. Si vous n’attribuez pas de nom spécifique à vos données d’entrée, le nom par défaut de la variable est _InputDataSet_.

## <a name="create-a-table-for-the-model"></a>Créer une table pour le modèle

Ensuite, stockez le modèle afin de pouvoir le reformer ou l’utiliser pour la prédiction. La sortie d’un package R qui crée un modèle est généralement un **objet binaire**. Par conséquent, la table dans laquelle vous stockez le modèle doit fournir une colonne de type **varbinary (max)** .

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

Notez que si vous exécutez ce code une deuxième fois, vous recevez cette erreur:

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

Maintenant que vous avez un modèle, dans le dernier démarrage rapide, vous apprendrez à générer des prédictions à partir de celui-ci et à tracer les résultats.

> [!div class="nextstepaction"]
> [Démarrage rapide : Prédire et tracer à partir du modèle](quickstart-r-predict-from-model.md)