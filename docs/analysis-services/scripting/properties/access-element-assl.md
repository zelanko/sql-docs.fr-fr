---
title: "Accéder à l’élément (ASSL) | Documents Microsoft"
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
- Access Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Access
helpviewer_keywords:
- Access element
ms.assetid: 6ad99010-fac5-48e9-a099-ecbca380e127
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f04bafc11cdda8d9c0e82b6cb8dee3e3916099eb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="access-element-assl"></a>Élément Access (ASSL)
  Indique le niveau d’accès accordé à un [CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CellPermission>  
   ...  
   <Access>...</Access>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*En lecture*|L'accès en lecture seule est autorisé.|  
|*Lecture du contingent*|L'accès de lecture du contingent est autorisé.|  
|*Lecture/écriture*|L'accès en lecture/écriture est autorisé.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **accès** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.CellPermissionAccess>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

