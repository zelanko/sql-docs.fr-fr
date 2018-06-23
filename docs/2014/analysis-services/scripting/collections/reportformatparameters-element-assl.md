---
title: Élément ReportFormatParameters (ASSL) | Documents Microsoft
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
- ReportFormatParameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportFormatParameters
helpviewer_keywords:
- ReportFormatParameters element
ms.assetid: f2e677bf-7b6b-4ce4-b0ec-75a4999306c9
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0e76ba9b70c485a938910eef7a7285520163b1bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144173"
---
# <a name="reportformatparameters-element-assl"></a>Élément ReportFormatParameters (ASSL)
  Contient la collection d'éléments [ReportFormatParameter](../objects/reportformatparameter-element-asl.md) pour un élément [ReportAction](../data-type/action-data-type-assl.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action xsi:type="ReportAction">  
   ...  
   <ReportFormatParameters>  
      <ReportFormatParameter>...</ReportFormatParameter>  
   </ReportFormatParameters>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Action](../objects/action-element-assl.md) de type [ReportAction](../data-type/action-data-type-assl.md)|  
|Éléments enfants|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `ReportFormatParameters` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  