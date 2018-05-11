---
title: Élément MembersWithDataCaption (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0d9683e8440dcbc2d6d4f8793fe9027a14c92ef4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="memberswithdatacaption-element-assl"></a>Élément MembersWithDataCaption (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fournit une chaîne de modèle utilisée pour créer des légendes pour les membres de données générés par le système.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeTranslation> <!-- or DimensionAttribute -->  
   ...  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   ...  
</AttributeTranslation>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de la **MembersWithDataCaption** élément est utilisé uniquement par les attributs parents (en d’autres termes, la valeur de la [utilisation](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) élément de la **DimensionAttribute** élément parent a la valeur *Parent*) pour déterminer la légende des membres de données dans l’attribut parent. Pour plus d’informations sur les membres de données, consultez [Attributs dans des hiérarchies de type parent-enfant](../../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md).  
  
 Les éléments qui correspondent aux parents de **MembersWithDataCaption** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.AttributeTranslation> et <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément MembersWithData &#40;ASSL&#41;](../../../analysis-services/scripting/properties/memberswithdata-element-assl.md)   
 [Type de données AttributeTranslation &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
