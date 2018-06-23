---
title: Élément IncrementalProcessingNotifications (ASSL) | Documents Microsoft
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
- IncrementalProcessingNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotifications element
ms.assetid: 46f3c9d0-46cc-4833-8f15-7831207f57ce
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c19cc7a3a0b4ade2dab73b3ef5d28bc33c2ac57c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051357"
---
# <a name="incrementalprocessingnotifications-element-assl"></a>Élément IncrementalProcessingNotifications (ASSL)
  Contient la collection de [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md) les éléments qui fournissent des informations pour le [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les requêtes à exécuter afin de déterminer la progression de traitement incrémentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCachingIncrementalProcessingBinding>  
   <IncrementalProcessingNotifications>  
      <IncrementalProcessingNotification>...  
   ...</IncrementalProcessingNotification>  
   </IncrementalProcessingNotifications>  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md)|  
|Éléments enfants|[IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.IncrementalProcessingNotificationCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  