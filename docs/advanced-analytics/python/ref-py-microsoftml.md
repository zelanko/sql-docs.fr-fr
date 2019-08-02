---
title: package Python microsoftml
description: Présente les algorithmes et les modèles de Microsoft Machine Learning pour Python, en ce qui concerne les charges de travail SQL Server Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c7e7a25749484ff0db4d133f10862438ae5f8ea1
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715142"
---
# <a name="microsoftml-python-module-in-sql-server"></a>microsoftml (module python dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**microsoftml** est un module compatible Python35 de Microsoft fournissant des algorithmes de machine learning hautes performances. Il comprend des fonctions de formation et de transformations, de notation, d’analyse de texte et d’image, et d’extraction de fonctionnalités pour dériver des valeurs de données existantes.

Les API Machine Learning ont été développées par Microsoft pour les applications Machine Learning internes et ont été affinées au fil des années pour prendre en charge des performances élevées sur Big Data, à l’aide du traitement multicœur et de la diffusion rapide de données. Ce package est issu d’un équivalent python d’une version R, [MicrosoftML](../r/ref-r-microsoftml.md), qui a des fonctions similaires. 

## <a name="full-reference-documentation"></a>Documentation de référence complète

La bibliothèque **microsoftml** est distribuée dans plusieurs produits Microsoft, mais l’utilisation est la même que vous obteniez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont identiques, la [documentation des fonctions microsoftml individuelles](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) est publiée dans un seul emplacement sous la [référence python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour Microsoft machine learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="versions-and-platforms"></a>Versions et plateformes

Le module **microsoftml** est basé sur Python 3,5 et n’est disponible que lorsque vous installez l’un des produits ou téléchargements Microsoft suivants:

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Bibliothèques clientes Python pour un client de science des données](setup-python-client-tools-sql.md)

> [!NOTE]
> Les versions complètes du produit sont uniquement Windows, à partir de SQL Server 2017. La prise en charge de Linux pour **microsoftml** est une nouveauté de [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Dépendances de package

Les algorithmes dans **microsoftml** dépendent de [revoscalepy](ref-py-revoscalepy.md) pour:

+ Objets de source de données. Les données consommées par les fonctions **microsoftml** sont créées à l’aide de fonctions **revoscalepy** .
+ L’informatique à distance (passage de l’exécution des fonctions à une instance SQL Server distante). La bibliothèque **revoscalepy** fournit des fonctions permettant de créer et d’activer un contexte de calcul distant pour SQL Server.

Dans la plupart des cas, vous devez charger les packages ensemble chaque fois que vous utilisez **microsoftml**.

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous faire une idée de la façon dont chacune d’elles est utilisée. Vous pouvez également utiliser la [table des matières](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-training-functions"></a>1-fonctions de formation

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Former un ensemble de modèles. |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Forêt aléatoire. |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Modèle linéaire. avec la jambage de coordonnée double stochastique. |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Arbres amplifiés. |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Régression logistique. |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Réseau neuronal. |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Détection des anomalies. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2-fonctions de transformation

### <a name="categorical-variable-handling"></a>Gestion des variables catégoriques

| Fonction | Description |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Convertit une colonne de texte en catégories. |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Hache et convertit une colonne de texte en catégories. |

### <a name="schema-manipulation"></a>Manipulation de schéma

| Fonction | Description |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Concatène plusieurs colonnes en un seul vecteur. |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Supprime des colonnes d’un jeu de données. |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Conserve les colonnes d’un jeu de données. |


### <a name="variable-selection"></a>sélection des variables

| Fonction | Description |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Sélection des fonctionnalités en fonction du nombre. |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Sélection des fonctionnalités basées sur des informations mutuelles. |


### <a name="text-analytics"></a>Analyse de texte

| Fonction | Description |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | Convertit les colonnes de texte en fonctionnalités numériques. |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Analyse des sentiments. |


### <a name="image-analytics"></a>Image Analytics 

| Fonction | Description |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Charge une image. |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Redimensionne une image. |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Extrait les pixels d’une image. |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Convertit une image en fonctionnalités. |

### <a name="featurization-functions"></a>Caractérisation, fonctions

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Transformation de données pour les sources de données |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3-fonctions de calcul de score

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Scores à l’aide d’un modèle de Machine Learning Microsoft |

## <a name="how-to-call-microsoftml"></a>Comment appeler microsoftml

Les fonctions dans **microsoftml** peuvent être appelées dans du code python encapsulé dans des procédures stockées. La plupart des développeurs créent des solutions **microsoftml** localement, puis migrent le code python terminé vers les procédures stockées en tant qu’exercice de déploiement.

Le package **microsoftml** pour Python est installé par défaut, mais contrairement à **revoscalepy**, il n’est pas chargé par défaut quand vous démarrez une session Python à l’aide des exécutables python installés avec SQL Server.

Dans un premier temps, importez le package **microsoftml** , puis importez **revoscalepy** si vous devez utiliser des contextes de calcul à distance ou des objets de source de données ou de connectivité associés. Ensuite, référencez les fonctions individuelles dont vous avez besoin.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Voir aussi

+ [Didacticiels Python](../tutorials/sql-server-python-tutorials.md)
+ [Tutoriel : Incorporer du code python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Informations de référence sur Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

