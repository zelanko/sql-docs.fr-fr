---
title: Bibliothèque de fonctions R MicrosoftML
description: Présentation de la bibliothèque de fonctions MicrosoftML dans SQL Server 2016 R services et SQL Server Machine Learning Services avec R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: af9e85586a2aad69a87072caa820fff4026d1feb
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715663"
---
# <a name="microsoftml-r-library-in-sql-server"></a>MicrosoftML (bibliothèque R dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**MicrosoftML** est une bibliothèque de fonctions R de Microsoft fournissant des algorithmes de machine learning hautes performances. Il comprend des fonctions de formation et de transformations, de notation, d’analyse de texte et d’image, et d’extraction de fonctionnalités pour dériver des valeurs de données existantes.

Les API Machine Learning ont été développées par Microsoft pour les applications Machine Learning internes et ont été affinées au fil des années pour prendre en charge des performances élevées sur Big Data, à l’aide du traitement multicœur et de la diffusion rapide de données. MicrosoftML comprend également de nombreuses transformations pour le traitement du texte et de l’image.

## <a name="full-reference-documentation"></a>Documentation de référence complète

La bibliothèque **MicrosoftML** est distribuée dans plusieurs produits Microsoft, mais l’utilisation est la même que vous obteniez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont identiques, la [documentation des fonctions RevoScaleR individuelles](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) est publiée dans un seul emplacement sous la [référence R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft machine learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="versions-and-platforms"></a>Versions et plateformes

La bibliothèque **MicrosoftML** est basée sur R 3.4.3 et n’est disponible que lorsque vous installez l’un des produits ou téléchargements Microsoft suivants:

+ [SQL Server 2016 R services](../install/sql-r-services-windows-install.md)
+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Client Microsoft R](set-up-a-data-science-client.md)

> [!NOTE]
> Les versions complètes du produit sont uniquement Windows, à partir de SQL Server 2017. La prise en charge de Linux pour **MicrosoftML** est une nouveauté de [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Dépendances de package

Les algorithmes dans **MicrosoftML** dépendent de [RevoScaleR](ref-r-revoscaler.md) pour:

+ Objets de source de données. Les données consommées par les fonctions **MicrosoftML** sont créées à l’aide de fonctions **RevoScaleR** .
+ L’informatique à distance (passage de l’exécution des fonctions à une instance SQL Server distante). La bibliothèque **RevoScaleR** fournit des fonctions permettant de créer et d’activer un contexte de calcul distant pour SQL Server.

Dans la plupart des cas, vous devez charger les packages ensemble chaque fois que vous utilisez **MicrosoftML**.

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous faire une idée de la façon dont chacune d’elles est utilisée. Vous pouvez également utiliser la [table des matières](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1-algorithmes d’apprentissage automatique

| Nom de la fonction | Description |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Une implémentation de FastRank, une implémentation efficace de l’algorithme de dégradé Booster MART.  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Une implémentation de forêt aléatoire de forêt et de régression quantile à l’aide de [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Régression logistique à l’aide de L-BFGS.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Une classe prend en charge les machines à vecteurs.  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Filet neuronal binaire, multiclasse et de régression.  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Optimisation de la jambage de coordonnée double stochastique pour la classification et la régression linéaires binaires. |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Forme un certain nombre de modèles de différents types pour obtenir des performances prédictives supérieures à celles obtenues à partir d’un modèle unique.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2-fonctions de transformation

| Nom de la fonction | Description |
|---------------|-------------|
|[concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Transformation pour créer une colonne vectorielle unique à partir de plusieurs colonnes.  |
|[categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Créer un vecteur d’indicateur à l’aide d’une transformation catégorique avec dictionnaire.  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Convertit la valeur catégorique en tableau d’indicateurs par hachage. |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Produit un jeu de nombres de séquences de mots consécutifs, appelés n-grammes, à partir d’un corpus de texte donné. Il offre la détection de la langue, la création de jetons, la mots vides des suppressions, la normalisation du texte et la génération de fonctionnalités.  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Notations du texte en langage naturel et crée une colonne qui contient les probabilités que les sentiments du texte soient positifs.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | permet de définir des arguments pour l’extraction de fonctionnalités basées sur le nombre et le hachage.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Sélectionne un ensemble de colonnes à reformer, en supprimant toutes les autres. |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Sélectionne des fonctionnalités à partir des variables spécifiées à l’aide d’un mode spécifié.|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Charge des données d’image.|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Redimensionne une image en une dimension spécifiée à l’aide d’une méthode de redimensionnement spécifiée.|
|[extractPixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Extrait les valeurs en pixels d’une image.|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Featurizes une image à l’aide d’un modèle de réseau neuronal profond pré-formé.|


## <a name="3-scoring-and-training-functions"></a>3-fonctions de score et de formation

| Nom de la fonction | Description |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Exécute la bibliothèque de notations à partir de SQL Server, à l’aide de la procédure stockée ou à partir du code R, ce qui permet d’obtenir des résultats de prédiction beaucoup plus rapides.|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Transforme les données d’un jeu de données d’entrée en jeu de données de sortie.|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Fournit un résumé d’un modèle Microsoft R Machine Learning.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4-fonctions de perte pour la classification et la régression

| Nom de la fonction | Description |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de classification exponentielle. | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Caractéristiques de la fonction de perte de classification des journaux.  |
|[hingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Caractéristiques de la fonction de perte de classification de la charnière. | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spécifications de la fonction de perte de classification Smooth charniere.  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Caractéristiques de la fonction de perte de régression de poisson. | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Caractéristiques de la fonction de perte de régression au carré.   |   

## <a name="5-feature-selection-functions"></a>5-fonctions de sélection de fonctionnalités

| Nom de la fonction | Description |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Spécification de la sélection des fonctionnalités dans le mode nombre. |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Spécification de la sélection des fonctionnalités en mode d’informations mutuelles. |

## <a name="6-ensemble-modeling-functions"></a>6-ensemble de fonctions de modélisation

| Nom de la fonction | Description |
|---------------|-------------|
|[fastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Crée une liste contenant le nom et les arguments de la fonction pour former un modèle d’arborescence rapide avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Crée une liste contenant le nom et les arguments de la fonction pour former un modèle de forêt rapide avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Crée une liste contenant le nom et les arguments de la fonction pour l’apprentissage d’un modèle linéaire rapide avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Crée une liste contenant le nom et les arguments de la fonction pour l’apprentissage d’un modèle de régression logistique avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Crée une liste contenant le nom et les arguments de la fonction pour l’apprentissage d’un modèle OneClassSvm avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7-fonctions de réseau neuronal

| Nom de la fonction | Description |
|---------------|-------------|
|[optimiseur](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Spécifie des algorithmes d’optimisation pour l’algorithme Machine Learning [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) .|


## <a name="8-package-state-functions"></a>8-fonctions d’état de package

| Nom de la fonction | Description |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Objet d’environnement utilisé pour stocker l’État à l’ensemble du package. |


## <a name="how-to-use-microsoftml"></a>Utilisation de MicrosoftML

Les fonctions dans **MicrosoftML** peuvent être appelées dans du code R encapsulé dans des procédures stockées. La plupart des développeurs créent des solutions **MicrosoftML** localement, puis migrez le code R terminé vers les procédures stockées en tant qu’exercice de déploiement.

Le package **MicrosoftML** pour R est installé «prêt à l’emploi» dans SQL Server 2017. Il peut également être utilisé avec SQL Server 2016 si vous mettez à niveau les composants R pour l’instance: [Mettre à niveau une instance de SQL Server à l’aide de la liaison](../install/upgrade-r-and-python.md)

Le package n’est pas chargé par défaut. Dans un premier temps, chargez le package **MicrosoftML** , puis chargez **RevoScaleR** si vous devez utiliser des contextes de calcul à distance ou des objets de source de données ou de connectivité associés. Ensuite, référencez les fonctions individuelles dont vous avez besoin.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>Voir aussi

+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)
+ [En savoir plus sur l’utilisation des contextes de calcul](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R pour les développeurs SQL: Apprentissage et fonctionnement d’un modèle](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Exemples de produits Microsoft sur GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Référence R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 