---
title: Type de données CubeAttributeBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubeAttributeBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeAttributeBinding
helpviewer_keywords:
- CubeAttributeBinding data type
ms.assetid: 04e3d619-1de8-4fc8-a089-9a44ac0f930c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b0bf386c24a27c0c02caec6d71049d6d1eb8d5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164019"
---
# <a name="cubeattributebinding-data-type-assl"></a>Type de données CubeAttributeBinding (ASSL)
  Définit un type de données dérivé représentant la liaison d'un attribut dans une dimension de cube à une colonne d'action ou à une colonne de la structure d'exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <CubeID>...</CubeID>  
   <CubeDimensionID>...</CubeDimensionID>  
      <AttributeID>...</AttributeID>  
      <Type>...</Type>  
   <Ordinal>...</Ordinal>  
</CubeAttributeBinding>  
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
|Éléments enfants|[AttributeID](../properties/id-element-assl.md), [CubeDimensionID](../properties/dimensionid-element-assl.md), [CubeID](../properties/cubeid-element-assl.md), [Ordinal](../properties/ordinal-element-assl.md), [Type](../properties/type-element-binding-assl.md)|  
|Éléments dérivés|Consultez [de liaison](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
