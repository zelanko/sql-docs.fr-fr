---
title: Élément MiningModelPermissions (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningModelPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelPermissions
helpviewer_keywords:
- MiningModelPermissions element
ms.assetid: 6cbcf029-9627-4839-9fc5-15e58e1ba0c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 214e3286d9e12aed8ffa571442cfec4184495a78
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173879"
---
# <a name="miningmodelpermissions-element-assl"></a>Élément MiningModelPermissions (ASSL)
  Contient la collection d’autorisations pour un [MiningModel](../objects/miningmodel-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModel>  
   ...  
   <MiningModelPermissions>  
      <MiningModelPermission xsi:type="Permission">...</MiningModelPermission>  
   </MiningModelPermissions>  
   ...  
</MiningModel>  
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
|Éléments parents|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Éléments enfants|[MiningModelPermission](../objects/miningmodelpermission-element-assl.md) de type [autorisation](../data-type/permission-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningModelPermissionCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données d’autorisation &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
