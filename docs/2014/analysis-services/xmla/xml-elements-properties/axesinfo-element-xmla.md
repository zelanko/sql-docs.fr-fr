---
title: Élément AxesInfo (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AxesInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxesInfo
- microsoft.xml.analysis.axesinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxesInfo
helpviewer_keywords:
- AxesInfo element
ms.assetid: 15cfa67d-5acd-4737-8a81-2df34b334d3f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7bde7feb88ad570665200c1c3357bbba4127a963
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178489"
---
# <a name="axesinfo-element-xmla"></a>Élément AxesInfo (XMLA)
  Contient une collection de [AxisInfo](axisinfo-element-xmla.md) éléments, représentant les métadonnées d’axe par le parent [OlapInfo](olapinfo-element-xmla.md) élément.  
  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[OlapInfo](olapinfo-element-xmla.md)|  
|Éléments enfants|[AxisInfo](axisinfo-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `AxesInfo` contient un élément `AxisInfo` pour chaque axe dans le dataset multidimensionnel retourné par un élément `root` en utilisant le type de données `MDDataSet`.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
