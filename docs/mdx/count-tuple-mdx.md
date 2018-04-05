---
title: Nombre (Tuple) (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: c8f4a570-54a8-4c00-ac4b-eef0ebdb353c
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 76bea834dccee153edf96c78175f290a4e5551c5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="count-tuple-mdx"></a>Count (Tuple) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le nombre de dimensions d'un tuple.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>Arguments  
 *Tuple_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un tuple.  
  
## <a name="remarks"></a>Notes   
 Retourne le nombre de dimensions d'un tuple.  
  
## <a name="example"></a> Exemple  
 La mesure calculée dans la requête suivante retourne la valeur 2, qui est le nombre de hiérarchies présentes dans le tuple `([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])` :  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40; Dimension &#41; &#40; MDX &#41;](../mdx/count-dimension-mdx.md)   
 [Nombre &#40; Niveaux de hiérarchie &#41; &#40; MDX &#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Nombre &#40; Définir le &#41; &#40; MDX &#41;](../mdx/count-set-mdx.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
