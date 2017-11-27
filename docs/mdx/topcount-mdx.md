---
title: TopCount (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TOPCOUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- TopCount function
ms.assetid: 15026a8f-35c5-4307-8856-348f5c44bfd5
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 09b3d169600622822b2d3e5a78ad72c3164efcb9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="topcount-mdx"></a>TopCount (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Trie un jeu en ordre décroissant et retourne le nombre spécifié d'éléments avec les valeurs les plus élevées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Compter*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, la **TopCount** fonction trie, par ordre décroissant, les tuples dans le jeu spécifié par le jeu spécifié en fonction de la valeur spécifiée par l’expression numérique, telle qu’évaluée sur le jeu spécifié. Une fois le jeu trié, la **TopCount** fonction puis retourne le nombre spécifié de tuples avec la valeur la plus élevée.  
  
> [!IMPORTANT]  
>  Comme le [BottomCount](../mdx/bottomcount-mdx.md) (fonction), la **TopCount** fonction respecte jamais la hiérarchie.  
  
 Si une expression numérique n’est pas spécifiée, la fonction retourne le jeu de membres dans l’ordre naturel sans effectuer de tri, que le [Head (MDX)](../mdx/head-mdx.md) (fonction).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les 10 premières dates par Montant des ventes sur Internet :  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 L'exemple ci-dessous retourne pour la catégorie Bikes (bicyclettes) les cinq premiers membres du jeu contenant toutes les combinaisons de membres du niveau City (ville) de la hiérarchie Geography (zone géographique) dans la dimension Geography et toutes les années fiscales de la hiérarchie Fiscal de la dimension Date classés à l'aide de la mesure Reseller Sales Amount (volume de vente du revendeur) en commençant par les membres du jeu en question qui affichent le plus grand nombre de ventes.  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

