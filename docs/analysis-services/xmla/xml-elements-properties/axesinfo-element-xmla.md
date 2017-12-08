---
title: "Élément AxesInfo (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AxesInfo Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxesInfo
- microsoft.xml.analysis.axesinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxesInfo
helpviewer_keywords: AxesInfo element
ms.assetid: 15cfa67d-5acd-4737-8a81-2df34b334d3f
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f78f9500040b54e0f6fc2fe0c8a3588e2f75e454
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="axesinfo-element-xmla"></a>Élément AxesInfo (XMLA)
  Contient une collection de [AxisInfo](../../../analysis-services/xmla/xml-elements-properties/axisinfo-element-xmla.md) éléments, représentant les métadonnées d’axe par le parent [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<OlapInfo>  
   ...  
   <AxesInfo>  
      <AxisInfo>...</AxisInfo>  
   </AxesInfo>  
   ...  
</OlapInfo>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Éléments enfants|[AxisInfo](../../../analysis-services/xmla/xml-elements-properties/axisinfo-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **AxesInfo** élément contient un **AxisInfo** élément pour chaque axe dans le dataset multidimensionnel retourné par une **racine** à l’aide de l’élément le **MDDataSet** type de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
