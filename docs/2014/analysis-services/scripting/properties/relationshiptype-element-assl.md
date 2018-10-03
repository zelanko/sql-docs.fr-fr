---
title: Élément RelationshipType (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3cc0ca0577b63e655c42c9b8bdcb19b1a67cb538
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096709"
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
  
 L’énumération qui correspond aux valeurs autorisées pour `RelationshipType` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.RelationshipType>.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
