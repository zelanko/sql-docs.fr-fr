---
title: Élément RelationshipType (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- RelationshipType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RelationshipType
helpviewer_keywords:
- RelationshipType element
ms.assetid: 72e1ab0e-a95d-4ebe-857d-21de1bf9fe03
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a2e5b5ec9e9591a45a80f099397ed6568a986313
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153331"
---
# <a name="relationshiptype-element-assl"></a>Élément RelationshipType (ASSL)
  Indique si les relations de membres pour un [AttributeRelationship](../objects/attributerelationship-element-assl.md) peut être modifié.  
  
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
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[AttributeRelationship](../objects/attributerelationship-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Rigide*|Les relations de membres entre un attribut et un attribut associé ne peuvent pas être modifiées.|  
|*Flexible*|Les relations de membres entre un attribut et un attribut associé peuvent être modifiées.|  
  
 Par exemple, si `ZipCode` ne peut pas passer d’un `City` vers un autre, la relation à partir de `ZipCode` à `City` est marqué comme *rigide*.  
  
 L’énumération qui correspond aux valeurs autorisées pour `RelationshipType` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.RelationshipType>.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  