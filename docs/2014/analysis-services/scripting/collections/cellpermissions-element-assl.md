---
title: Élément CellPermissions (ASSL) | Documents Microsoft
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
- CellPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellPermissions
helpviewer_keywords:
- CellPermissions element
ms.assetid: 4a604f2f-f4c3-42bd-a42b-951263942cc6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fe89d1e2de728773d9eaae32023e801676a02bb0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141647"
---
# <a name="cellpermissions-element-assl"></a>Élément CellPermissions (ASSL)
  Contient la collection d’autorisations pour les cellules dans le type [Cube](../objects/cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubePermission>  
   ...  
   <CellPermissions>  
      <CellPermission>...</CellPermission>  
   </CellPermissions>  
   ...  
</CubePermission>  
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
|Éléments parents|[CubePermission](../objects/cubepermission-element-assl.md)|  
|Éléments enfants|[CellPermission](../objects/cellpermission-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 La collection peut contenir au maximum un `CellPermission` de l’objet pour chaque valeur autorisée de la [accès](../properties/access-element-assl.md) élément.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CellPermissionCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données d’autorisation &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  