---
title: Utilisation des membres, Tuples et jeux (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDX [Analysis Services], tuples
- member keys [MDX]
- MDX [Analysis Services], sets
- calculated members [MDX]
- members [MDX]
- Multidimensional Expressions [Analysis Services], members
- named sets [MDX]
- Multidimensional Expressions [Analysis Services], tuples
- member functions [MDX]
- sets [MDX]
- MDX [Analysis Services], members
- member names [MDX]
- Multidimensional Expressions [Analysis Services], sets
- tuple functions
- tuples
- set functions [MDX]
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c5929d1c9d926005cd919d4e939e46c950723b64
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="working-with-members-tuples-and-sets-mdx"></a>Utilisation de membres, de tuples et de jeux (MDX)
  MDX fournit de nombreuses fonctions chargées de retourner un ou plusieurs membres, tuples ou jeux ou conçues pour agir sur un membre, un tuple ou un jeu donné.  
  
## <a name="member-functions"></a>Fonctions de membre  
 MDX intègre plusieurs fonctions à l'aide desquelles vous pouvez extraire des membres d'autres entités MDX, notamment des dimensions, des niveaux, des jeux ou des tuples. Par exemple, la fonction [FirstChild](../../../mdx/firstchild-mdx.md) est une fonction qui agit sur un membre et retourne un membre.  
  
 Pour obtenir le premier membre enfant de la dimension Time, vous pouvez le définir explicitement, comme le montre l'exemple suivant :  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 Vous pouvez également utiliser la fonction **FirstChild** pour retourner ce même membre, comme dans l’exemple ci-dessous.  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 Pour plus d’informations sur les fonctions de membre MDX, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="tuple-functions"></a>fonctions de tuple  
 MDX fournit plusieurs fonctions permettant de retourner des tuples ; ces fonctions peuvent être utilisées partout où un tuple est accepté. Par exemple, vous pouvez utiliser la fonction [Item &#40;Tuple&#41; &#40;MDX&#41;](../../../mdx/item-tuple-mdx.md) pour extraire le premier tuple du jeu, ce qui est très utile lorsque vous savez qu’un jeu est composé d’un seul tuple et souhaitez fournir ce tuple à une fonction qui en nécessite un.  
  
 L'exemple ci-dessous retourne le premier tuple du jeu de tuples dans l'axe des colonnes.  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 Pour plus d’informations sur les fonctions de tuple, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="set-functions"></a>Fonctions de jeu  
 MDX fournit plusieurs fonctions qui retournent des jeux. Pour extraire un jeu, il existe d'autres méthodes que la spécification explicite de tuples et leur mise entre accolades. Pour plus d’informations sur l’utilisation des fonctions de membre pour retourner un jeu, consultez [Concepts clés dans MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md). Il existe beaucoup d'autres fonctions de jeu.  
  
 L'opérateur deux points (:) permet d'utiliser l'ordre naturel des membres pour créer un jeu. Par exemple, le jeu illustré dans l'exemple suivant contient des tuples pour les trimestres 1 à 4 (Q1 et Q4) de l'année civile 2002.  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 Si vous n'utilisez pas l'opérateur deux points pour créer le jeu, vous pouvez créer le même jeu de membres en spécifiant les tuples dans l'exemple suivant :  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 L'opérateur deux points est une fonction inclusive. Les membres situés de part et d'autre de celui-ci sont inclus dans le jeu de résultats.  
  
 Pour plus d’informations sur les fonctions de jeu, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="array-functions"></a>Fonctions de tableau  
 Une fonction de tableau agit sur un jeu et retourne un tableau. Pour plus d’informations sur les fonctions de tableau, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="hierarchy-functions"></a>Fonctions de hiérarchie  
 Une fonction de hiérarchie retourne une hiérarchie en agissant sur un membre, un niveau, une hiérarchie ou une chaîne. Pour plus d’informations sur les fonctions de hiérarchie, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="level-functions"></a>Fonctions de niveau  
 Une fonction de niveau retourne un niveau en agissant sur un membre, un niveau ou une chaîne. Pour plus d’informations sur les fonctions de niveau, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="logical-functions"></a>Fonctions logiques  
 Une fonction logique agit sur une expression MDX pour retourner des informations sur les tuples, les membres ou les jeux au sein de l'expression. Par exemple, la fonction [IsEmpty &#40;MDX&#41;](../../../mdx/isempty-mdx.md) évalue si une expression a retourné une valeur de cellule vide. Pour plus d’informations sur les fonctions logiques, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="numeric-functions"></a>Fonctions numériques  
 Une fonction numérique agit sur une expression MDX pour retourner une valeur scalaire. Par exemple, la fonction [Aggregate &#40;MDX&#41;](../../../mdx/aggregate-mdx.md) retourne une valeur scalaire calculée en agrégeant des mesures sur les tuples dans un jeu spécifique. Pour plus d’informations sur les fonctions numériques, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="string-functions"></a>Fonctions de chaîne  
 Une fonction de chaîne agit sur une expression MDX pour retourner une chaîne. Par exemple, la fonction [UniqueName &#40;MDX&#41;](../../../mdx/uniquename-mdx.md) retourne une valeur de chaîne qui contient le nom unique d’une dimension, d’une hiérarchie, d’un niveau ou d’un membre. Pour plus d’informations sur les fonctions de chaîne, consultez [Guide de référence des fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés dans MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [Principes de base de requête MDX &#40; Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  
