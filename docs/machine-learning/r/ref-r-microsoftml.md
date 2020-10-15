---
title: Package R MicrosoftML
description: MicrosoftML est un package R de Microsoft qui fournit des algorithmes de Machine Learning hautes performances. Il comprend des fonctions d’apprentissage et de transformation, de scoring, d’analyse de texte et d’image, ainsi que d’extraction de caractéristiques pour dériver des valeurs à partir de données existantes. Le package, inclus dans SQL Server Machine Learning Services et SQL Server 2016 R Services, prend en charge les opérations hautes performances sur le Big Data, l’utilisation du traitement multicœur et le streaming de données rapide. MicrosoftML comprend également de nombreuses transformations pour le traitement du texte et de l’image.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/06/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6295756f727dacffbfa54c1dccaf223cfac58351
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956886"
---
# <a name="microsoftml-r-package-in-sql-server-machine-learning-services"></a>MicrosoftML (package R de SQL Server Machine Learning Services)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

**MicrosoftML** est un package R de Microsoft qui fournit des algorithmes de Machine Learning hautes performances. Il comprend des fonctions d’apprentissage et de transformation, de scoring, d’analyse de texte et d’image, ainsi que d’extraction de caractéristiques pour dériver des valeurs à partir de données existantes. Le package, inclus dans [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) et [SQL Server 2016 R Services](sql-server-r-services.md), prend en charge les opérations hautes performances sur le Big Data, l’utilisation du traitement multicœur et le streaming de données rapide. MicrosoftML comprend également de nombreuses transformations pour le traitement du texte et de l’image.

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le package **MicrosoftML** est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même quelle que soit sa provenance (SQL Server ou un autre produit). Étant donné que les fonctions sont les mêmes, la [documentation de chaque fonction RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) est publiée au même endroit sous la [référence R](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft Machine Learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="versions-and-platforms"></a>Versions et plateformes

Le package **MicrosoftML** s’appuie sur R 3.4.3 et n’est disponible que si l’un des produits ou téléchargements Microsoft suivants est installé :

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [Services de Machine Learning SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](/machine-learning-server/)
+ [Microsoft R Client](set-up-a-data-science-client.md)

> [!NOTE]
> Les versions complètes du produit sont uniquement disponibles sous Windows dans SQL Server 2017. Windows et Linux sont pris en charge pour **MicrosoftML** dans [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Dépendances de package

Les algorithmes dans **MicrosoftML** dépendent de [RevoScaleR](ref-r-revoscaler.md) pour :

+ Les objets sources de données. Les données consommées par les fonctions **MicrosoftML** sont créées à l’aide des fonctions **RevoScaleR**.
+ Le calcul à distance (le passage de l’exécution des fonctions vers une instance SQL Server distante). Le package **RevoScaleR** fournit des fonctions permettant de créer et d’activer un contexte de calcul distant pour SQL Server.

Dans la plupart des cas, vous devez charger les packages ensemble chaque fois que vous utilisez **MicrosoftML**.

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous donner une idée de la façon dont chacune d’elles est utilisée. Vous pouvez également utiliser la [table des matières](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1-Nouveaux algorithmes de Machine Learning

| Nom de la fonction | Description |
|---------------|-------------|
|[rxFastTrees](/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Implémentation de FastRank, une implémentation efficace de l’algorithme de boosting de gradient MART.  |
|[rxFastForest](/machine-learning-server/r-reference/microsoftml/rxfastforest) | Implémentation de forêt aléatoire et de forêt de régression quantile utilisant [rxFastTrees](/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](/machine-learning-server/r-reference/microsoftml/logisticregression) | Régression logistique à l’aide de L-BFGS.  |
|[rxOneClassSvm](/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Machines à vecteurs de support à une classe.  
|[rxNeuralNet](/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Réseau neuronal binaire, multiclasse et de régression.  |
|[rxFastLinear](/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Optimisation de l’élévation stochastique à double coordonnée pour la régression et la classification binaire linéaire. |
|[rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble) | Effectuer l’apprentissage de différents types de modèles pour obtenir des performances prédictives supérieures à celles obtenues à partir d’un modèle unique.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2-Fonctions de transformation

| Nom de la fonction | Description |
|---------------|-------------|
|[concat](/machine-learning-server/r-reference/microsoftml/concat) | Transformation permettant de créer une seule colonne à valeurs vectorielles à partir de plusieurs colonnes.  |
|[categorical](/machine-learning-server/r-reference/microsoftml/categorical) | Crée un vecteur d’indicateur à l’aide d’une transformation catégorielle avec un dictionnaire.  |
|[categoricalHash](/machine-learning-server/r-reference/microsoftml/categoricalhash) | Convertit la valeur catégorielle en tableau d’indicateurs par hachage. |
|[featurizeText](/machine-learning-server/r-reference/microsoftml/featurizetext) | Génère un ensemble de nombres de séquences de mots consécutifs (appelées n-grams) à partir d’un corpus de texte donné. Il offre des fonctions de détection de la langue, de segmentation du texte en unités lexicales, de suppression des mots vides, de normalisation du texte et de génération de caractéristiques.  |
|[getSentiment](/machine-learning-server/r-reference/microsoftml/getsentiment) | Génère un score pour du texte en langage naturel et crée une colonne comprenant les probabilités que les sentiments du texte soient positifs.|
|[ngram](/machine-learning-server/r-reference/microsoftml/ngram) | Permet de définir des arguments pour les extractions de fonctionnalités basées sur le nombre et le hachage.|
|[selectColumns](/machine-learning-server/r-reference/microsoftml/selectcolumns) | Sélectionne un ensemble de colonnes à entraîner à nouveau et supprime toutes les autres. |
|[selectFeatures](/machine-learning-server/r-reference/microsoftml/selectfeatures) | Sélectionne des fonctionnalités à partir de variables spécifiées à l’aide d’un mode spécifié.|
|[loadImage](/machine-learning-server/r-reference/microsoftml/loadimage) | Charge des données d’image.|
|[resizeImage](/machine-learning-server/r-reference/microsoftml/resizeimage) | Change la taille d’une image aux dimensions spécifiées à l’aide d’une méthode de redimensionnement spécifiée.|
|[extractPixels](/machine-learning-server/r-reference/microsoftml/extractpixels) | Extrait les valeurs en pixels d’une image.|
|[featurizeImage](/machine-learning-server/r-reference/microsoftml/featurizeimage) | Génère des fonctionnalités pour une image à l’aide d’un modèle de réseau neuronal profond pré-entraîné.|


## <a name="3-scoring-and-training-functions"></a>3-Fonctions de scoring et d’apprentissage

| Nom de la fonction | Description |
|---------------|-------------|
|[rxPredict.mlModel](/machine-learning-server/r-reference/microsoftml/rxpredict) | Exécute la bibliothèque de scoring à partir de SQL Server à l’aide de la procédure stockée, ou à partir du code R en activant le scoring en temps réel, ce qui permet d’obtenir des performances de prédiction beaucoup plus rapides.|
|[rxFeaturize](/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Transforme les données d’un jeu de données d’entrée en jeu de données de sortie.|
|[mlModel](/machine-learning-server/r-reference/microsoftml/mlmodel) | Fournit un résumé d’un modèle Machine Learning Microsoft R.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4-Fonctions de perte pour la régression et la classification

| Nom de la fonction | Description |
|---------------|-------------|
|[expLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de classification exponentielle. | 
|[logLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de classification des journaux.  |
|[hingeLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de classification de marge maximale. | 
|[smoothHingeLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de classification de marge maximale régulière.  |
| [poissonLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spécifications de la fonction de perte de régression de Poisson. | 
|[squaredLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spécifications de la fonction de perte de régression quadratique.   |   

## <a name="5-feature-selection-functions"></a>5-Fonctions de sélection des fonctionnalités

| Nom de la fonction | Description |
|---------------|-------------|
|[minCount](/machine-learning-server/r-reference/microsoftml/mincount) | Spécification pour la sélection des fonctionnalités en mode de dénombrement. |
|[mutualInformation](/machine-learning-server/r-reference/microsoftml/mutualinformation) | Spécification pour la sélection des fonctionnalités en mode Informations mutuelles. |

## <a name="6-ensemble-modeling-functions"></a>6-Fonctions de modélisation d’ensembles

| Nom de la fonction | Description |
|---------------|-------------|
|[fastTrees](/machine-learning-server/r-reference/microsoftml/fasttrees) | Crée une liste contenant le nom et les arguments de la fonction pour effectuer l’apprentissage d’un modèle d’arborescence rapide avec [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](/machine-learning-server/r-reference/microsoftml/rxfastforest) | Crée une liste contenant le nom et les arguments de la fonction pour effectuer l’apprentissage d’un modèle de forêt rapide avec [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](/machine-learning-server/r-reference/microsoftml/fastlinear) | Crée une liste contenant le nom et les arguments de la fonction pour effectuer l’apprentissage d’un modèle linéaire rapide avec [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](/machine-learning-server/r-reference/microsoftml/logisticregression) | Crée une liste contenant le nom et les arguments de la fonction pour effectuer l’apprentissage d’un modèle de régression logistique avec [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Crée une liste contenant le nom et les arguments de la fonction pour effectuer l’apprentissage d’un modèle OneClassSvm avec [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7-Fonctions de mise en réseau neuronal

| Nom de la fonction | Description |
|---------------|-------------|
|[optimizer](/machine-learning-server/r-reference/microsoftml/optimizer) | Spécifie des algorithmes d’optimisation pour l’algorithme de Machine Learning [rxNeuralNet](/machine-learning-server/r-reference/microsoftml/rxneuralnet).|


## <a name="8-package-state-functions"></a>8-Fonctions d’état de package

| Nom de la fonction | Description |
|---------------|-------------|
|[rxHashEnv](/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Objet d’environnement utilisé pour stocker l’état de l’ensemble du package. |


## <a name="how-to-use-microsoftml"></a>Utiliser MicrosoftML

Les fonctions de **MicrosoftML** peuvent être appelées dans du code R encapsulé dans des procédures stockées. La plupart des développeurs créent des solutions **MicrosoftML** localement, puis migrent le code R terminé vers les procédures stockées en guise d’exercice de déploiement.

Le package **MicrosoftML** pour R est installé « prêt à l’emploi » dans SQL Server 2017. Il est également compatible avec SQL Server 2016 si vous mettez à niveau les composants R pour l’instance : [Upgrade an instance of SQL Server using binding](../install/upgrade-r-and-python.md) (Mettre à niveau une instance de SQL Server à l’aide de la liaison)

Le package n’est pas chargé par défaut. Dans un premier temps, chargez le package **MicrosoftML**, puis chargez **RevoScaleR** si vous devez utiliser des contextes de calcul distants ou des objets de source de données ou de connectivité associés. Ensuite, référencez les fonctions individuelles dont vous avez besoin.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>Voir aussi

+ [Tutoriels sur R](../tutorials/r-tutorials.md)
+ [En savoir plus sur l’utilisation des contextes de calcul](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R pour les développeurs SQL : apprentissage et fonctionnement d’un modèle](../tutorials/r-taxi-classification-introduction.md)
+ [Exemples de produits Microsoft sur GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Référence R (Microsoft Machine Learning Server)](/machine-learning-server/r-reference/introducing-r-server-r-package-reference)