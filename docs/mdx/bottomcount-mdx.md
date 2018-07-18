---
title: BottomCount (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 424c928f64b784070520f4cebe450dd5465fea41
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739778"
---
# <a name="bottomcount-mdx"></a>BottomCount (MDX)


  Trie un jeu par ordre croissant et retourne le nombre de tuples spécifié dans le jeu concerné avec les valeurs les plus faibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BottomCount(Set_Expression, Count [,Numeric_Expression])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Nombre*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est précisée, cette fonction trie les tuples par ordre croissant dans le jeu spécifié en fonction de la valeur de cette expression numérique telle qu'évaluée sur le jeu. Le **BottomCount** fonction puis retourne le nombre spécifié de tuples avec la valeur la plus faible.  
  
> [!IMPORTANT]  
>  Le **BottomCount** fonction, comme le [TopCount](../mdx/topcount-mdx.md) de fonction, la hiérarchie.  
  
 Si une expression numérique n’est pas spécifiée, la fonction retourne le jeu de membres dans l’ordre naturel sans effectuer de tri, que le [Tail (MDX)](../mdx/tail-mdx.md) (fonction).  
  
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
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
