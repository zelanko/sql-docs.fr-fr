---
title: "Type de données ProactiveCachingInheritedBinding (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ProactiveCachingInheritedBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ProactiveCachingInheritedBinding data type
ms.assetid: 913fa19f-1ecb-4fca-897e-12f0fb02cf8b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8692a0fc3f714f9654d3e4aabd85e0617b0dcee2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="proactivecachinginheritedbinding-data-type-assl"></a>Type de données ProactiveCachingInheritedBinding (ASSL)
  Définit un type de données dérivé qui représente les informations de la [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) élément sur les modifications de source de données dans les tables et les vues identifiées par le biais des liaisons de données existantes qui exigent une reconstruction du cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCachingInheritedBinding>  
   <!-- This element has no child elements that extend ProactiveCachingObjectNotificationBinding -->  
</ProactiveCachingInheritedBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[ProactiveCachingObjectNotificationBinding](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|Aucune|  
|Éléments dérivés|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la **ProactiveCachingBinding** type, y compris une table de la hiérarchie d’héritage de **ProactiveCachingBinding** types, consultez [Type de données ProactiveCachingBinding &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md).  
  
 Pour plus d’informations sur la **liaison** type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la **liaison** type et la hiérarchie d’héritage de **liaison** types, consultez [Type de liaison de données &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et liaisons &#40; SSAS multidimensionnel &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ProactiveCachingInheritedBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

