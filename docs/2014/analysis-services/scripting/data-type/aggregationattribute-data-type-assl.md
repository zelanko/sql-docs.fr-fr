---
title: Type de données AggregationAttribute (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AggregationAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationAttribute
helpviewer_keywords:
- AggregationAttribute data type
ms.assetid: 636827c7-938d-4b7d-9827-46da3bc60d9a
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 388bd739938a7b756157659ce34c0a215710a034
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044552"
---
# <a name="aggregationattribute-data-type-assl"></a>Type de données AggregationAttribute (ASSL)
  Définit un type de données primitif qui représente l’association entre un [agrégation](../objects/aggregation-element-assl.md) élément et un attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AggregationAttribute>  
   <AttributeID>...</AttributeID>  
      <Annotations>...</Annotations>  
</AggregationAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[AttributeID](../properties/id-element-assl.md), [Annotations](../collections/annotations-element-assl.md)|  
|Éléments dérivés|[Attribut](../objects/attribute-element-assl.md) ([attributs](../collections/attributes-element-assl.md) collection de [AggregationDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 La classe correspondante dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.AggregationAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément aggregation &#40;ASSL&#41;](../objects/aggregation-element-assl.md)   
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  