---
title: Élément StopTime (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- StopTime Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- StopTime
helpviewer_keywords:
- StopTime element
ms.assetid: 6f863d53-033b-46e0-9837-e891e739b4b0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8de76230ef19e04d921c93ce54d368e55424c230
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141049"
---
# <a name="stoptime-element-assl"></a>Élément StopTime (ASSL)
  Spécifie la date et l’heure à laquelle un [Trace](../objects/trace-element-assl.md) élément doit s’arrêter.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Trace>  
   ...  
   <StopTime>...</StopTime>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|DateTime|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Trace](../objects/trace-element-assl.md)|  
|Éléments enfants|None|  
  
 L’élément qui correspond au parent de `StopTime` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Voir aussi  
 [Effectue le suivi élément &#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  