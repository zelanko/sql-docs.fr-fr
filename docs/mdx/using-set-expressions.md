---
title: À l’aide d’Expressions de jeu | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- expressions [MDX], set
- tuples
- set expressions [MDX]
ms.assetid: 88d65872-0cbe-4c95-b36f-e1aa4ac8ed07
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 26ebed881d32bb9d550ae9630ee7b60cb15cd153
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="using-set-expressions"></a>Utilisation d'expressions de jeu
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Un jeu est constitué d'une liste triée de zéro tuple ou plus. Un jeu qui ne contient aucun tuple est appelé jeu vide.  
  
 L'expression complète d'un jeu est constituée de zéro ou de davantage de tuples spécifiés de manière explicite entre accolades :  
  
 {[{ *Tuple_expression* | *cet argument* } [, { *Tuple_expression* | *cet argument* }]...]}  
  
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
  
 {([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),  
  
 ([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),  
  
 ([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}  
  
 se compose de trois tuples, chacun contient deux références explicites aux membres sur la hiérarchie Product Categories de la dimension Product et la hiérarchie de calendrier de la dimension Date.  
  
 Pour obtenir des exemples de fonctions qui renvoient des jeux, consultez [utilisation des membres, Tuples et jeux &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
