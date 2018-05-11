---
title: Élément ordinal (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 88c2409d42fc23f017989218d8ea87172d1b8d3d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="ordinal-element-assl"></a>Élément Ordinal (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indique le nombre ordinal auquel s'associer dans des collections, telles que des clés et des traductions.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Ordinal>...</Ordinal>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|**0**|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md), [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 **AttributeBinding** et **CubeAttributeBinding** éléments dans lesquels la [Type](../../../analysis-services/scripting/properties/type-element-binding-assl.md) propriété a la valeur *clé* ou *traduction* peut être lié à un attribut qui est à son tour lié à une collection de colonnes dans la vue de source de données. La valeur de l'élément **Ordinal** détermine à quelle colonne l'élément **AttributeBinding** ou **CubeAttributeBinding** se rapporte dans cette collection.  
  
 Les éléments qui correspondent aux parents de **Ordinal** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.AttributeBinding> et <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
