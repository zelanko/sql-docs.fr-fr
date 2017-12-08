---
title: "Élément (ASSL) de traces | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: Traces Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Traces
helpviewer_keywords: Traces element
ms.assetid: 7ca2c7d1-fda3-4c76-9e32-fd9b5dda56e9
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: afa73f44f7a72579a4c8476ff0053dce828435a1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="traces-element-assl"></a>Élément Traces (ASSL)
  Contient la collection d'éléments [Trace](../../../analysis-services/scripting/objects/trace-element-assl.md) associée à un élément [Server](../../../analysis-services/scripting/objects/server-element-assl.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Server>  
      ...  
   <Traces>  
      <Trace>...</Trace>  
   </Traces>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Éléments enfants|[Trace](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.TraceCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
