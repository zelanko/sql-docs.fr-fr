---
title: Valeur d’élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Value
helpviewer_keywords:
- Value element
ms.assetid: a2fad411-73fd-42df-b4e1-df2cb8454182
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d338b8607d8515bf89183eeadd24252c55af8fc5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218189"
---
# <a name="value-element-assl"></a>Élément Value (ASSL)
  Contient la valeur de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AlgorithmParameter> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Value>...</Value>  
   ...  
</AlgorithmParameter>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
|Ancêtre ou parent|Type de données|  
|------------------------|---------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Tout simpleType|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Tout simpleType|  
|Autres|String|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md), [Annotation](../objects/annotation-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [ReportFormatParameter](../objects/reportformatparameter-element-asl.md), [ReportParameter](../objects/reportparameter-element-assl.md), [ServerProperty](../objects/serverproperty-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `Value` contient la valeur associée à l'objet parent. La valeur attendue pour l'élément `Value` varie selon l'élément parent, tel que décrit dans le tableau suivant.  
  
|Élément parent|Valeur attendue|  
|--------------------|--------------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Valeur du paramètre d'algorithme.|  
|[Annotation](../objects/annotation-element-assl.md)|Valeur de l'annotation.|  
|[Indicateur de performance clé](../objects/kpi-element-assl.md)|Expression MDX (Multidimensional Expressions) utilisée pour calculer la valeur de l'indicateur de performance clé (KPI).|  
|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|Valeur du paramètre de format de rapport.|  
|[ReportParameter](../objects/reportparameter-element-assl.md)|Expression MDX permettant de calculer la valeur du paramètre de rapport.|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Valeur de la propriété de serveur pour l'instance en cours d'exécution.|  
  
 Les éléments qui correspondent aux parents de `Value` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.AlgorithmParameter>, <xref:Microsoft.AnalysisServices.Annotation>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.ReportParameter> et <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
