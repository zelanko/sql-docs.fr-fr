---
title: Élément OverrideBehavior (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 99f433d9346926a963e720fcdd0da9cfcd66c6cc
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="overridebehavior-element-assl"></a>Élément OverrideBehavior (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indique le comportement de substitution de la relation décrite par un [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <OverrideBehavior>...</OverrideBehavior>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Fort*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L'élément **OverrideBehavior** détermine comment le positionnement sur l'attribut associé affecte le positionnement sur l'attribut  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Fort*|Indique le comportement de substitution de la relation décrite par un élément AttributeRelationship. Détermine comment le positionnement sur un attribut affecte la position de l'autre.|  
|*Aucun*|Aucun effet.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **OverrideBehavior** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.OverrideBehavior>.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
