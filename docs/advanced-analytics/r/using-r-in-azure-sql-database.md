---
title: "À l’aide de R dans la base de données SQL Azure | Documents Microsoft"
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 8960f8a8c5dadaa0c53cd4fcb1ab786ce6e720a7
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="using-r-in-azure-sql-database"></a>À l’aide de R dans la base de données SQL Azure

En octobre 2017, l’équipe de développement SQL Server annoncé pour prendre en charge l’exécution de R code de bases de données à l’aide de procédures stockées, semblables à R Services dans SQL Server 2016. 

Pour maintenir à jour sur le calendrier de publication et les événements à venir, consultez le [de SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/) ou [blog Microsoft R Server](https://blogs.msdn.microsoft.com/rserver/).

> [!IMPORTANT]
> Actuellement, la version préliminaire de la prise en charge R est disponible dans la base de données SQL Azure dans l’ouest des États-Unis uniquement et fonctionnalités sont limitées par rapport aux fonctionnalités de R et d’exécution dans SQL Server 2016 ou 2017 de code Python.

## <a name="whats-included"></a>Ce qui est inclus

La fonctionnalité de R dans base de données peut être utilisée sur les niveaux de service de base de données suivantes et les niveaux de performance :
 
- Niveau de Service Premium : P1, P2, P4, P6, P11, P15
- Premium service Reporting Services niveau – PRS1, PRS2, PRS4, PRS6
- Pool élastique Premium – 125 Edtu ou supérieur
- Pool de RS élastique Premium – 125 Edtu ou supérieur

La version d’évaluation inclut ces packages :

+   Microsoft R Open R version 3.3.3
+   Fonctions et des packages R de base sont préinstallées
+   Microsoft R Server 9.2, en y compris le package RevoScaleR

Dans la version préliminaire actuelle, vous pouvez effectuer les tâches suivantes :

+ Apprentissage des modèles à l’aide de toutes les données qui tient dans la mémoire
+   Calculer les scores de modèles à l’aide de toutes les données qui tient dans la mémoire
+   Parallélisme trivial pour l’exécution du Script R (à l’aide de le @parallel paramètre dans sp_execute_external_script)
+   Diffusion en continu de l’exécution pour l’exécution du Script R (à l’aide de @r_RowsPerRead paramètre dans sp_execute_external_script)
+   Exécuter un script R unique à la fois


Les tâches suivantes ne sont pas pris en charge dans la version préliminaire de R sur la base de données SQL Azure :

+ Vous ne pouvez pas activer l’exécution du script R sur les bases de données spécifiques.
+ Vues de gestion dynamique pour l’analyse du processeur et utilisation de la mémoire de scripts R ne sont pas disponibles.
+ Aucun des packages tiers ne peuvent être installés. L’instruction de créer une bibliothèque externe n’est pas pris en charge.

## <a name="example"></a> Exemple

Dans la base de données SQL Azure, toutes les commandes de R sont exécutées à partir de T-SQL, à l’aide de la procédure stockée [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). 

L’exemple suivant montre comment tester la fonctionnalité d’aperçu, à l’aide de l’ensemble de données iris inclus avec r de base.

### <a name="step-1-create-the-data-tables"></a>Étape 1. Créer les tables de données

Commencez par créer deux tables : un pour stocker les données sources extraites à partir de R et l’autre pour stocker le modèle formé.

```sql
DROP TABLE IF EXISTS iris_data, iris_models;
GO
CREATE TABLE iris_data (
        id INT NOT NULL IDENTITY PRIMARY KEY
        , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
        , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
        , "Species" VARCHAR(100) NULL
);
CREATE TABLE iris_models (
    model_name VARCHAR(30) NOT NULL PRIMARY KEY,
    model VARBINARY(max) NOT NULL,
    native_model VARBINARY(MAX) NOT NULL
);
GO
```

### <a name="step-2-populate-table-with-data-from-the-iris-dataset"></a>Étape 2. Remplir la table avec des données à partir du dataset iris

Une fois que les tables ont été créées, exécutez le code suivant pour insérer des données d’apprentissage dans la table. La procédure stockée sp_execute_external_script appelle R et retourne le jeu de données iris sous la forme d’une trame de données, en utilisant le schéma spécifié dans l’instruction INSERT INTO.

```sql
INSERT INTO iris_data
("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
EXEC sp_execute_external_script @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

### <a name="step-3-create-the-stored-procedure-that-generates-the-model"></a>Étape 3. Créez la procédure stockée qui génère le modèle

La procédure stockée suivante effectue le travail de création et de formation du modèle, ce qui peut être enregistré dans un des deux formats binaires réellement.

```sql
CREATE PROCEDURE generate_iris_model
    @trained_model VARBINARY(MAX) OUTPUT, 
    @native_trained_model VARBINARY(MAX) OUTPUT
AS
BEGIN
  EXEC sp_execute_external_script @language = N'R'
  , @script = N'
    iris_model <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris_rx_data);
    trained_model <- as.raw(serialize(iris_model, connection=NULL));
    native_trained_model <- rxSerializeModel(iris_model, realtimeScoringOnly = TRUE)
    '
  , @input_data_1 = N'SELECT "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" FROM iris_data'
  , @input_data_1_name = N'iris_rx_data'
  , @params = N'@trained_model VARBINARY(MAX) OUTPUT, @native_trained_model VARBINARY(MAX) OUTPUT
    , @trained_model = @trained_model OUTPUT
    , @native_trained_model = @native_trained_model OUTPUT;
End
```

+ Le **sortie** mot clé dans les paramètres d’entrée indique que les valeurs doivent être transmises et utilisés pour la sortie, ainsi.
+ La ligne commençant par `iris_model` définit un modèle d’arbre de décision pour prédire espèces selon les attributs de fleur.
+ L’appel à `serialize` enregistre le modèle dans un format binaire adapté pour le stockage dans SQL Server. 
+ Avec les modèles basés sur les algorithmes de RevoScaleR, vous pouvez également utiliser le [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) fonction, qui enregistre le modèle dans un nouveau format binaire natif. Les modèles enregistrés dans ce format peuvent être chargées pour calculer les scores avec la fonction de prédiction dans SQL Server.

### <a name="step-4-train-and-save-the-model"></a>Étape 4. L’apprentissage et enregistrer le modèle

Après avoir créé la procédure stockée, appelez-la pour traiter les données d’entrée et de créer un modèle. Le code suivant enregistre également le modèle à la table **iris_models**, de sorte que vous pouvez l’utiliser ultérieurement pour prédire les espèces de fleur.

```sql
DECLARE @model VARBINARY(MAX), @native_modelVARBINARY(MAX);
EXEC generate_iris_model @model OUTPUT, @native_model OUTPUT;
DELETE FROM iris_models WHERE model_name = 'iris.dtree';
INSERT INTO iris_models (model_name, model, native_model) VALUES('iris.dtree', @model, @native_model);
SELECT model_name, datalength(model)/1024. AS model_size_kb, datalength(native_model)/1024. AS native_model_size_kb FROM iris_models;
GO
```

### <a name="step-5-create-a-stored-procedure-for-scoring"></a>Étape 5. Créer une procédure stockée pour calculer les scores

Ensuite, créez une procédure stockée pour calculer les scores. Cette procédure stockée charge un modèle spécifié à partir de la table et crée des scores en fonction des données d’entrée.

```sql
CREATE PROCEDURE predict_iris_species (@model varchar(100))
AS
BEGIN
  DECLARE @rx_model VARBINARY(MAX) = (SELECT model FROM iris_models WHERE model_name = @model);
  EXEC sp_execute_external_script @language = N'R'
  , @script = N'
    irismodel<-unserialize(rx_model);
    OutputDataSet <-rxPredict(irismodel, iris_rx_data, extraVarsToWrite = c("Species", "id"));
      '
  , @input_data_1 = N'SELECT "id", "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" FROM iris_data'
  , @input_data_1_name = N'iris_rx_data'
  , @params = N'@rx_model varbinary(max)'
  , @rx_model = @rx_model
  WITH RESULT SETS ( ("setosa_Pred" FLOAT, "versicolor_Pred" FLOAT, "virginica_Pred" FLOAT, "Species.Actual" VARCHAR(100), "id" INT));
END;
GO
```

Cette procédure stockée utilise le [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) (fonction), mais vous pourriez également utiliser la fonction PREDICT native dans T-SQL comme indiqué [ici](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/09/25/announcing-general-availability-of-native-scoring-using-predict-function-in-azure-sql-database/). Utilisation de la fonction PREDICT exige que vous utilisiez un [ **rx** modèle](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler) et enregistrer le modèle à l’aide de [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel).

### <a name="step-6-use-the-stored-procedure-to-generate-predictions"></a>Étape 6. Utilisez la procédure stockée pour générer des prédictions

Pour générer des scores à partir du modèle, exécutez la procédure stockée. Vous pouvez insérer les valeurs dans une table, ou les prédictions de retour à une application appelante.

```sql
EXEC predict_iris_species 'iris.dtree';
GO
```

## <a name="related-resources"></a>Ressources connexes

Azure Marketplace fournit également plusieurs machines virtuelles qui incluent SQL Server 2017 :

+ [Configurer un ordinateur virtuel pour l’apprentissage sur Azure](provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

Consultez également ces machines virtuelles, qui sont préconfigurées avec une variété d’outils d’apprentissage courants :

+ [Machine virtuelle pour la science des données](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview)
+ [Machine virtuelle de formation approfondie](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)

