---
title: Élément optionality (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0fc2d3f4d741e25596963ee555d1d164fb9a8b1c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="optionality-element-assl"></a>Élément Optionality (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indique le caractère facultatif des membres pour une [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <Optionality>...</OPtionality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Obligatoire*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Obligatoire*|Chaque membre dans l'attribut associé doit être associé à au moins un membre dans l'attribut propriétaire de l'élément **AttributeRelationship** .|  
|*Facultatif*|Chaque membre dans l'attribut associé ne doit pas être associé à au moins un membre dans l'attribut propriétaire de l'élément **AttributeRelationship** .|  
  
 L’énumération qui correspond aux valeurs autorisées pour **cardinalité** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Optionality>.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
