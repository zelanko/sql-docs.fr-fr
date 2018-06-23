---
title: Élément ReportingFirstMonth (ASSL) | Documents Microsoft
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
- ReportingFirstMonth Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportingFirstMonth
helpviewer_keywords:
- ReportingFirstMonth element
ms.assetid: cdce83ab-ac22-4f4a-b8f2-1739883be8dd
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 227793bb2de61aa38166ee9cca0d0d01d0f5f6a6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040744"
---
# <a name="reportingfirstmonth-element-assl"></a>Élément ReportingFirstMonth (ASSL)
  Définit le premier mois de création de rapports pour le [TimeBinding](../data-type/binding-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<TimeBinding>  
   ...  
   <ReportingFirstMonth>...</ReportingFirstMonth>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier (1 à 12 où 1=Janvier et 12=Décembre)|  
|Valeur par défaut|`1`|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `ReportingFirstMonth` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  