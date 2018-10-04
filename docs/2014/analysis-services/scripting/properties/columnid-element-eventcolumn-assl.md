---
title: Élément ColumnID (EventColumn) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ColumnID Element (EventColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnID
helpviewer_keywords:
- ColumnID element
ms.assetid: c4f4fbad-9d70-4de2-8cf7-caee80a4a1e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4eeb9954f3318a9286865454b6eb61a15f4d4236
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216389"
---
# <a name="columnid-element-eventcolumn-assl"></a>Élément ColumnID (EventColumn) (ASSL)
  Contient l’identificateur (ID) de la colonne d’informations à capturer pour un événement dans le cadre d’un [Trace](../objects/trace-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément obligatoire qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[EventColumn](../data-type/eventcolumn-data-type-assl.md)|  
|Éléments enfants|Aucun.|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `ColumnID` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.TraceColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Columns &#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Élément d’événement &#40;ASSL&#41;](../objects/event-element-assl.md)   
 [Élément Events &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
