---
description: Count (Tuple) (MDX)
title: Count (Tuple) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4212e3ed86d10035793cecd45ab071feb57e5abf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500552"
---
# <a name="count-tuple-mdx"></a>Count (Tuple) (MDX)


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
  
## <a name="example"></a>Exemple  
 La mesure calculée dans la requête suivante retourne la valeur 2, qui est le nombre de hiérarchies présentes dans le tuple `([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])` :  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;dimension&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Nombre &#40;niveaux de hiérarchie&#41; &#40;&#41;MDX ](../mdx/count-hierarchy-levels-mdx.md)   
 [Nombre &#40;défini&#41; &#40;&#41;MDX ](../mdx/count-set-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
