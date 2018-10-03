---
title: Élément ReportFormatParameter (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportFormatParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportFormatParameter
helpviewer_keywords:
- ReportFormatParameter element
ms.assetid: 064a8683-c44b-4261-be4d-32226d3d3119
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f3dd567a88a76837e13d051988620eb1886ef40
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48188019"
---
# <a name="reportformatparameter-element-assl"></a>Élément ReportFormatParameter (ASSL)
  Contient le nom et la valeur d’un paramètre qui spécifie comment un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] rapport est mis en forme au moment de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ReportFormatParameters>  
   <ReportFormatParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportFormatParameter>  
</ReportFormatParameters>  
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
|Élément parent|[ReportFormatParameters](../collections/reportformatparameters-element-assl.md)|  
|Éléments enfants|[Nom](../properties/name-element-assl.md), [Valeur](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `ReportFormatParameter` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ReportAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Élément action &#40;ASSL&#41;](action-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
