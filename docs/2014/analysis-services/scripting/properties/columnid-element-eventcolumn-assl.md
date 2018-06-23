---
title: Élément ColumnID (EventColumn) (ASSL) | Documents Microsoft
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
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 71e51ec736b10a6d72621efb2a9b094882ed8057
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153334"
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
 L’élément qui correspond au parent de `ColumnID` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.TraceColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Columns &#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Élément Event &#40;ASSL&#41;](../objects/event-element-assl.md)   
 [Élément Events &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  