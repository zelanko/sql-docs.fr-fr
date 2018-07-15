---
title: Élément DimensionPermission (ASSL) | Microsoft Docs
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
- DimensionPermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionPermission
helpviewer_keywords:
- DimensionPermission element
ms.assetid: e06efbda-64fd-4dca-a2b5-c8ffbf21512c
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 058a86c54c714dd2244fc45f26cfa53fe503327d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322799"
---
# <a name="dimensionpermission-element-assl"></a>Élément DimensionPermission (ASSL)
  Définit les autorisations qui appartiennent à un particulier [rôle](role-element-assl.md) élément pour une dimension de base de données spécifique ou d’une dimension de cube.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionPermissions>  
   <DimensionPermission xsi:type="DimensionPermission">...</DimensionPermission> <!-- ancestor: Dimension -->  
   <!-- or -->  
   <DimensionPermission xsi:type="CubeDimensionPermission">...</DimensionPermission> <!-- ancestor: CubePermission -->  
</DimensionPermissions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur||  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif susceptible d'apparaître une fois ou plusieurs fois.|  
  
|Ancêtre ou parent|Type de données|  
|------------------------|---------------|  
|[Dimension](../data-type/permission-data-type-assl.md)|  
|[CubePermission](../data-type/cubedimensionpermission-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionPermissions](../collections/dimensionpermissions-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Les éléments correspondants dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.DimensionPermission> et <xref:Microsoft.AnalysisServices.CubeDimensionPermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
