---
title: Accéder à l’élément (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Access Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Access
helpviewer_keywords:
- Access element
ms.assetid: 6ad99010-fac5-48e9-a099-ecbca380e127
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d1eea0d7e8b0d26692c2cc6e0400d4ceaf7aa8ad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142797"
---
# <a name="access-element-assl"></a>Élément Access (ASSL)
  Indique le niveau d’accès accordé à un [CellPermission](../objects/cellpermission-element-assl.md) élément.  
  
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
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CellPermission](../objects/cellpermission-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*En lecture*|L'accès en lecture seule est autorisé.|  
|*Lecture du contingent*|L'accès de lecture du contingent est autorisé.|  
|*Lecture/écriture*|L'accès en lecture/écriture est autorisé.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `Access` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.CellPermissionAccess>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  