---
title: "Élément Event (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: Event Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: EVENT
helpviewer_keywords: Event element
ms.assetid: c7911bcd-e601-4a96-a6d8-20b7c7375ff2
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f21f26b92e2fac6b57457ddfd605abd89f09216a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="event-element-assl"></a>Élément Event (ASSL)
  Définit un **événement** à capturer dans le cadre d’un [Trace](../../../analysis-services/scripting/objects/trace-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Events>  
   <Event>  
      <EventID>...</EventID>  
      <Columns>...</Columns>  
   </Event>  
</Events>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Événements](../../../analysis-services/scripting/collections/events-element-assl.md)|  
|Éléments enfants|[Colonnes](../../../analysis-services/scripting/collections/columns-element-assl.md), [ID d’événement](../../../analysis-services/scripting/properties/eventid-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.TraceEvent>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément trace &#40; ASSL &#41;](../../../analysis-services/scripting/objects/trace-element-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
