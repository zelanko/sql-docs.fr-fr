---
title: Élément MembersWithData (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MembersWithData Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6021c376319135614c6938ee522acf0151c72989
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="memberswithdata-element-assl"></a>Élément MembersWithData (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Détermine s’il faut afficher les membres de données pour les membres non-feuilles dans l’attribut parent.  
  
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
|Élément parent|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes   
 La valeur de la **MembersWithData** élément est utilisé uniquement par les attributs parents (en d’autres termes, la valeur de la [utilisation](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) élément de la **DimensionAttribute** élément parent a la valeur *Parent*) pour déterminer s’il faut afficher les membres de données pour les membres non-feuilles dans l’attribut parent. Pour plus d’informations sur les membres de données, consultez [Attributs dans des hiérarchies de type parent-enfant](../../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md).  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*NonLeafDataHidden*|Les données non-feuilles sont masquées.|  
|*NonLeafDataVisible*|Les données non-feuilles sont visibles.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **MembersWithData** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MembersWithData>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément MembersWithDataCaption &#40; ASSL &#41;](../../../analysis-services/scripting/properties/memberswithdatacaption-element-assl.md)   
 [Type de données DimensionAttribute &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
