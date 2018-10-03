---
title: Élément AttributePermissions (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributePermissions
helpviewer_keywords:
- AttributePermissions element
ms.assetid: ac703177-5936-440e-b1a5-a254a89258bc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 00abbc7be0b8efa045074773ee6e2a3526192694
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227959"
---
# <a name="attributepermissions-element-assl"></a>Élément AttributePermissions (ASSL)
  Contient la collection d’autorisations d’attribut pour une personne [rôle](../objects/role-element-assl.md) élément sur une dimension spécifique d’un [Cube](../objects/cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimensionPermission> <!-- or DimensionPermission -->  
   <AttributePermissions>  
      <AttributePermission>...</AttributePermission>  
      </AttributePermissions>  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CubeDimensionPermission](../data-type/permission-data-type-assl.md), [DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
|Éléments enfants|[AttributePermission](../objects/attributepermission-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour `DimensionPermission`, cette collection peut contenir un seul élément `AttributePermission` par attribut.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AttributePermissionCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données d’autorisation &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
