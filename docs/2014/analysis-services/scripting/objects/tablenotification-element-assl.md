---
title: Élément TableNotification (ASSL) | Documents Microsoft
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
- TableNotification Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- TableNotification element
ms.assetid: 3afd075a-74f9-428c-b527-ee497cbe71e7
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 12dec839000f56e8d82a3f5b0e6398f20ccfb35f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142587"
---
# <a name="tablenotification-element-assl"></a>Élément TableNotification (ASSL)
  Contient des informations pour le [ProactiveCaching](proactivecaching-element-assl.md) élément sur une table ou une vue dans une source de données qui a été modifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<TableNotifications>  
   <TableNotification>  
      <DbTableName>...</DbTableName>  
      <DbSchemaName>...</DbSchemaName>  
...</TableNotification>  
</TableNotifications>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[TableNotifications](../collections/tablenotifications-element-assl.md)|  
|Éléments enfants|[DbSchemaName](../properties/name-element-assl.md), [DbTableName](../properties/dbtablename-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.TableNotification>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ProactiveCachingTablesBinding &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Type de données ProactiveCachingObjectNotificationBinding &#40;ASSL&#41;](../data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)   
 [Type de données ProactiveCachingBinding &#40;ASSL&#41;](../data-type/proactivecachingbinding-data-type-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  