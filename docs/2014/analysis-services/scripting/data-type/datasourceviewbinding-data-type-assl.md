---
title: Type de données DataSourceViewBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSourceViewBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataSourceViewBinding
helpviewer_keywords:
- DataSourceViewBinding data type
ms.assetid: 1f08e2d8-b279-4181-9257-e56f9fcbd9bf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 33a8c49ca844fa98d41feab4161ed2c3b144712b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054489"
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
|Types de données de base|[Liaison](binding-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[DataSourceViewID](../properties/id-element-assl.md)|  
|Éléments dérivés|Consultez [de liaison](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DataSourceViewBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
