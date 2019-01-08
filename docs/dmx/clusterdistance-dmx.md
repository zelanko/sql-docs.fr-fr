---
title: ClusterDistance (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ad3d0d06016fe8684cacaf73286b229a423aa7c6
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52533660"
---
# <a name="clusterdistance-dmx"></a>ClusterDistance (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Le **ClusterDistance** fonction retourne la distance séparant le cas d’entrée à partir du cluster spécifié, ou si aucun cluster n’est spécifié, la distance séparant le cas d’entrée du cluster plus probable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>S'applique à  
 Cette fonction ne peut être utilisée que si le modèle d'exploration de données sous-jacent prend en charge le clustering. La fonction peut être utilisée avec n'importe quel type de modèle de clustering (EM, K-Means, etc.), mais les résultats diffèrent selon l'algorithme.  
  
## <a name="return-type"></a>Type de retour  
 Une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Le **ClusterDistance** fonction retourne la distance entre le cas d’entrée et le cluster qui a la probabilité la plus élevée pour que les cas d’entrée.  
  
 En cas de clustering K-Means, puisque les cas ne peuvent appartenir qu'à un seul cluster, avec un poids d'appartenance de 1, la distance de cluster est toujours 0. Toutefois, dans le cas de K-Means, chaque cluster est supposé avoir un centroïde. Vous pouvez obtenir la valeur du centroïde en interrogeant ou en parcourant la table imbriquée NODE_DISTRIBUTION dans le contenu du modèle d'exploration de données. Pour plus d’informations, consultez [Contenu du modèle d’exploration de données pour les modèles de clustering &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md).  
  
 Dans le cas de la méthode de clustering EM, tous les points à l'intérieur du cluster sont considérés comme ayant la même probabilité ; il n'ya donc pas, par définition, de centroïde pour le cluster par conception. La valeur de **ClusterDistance** entre un cas particulier et un cluster particulier *N* est calculé comme suit :  
  
 ClusterDistance(N) =1-(membershipWeight(N))  
  
 - ou -  
  
 ClusterDistance(N) = 1-ClusterProbability (N))  
  
## <a name="related-prediction-functions"></a>Fonctions de prédiction connexes  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit les fonctions supplémentaires suivantes permettant d'interroger des modèles de clustering :  
  
-   Utilisez le [Cluster &#40;DMX&#41; ](../dmx/cluster-dmx.md) fonction pour retourner le cluster le plus probable.  
  
-   Utilisez le [ClusterProbability &#40;DMX&#41; ](../dmx/clusterprobability-dmx.md) fonction pour obtenir la probabilité qu’un cas appartienne à un cluster particulier. Cette valeur est l'inverse de la distance de cluster.  
  
-   Utilisez le [PredictHistogram &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md) fonction pour retourner un histogramme de la probabilité du cas d’entrée dans chacun des clusters du modèle.  
  
-   Utilisez le [PredictCaseLikelihood &#40;DMX&#41; ](../dmx/predictcaselikelihood-dmx.md) fonction pour retourner une mesure comprise entre 0 et 1 qui indique la probabilité un cas d’entrée est d’exister compte tenu du modèle appris par l’algorithme.  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>Exemple 1 : Obtention de la Distance de Cluster à Cluster le plus probable  
 L'exemple suivant retourne la distance séparant le cas spécifié du cluster auquel il est le plus susceptible d'appartenir.  
  
```  
SELECT  
    ClusterDistance()  
FROM  
    [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Résultats de l'exemple :  
  
|Expression|  
|----------------|  
|0.0477390930705145|  
  
 Pour déterminer de quel cluster il s'agit, vous pouvez substituer `Cluster` à `ClusterDistance` dans l'exemple précédent.  
  
 Résultats de l'exemple :  
  
|$CLUSTER|  
|--------------|  
|Cluster 6|  
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>Exemple 2 : Obtention de la Distance à un Cluster spécifié  
 La syntaxe suivante utilise l'ensemble de lignes du schéma Content du modèle d'exploration de données pour retourner la liste des ID et légendes de nœud des clusters du modèle. Vous pouvez ensuite utiliser la légende du nœud en tant qu’argument d’identificateur de cluster dans le **ClusterDistance** (fonction).  
  
```  
SELECT NODE_UNIQUE_NAME, NODE_CAPTION   
FROM <model>.CONTENT   
WHERE NODE_TYPE = 5  
```  
  
 Résultats de l'exemple :  
  
|NODE_UNIQUE_NAME|NODE_CAPTION|  
|------------------------|-------------------|  
|001|Cluster 1|  
|002|Cluster 2|  
  
 L'exemple de syntaxe suivant retourne la distance séparant le cas spécifié du cluster appelé Cluster 2.  
  
```  
SELECT  
    ClusterDistance('Cluster 2')  
AS [Cluster 2 Distance]  
FROM [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Résultats de l'exemple :  
  
|Cluster 2 Distance|  
|------------------------|  
|0.97008209236394|  
  
## <a name="see-also"></a>Voir aussi  
 [Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Contenu du modèle d’exploration de données pour les modèles de clustering &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
