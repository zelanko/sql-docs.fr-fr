---
title: Utilisation des fonctions set | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 52e0c140acb944a774f5ab167bb81c662e3e32d7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038050"
---
# <a name="using-set-functions"></a>Utilisation de fonctions de jeu


  Une fonction de jeu récupère un jeu à partir d'une dimension, d'une hiérarchie, ou d'un niveau, ou encore en parcourant les emplacements absolus et relatifs des membres contenus dans ces objets et en construisant des jeux de différentes manières.  
  
 Les fonctions de jeu, comme les fonctions de membre et de tuple, sont essentielles à la négociation des structures multidimensionnelles présentes dans Analysis Services. Elles sont également essentielles pour l'obtention de résultats à partir de requêtes MDX (Multidimensional Expressions), car les expressions de jeu définissent les axes d'une requête MDX.  
  
 L’une des fonctions d’ensemble les plus courantes est les [membres &#40;définir&#41; &#40;fonction&#41;MDX](../mdx/members-set-mdx.md) , qui récupère un jeu contenant tous les membres d’une dimension, d’une hiérarchie ou d’un niveau. Ce qui suit est un exemple de son utilisation dans une requête :  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns all of the members on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Une autre fonction couramment utilisée est la fonction [Crossjoin &#40;&#41;MDX](../mdx/crossjoin-mdx.md) . Elle retourne un jeu de tuples qui représente le produit cartésien des jeux passés dans celui-ci comme paramètres. En termes pratiques, cette fonction vous permet de créer des axes « imbriqués » ou de « tableau croisé dynamique » dans les requêtes :  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns a set containing every combination of all of the members`  
  
 `//on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension and all of the members on the Category level`  
  
 `//of the Category hierarchy on the Product dimension`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 La fonction des [descendants &#40;MDX&#41;](../mdx/descendants-mdx.md) est similaire à la fonction **Children** , mais elle est plus puissante. Elle retourne les descendants de tout membre à un ou plusieurs niveaux dans une hiérarchie :  
  
 SELECT  
  
 [Measures].[Internet Sales Amount]  
  
 ON Columns,  
  
 //Retourne un jeu qui contient toutes les dates sous l'année civile  
  
 //2004 dans la hiérarchie de calendrier de la dimension Date  
  
 DESCENDANTS(  
  
 [Date]. [Calendar]. [Année civile]. & [2004]  
  
 , [Date].[Calendar].[Date])  
  
 ON Rows  
  
 FROM [Adventure Works]  
  
 La fonction [order &#40;MDX&#41;](../mdx/order-mdx.md) vous permet de trier le contenu d’un jeu dans l’ordre croissant ou décroissant en fonction d’une expression numérique particulière. La requête suivante retourne les mêmes membres sur les lignes que la requête précédente, mais elle les classe désormais selon la mesure Internet Sales Amount (volume de vente Internet) :  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//ordered by Internet Sales Amount`  
  
 `ORDER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount], BDESC)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Cette requête illustre également comment le jeu retourné par une fonction de jeu, Descendants, peut être passé comme un paramètre à une autre fonction de jeu, Order.  
  
 Le filtrage d’un jeu en fonction de certains critères est très utile lors de l’écriture de requêtes. à cette fin, vous pouvez utiliser la fonction [Filter &#40;&#41;MDX](../mdx/filter-mdx.md) , comme illustré dans l’exemple suivant :  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//where Internet Sales Amount is greater than $70000`  
  
 `FILTER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount]>70000)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 D'autres fonctions plus sophistiquées existent et vous permettent de filtrer un jeu d'autres manières. Par exemple, la requête suivante affiche la fonction [topcount &#40;&#41;MDX](../mdx/topcount-mdx.md) retourne les n premiers éléments d’un jeu :  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing the top 10 Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension by Internet Sales Amount`  
  
 `TOPCOUNT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,10, [Measures].[Internet Sales Amount])`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Enfin, il est possible d’effectuer un certain nombre d’opérations Set logiques à l’aide de fonctions telles que [Intersect &#40;mdx&#41;](../mdx/intersect-mdx.md), [Union &#40;MDX&#41;](../mdx/union-mdx.md) et, [à l’exception](../mdx/except-mdx-function.md) des fonctions &#40;MDX&#41;. La requête suivante affiche des exemples de ces deux dernières fonctions :  
  
 `SELECT`  
  
 `//Returns a set containing the Measures Internet Sales Amount, Internet Tax Amount and`  
  
 `//Internet Total Product Cost`  
  
 `UNION(`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}`  
  
 `, {[Measures].[Internet Total Product Cost]}`  
  
 `)`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//except the January 1st 2004`  
  
 `EXCEPT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,{[Date].[Calendar].[Date].&[915]})`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [Utilisation des fonctions membres](../mdx/using-member-functions.md)   
 [Utilisation de fonctions de tuple](../mdx/using-tuple-functions.md)  
  
  
