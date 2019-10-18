---
title: Créer et évaluer un modèle prédictif dans R
titleSuffix: SQL Server Machine Learning Services
description: Créez un modèle prédictif simple dans R à l’aide de SQL Server Machine Learning Services, puis prédictionez un résultat à l’aide de nouvelles données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9acfe1e546c332801e9a5c1a7d97758053d9a0f4
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542125"
---
# <a name="quickstart-create-and-score-a-predictive-model-in-r-with-sql-server-machine-learning-services"></a>Démarrage rapide : créer et évaluer un modèle prédictif dans R avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous allez créer et effectuer l’apprentissage d’un modèle prédictif à l’aide de R, enregistrer le modèle dans une table de votre instance de SQL Server, puis utiliser le modèle pour prédire des valeurs à partir de nouvelles données à l’aide de [SQL Server machine learning services](../what-is-sql-server-machine-learning.md).

Vous allez créer et exécuter deux procédures stockées qui s’exécutent dans SQL. La première utilise le jeu de données **mtcars** inclus avec R et génère un modèle linéaire généralisé simple (GLM) qui prédit la probabilité qu’un véhicule ait été équipé d’une transmission manuelle. La deuxième procédure concerne la notation : elle appelle le modèle généré dans la première procédure pour générer un ensemble de prédictions en fonction de nouvelles données. En plaçant le code R dans une procédure stockée SQL, les opérations sont contenues dans SQL, sont réutilisables et peuvent être appelées par d’autres procédures stockées et applications clientes.

> [!TIP]
> Si vous avez besoin d’un actualisateur sur des modèles linéaires, essayez ce didacticiel qui décrit le processus d’ajustement d’un modèle à l’aide de rxLinMod : [modèles linéaires](/machine-learning-server/r/how-to-revoscaler-linear-model)

En suivant ce guide de démarrage rapide, vous apprendrez à :

> [!div class="checklist"]
> - Comment incorporer du code R dans une procédure stockée
> - Comment passer des entrées à votre code via des entrées sur la procédure stockée
> - Comment les procédures stockées sont utilisées pour rendre les modèles opérationnels

## <a name="prerequisites"></a>Conditions préalables requises

- Ce guide de démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) avec le langage R installé.

  Votre instance de SQL Server peut se trouver dans une machine virtuelle Azure ou en local. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que **SQL Server Launchpad service** est en cours d’exécution avant de commencer.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts R. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-the-model"></a>Créer le modèle

Pour créer le modèle, vous allez créer des données sources pour l’apprentissage, créer le modèle et le former à l’aide des données, puis stocker le modèle dans une base de données SQL où il peut être utilisé pour générer des prédictions avec de nouvelles données.

### <a name="create-the-source-data"></a>Créer la source de données

1. Ouvrez SSMS, connectez-vous à votre instance de SQL Server, puis ouvrez une nouvelle fenêtre de requête.

1. Créez une table pour enregistrer les données d’apprentissage.

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

1. Insérez les données à partir du DataSet intégré `mtcars`.

   ```SQL
   INSERT INTO dbo.MTCars
   EXEC sp_execute_external_script @language = N'R'
       , @script = N'MTCars <- mtcars;'
       , @input_data_1 = N''
       , @output_data_1_name = N'MTCars';
   ```

   > [!TIP]
   > Le runtime R contient de nombreux datasets de tailles diverses. Pour obtenir la liste des jeux de données installés avec R, tapez `library(help="datasets")` à partir d’une invite de commandes R.

### <a name="create-and-train-the-model"></a>Créer et effectuer l’apprentissage du modèle

Les données de vitesse de la voiture contiennent deux colonnes, numériques : puissance (`hp`) et poids (`wt`). À partir de ces données, vous allez créer un modèle GLM (generalize Linear model) qui estime la probabilité qu’un véhicule ait été équipé d’une transmission manuelle.

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

- Le premier argument de `glm` est le paramètre *Formula* , qui définit `am` comme dépendant de `hp + wt`.
- Les données d’entrée sont stockées dans la variable `MTCarsData`, qui est remplie par la requête SQL. Si vous n’attribuez pas de nom spécifique à vos données d’entrée, le nom par défaut de la variable est _InputDataSet_.

### <a name="store-the-model-in-the-sql-database"></a>Stocker le modèle dans la base de données SQL

Ensuite, stockez le modèle dans une base de données SQL afin de pouvoir l’utiliser à des fins de prédiction ou de reformation. 

1. Créez une table pour stocker le modèle.

   La sortie d’un package R qui crée un modèle est généralement un objet binaire. Par conséquent, la table dans laquelle vous stockez le modèle doit fournir une colonne de type **varbinary (max)** .

   ```sql
   CREATE TABLE GLM_models (
       model_name varchar(30) not null default('default model') primary key,
       model varbinary(max) not null
   );
   ```

1. Exécutez l’instruction Transact-SQL suivante pour appeler la procédure stockée, générer le modèle et l’enregistrer dans la table que vous avez créée.

   ```sql
   INSERT INTO GLM_models(model)
   EXEC generate_GLM;
   ```

   > [!TIP]
   > Si vous exécutez ce code une deuxième fois, vous recevez l’erreur suivante : «violation de la contrainte de clé primaire... Impossible d’insérer une clé en double dans l’objet dbo. stopping_distance_models ". Vous pouvez éviter cette erreur en mettant à jour le nom de chaque nouveau modèle. Par exemple, vous pouvez opter pour un nom plus descriptif en indiquant par exemple le type du modèle, le jour de sa création, etc.

     ```sql
     UPDATE GLM_models
     SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
     WHERE model_name = 'default model'
     ```

## <a name="score-new-data-using-the-trained-model"></a>Noter les nouvelles données à l’aide du modèle formé

Le *score* est un terme utilisé dans la science des données pour signifier la génération de prédictions, de probabilités ou d’autres valeurs basées sur les nouvelles données introduites dans un modèle formé. Vous utiliserez le modèle que vous avez créé dans la section précédente pour noter les prédictions sur les nouvelles données.

### <a name="create-a-table-of-new-data"></a>Créer une table de nouvelles données

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

### <a name="predict-manual-transmission"></a>Prédire la transmission manuelle

Pour obtenir des prédictions basées sur votre modèle, écrivez un script SQL qui effectue les opérations suivantes :

1. Obtenir le modèle voulu
1. Obtenir les nouvelles données d’entrée
1. Appeler une fonction de prédiction R compatible avec ce modèle

Au fil du temps, la table peut contenir plusieurs modèles R, tous construits à l’aide de différents paramètres ou algorithmes, ou formés sur différents sous-ensembles de données. Dans cet exemple, nous allons utiliser le modèle nommé `default model`.

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

- Utilisez une instruction SELECT pour obtenir un seul modèle de la table à passer comme paramètre d’entrée.

- Après avoir récupéré le modèle de la table, appelez la fonction `unserialize` sur ce modèle.

- Appliquez la fonction `predict` avec les arguments appropriés au modèle et fournissez les nouvelles données d’entrée.

> [!NOTE]
> Dans l’exemple, la fonction `str` est ajoutée au cours de la phase de test, afin de vérifier le schéma des données retournées à partir de R. Vous pouvez supprimer l’instruction ultérieurement.
>
> Les noms de colonne utilisés dans le script R ne sont pas nécessairement passés à la sortie de la procédure stockée. Ici, la clause WITH RESULTs est utilisée pour définir de nouveaux noms de colonnes.

**Résultats**

![Jeu de résultats pour la prédiction des properbility de transmission manuelle](./media/r-predict-am-resultset.png)

Il est également possible d’utiliser l’instruction [Predict (Transact-SQL)](../../t-sql/queries/predict-transact-sql.md) pour générer une valeur prédite ou un score basé sur un modèle stocké.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server Machine Learning Services, consultez :

- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
