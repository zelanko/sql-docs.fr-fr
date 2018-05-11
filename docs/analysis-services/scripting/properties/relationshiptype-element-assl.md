---
title: Élément RelationshipType (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d740a3bed4b9fe8d9aa3bf259a9b83a59af26f5a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="relationshiptype-element-assl"></a>Élément RelationshipType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indique si les relations de membres pour un [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) peut être modifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <RelationshipType>...</RelationshipType>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Flexible*|  
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
|*Rigide*|Les relations de membres entre un attribut et un attribut associé ne peuvent pas être modifiées.|  
|*Flexible*|Les relations de membres entre un attribut et un attribut associé peuvent être modifiées.|  
  
 Par exemple, si **ZipCode** ne peut pas passer d'un attribut **City** à un autre, la relation entre **ZipCode** et **City** est marquée comme *Rigid*.  
  
 L’énumération qui correspond aux valeurs autorisées pour **RelationshipType** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.RelationshipType>.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
