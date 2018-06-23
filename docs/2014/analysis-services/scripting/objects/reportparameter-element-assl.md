---
title: Élément ReportParameter (ASSL) | Documents Microsoft
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
- ReportParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportParameter
helpviewer_keywords:
- ReportParameter element
ms.assetid: 653a5c64-f1af-4796-bb7b-b44a40e52901
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 58aeafeaee114c1d08d0ad8b0119bee2dc5d5dea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052032"
---
# <a name="reportparameter-element-assl"></a>Élément ReportParameter (ASSL)
  Contient le nom et la valeur d’un paramètre est passé à une [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] rapport en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ReportParameters>  
      <ReportParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportParameter>  
</ReportParameters>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ReportParameters](../collections/reportparameters-element-assl.md)|  
|Éléments enfants|[Nom](../properties/name-element-assl.md), [Valeur](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `Value` doit contenir une expression MDX (Multidimensional Expressions).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ReportParameter>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ReportAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Élément action &#40;ASSL&#41;](action-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  