---
title: "Type de données DataSourceViewBinding (ASSL) | Documents Microsoft"
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
- DataSourceViewBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataSourceViewBinding
helpviewer_keywords:
- DataSourceViewBinding data type
ms.assetid: 1f08e2d8-b279-4181-9257-e56f9fcbd9bf
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5cec38378d59d2250016b722906781e399342fa7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="datasourceviewbinding-data-type-assl"></a>Type de données DataSourceViewBinding (ASSL)
  Définit un type de données dérivé représentant une liaison entre une vue de source de données et l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataSourceViewBinding>  
   <!-- The following elements extend Binding -->  
   <DataSourceViewID>...</DataSourceViewID>  
</DataSourceViewBinding>  
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
|Éléments enfants|[DataSourceViewID](../../../analysis-services/scripting/properties/datasourceviewid-element-assl.md)|  
|Éléments dérivés|Consultez [de liaison](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la **liaison** type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la **liaison** type et la hiérarchie d’héritage de **liaison** types, consultez [Type de liaison de données &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et liaisons &#40; SSAS multidimensionnel &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DataSourceViewBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

