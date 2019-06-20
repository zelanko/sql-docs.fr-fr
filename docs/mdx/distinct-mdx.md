---
title: Distinct (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fc3e4680991f88743bbab8eec1de3bb629c94b66
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248253"
---
# <a name="distinct-mdx"></a>Distinct (MDX)


  Évalue un jeu spécifié, supprime les tuples dupliqués du jeu et retourne le jeu obtenu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Distinct(Set_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Si le **Distinct** fonction trouve des tuples dupliqués dans le jeu spécifié, la fonction conserve uniquement la première instance du tuple dupliqué tout en conservant l’ordre du jeu.  
  
## <a name="examples"></a>Exemples  
 L'exemple de requête suivant illustre comment utiliser la fonction Distinct avec un jeu nommé, et comment l'utiliser avec la fonction Count pour rechercher le nombre de tuples distincts dans un jeu :  
  
 `WITH SET MySet AS`  
  
 `{[Customer].[Customer Geography].[Country].&[Australia],[Customer].[Customer Geography].[Country].&[Australia],`  
  
 `[Customer].[Customer Geography].[Country].&[Canada],[Customer].[Customer Geography].[Country].&[France],`  
  
 `[Customer].[Customer Geography].[Country].&[United Kingdom],[Customer].[Customer Geography].[Country].&[United Kingdom]}`  
  
 `MEMBER MEASURES.SETCOUNT AS`  
  
 `COUNT(MySet)`  
  
 `MEMBER MEASURES.SETDISTINCTCOUNT AS`  
  
 `COUNT(DISTINCT(MySet))`  
  
 `SELECT {MEASURES.SETCOUNT, MEASURES.SETDISTINCTCOUNT} ON 0,`  
  
 `DISTINCT(MySet) ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
