---
title: Querynotification, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- QueryNotification Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- QueryNotification element
ms.assetid: 0ee06730-81ff-4913-96e6-f39b6f181650
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4eddd5a96c5c5ab541ba9349d7b664b110589a74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177731"
---
# <a name="querynotification-element-assl"></a>Élément QueryNotification (ASSL)
  Contient des informations pour l’élément [ProactiveCaching](proactivecaching-element-assl.md) à propos de la requête à exécuter pour déterminer si une source de données a été modifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<QueryNotifications>  
   <QueryNotification>  
      <Query>...</Query>  
...</QueryNotification>  
</QueryNotifications>  
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
|Éléments parents|[QueryNotifications](../collections/querynotifications-element-assl.md)|  
|Éléments enfants|[Requête](../properties/query-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.QueryNotification>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ProactiveCachingQueryBinding &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
