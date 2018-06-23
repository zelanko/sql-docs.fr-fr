---
title: Élément CurrentTimeMember (ASSL) | Documents Microsoft
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
- CurrentTimeMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CurrentTimeMember
helpviewer_keywords:
- CurrentTimeMember element
ms.assetid: 2e73009c-9f2b-441c-bdf0-ca19b160da4f
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48fc08b2d45ed75c2a57154efbc154cd9b1b0496
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143121"
---
# <a name="currenttimemember-element-assl"></a>Élément CurrentTimeMember (ASSL)
  Définit le membre actuel d’une dimension associée de temps un [Kpi](../objects/kpi-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Kpi>  
   ...  
   <CurrentTimeMember>...</CurrentTimeMember>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Indicateur de performance clé](../objects/kpi-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est une instruction MDX (Multidimensional Expressions) dont l'évaluation fournit un membre unique d'une dimension de temps, utilisé pour récupérer la période de temps actuelle lors de l'évaluation de l'indicateur de performance clé (KPI).  
  
 L’élément qui correspond au parent de `CurrentTimeMember` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  