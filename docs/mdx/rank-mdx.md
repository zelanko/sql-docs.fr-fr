---
title: Rank (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b1d234f02c8dfcd36073059210c1999cb95f5ab0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200662"
---
# <a name="rank-mdx"></a>Rank (MDX)


  Retourne le rang de base un d'un tuple dans un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Rank(Tuple_Expression, Set_Expression [ ,Numeric Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Tuple_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un tuple.  
  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, le **rang** fonction détermine le rang de base un pour le tuple spécifié en évaluant l’expression numérique spécifiée par rapport au tuple. Si une expression numérique est spécifiée, le **rang** fonction attribue le même rang aux tuples dotés de valeurs en double dans le jeu. L'attribution du même rang aux doublons affecte le rang des tuples suivants dans le jeu. Soit par exemple un jeu constitué des tuples suivants, `{(a,b), (e,f), (c,d)}` : le tuple `(a,b)` a la même valeur que le tuple `(c,d)`. Si le tuple `(a,b)` a le rang 1, alors `(a,b)` et `(c,d)` ont tous deux le rang 1. Toutefois, le tuple `(e,f)` aura un rang égal à 3. Il ne peut y avoir aucun tuple dans ce jeu avec un rang égal à 2.  
  
 Si une expression numérique n’est pas spécifiée, le **rang** fonction retourne la position ordinale de base un du tuple spécifié.  
  
 Le **rang** fonction ne trie pas le jeu.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne le jeu de tuples contenant les clients et les dates d’achat, à l’aide de la **filtre**, **NonEmpty**, **élément**, et **rang** fonctions pour rechercher la dernière date à laquelle chaque client a effectué un achat.  
  
```  
WITH SET MYROWS AS FILTER  
   (NONEMPTY  
      ([Customer].[Customer Geography].MEMBERS  
         * [Date].[Date].[Date].MEMBERS  
         , [Measures].[Internet Sales Amount]  
      ) AS MYSET  
   , NOT(MYSET.CURRENT.ITEM(0)  
      IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))  
   )  
SELECT [Measures].[Internet Sales Amount] ON 0,  
MYROWS ON 1  
FROM [Adventure Works]  
```  
  
 L’exemple suivant utilise le **ordre** (fonction), plutôt que la **rang** fonction, pour classer les membres de la hiérarchie City en fonction de la mesure Reseller Sales Amount et les affiche ensuite dans l’ordre de classement. À l’aide de la **ordre** de fonction à la première commande le jeu de membres de la hiérarchie City, le tri est effectué une seule fois et suivi par une analyse linéaire avant d’être présenté dans l’ordre de tri.  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Order &#40;MDX&#41;](../mdx/order-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
