---
title: "Élément CellPermission (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CellPermission Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CellPermission
helpviewer_keywords: CellPermission element
ms.assetid: 54a6afc0-1fcb-4b24-851a-6d81e1fe0efc
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a96c177ed5ada769d469120d970cc27325bc1ed1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="cellpermission-element-assl"></a>Élément CellPermission (ASSL)
  Décrit les autorisations que les membres d’un [rôle](../../../analysis-services/scripting/objects/role-element-assl.md) élément avoir sur les cellules individuelles d’un [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CellPermissions>  
   <CellPermission>  
      <Access>...</Access>  
            <Description>...</Description>  
      <Expression>...</Expression>  
      <Annotations>...</Annotations>  
   </CellPermission>  
</CellPermissions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CellPermissions](../../../analysis-services/scripting/collections/cellpermissions-element-assl.md)|  
|Éléments enfants|[Accès](../../../analysis-services/scripting/properties/access-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Description](../../../analysis-services/scripting/properties/description-element-assl.md), [Expression](../../../analysis-services/scripting/properties/expression-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CellPermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
