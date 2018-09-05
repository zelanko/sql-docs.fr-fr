---
title: Notation native dans l’apprentissage de SQL Server | Microsoft Docs
description: Générer des prédictions à l’aide de la fonction de prédire le T-SQL, notation entrées dta par rapport à un modèle préentraîné écrites en R ou Python sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2f55962069c67fe7907968e024cdacb920b02d4e
ms.sourcegitcommit: 2a47e66cd6a05789827266f1efa5fea7ab2a84e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43348610"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Notation native à l’aide de la fonction de prédire le T-SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Notation native tire parti des fonctionnalités extension du C++ natives dans SQL Server 2017 pour générer des valeurs de prédiction ou *scores* pour les nouvelles entrées de données quasiment en temps réel. Cette méthodologie offre la vitesse de traitement plus rapide de prévision et prédiction des charges de travail, mais il est fourni avec les exigences de plate-forme et de la bibliothèque : seuls les fonctions RevoScaleR et revoscalepy ont des implémentations C++.

Notation native nécessite que vous disposez d’un modèle déjà formé. Dans SQL Server 2017 Windows ou Linux, ou dans la base de données SQL Azure, vous pouvez utiliser la fonction PREDICT dans Transact-SQL pour appeler la notation native. La fonction PREDICT prend un modèle préformé et génère les scores sur les entrées de données que vous fournissez.

## <a name="how-native-scoring-works"></a>Comment native notation fonctionne

Notation utilise native C++ bibliothèques natives à partir de Microsoft qui peut lire un modèle déjà formé, précédemment stockées dans un format binaire spécial ou enregistré sur le disque en tant que flux d’octets bruts et générer des scores pour nouvelles entrées de données que vous fournissez. Étant donné que le modèle est formé, publiées et stockées, il peut être utilisé pour calculer les scores sans avoir à appeler l’interpréteur R ou Python. Par conséquent, la surcharge de plusieurs des interactions de processus est réduite, ce qui entraîne des performances de prédiction beaucoup plus rapide dans les scénarios de production d’entreprise.

Pour utiliser la notation native, appelez la fonction T-SQL prédire et passer les entrées requises suivantes :

+ Un modèle compatible basé sur un algorithme pris en charge.
+ Données d’entrée, généralement définies comme une requête SQL.

La fonction renvoie des prédictions pour les données d’entrée, ainsi que toutes les colonnes de données source que vous souhaitez passer.

## <a name="prerequisites"></a>Prérequis

PRÉDIRE est disponible sur toutes les éditions du moteur de base de données SQL Server 2017 et activé par défaut, y compris SQL Server 2017 Machine Learning Services sur Windows, SQL Server 2017 (Windows), SQL Server 2017 (Linux) ou base de données SQL Azure. Vous n’avez pas besoin installer R, Python, ou activer des fonctionnalités supplémentaires.

+ Le modèle doit être formé à l’avance à l’aide d’une des prises en charge **rx** algorithmes répertoriés ci-dessous.

+ Sérialiser le modèle à l’aide [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) pour R, et [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour Python. Ces fonctions de sérialisation ont été optimisées pour prendre en charge rapide de notation.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Algorithmes pris en charge

+ modèles de revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) 
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) 
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) 
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) 

+ Modèles de RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Si vous avez besoin d’utiliser des modèles à partir de MicrosoftML ou microsoftml, utilisez [notation en temps réel avec sp_rxPredict](real-time-scoring.md).

Types de modèles non pris en charge sont les suivants :

+ Modèles contenant d’autres transformations
+ Modèles à l’aide de la `rxGlm` ou `rxNaiveBayes` algorithmes dans RevoScaleR ou revoscalepy équivalents
+ Modèles PMML
+ Modèles créés à l’aide d’autres bibliothèques open source ou tierces

## <a name="example-predict-t-sql"></a>Exemple : Prédire (T-SQL)

Dans cet exemple, vous créez un modèle et puis appelez la fonction de prédiction en temps réel à partir de T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Étape 1. Préparer et enregistrer le modèle

Exécutez le code suivant pour créer la base de données exemple et les tables requises.

```SQL
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

Utilisez l’instruction suivante pour remplir la table de données avec des données à partir de la **iris** jeu de données.

```SQL
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

Maintenant, créez une table pour stocker les modèles.

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Le code suivant crée un modèle basé sur le **iris** jeu de données et l’enregistre dans la table nommée **modèles**.

```SQL
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
> Veillez à utiliser le [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) fonction à partir de RevoScaleR pour enregistrer le modèle. Le standard de R `serialize` fonction ne peut pas générer le format requis.

Vous pouvez exécuter une instruction telle que la suivante pour afficher le modèle stocké au format binaire :

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Étape 2. Exécutez PREDICT sur le modèle

L’instruction PREDICT simple suivante obtient une classification du modèle d’arborescence de décision à l’aide du **notation native** (fonction). Il prévoit l’espèce iris en fonction des attributs fournis, la longueur des pétales et la largeur.

```SQL
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

Si vous obtenez l’erreur, « erreur s’est produite pendant l’exécution de la fonction PREDICT. Modèle est endommagé ou non valide », cela signifie généralement que votre requête n’a pas retourné d’un modèle. Vérifiez si vous avez correctement tapé le nom du modèle, ou si la table de modèles est vide.

> [!NOTE]
> Étant donné que les colonnes et les valeurs retournées par **PREDICT** peut varier selon le type de modèle, vous devez définir le schéma des données retournées à l’aide un **WITH** clause.

## <a name="next-steps"></a>Étapes suivantes

Pour une solution complète qui inclut la notation native, consultez ces exemples à partir de l’équipe de développement SQL Server :

+ Déployer votre script ML : [à l’aide d’un modèle Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Déployer votre script ML : [à l’aide d’un modèle R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)