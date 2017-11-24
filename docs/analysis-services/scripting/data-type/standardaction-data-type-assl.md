---
title: "Type de données StandardAction (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: StandardAction Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: StandardAction
helpviewer_keywords: StandardAction data type
ms.assetid: 81b574d5-06c1-4587-8bd2-0e5c5e3b1d99
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 27f3ae41d9dd941e1fa372005ddbdcbc39534c24
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="standardaction-data-type-assl"></a>Type de données StandardAction (ASSL)
  Définit un type de données dérivé représentant tous les éléments [Action](../../../analysis-services/scripting/objects/action-element-assl.md) éléments autres qu’un [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md) élément ou un [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<StandardAction>  
   <!-- The following elements extend Action -->  
   <Expression>...</Expression>  
</StandardAction>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Action](../../../analysis-services/scripting/data-type/action-data-type-assl.md)|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[Expression](../../../analysis-services/scripting/properties/expression-element-assl.md)|  
|Éléments dérivés|[Action](../../../analysis-services/scripting/objects/action-element-assl.md) ([Actions](../../../analysis-services/scripting/collections/actions-element-assl.md) collection de [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) ou [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
