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
ms.openlocfilehash: 1081cacd0676f4eb0512780e9ddc7641edb99ca1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037072"
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
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, la fonction **Rank** détermine le classement de base 1 pour le tuple spécifié en évaluant l’expression numérique spécifiée par rapport au tuple. Si une expression numérique est spécifiée, la fonction **Rank** assigne le même rang aux tuples avec des valeurs dupliquées dans le jeu. L'attribution du même rang aux doublons affecte le rang des tuples suivants dans le jeu. Soit par exemple un jeu constitué des tuples suivants, `{(a,b), (e,f), (c,d)}` : le tuple `(a,b)` a la même valeur que le tuple `(c,d)`. Si le tuple `(a,b)` a le rang 1, alors `(a,b)` et `(c,d)` ont tous deux le rang 1. Toutefois, le tuple `(e,f)` aura un rang égal à 3. Il ne peut y avoir aucun tuple dans ce jeu avec un rang égal à 2.  
  
 Si aucune expression numérique n’est spécifiée, la fonction **Rank** retourne la position ordinale de base un du tuple spécifié.  
  
 La fonction **Rank** n’ordonne pas l’ensemble.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne le jeu de tuples contenant les clients et les dates d’achat, à l’aide des fonctions **filtre**, non **vide**, **élément**et **rang** pour rechercher la dernière date à laquelle chaque client a effectué un achat.  
  
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
  
 L’exemple suivant utilise la fonction **Order** , plutôt que la fonction **Rank** , pour classer les membres de la hiérarchie City en fonction de la mesure Reseller Sales Amount, puis les affiche dans l’ordre de classement. En utilisant la fonction **Order** pour trier en premier le jeu de membres de la hiérarchie City, le tri n’est effectué qu’une seule fois et suivi d’une analyse linéaire avant d’être présenté dans l’ordre de tri.  
  
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
 [Ordre &#40;&#41;MDX](../mdx/order-mdx.md)   
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
