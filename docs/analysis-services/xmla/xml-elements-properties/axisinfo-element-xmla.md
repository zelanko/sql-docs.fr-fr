---
title: "Élément AxisInfo (XMLA) | Documents Microsoft"
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
apiname: AxisInfo Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxisInfo
- microsoft.xml.analysis.axisinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxisInfo
helpviewer_keywords: AxisInfo element
ms.assetid: 060741db-b2ec-4174-9277-58d996440a88
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 63c34fdea2c6f00d109cd155cfaff82fa592c4e4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="axisinfo-element-xmla"></a>Élément AxisInfo (XMLA)
  Représente les métadonnées d’un axe contenue par le parent [AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AxesInfo>  
   ...  
   <AxisInfo name="string">  
      <HierarchyInfo>...</HierarchyInfo>  
   </AxisInfo>  
   ...  
</AxesInfo>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md)|  
|Éléments enfants|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|Nom|Attribut **String** requis. Nom de l'axe.|  
  
## <a name="remarks"></a>Notes  
 Dans un **racine** élément qui utilise le **MDDataSet** objet, un **AxisInfo** élément contient une collection de **HierarchyInfo** éléments qui, combinée avec la valeur de la **nom** attribut, représente la définition d’un axe retournée dans le dataset multidimensionnel.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
