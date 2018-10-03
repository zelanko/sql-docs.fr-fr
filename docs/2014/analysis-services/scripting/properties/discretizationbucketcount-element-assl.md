---
title: Élément DiscretizationBucketCount (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscretizationBucketCount Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationBucketCount
helpviewer_keywords:
- DiscretizationBucketCount element
ms.assetid: 551a73ae-59e1-4079-a2d9-988df96b5e07
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5fea5841750555185cbeb40f99b9dc5d312be490
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202159"
---
# <a name="discretizationbucketcount-element-assl"></a>Élément DiscretizationBucketCount (ASSL)
  Contient le nombre de compartiments où effectuer la discrétisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de l'élément `DiscretizationBucketCount` détermine comment sont créés des groupes, ou « compartiments », lorsque les valeurs de l'élément `DimensionAttribute` ou `ScalarMiningStructureColumn` sont discrétisées, c.-à-d. organisées en un ensemble de groupes spécifique. Si l’élément n’est pas spécifié, ou si zéro est spécifié pour la valeur de l’élément, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crée un nombre approprié de groupes en fonction de la méthode de discrétisation. Pour plus d’informations sur les méthodes de discrétisation, consultez [méthodes de discrétisation &#40;d’exploration de données&#41;](../../data-mining/discretization-methods-data-mining.md).  
  
 Les éléments qui correspondent aux parents de `DiscretizationBucketCount` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.DimensionAttribute> et <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DiscretizationMethod &#40;ASSL&#41;](discretizationmethod-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
