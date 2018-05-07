---
title: Élément ReportFormatParameter (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1abce4d8ef10915aef1a0c38fd6b2b98ff6c7dec
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="reportformatparameter-element---asl"></a>Élément ReportFormatParameter - ASL
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ReportFormatParameters](../../../analysis-services/scripting/collections/reportformatparameters-element-assl.md)|  
|Éléments enfants|[Nom](../../../analysis-services/scripting/properties/name-element-assl.md), [Valeur](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **ReportFormatParameter** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ReportAction &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Élément action &#40;ASSL&#41;](../../../analysis-services/scripting/objects/action-element-assl.md)   
 [Objets & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
