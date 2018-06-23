---
title: Type de données PerspectiveCalculation (ASSL) | Documents Microsoft
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
- PerspectiveCalculation Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveCalculation
helpviewer_keywords:
- PerspectiveCalculation data type
ms.assetid: 5a5173d2-c96d-4a55-a35c-0cbfd5b0e599
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1214bc349c09f02f522569b26dd48e82d5e42b99
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155133"
---
# <a name="perspectivecalculation-data-type-assl"></a>Type de données PerspectiveCalculation (ASSL)
  Définit un type de données primitif qui représente la relation entre un calcul et une [Perspective](../objects/perspective-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<PerspectiveCalculation>  
      <Name>...</Name>  
   <Type>...</Type>  
   <Annotations>...</Annotations>  
</PerspectiveCalculation>  
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
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [nom](../properties/name-element-assl.md), [Type](../properties/type-element-perspectivecalculation-assl.md)|  
|Éléments dérivés|[Calcul](../objects/calculation-element-assl.md) ([calculs](../collections/calculations-element-assl.md) collection de [Perspective](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.PerspectiveCalculation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  