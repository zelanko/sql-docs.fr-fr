---
title: Référence des fonctions DMX (Data Mining Extensions) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7b25146ce36a0b58bb46bcacb4348f8e34221068
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971803"
---
# <a name="data-mining-extensions-dmx-function-reference"></a>Fonctions DMX (Data Mining Extensions)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge plusieurs fonctions du langage DMX (Data Mining Extensions). Les fonctions étendent les résultats d'une requête de prévision afin d'inclure les informations qui décrivent en détail la prévision. Les fonctions permettent aussi de mieux contrôler la présentation des résultats de la prévision. Le tableau suivant fournit des liens vers des ressources vous permettant de comprendre l'utilisation des fonctions dans DMX.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)|Répertorie les fonctions qui peuvent être utilisées avec tous les types de modèles et fournit des liens vers des informations supplémentaires sur l'interrogation de types spécifiques de modèles d'exploration de données.|  
|[Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)|Fournit une vue d'ensemble de la création d'une requête de prédiction à l'aide de DMX.|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|Retourne une table qui contient un nombre spécifié de lignes à partir du niveau inférieur d'un jeu, triée en ordre croissant d'après une expression de classement.|  
  
 Le tableau ci-après répertorie les fonctions prises en charge par DMX.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|Retourne une table qui contient les n dernières lignes d'éléments de l'expression de table, triées par ordre croissant selon une expression de classement.|  
|[BottomPercent&#41;DMX &#40;](../dmx/bottompercent-dmx.md)|Retourne une table qui contient le plus petit nombre de lignes de niveau inférieur qui représentent un pourcentage spécifié, triée en ordre croissant d'après une expression de classement.|  
|[BottomSum&#41;DMX &#40;](../dmx/bottomsum-dmx.md)|Retourne une table qui contient le plus petit nombre de lignes de niveau inférieur qui représentent une somme spécifiée, triée en ordre croissant en fonction d'une expression de classement.|  
|[Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)|Retourne le cluster qui est le plus susceptible de contenir le cas d'entrée.|  
|[ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)|Retourne la probabilité d'appartenance du cas d'entrée au cluster.|  
|[Existe &#40;DMX&#41;](../dmx/exists-dmx.md)|Retourne la valeur true si le jeu de résultats retourné par l'instruction SELECT spécifiée contient au moins une ligne.|  
|[IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)|Indique si le nœud actuel provient du nœud spécifié.|  
|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)|Indique si le nœud spécifié contient le cas.|  
|[IsTestCase&#41;DMX &#40;](../dmx/istestcase-dmx.md)|Indique si un cas appartient ou non au jeu de scénarios de test.|  
|[IsTrainingCase&#41;DMX &#40;](../dmx/istrainingcase-dmx.md)|Indique si un cas appartient ou non au jeu de cas d'apprentissage.|  
|[Lag &#40;DMX&#41;](../dmx/lag-dmx.md)|Retourne la tranche de temps qui sépare la date du cas actuel de la dernière date des données.|  
|[Predict &#40;DMX&#41;](../dmx/predict-dmx.md)|Réalise une prévision sur une colonne donnée.|  
|[PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)|Retourne la valeur de probabilité ajustée pour la colonne prédictible spécifiée.|  
|[PredictAssociation &#40;DMX&#41;](../dmx/predictassociation-dmx.md)|Prévoit l'appartenances associative dans une colonne.|  
|[PredictCaseLikelihood &#40;DMX&#41;](../dmx/predictcaselikelihood-dmx.md)|Retourne le degré de vraisemblance de l'intégration du cas d'entrée dans le modèle existant. Cette fonction ne peut être utilisée qu'avec des modèles de clustering.|  
|[PredictHistogram &#40;DMX&#41;](../dmx/predicthistogram-dmx.md)|Retourne une table qui représente l'histogramme relatif à une colonne spécifiée.|  
|[PredictNodeId &#40;DMX&#41;](../dmx/predictnodeid-dmx.md)|Retourne l'ID de nœud pour un cas sélectionné.|  
|[PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)|Retourne la probabilité de la colonne spécifiée.|  
|[PredictSequence &#40;DMX&#41;](../dmx/predictsequence-dmx.md)|Prévoit les valeurs suivantes d'une séquence.|  
|[PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)|Récupère la valeur d'écart-type de la colonne spécifiée.|  
|[PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)|Retourne la valeur de support de la colonne.|  
|[PredictTimeSeries &#40;DMX&#41;](../dmx/predicttimeseries-dmx.md)|Prévoit les valeurs suivantes d'une série chronologique.|  
|[PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)|Retourne la valeur de variance de la colonne spécifiée.|  
|[RangeMax&#41;DMX &#40;](../dmx/rangemax-dmx.md)|Retourne la valeur supérieure du compartiment de prévision découverte pour une colonne discrétisée spécifiée.|  
|[RangeMid&#41;DMX &#40;](../dmx/rangemid-dmx.md)|Retourne la valeur intermédiaire du compartiment de prévision découverte pour une colonne discrétisée spécifiée.|  
|[RangeMin&#41;DMX &#40;](../dmx/rangemin-dmx.md)|Retourne la valeur inférieure du compartiment de prévision découverte pour une colonne discrétisée spécifiée.|  
|[StructureColumn&#41;DMX &#40;](../dmx/structurecolumn-dmx.md)|Retourne la valeur de la colonne de structure d'exploration de données de la table spécifiée.|  
|[&#40;DMX&#41;](../dmx/topcount-dmx.md)|Retourne une table qui contient un nombre spécifié de lignes à partir du niveau supérieur d'un jeu, classée par ordre décroissant d'après une expression de classement.|  
|[&#41;DMX &#40;](../dmx/toppercent-dmx.md)|Retourne une table qui contient le plus petit nombre de lignes de niveau supérieur qui représentent un pourcentage spécifié, triée en ordre décroissant d'après une expression de classement.|  
|[&#41;DMX &#40;DMX](../dmx/topsum-dmx.md)|Retourne une table qui contient le plus petit nombre de lignes de niveau supérieur qui représentent une somme spécifiée, triée en ordre décroissant d'après une expression de classement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
