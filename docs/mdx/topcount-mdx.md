---
title: TopCount (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0f607f3111c150bff3d5dc562c77901a381bedc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036602"
---
# <a name="topcount-mdx"></a>TopCount (MDX)


  Trie un jeu en ordre décroissant et retourne le nombre spécifié d'éléments avec les valeurs les plus élevées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Saut*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, la fonction **TopCount** trie, dans l’ordre décroissant, les tuples dans le jeu spécifié par le jeu spécifié en fonction de la valeur spécifiée par l’expression numérique, évaluée sur le jeu spécifié. Une fois le jeu trié, la fonction **TopCount** retourne le nombre spécifié de tuples ayant la valeur la plus élevée.  
  
> [!IMPORTANT]  
>  À l’instar de la fonction [BottomCount](../mdx/bottomcount-mdx.md) , la fonction **TopCount** interrompt toujours la hiérarchie.  
  
 Si aucune expression numérique n’est spécifiée, la fonction retourne le jeu de membres dans l’ordre naturel, sans aucun tri, qui se comporte comme la fonction [Head (MDX)](../mdx/head-mdx.md) .  
  
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
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
