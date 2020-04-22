---
title: Scoring natif à l’aide de la fonction T-SQL PREDICT
description: Générez des prédictions à l’aide de PREDICT, une fonction T-SQL utilisée pour le scoring des entrées de données par rapport à un modèle préentraîné écrit en R ou Python sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6bc7dfadecfe24d5bd91b7dd12eaa3b68ef01753
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487688"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Scoring natif à l’aide de la fonction T-SQL PREDICT
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Le scoring natif utilise la [fonction T-SQL PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) et les fonctionnalités des extensions C++ natives dans SQL Server 2017 pour générer des valeurs de prédiction ou des *scores* pour les nouvelles entrées de données en quasi temps réel. Cette méthodologie offre la vitesse de traitement la plus rapide possible pour les charges de travail de prévision et de prédiction, mais elle s’accompagne d’exigences en matière de plateforme et de bibliothèque : seules les fonctions de RevoScaleR et de revoscalepy ont des implémentations en C++.

Le scoring natif nécessite un modèle déjà entraîné. Dans SQL Server 2017 sur Windows ou sur Linux, vous pouvez appeler la fonction PREDICT dans Transact-SQL pour appeler le scoring natif sur les nouvelles données que vous fournissez en tant que paramètre d’entrée. La fonction PREDICT retourne des scores pour les entrées de données que vous fournissez.

## <a name="how-native-scoring-works"></a>Fonctionnement du scoring natif

Le scoring natif utilise les bibliothèques C++ natives de Microsoft capables de lire un modèle déjà entraîné, précédemment stocké dans un format binaire spécial ou enregistré sur un disque sous la forme d’un flux d’octets bruts, et de générer des scores pour les nouvelles entrées de données que vous fournissez. Le modèle étant entraîné, publié et stocké, vous pouvez l’utiliser pour le scoring sans avoir à appeler l’interpréteur R ou Python. La surcharge liée aux interactions de plusieurs processus s’en trouve donc réduite, ce qui accroît significativement les performances de prédiction dans les scénarios de production en entreprise.

Pour utiliser le scoring natif, appelez la fonction T-SQL PREDICT et passez les entrées obligatoires suivantes :

+ Modèle compatible basé sur un algorithme pris en charge.
+ Données d’entrée, généralement définies en tant que requête SQL.

La fonction retourne des prédictions pour les données d’entrée ainsi que toutes les colonnes de données sources que vous souhaitez passer.

## <a name="prerequisites"></a>Prérequis

PREDICT est disponible et activé par défaut dans toutes les éditions du moteur de base de données SQL Server 2017 et versions ultérieures, y compris dans SQL Server Machine Learning Services sur Windows, SQL Server 2017 et versions ultérieures sur Windows et Linux. Vous n’avez pas besoin d’installer R ou Python ni d’activer des fonctionnalités supplémentaires.

+ Le modèle doit être entraîné à l’avance à l’aide de l’un des algorithmes **rx** pris en charge listés ci-dessous.

+ Sérialisez le modèle avec [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) pour R et [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour Python. Ces fonctions de sérialisation ont été optimisées pour prendre en charge le scoring rapide.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Algorithmes pris en charge

+ Modèles revoscalepy

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

Si vous devez utiliser des modèles de MicrosoftML ou microsoftml, utilisez le [scoring en temps réel avec sp_rxPredict](real-time-scoring.md).

Parmi les types de modèles non pris en charge, citons les suivants :

+ Modèles contenant d’autres transformations
+ Modèles utilisant les algorithmes `rxGlm` ou `rxNaiveBayes` dans les équivalents RevoScaleR ou revoscalepy
+ Modèles PMML
+ Modèles créés à l’aide d’autres bibliothèques open source ou tierces

## <a name="example-predict-t-sql"></a>Exemple : PREDICT (T-SQL)

Dans cet exemple, vous créez un modèle, puis appelez la fonction de prédiction en temps réel à partir de T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Étape 1. Préparer et enregistrer le modèle

Exécutez le code suivant pour créer l’exemple de base de données et les tables obligatoires.

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

Utilisez l’instruction suivante pour remplir la table de données avec les données du jeu de données **iris**.

```sql
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

Créez à présent une table pour stocker les modèles.

```sql
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Le code suivant crée un modèle basé sur le jeu de données **iris** et l’enregistre dans la table nommée **models**.

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
> Veillez à utiliser la fonction [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) de RevoScaleR pour enregistrer le modèle. La fonction R `serialize` standard ne peut pas générer le format demandé.

Vous pouvez exécuter une instruction telle que la suivante pour afficher le modèle stocké au format binaire :

```sql
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Étape 2. Exécuter PREDICT sur le modèle

L’instruction PREDICT simple suivante obtient une classification à partir du modèle d’arbre de décision à l’aide de la fonction de **scoring natif**. Elle prédit les espèces d’iris en fonction des attributs que vous fournissez (longueur et largeur des pétales).

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

Le message « Une erreur s’est produite lors de l’exécution de la fonction PREDICT. Le modèle est endommagé ou non valide. » signifie généralement que votre requête n’a pas retourné de modèle. Vérifiez que vous avez correctement tapé le nom du modèle ou que la table des modèles n’est pas vide.

> [!NOTE]
> Les colonnes et les valeurs retournées par **PREDICT** pouvant varier selon le type de modèle, vous devez définir le schéma des données retournées à l’aide d’une clause **WITH**.

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir une solution complète intégrant le scoring natif, consultez les exemples suivants proposés par l’équipe de développement SQL Server :

+ Déployer votre script ML : [Utilisation d’un modèle Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Déployer votre script ML : [Utilisation d’un modèle R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)