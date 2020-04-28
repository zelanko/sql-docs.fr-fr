---
title: Utilisation d’expressions Set | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1588d955e728830da4417160591a5c2b6c231473
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68893505"
---
# <a name="using-set-expressions"></a>Utilisation d'expressions de jeu


  Un jeu est constitué d'une liste triée de zéro tuple ou plus. Un jeu qui ne contient aucun tuple est appelé jeu vide.  
  
 L'expression complète d'un jeu est constituée de zéro ou de davantage de tuples spécifiés de manière explicite entre accolades :  
  
 {[{ *Tuple_expression* | *Member_expression* } [, { *Tuple_expression* | *Member_expression* }]...]}  
  
 Les expressions de membre spécifiées dans une expression de jeu sont converties en expressions de tuple à un membre.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant affiche deux expressions d'ensemble utilisées sur les axes des colonnes et des lignes d'une requête :  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Sur l'axe des colonnes, le jeu  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 se compose de deux membres de la dimension de mesures. Sur l'axe des lignes, le jeu  
  
 {([Produit]. [Product Categories]. [Category]. & [4], [date]. [Calendar]. [Année civile]. & [2004]),  
  
 ([Produit]. [Product Categories]. [Category]. & [1], [date]. [Calendar]. [Année civile]. & [2003]),  
  
 ([Produit]. [Product Categories]. [Category]. & [3], [date]. [Calendar]. [Année civile]. & [2004])}  
  
 se compose de trois tuples, chacun contient deux références explicites aux membres sur la hiérarchie Product Categories de la dimension Product et la hiérarchie de calendrier de la dimension Date.  
  
 Pour obtenir des exemples de fonctions qui retournent des jeux, consultez [utilisation de membres, de tuples et de jeux &#40;&#41;MDX ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx).  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
