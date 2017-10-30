---
title: BottomCount (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BOTTOMCOUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- BottomCount function
ms.assetid: 1441dab3-7885-4e92-9d48-21d832286677
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 972ec04cf1a64e5e2a20b0befa4c85afd31631de
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="bottomcount-mdx"></a>BottomCount (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Trie un jeu par ordre croissant et retourne le nombre de tuples spécifié dans le jeu concerné avec les valeurs les plus faibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BottomCount(Set_Expression, Count [,Numeric_Expression])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Compter*  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

