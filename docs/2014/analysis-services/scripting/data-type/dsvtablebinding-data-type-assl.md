---
title: Type de données DSVTableBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DSVTableBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DSVTableBinding
helpviewer_keywords:
- DSVTableBinding data type
ms.assetid: 149e753f-6218-4805-9223-7155b6827e64
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7b2ceab8524135338aa066837c50170268711a9d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095729"
---
# <a name="dsvtablebinding-data-type-assl"></a>Type de données DSVTableBinding (ASSL)
  Définit un type de données dérivé qui représente la liaison entre une table et un [DataSourceView](../objects/datasourceview-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DSVTableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceViewID>...</DataSourceViewID>  
   <TableID>...</TableID>  
</DSVTableBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[TabularBinding](binding-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[DataSourceViewID](../properties/id-element-assl.md), [TableID](../properties/tableid-element-assl.md)|  
|Éléments dérivés|Consultez [de liaison](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [liaison](binding-data-type-assl.md) élément.  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DSVTableBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
