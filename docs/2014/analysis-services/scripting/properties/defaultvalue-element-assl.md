---
title: Élément DefaultValue (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DefaultValue Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultValue
helpviewer_keywords:
- DefaultValue element
ms.assetid: 87e964a3-f317-46c3-98c7-b3621765c77b
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a319f22dc353f860ca3b0fa3a8e4b0cf60f421ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142902"
---
# <a name="defaultvalue-element-assl"></a>Élément DefaultValue (ASSL)
  Contient la valeur par défaut en lecture seule de la [ServerProperty](../objects/serverproperty-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ServerProperty>  
   ...  
   <DefaultValue>   </DefaultValue>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout simpleType|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ServerProperty](../objects/serverproperty-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Cet élément contient la valeur par défaut en lecture seule installation le `ServerProperty` pour l’instance actuelle de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. La valeur par défaut est fournie par l'instance et ne peut, en règle générale, être modifiée.  
  
 L’élément qui correspond au parent de `DefaultValue` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ServerProperties &#40;ASSL&#41;](../collections/serverproperties-element-assl.md)   
 [Élément serveur &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  