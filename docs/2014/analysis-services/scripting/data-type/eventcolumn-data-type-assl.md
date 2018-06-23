---
title: Type de données EventColumn (ASSL) | Documents Microsoft
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
- EventColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EventColumn
helpviewer_keywords:
- EventColumn data type
ms.assetid: c0009f1d-d136-4155-9a1b-7baacda4b552
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f4e64defcd407e49b4f8e28d9034a2efeb440924
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141890"
---
# <a name="eventcolumn-data-type-assl"></a>Type de données EventColumn (ASSL)
  Définit un type de données primitif qui représente une colonne d’informations à capturer pour un [événement](../objects/event-element-assl.md) élément dans le cadre d’un [Trace](../objects/trace-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
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
|Éléments enfants|[ColumnID](../properties/columnid-element-eventcolumn-assl.md)|  
|Éléments dérivés|[Colonne](../objects/column-element-assl.md) ([colonnes](../collections/columns-element-assl.md) collection de [Trace](../objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Events &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  