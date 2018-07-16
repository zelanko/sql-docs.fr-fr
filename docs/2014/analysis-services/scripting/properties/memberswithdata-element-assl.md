---
title: Élément MembersWithData (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MembersWithData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0c2e35549f4db2de489916ad1760954d4f6dfd5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218229"
---
# <a name="memberswithdata-element-assl"></a>Élément MembersWithData (ASSL)
  Détermine si les membres de données pour les membres non-feuilles de l'attribut parent sont affichés ou non.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <MembersWithData>...</MembersWithData>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*NonLeafDataVisible*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de la `MembersWithData` élément est utilisé uniquement par les attributs parents (en d’autres termes, la valeur de la [utilisation](usage-element-dimensionattribute-assl.md) élément de la `DimensionAttribute` élément parent a la valeur *Parent*) pour déterminer si Pour afficher les membres de données pour les membres non-feuilles dans l’attribut parent. Pour plus d’informations sur les membres de données, consultez [Attributs dans des hiérarchies de type parent-enfant](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*NonLeafDataHidden*|Les données non-feuilles sont masquées.|  
|*NonLeafDataVisible*|Les données non-feuilles sont visibles.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `MembersWithData` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MembersWithData>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément MembersWithDataCaption &#40;ASSL&#41;](caption-element-assl.md)   
 [Type de données DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
