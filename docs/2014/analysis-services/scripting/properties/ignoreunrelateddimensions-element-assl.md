---
title: Élément IgnoreUnrelatedDimensions (ASSL) | Documents Microsoft
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
- IgnoreUnrelatedDimensions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- IgnoreUnrelatedDimensions
helpviewer_keywords:
- IgnoreUnrelatedDimensions element
ms.assetid: c7d7a1cd-a8e0-4ae7-9464-a1d2a55a86ab
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a85e4c3b5d113b6e122f699425a8b0ffaf88a091
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143349"
---
# <a name="ignoreunrelateddimensions-element-assl"></a>Élément IgnoreUnrelatedDimensions (ASSL)
  Détermine si les dimensions non liées sont ignorées lorsque des membres de dimensions qui ne sont pas associées au groupe de mesures sont inclus dans une requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|True|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Groupe de mesures](../objects/group-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Lorsque `IgnoreUnrelatedDimensions` possède la valeur `true`, les dimensions non liées sont forcées à leur niveau maximum ; lorsque la valeur définie est `false`, les dimensions ne sont pas forcées à leur niveau maximum. Cette propriété est semblable à la MDX (Multidimensional Expressions) [ValidMeasure](/sql/mdx/validmeasure-mdx) (fonction).  
  
 L’élément qui correspond au parent de `IgnoreUnrelatedDimensions` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
