---
title: Package Python microsoftml
description: microsoftml est un package Python de Microsoft qui fournit des algorithmes de Machine Learning hautes performances. Il comprend des fonctions d’apprentissage et de transformation, de scoring, d’analyse de texte et d’image, ainsi que d’extraction de caractéristiques pour dériver des valeurs à partir de données existantes. Il est inclus dans SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15'
ms.openlocfilehash: ec421e1b0e112a535e3caa59cf83e01c4e02086c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470940"
---
# <a name="microsoftml-python-package-in-sql-server-machine-learning-services"></a>microsoftml (package Python de SQL Server Machine Learning Services)
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

**microsoftml** est un package Python de Microsoft qui fournit des algorithmes de Machine Learning hautes performances. Il comprend des fonctions d’apprentissage et de transformation, de scoring, d’analyse de texte et d’image, ainsi que d’extraction de caractéristiques pour dériver des valeurs à partir de données existantes. Le package, inclus dans [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md), prend en charge les opérations hautes performances sur le Big Data, l’utilisation du traitement multicœur et le streaming de données rapide.

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le package **microsoftml** est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même quelle que soit sa provenance (SQL Server ou un autre produit). Étant donné que les fonctions sont les mêmes, la [documentation de chaque fonction microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) est publiée au même endroit sous la [référence Python](/machine-learning-server/python-reference/introducing-python-package-reference) pour Microsoft Machine Learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="versions-and-platforms"></a>Versions et plateformes

Le module **microsoftml** est basé sur Python 3.5 et n’est disponible que lorsque vous installez l’un des produits ou téléchargements Microsoft suivants :

+ [Services de Machine Learning SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](/machine-learning-server/)
+ [Bibliothèques clientes Python pour un client de science des données](setup-python-client-tools-sql.md)

> [!NOTE]
> Les versions complètes du produit sont uniquement disponibles sous Windows dans SQL Server 2017. Windows et Linux sont pris en charge pour **microsoftml** dans [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Dépendances de package

Les algorithmes dans **microsoftml** dépendent de [revoscalepy](ref-py-revoscalepy.md) pour :

+ Les objets sources de données. Les données consommées par les fonctions **microsoftml** sont créées à l’aide des fonctions **revoscalepy**.
+ Le calcul à distance (le passage de l’exécution des fonctions vers une instance SQL Server distante). Le package **revoscalepy** fournit des fonctions permettant de créer et d’activer un contexte de calcul distant pour SQL Server.

Dans la plupart des cas, vous devez charger les packages ensemble chaque fois que vous utilisez **microsoftml**.

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous donner une idée de la façon dont chacune d’elles est utilisée. Vous pouvez également utiliser la [table des matières](/machine-learning-server/python-reference/introducing-python-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-training-functions"></a>1 - Fonctions d’entraînement

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_ensemble](/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Effectuer l’apprentissage d’un ensemble de modèles. |
|[microsoftml.rx_fast_forest](/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Forêt aléatoire. |
|[microsoftml.rx_fast_linear](/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Modèle linéaire. avec élévation stochastique à double coordonnée. |
|[microsoftml.rx_fast_trees](/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Arbres augmentés. |
|[microsoftml.rx_logistic_regression](/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Régression logistique. |
|[microsoftml.rx_neural_network](/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Réseau neuronal. |
|[microsoftml.rx_oneclass_svm](/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Détection d’anomalie. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2 - Fonctions de transformation

### <a name="categorical-variable-handling"></a>Gestion des variables de catégorie

| Fonction | Description |
|----------|-------------|
|[microsoftml.categorical](/machine-learning-server/python-reference/microsoftml/categorical) | Convertit une colonne de texte en catégories. |
|[microsoftml.categorical_hash](/machine-learning-server/python-reference/microsoftml/categorical-hash) | Hache et convertit une colonne de texte en catégories. |

### <a name="schema-manipulation"></a>Manipulation de schéma

| Fonction | Description |
|----------|-------------|
|[microsoftml.concat](/machine-learning-server/python-reference/microsoftml/concat) | Concatène plusieurs colonnes en un seul vecteur. |
|[microsoftml.drop_columns](/machine-learning-server/python-reference/microsoftml/drop-columns) | Supprime des colonnes d’un jeu de données. |
|[microsoftml.select_columns](/machine-learning-server/python-reference/microsoftml/select-columns) | Conserve les colonnes d’un jeu de données. |


### <a name="variable-selection"></a>sélection des variables

| Fonction | Description |
|----------|-------------|
|[microsoftml.count_select](/machine-learning-server/python-reference/microsoftml/count-select) |Sélection des caractéristiques en fonction du nombre. |
|[microsoftml.mutualinformation_select](/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Sélection des caractéristiques en fonction des informations mutuelles. |


### <a name="text-analytics"></a>Analytique de texte

| Fonction | Description |
|----------|-------------|
|[microsoftml.featurize_text](/machine-learning-server/python-reference/microsoftml/featurize-text) | Convertit les colonnes de texte en caractéristiques numériques. |
|[microsoftml.get_sentiment](/machine-learning-server/python-reference/microsoftml/get-sentiment) | Analyse des sentiments. |


### <a name="image-analytics"></a>Analyse d’image 

| Fonction | Description |
|----------|-------------|
|[microsoftml.load_image](/machine-learning-server/python-reference/microsoftml/load-image) | Charge une image. |
|[microsoftml.resize_image](/machine-learning-server/python-reference/microsoftml/resize-image) | Redimensionne une image. |
|[microsoftml.extract_pixels](/machine-learning-server/python-reference/microsoftml/extract-pixels) | Extrait les pixels d’une image. |
|[microsoftml.featurize_image](/machine-learning-server/python-reference/microsoftml/featurize-image) | Convertit une image en caractéristiques. |

### <a name="featurization-functions"></a>Fonctions de caractérisation

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_featurize](/machine-learning-server/python-reference/microsoftml/rx-featurize) | Transformation de données pour les sources de données |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3 - Fonctions de scoring

| Fonction | Description |
|----------|-------------|
|[microsoftml.rx_predict](/machine-learning-server/python-reference/microsoftml/rx-predict) | Scores à l’aide d’un modèle Machine Learning Microsoft |

## <a name="how-to-call-microsoftml"></a>Comment appeler microsoftml

Les fonctions de **microsoftml** peuvent être appelées dans du code Python encapsulé dans des procédures stockées. La plupart des développeurs créent des solutions **microsoftml** localement, puis migrent le code Python terminé vers les procédures stockées en guise d’exercice de déploiement.

Le package **microsoftml** pour Python est installé par défaut, mais contrairement à **revoscalepy**, il n’est pas chargé par défaut quand vous démarrez une session Python à l’aide des exécutables Python installés avec SQL Server.

Dans un premier temps, importez le package **microsoftml** et importez **revoscalepy** si vous devez utiliser des contextes de calcul distants ou des objets de source de données ou de connectivité associés. Ensuite, référencez les fonctions individuelles dont vous avez besoin.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Voir aussi

+ [Didacticiels Python](../tutorials/python-tutorials.md)
+ [Référence Python (Microsoft Machine Learning Server)](/machine-learning-server/python-reference/introducing-python-package-reference)