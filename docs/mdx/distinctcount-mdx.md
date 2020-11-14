---
description: DistinctCount (MDX)
title: DistinctCount (MDX) | Microsoft Docs
ms.date: 11/12/2020
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 28807d1a24f97a6b197ad56d0434399ab53cd742
ms.sourcegitcommit: 54cd97a33f417432aa26b948b3fc4b71a5e9162b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94584846"
---
# <a name="distinctcount-mdx"></a>DistinctCount (MDX)


  Retourne le nombre des différents tuples non vides d'un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DistinctCount(Set_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Remarques  
 La fonction **DistinctCount** équivaut à `Count(Distinct(Set_Expression), EXCLUDEEMPTY)` .  
  
## <a name="examples"></a>Exemples  
 La requête suivante montre comment utiliser la fonction DistinctCount :  
  
 `WITH SET MySet AS`  
  
 `{[Customer].[Customer Geography].[Country].&[Australia],[Customer].[Customer Geography].[Country].&[Australia],`  
  
 `[Customer].[Customer Geography].[Country].&[Canada],[Customer].[Customer Geography].[Country].&[France],`  
  
 `[Customer].[Customer Geography].[Country].&[United Kingdom],[Customer].[Customer Geography].[Country].&[United Kingdom]}`  
  
 `*`  
  
 `{([Date].[Calendar].[Date].&[20010701],[Measures].[Internet Sales Amount] )}`  
  
 `//Returns the value 3 because Internet Sales Amount is null`  
  
 `//for the UK on the date specified`  
  
 `MEMBER MEASURES.SETDISTINCTCOUNT AS`  
  
 `DISTINCTCOUNT(MySet)`  
  
 `SELECT {MEASURES.SETDISTINCTCOUNT} ON 0`  
  
 `FROM [Adventure Works]`  
 
La fonction DistinctCount retourne le nombre d’éléments distincts dans un jeu. dans cet exemple, le second paramètre facultatif est utilisé pour exclure les éléments qui n’ont pas de valeur pour un tuple donné. Dans ce cas, il y a quatre éléments distincts dans le jeu dans le premier paramètre, mais la fonction retourne trois, car seuls l’Australie, le Canada et la France ont des données pour le montant des ventes sur Internet pour le 1er juillet 2001.
 
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;défini&#41; &#40;&#41;MDX ](../mdx/count-set-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
