---
title: Notation Native utilisant l’instruction T-SQL PREDICT
description: Générez des prédictions à l’aide de la fonction T-SQL PREDICT, en évaluant les entrées DTA par rapport à un modèle pré-formé écrit en R ou python sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f84b799fa901f7461f448683cceffe78e1dddfd3
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714949"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Notation native à l’aide de la fonction T-SQL PREDICT
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Le score natif utilise la fonction de prédiction [T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) et les fonctionnalités d’Extension natives C++ dans SQL Server 2017 pour générer des valeurs de prédiction ou des *scores* pour les nouvelles entrées de données en temps quasi-réel. Cette méthodologie offre la vitesse de traitement la plus rapide possible des prévisions et des charges de travail de prédiction, mais est fournie avec les exigences de la plateforme et C++ de la bibliothèque: seules les fonctions de RevoScaleR et revoscalepy ont des implémentations.

La notation Native nécessite que vous disposiez d’un modèle déjà formé. Dans 2017 SQL Server Windows ou Linux, ou dans Azure SQL Database, vous pouvez appeler la fonction PREDICT dans Transact-SQL pour appeler le score natif sur les nouvelles données que vous fournissez en tant que paramètre d’entrée. La fonction PREDICT retourne les scores sur les entrées de données que vous fournissez.

## <a name="how-native-scoring-works"></a>Fonctionnement de la notation Native

Le score natif utilise C++ des bibliothèques natives de Microsoft capables de lire un modèle déjà formé, précédemment stocké dans un format binaire spécial ou enregistré sur le disque en tant que flux d’octets bruts, et de générer des scores pour les nouvelles entrées de données que vous fournissez. Étant donné que le modèle est formé, publié et stocké, il peut être utilisé pour le calcul de score sans avoir à appeler l’interpréteur R ou python. Par conséquent, la surcharge liée à l’interaction de plusieurs processus est réduite, ce qui entraîne des performances de prédiction beaucoup plus rapides dans les scénarios de production d’entreprise.

Pour utiliser le score natif, appelez la fonction T-SQL PREDICT et transmettez les entrées requises suivantes:

+ Modèle compatible basé sur un algorithme pris en charge.
+ Données d’entrée, généralement définies en tant que requête SQL.

La fonction retourne des prédictions pour les données d’entrée, ainsi que toutes les colonnes de données sources que vous souhaitez transmettre.

## <a name="prerequisites"></a>Prérequis

PREDICT est disponible dans toutes les éditions du moteur de base de données SQL Server 2017 et activé par défaut, y compris SQL Server Machine Learning Services sur Windows, SQL Server 2017 (Windows), SQL Server 2017 (Linux) ou Azure SQL Database. Vous n’avez pas besoin d’installer R, Python ou d’activer des fonctionnalités supplémentaires.

+ Le modèle doit être formé à l’avance à l’aide de l’un des algorithmes **RX** pris en charge listés ci-dessous.

+ Sérialisez le modèle à l’aide de [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) pour R et [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour Python. Ces fonctions de sérialisation ont été optimisées pour prendre en charge la notation rapide.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Algorithmes pris en charge

+ modèles revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) 
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) 
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) 
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) 

+ Modèles RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Si vous devez utiliser des modèles à partir de MicrosoftML ou MicrosoftML, utilisez [le score en temps réel avec sp_rxPredict](real-time-scoring.md).

Les types de modèles non pris en charge sont les suivants:

+ Modèles contenant d’autres transformations
+ Modèles utilisant les `rxGlm` algorithmes ou `rxNaiveBayes` dans les équivalents de RevoScaleR ou revoscalepy
+ Modèles PMML
+ Modèles créés à l’aide d’autres bibliothèques Open source ou tierces

## <a name="example-predict-t-sql"></a>Exemple : PREDICT (T-SQL)

Dans cet exemple, vous créez un modèle, puis appelez la fonction de prédiction en temps réel à partir de T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Étape 1. Préparer et enregistrer le modèle

Exécutez le code suivant pour créer l’exemple de base de données et les tables requises.

```sql
CREATE DATABASE NativeScoringTest;
GO
USE NativeScoringTest;
GO
DROP TABLE IF EXISTS iris_rx_data;
GO
CREATE TABLE iris_rx_data (
  "Sepal.Length" float not null, "Sepal.Width" float not null
  , "Petal.Length" float not null, "Petal.Width" float not null
  , "Species" varchar(100) null
);
GO
```

Utilisez l’instruction suivante pour remplir la table de données avec les données du jeu de données **Iris** .

```sql
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

À présent, créez une table pour le stockage des modèles.

```sql
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Le code suivant crée un modèle basé sur le jeu de données **Iris** et l’enregistre dans latable nommée Models.

```sql
DECLARE @model varbinary(max);
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'
    iris.sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
    iris.dtree <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris[iris.sub, ])
    model <- rxSerializeModel(iris.dtree, realtimeScoringOnly = TRUE)
    '
  , @params = N'@model varbinary(max) OUTPUT'
  , @model = @model OUTPUT
  INSERT [dbo].[ml_models]([model_name], [model_version], [native_model_object])
  VALUES('iris.dtree','v1', @model) ;
```

> [!NOTE] 
> Veillez à utiliser la fonction [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) à partir de RevoScaleR pour enregistrer le modèle. La fonction R `serialize` standard ne peut pas générer le format requis.

Vous pouvez exécuter une instruction telle que la suivante pour afficher le modèle stocké au format binaire:

```sql
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Étape 2. Exécuter la prédiction sur le modèle

L’instruction PREDICT simple suivante obtient une classification du modèle d’arbre de décision à l’aide de la fonction de **notation Native** . Il prédit les espèces d’iris en fonction des attributs que vous fournissez, de la longueur et de la largeur des pétales.

```sql
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

Si vous recevez l’erreur «une erreur s’est produite lors de l’exécution de la fonction PREDICT. Le modèle est endommagé ou non valide. il signifie généralement que votre requête n’a pas retourné de modèle. Vérifiez si vous avez tapé correctement le nom du modèle ou si la table des modèles est vide.

> [!NOTE]
> Étant donné que les colonnes et les valeurs retournées par **Predict** peuvent varier selon le type de modèle, vous devez définir le schéma des données retournées à l’aide d’une clause **with** .

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir une solution complète incluant une notation native, consultez les exemples suivants de l’équipe de développement SQL Server:

+ Déployez votre script ML: [Utilisation d’un modèle python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Déployez votre script ML: [Utilisation d’un modèle R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)