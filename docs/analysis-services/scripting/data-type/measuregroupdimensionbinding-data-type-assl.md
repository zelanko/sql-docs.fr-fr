---
title: "Type de données MeasureGroupDimensionBinding (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MeasureGroupDimensionBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MeasureGroupDimensionBinding
helpviewer_keywords:
- MeasureGroupDimensionBinding data type
ms.assetid: 770e5ef8-aea1-4c9e-8e0a-2cbac43f2383
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c1b3d19d4525aefae8ff3f777ae9c04a72e6382
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="measuregroupdimensionbinding-data-type-assl"></a>Type de données MeasureGroupDimensionBinding (ASSL)
  Définit un type de données dérivé représentant une liaison entre une dimension et un groupe de mesures.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroupDimensionBinding>  
   <!-- The following elements extend Binding -->  
   <CubeDimensionID>...</CubeDimensionId>  
</MeasureGroupDimensionBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Liaison](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)|  
|Éléments dérivés|Consultez [de liaison](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la **liaison** type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la **liaison** type et la hiérarchie d’héritage de **liaison** types, consultez [Type de liaison de données &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et liaisons &#40; SSAS multidimensionnel &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MeasureGroupDimensionBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

