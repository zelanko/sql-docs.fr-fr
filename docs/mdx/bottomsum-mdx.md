---
description: BottomSum (MDX)
title: BottomSum (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 51be20fdd7378b361cd8d962941e55532503e4e1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494962"
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)


  Trie un jeu spécifié par ordre croissant et retourne un jeu de tuples avec les valeurs les plus faibles dont le total est égal ou inférieur à une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Valeur*  
 Expression numérique valide qui précise la valeur par rapport à laquelle chaque tuple est comparé.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 La fonction **BottomSum** calcule la somme d’une mesure spécifiée évaluée sur un jeu spécifié, en triant le jeu dans l’ordre croissant. Elle retourne ensuite les éléments dotés des valeurs les plus faibles dont le total de l'expression numérique spécifiée correspond au moins à la valeur indiquée (somme). Enfin, elle retourne le plus petit sous-ensemble d'un jeu dont le total cumulé est égal au moins à la valeur précisée. Les éléments retournés sont triés du plus petit au plus grand.  
  
> [!IMPORTANT]  
>  La fonction **BottomSum** , comme la fonction [Tops](../mdx/topsum-mdx.md) , interrompt toujours la hiérarchie.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne pour la catégorie Bikes (bicyclettes) le plus petit jeu de membres au niveau City (ville) de la hiérarchie Geography (zone géographique) dans la dimension Geography de l'année fiscale 2003 dont le total cumulé et obtenu à l'aide de la mesure Reseller Sales Amount (volume de vente du revendeur) correspond au moins à la somme de 50 000 (en commençant par les membres de jeu en question avec le nombre le plus faible de ventes) :  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
