---
description: TopSum (MDX)
title: TopS (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 665a1ace9df98303da19b861cdd3ce6340ec8368
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412902"
---
# <a name="topsum-mdx"></a>TopSum (MDX)


  Trie un jeu et retourne les éléments situés le plus en haut, dont le total cumulatif est au moins une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Valeur*  
 Expression numérique valide qui précise la valeur par rapport à laquelle chaque tuple est comparé.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) qui retourne une mesure.  
  
## <a name="remarks"></a>Notes  
 La fonction **Tops** calcule la somme d’une mesure spécifiée évaluée sur un jeu spécifié, en triant le jeu dans l’ordre décroissant. Elle retourne ensuite les éléments dotés des valeurs les plus élevées dont le total de l'expression numérique spécifiée correspond au moins à la valeur indiquée. Enfin, elle retourne le plus petit sous-ensemble d'un jeu dont le total cumulé est égal au moins à la valeur précisée. Les éléments retournés sont triés du plus grand au plus petit.  
  
> [!IMPORTANT]  
>  À l’instar de la fonction [BottomSum](../mdx/bottomsum-mdx.md) , la fonction **Tops** arrête toujours la hiérarchie.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne pour la catégorie Bikes (bicyclettes) le plus petit jeu de membres au niveau City (ville) de la hiérarchie Geography (zone géographique) dans la dimension Geography dont le total cumulé et obtenu à l'aide de la mesure Reseller Sales Amount (volume de vente du revendeur) correspond au moins à la somme de 6 000 000 (en commençant par les membres de jeu en question avec le nombre de ventes le plus important).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
