---
title: Élément ReportingFirstWeekOfMonth (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ReportingFirstWeekOfMonth Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportingFirstWeekOfMonth
helpviewer_keywords:
- ReportingFirstWeekOfMonth element
ms.assetid: 29818404-ad45-403f-8fd9-3e3246d301ad
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8f1e3383fe311ca82ee85c5f72d0b56cc00503fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152899"
---
# <a name="reportingfirstweekofmonth-element-assl"></a>Élément ReportingFirstWeekOfMonth (ASSL)
  Définit la première semaine du mois de création de rapports pour le [TimeBinding](../data-type/binding-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<TimeBinding>  
   ...  
   <ReportingFirstWeekOfMonth>...</ReportingFirstWeekOfMonth>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier (1 à 4)|  
|Valeur par défaut|`1`|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `ReportingFirstWeekOfMonth` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  