---
title: Élément ReportParameter (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 133ddf4701a979ae8041ca470d5f18eaca9bd9be
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="reportparameter-element---assl"></a>Élément ReportParameter - ASSL
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ReportParameters](../../../analysis-services/scripting/collections/reportparameters-element-assl.md)|  
|Éléments enfants|[Nom](../../../analysis-services/scripting/properties/name-element-assl.md), [Valeur](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément **Value** doit contenir une expression MDX (Multidimensional Expressions).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ReportParameter>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ReportAction &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Élément action &#40;ASSL&#41;](../../../analysis-services/scripting/objects/action-element-assl.md)   
 [Objets & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
