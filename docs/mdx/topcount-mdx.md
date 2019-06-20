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
manager: kfile
ms.openlocfilehash: fa8edcf8af510a41affdcbcc9924edf69cf4c220
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63228046"
---
# <a name="topcount-mdx"></a>TopCount (MDX)


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
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, le **TopCount** fonction trie, par ordre décroissant, les tuples dans le jeu spécifié par le jeu spécifié en fonction de la valeur spécifiée par l’expression numérique, telle qu’évaluée sur le texte spécifié ensemble. Une fois le jeu trié, la **TopCount** fonction puis retourne le nombre spécifié de tuples avec la valeur la plus élevée.  
  
> [!IMPORTANT]  
>  Comme le [BottomCount](../mdx/bottomcount-mdx.md) (fonction), le **TopCount** fonction respecte jamais la hiérarchie.  
  
 Si une expression numérique n’est pas spécifiée, la fonction retourne le jeu de membres dans l’ordre naturel sans effectuer de tri, qui se comporte comme la [Head (MDX)](../mdx/head-mdx.md) (fonction).  
  
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
