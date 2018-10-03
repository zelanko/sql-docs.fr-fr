---
title: Méthodes de discrétisation (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- discretization [Analysis Services]
- columns [data mining], discretization
- THRESHOLDS method
- CLUSTERS method
- DiscretizationBuckets property
- AUTOMATIC method
- EQUAL_AREAS method
- coding [Data Mining]
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7cf775406905a920861236dafa8d740c9074101
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187050"
---
# <a name="discretization-methods-data-mining"></a>Méthodes de discrétisation (exploration de données)
  Certains algorithmes utilisés pour créer des modèles d’exploration de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nécessitent des types de contenu spécifiques pour pouvoir fonctionner correctement. Par exemple, l'algorithme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes ne peut pas utiliser de colonnes continues comme entrée ni prédire des valeurs continues. En outre, certaines colonnes peuvent contenir tellement de valeurs que l'algorithme ne peut pas identifier facilement les motifs intéressants qui ressortent des données et qui vont servir à créer un modèle.  
  
 Dans ce cas, vous pouvez discrétiser les données des colonnes afin de pouvoir utiliser les algorithmes pour créer un modèle d'exploration de données. La*discrétisation* est le processus consistant à mettre des valeurs dans des compartiments afin d’obtenir un nombre limité d’états possibles. Les compartiments eux-mêmes sont traités comme des valeurs discrètes et ordonnées. Vous pouvez discrétiser les colonnes de nombres et de chaînes.  
  
 Plusieurs méthodes vous permettent de discrétiser des données. Si votre solution d’exploration de données utilise des données relationnelles, vous pouvez déterminer le nombre de compartiments à utiliser pour le regroupement des données en définissant la valeur de la propriété <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> . Le nombre de compartiments par défaut est 5.  
  
 Si votre solution d’exploration de données utilise les données d’un cube OLAP (Online Analytical Processing), l’algorithme d’exploration de données calcule automatiquement le nombre de compartiments à générer, en utilisant l’équation suivante, où « n » est le nombre de valeurs distinctes de données dans la colonne :  
  
 `Number of Buckets = sqrt(n)`  
  
 Si vous ne voulez pas qu’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calcule le nombre de compartiments, vous pouvez utiliser la propriété <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> pour spécifier manuellement le nombre de compartiments.  
  
 Le tableau suivant décrit les méthodes que vous pouvez utiliser pour discrétiser des données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Méthode de discrétisation|Description|  
|---------------------------|-----------------|  
|`AUTOMATIC`|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] détermine la méthode de discrétisation à utiliser.|  
|`CLUSTERS`|L'algorithme divise les données en groupes en échantillonnant les données d'apprentissage, en initialisant à un certain nombre de points aléatoires, puis en exécutant plusieurs itérations de l'algorithme MC (Microsoft Clustering) à l'aide de la méthode de clustering EM (expectation-maximisation). La méthode `CLUSTERS` est utile car elle fonctionne sur n'importe quelle courbe de distribution. Cependant, elle nécessite une durée de traitement plus longue que les autres méthodes de discrétisation.<br /><br /> Cette méthode peut uniquement être utilisée sur des colonnes numériques.|  
|`EQUAL_AREAS`|L'algorithme divise les données en groupes contenant un nombre égal de valeurs. Cette méthode convient surtout aux courbes de distribution normales, mais elle n'est pas efficace si la distribution comprend un nombre élevé de valeurs dans un groupe resserré de valeurs continues. Par exemple, si la moitié des éléments a un coût de 0, la moitié des données se trouvera sous un point unique de la courbe. Dans ce type de distribution, cette méthode disperse les données pour tenter d'établir une discrétisation équivalente dans plusieurs zones, ce qui engendre une représentation inexacte des données.|  
  
## <a name="remarks"></a>Notes  
  
-   Vous pouvez utiliser la `EQUAL_AREAS` méthode pour discrétiser des chaînes.  
  
-   Le `CLUSTERS` méthode utilise un échantillon aléatoire de 1 000 enregistrements pour discrétiser les données. Utilisez la méthode `EQUAL_AREAS` si vous ne voulez pas que l'algorithme échantillonne les données.  
  
-   Le didacticiel du modèle d'exploration de données du réseau neuronal fournit un exemple montrant comment la discrétisation peut être personnalisée. Pour plus d’informations, consultez [leçon 5 : génération réseau neuronal et modèles de régression logistique &#40;didacticiel d’exploration de données intermédiaire&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;exploration de données&#41;](content-types-data-mining.md)   
 [Types de contenu &#40;DMX&#41;](/sql/dmx/content-types-dmx)   
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)   
 [Types de données &#40;exploration de données&#41;](data-types-data-mining.md)   
 [Colonnes de Structure d’exploration de données](mining-structure-columns.md)   
 [Distributions de colonnes &#40;exploration de données&#41;](column-distributions-data-mining.md)  
  
  
