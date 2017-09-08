---
title: "Type de données CubeDimensionPermission (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CubeDimensionPermission Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeDimensionPermission
helpviewer_keywords:
- CubeDimensionPermission data type
ms.assetid: d9d39859-5f33-48bc-a402-0071755918de
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0058f41feb1bf215c6d479492c6303c613ef7b53
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cubedimensionpermission-data-type-assl"></a>Type de données CubeDimensionPermission (ASSL)
  Définit un type de données primitif qui représente les autorisations d'un rôle unique dans une dimension spécifique au sein d'un cube.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimensionPermission>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Description>...</Description>  
   <Read>...</Read>  
   <Write>...</Write>  
   <AttributePermissions>...</AttributePermissions>  
   <Annotations>...</Annotations>  
</CubeDimensionPermission>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|Aucune|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributePermissions](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md), [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md), [Description](../../../analysis-services/scripting/properties/description-element-assl.md), [en lecture](../../../analysis-services/scripting/properties/read-element-assl.md), [écrire](../../../analysis-services/scripting/properties/write-element-assl.md)|  
|Éléments dérivés|[DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md) ([DimensionPermissions](../../../analysis-services/scripting/collections/dimensionpermissions-element-assl.md) collection de [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md) ou [CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeDimensionPermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
