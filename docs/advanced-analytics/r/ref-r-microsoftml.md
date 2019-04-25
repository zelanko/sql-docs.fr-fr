---
title: Bibliothèque de fonctions MicrosoftML R - Services de SQL Server Machine Learning
description: Introduction à la bibliothèque de fonctions de MicrosoftML dans SQL Server 2016 R Services et SQL Server 2017 Machine Learning Services avec R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 73d9dcf56c0eb5e69704adf169946f6aa28a432c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641826"
---
# <a name="microsoftml-r-library-in-sql-server"></a>MicrosoftML (bibliothèque R dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**MicrosoftML** est une bibliothèque de fonctions R à partir de Microsoft en fournissant des algorithmes d’apprentissage automatique hautes performances. Il inclut des fonctions pour l’apprentissage et transformations, notation, analyse de texte et image et l’extraction des caractéristiques pour dériver les valeurs de données existantes.

La machine learning API ont été développées par Microsoft pour les applications d’apprentissage interne et ont été affinées au fil des années pour prendre en charge des performances élevées sur les big data, à l’aide de traitement multicœur et le streaming rapide des données. MicrosoftML inclut également de nombreuses transformations pour le traitement d’image et texte.

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le **MicrosoftML** library est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même, si vous obtenez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont les mêmes, [documentation pour les fonctions RevoScaleR individuelles](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) est publié dans un seul emplacement sous la [référence de R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft Machine Learning Server. Doivent tout propres au produit comportements existent, les différences sont notées dans la page d’aide (fonction).

## <a name="versions-and-platforms"></a>Versions et plateformes

Le **MicrosoftML** bibliothèque est basée sur R 3.4.3 et disponible uniquement lorsque vous installez un des produits Microsoft ou téléchargements suivantes :

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R client](set-up-a-data-science-client.md)

> [!NOTE]
> Les versions de produit complet sont Windows uniquement, en commençant par SQL Server 2017. Prise en charge de Linux pour **MicrosoftML** est une nouveauté de [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Dépendances de package

Algorithmes dans **MicrosoftML** dépendent [RevoScaleR](ref-r-revoscaler.md) pour :

+ Objets de source de données. Les données utilisées par **MicrosoftML** fonctions sont créées à l’aide de **RevoScaleR** fonctions.
+ Distant computing (exécution de fonction évolution vers une instance distante de SQL Server). Le **RevoScaleR** bibliothèque fournit des fonctions pour la création et l’activation à distance de contexte pour SQL server de calcul.

Dans la plupart des cas, vous allez charger les packages ensemble chaque fois que vous utilisez **MicrosoftML**.

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous donner une idée de l’utilisation de chacun d’eux. Vous pouvez également utiliser le [table des matières](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>Algorithmes d’apprentissage automatique-1

| Nom de la fonction | Description |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Une implémentation de FastRank, une implémentation efficace de la mini-Data WAREHOUSE algorithme de gradient boosting.  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Une forêt aléatoire et à l’aide de Quantile régression forêt implémentation [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Régression logistique à l’aide de L-BFGS.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Machines à vecteurs de prise en charge une seule classe.  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Régression binaire et multi-class neural net.  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Optimisation de l’élévation stochastique de coordonnées double pour classification binaire linéaire et la régression. |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Effectue l’apprentissage d’un nombre de modèles de différents genres d’obtenir mieux les performances de prédiction que pourrait être obtenu à partir d’un modèle unique.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>Fonctions de transformation de 2

| Nom de la fonction | Description |
|---------------|-------------|
|[concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Transformation à créer une colonne de valeur vectorielle unique à partir de plusieurs colonnes.  |
|[categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Créer un vecteur d’indicateur à l’aide de la transformation catégorielle avec le dictionnaire.  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Convertit la valeur catégorique en tableau d’indicateurs en hachant. |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Produit un ensemble de nombres de séquences de mots consécutifs, appelés n-grammes, à partir d’un corpus de donnée de texte. Il offre la détection de la langue, création de jetons, suppression de mots vides, une normalisation de reconnaissance et génération de fonctionnalités.  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Scores de texte en langage naturel et crée une colonne qui contient les probabilités que les sentiments dans le texte sont positives.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | permet de définir des arguments pour l’extraction des caractéristiques basées sur le hachage et count.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Sélectionne un ensemble de colonnes pour reformer, suppression de tous les autres. |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Sélectionne les fonctionnalités dans les variables spécifiées à l’aide d’un mode spécifié.|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Charges de données d’image.|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Redimensionne une image à une dimension spécifiée à l’aide d’une méthode de redimensionnement spécifiée.|
|[extractPixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Extrait les valeurs de pixel d’une image.|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Par caractériser une image à l’aide d’un modèle de réseau de neurones profond préformé.|


## <a name="3-scoring-and-training-functions"></a>3-score et les fonctions de formation

| Nom de la fonction | Description |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Exécute la bibliothèque de calcul de score à partir de SQL Server, à l’aide de la procédure stockée, ou à partir du code R l’activation de la notation en temps réel fournir des performances de prédiction beaucoup plus rapide.|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Transforme les données à partir d’un jeu de données d’entrée à un jeu de données de sortie.|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Fournit un résumé d’un modèle de Machine Learning de Microsoft R.|


## <a name="4-loss-functions-for-classification-and-regression"></a>Fonctions de perte de 4 pour la classification et de régression

| Nom de la fonction | Description |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de classification exponentielle. | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de classification de journal.  |
|[hingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte charnière classification. | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte charnière smooth classification.  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de régression de poisson. | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spécifications pour la fonction de perte de régression au carré.   |   

## <a name="5-feature-selection-functions"></a>Fonctions de sélection des fonctionnalités de 5

| Nom de la fonction | Description |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Spécification de sélection des fonctionnalités en mode de nombre. |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Spécification de sélection des fonctionnalités en mode d’information mutuelle. |

## <a name="6-ensemble-modeling-functions"></a>Fonctions de modélisation de l’ensemble de 6

| Nom de la fonction | Description |
|---------------|-------------|
|[fastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Crée une liste contenant le nom de la fonction et les arguments pour former un modèle d’arborescence rapide avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Crée une liste contenant le nom de la fonction et les arguments pour former un modèle de forêt rapide avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Crée une liste contenant le nom de la fonction et les arguments pour former un modèle linéaire rapide avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Crée une liste contenant le nom de la fonction et les arguments pour former un modèle de régression logistique avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Crée une liste contenant le nom de la fonction et les arguments pour former un modèle OneClassSvm avec [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>Fonctions de réseau neuronal à 7

| Nom de la fonction | Description |
|---------------|-------------|
|[optimizer](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Spécifie les algorithmes d’optimisation pour le [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) algorithme d’apprentissage automatique.|


## <a name="8-package-state-functions"></a>Fonctions de l’état de 8-package

| Nom de la fonction | Description |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Un objet d’environnement utilisé pour stocker l’état au niveau du package. |


## <a name="how-to-use-microsoftml"></a>L’utilisation de MicrosoftML

Fonctions dans **MicrosoftML** peuvent être appelées dans le code R encapsulé dans des procédures stockées. La plupart des développeurs build **MicrosoftML** solutions localement, puis migrez le code R terminé à des procédures stockées comme un exercice de déploiement.

Le **MicrosoftML** le package pour R est installé « out-of-the-box » dans SQL Server 2017. Il est également disponible pour une utilisation avec SQL Server 2016 si vous mettez à niveau les composants R pour l’instance : [Mise à niveau une instance de SQL Server à l’aide de la liaison](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

Le package n’est pas chargé par défaut. Dans un premier temps, chargez le **MicrosoftML** du package, puis charger **RevoScaleR** si vous devez utiliser des contextes de calcul distants ou les objets connexes de source des données ou de connectivité. Ensuite, référencez les fonctions individuelles que vous avez besoin.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>Voir aussi

+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)
+ [Apprenez à utiliser des contextes de calcul](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R pour les développeurs SQL : Former et de faire fonctionner un modèle](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft product samples sur GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Référence de R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 