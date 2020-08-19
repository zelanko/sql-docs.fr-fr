---
description: BottomCount (MDX)
title: BottomCount (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e331a84efe36cef11951afac3f304957e4ffcb00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494975"
---
# <a name="bottomcount-mdx"></a>BottomCount (MDX)


  Trie un jeu par ordre croissant et retourne le nombre de tuples spécifié dans le jeu concerné avec les valeurs les plus faibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BottomCount(Set_Expression, Count [,Numeric_Expression])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Count*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est précisée, cette fonction trie les tuples par ordre croissant dans le jeu spécifié en fonction de la valeur de cette expression numérique telle qu'évaluée sur le jeu. La fonction **BottomCount** retourne ensuite le nombre spécifié de tuples ayant la valeur la plus faible.  
  
> [!IMPORTANT]  
>  La fonction **BottomCount** , comme la fonction [TopCount](../mdx/topcount-mdx.md) , interrompt toujours la hiérarchie.  
  
 Si aucune expression numérique n’est spécifiée, la fonction retourne le jeu de membres dans l’ordre naturel, sans aucun tri, qui se comporte comme la fonction [tail (MDX)](../mdx/tail-mdx.md) .  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la mesure Reseller Order Quantity pour chaque année civile pour les cinq ventes de sous-catégorie de produit les plus basses classées selon la mesure Reseller Sales Amount.  
  
```  
SELECT BottomCount([Product].[Product Categories].[Subcategory].Members  
   , 10  
   , [Measures].[Reseller Sales Amount]) ON 0,  
   [Date].[Calendar].[Calendar Year].Members ON 1  
  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Reseller Order Quantity]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
