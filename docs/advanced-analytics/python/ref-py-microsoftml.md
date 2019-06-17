---
title: package microsoftml Python - SQL Server Machine Learning Services
description: Présente les algorithmes d’apprentissage Microsoft et d’un modèle pour Python, associées aux charges de travail de SQL Server machine learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 618c4b127c42aae6a5b8d7570f1962f8c8e38e9a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642360"
---
# <a name="microsoftml-python-module-in-sql-server"></a>microsoftml (module Python dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**microsoftml** est un module Python35 compatible de Microsoft en fournissant des algorithmes d’apprentissage automatique hautes performances. Il inclut des fonctions pour l’apprentissage et transformations, notation, analyse de texte et image et l’extraction des caractéristiques pour dériver les valeurs de données existantes.

La machine learning API ont été développées par Microsoft pour les applications d’apprentissage automatique interne et ont été affinées au fil des années pour prendre en charge des performances élevées sur les big data, à l’aide de traitement multicœur et le streaming rapide des données. Ce package d’origine comme équivalent d’une version de R, Python [MicrosoftML](../r/ref-r-microsoftml.md), qui a des fonctions similaires. 

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le **microsoftml** library est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même, si vous obtenez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont les mêmes, [documentation pour les fonctions individuelles microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) est publié dans un seul emplacement sous la [référence Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour Microsoft Machine Learning Server. Doivent tout propres au produit comportements existent, les différences sont notées dans la page d’aide (fonction).

## <a name="versions-and-platforms"></a>Versions et plateformes

Le **microsoftml** module est en fonction de Python 3.5 et disponible uniquement lorsque vous installez un des produits Microsoft ou des téléchargements suivants :

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Bibliothèques de client Python pour un client de science des données](setup-python-client-tools-sql.md)

> [!NOTE]
> Les versions de produit complet sont Windows uniquement, en commençant par SQL Server 2017. Prise en charge de Linux pour **microsoftml** est une nouveauté de [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Dépendances de package

Algorithmes dans **microsoftml** dépendent [revoscalepy](ref-py-revoscalepy.md) pour :

+ Objets de source de données. Les données utilisées par **microsoftml** fonctions sont créées à l’aide de **revoscalepy** fonctions.
+ Distant computing (exécution de fonction évolution vers une instance distante de SQL Server). Le **revoscalepy** bibliothèque fournit des fonctions pour la création et l’activation à distance de contexte pour SQL server de calcul.

Dans la plupart des cas, vous allez charger les packages ensemble chaque fois que vous utilisez **microsoftml**.

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous donner une idée de l’utilisation de chacun d’eux. Vous pouvez également utiliser le [table des matières](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-training-functions"></a>Fonctions de 1-formation

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Former un ensemble de modèles. |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Forêts aléatoires. |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Modèle linéaire. avec stochastique Ascent coordonnée double. |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Arbres augmentés. |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Régression logistique. |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Réseau neuronal. |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Détection des anomalies. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>Fonctions de transformation de 2

### <a name="categorical-variable-handling"></a>Gestion des variables catégorielles

| Fonction | Description |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Convertit une colonne de texte en catégories. |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Hache et convertit une colonne de texte en catégories. |

### <a name="schema-manipulation"></a>Manipulation de schéma

| Fonction | Description |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Concatène plusieurs colonnes dans un vecteur unique. |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Supprime les colonnes à partir d’un jeu de données. |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Conserve les colonnes d’un jeu de données. |


### <a name="variable-selection"></a>sélection des variables

| Fonction | Description |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Sélection des fonctionnalités en fonction du nombre. |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Sélection des fonctionnalités selon les informations réciproques. |


### <a name="text-analytics"></a>Analytique de texte

| Fonction | Description |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | Convertit les colonnes de texte en fonctionnalités numériques. |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Analyse des sentiments. |


### <a name="image-analytics"></a>Analytique de l’image 

| Fonction | Description |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Charge une image. |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Redimensionne une Image. |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Extrait les pixels d’une image. |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Convertit une image en fonctionnalités. |

### <a name="featurization-functions"></a>Fonctions de personnalisation

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Transformation des données pour les sources de données |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>Fonctions de calcul de score 3

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Résultats à l’aide d’un modèle d’apprentissage automatique Microsoft |

## <a name="how-to-call-microsoftml"></a>L’appel de microsoftml

Fonctions dans **microsoftml** peuvent être appelées dans le code Python encapsulé dans des procédures stockées. La plupart des développeurs build **microsoftml** solutions localement, puis migrez le code Python terminé à des procédures stockées comme un exercice de déploiement.

Le **microsoftml** package pour Python est installé par défaut, mais contrairement à **revoscalepy**, il n’est pas chargé par défaut lorsque vous démarrez une session de Python à l’aide de fichiers exécutables Python installés avec SQL Server.

Dans un premier temps importer le **microsoftml** empaqueter et importer **revoscalepy** si vous devez utiliser des contextes de calcul distants ou les objets connexes de source des données ou de connectivité. Ensuite, référencez les fonctions individuelles que vous avez besoin.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Voir aussi

+ [Didacticiels Python](../tutorials/sql-server-python-tutorials.md)
+ [Tutoriel : Incorporer le code Python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Référence Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

