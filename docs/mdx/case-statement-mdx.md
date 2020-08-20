---
description: Instruction CASE (MDX)
title: Instruction CASE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7a5907eb58fa102c46fa22af97116c4fad0f217a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466501"
---
# <a name="case-statement-mdx"></a>Instruction CASE (MDX)


  Permet de retourner des valeurs spécifiques à partir de plusieurs comparaisons sous certaines conditions. Il existe deux types d'instructions CASE :  
  
-   Une instruction CASE simple qui compare une expression à un jeu d'expressions simples pour retourner des valeurs spécifiques.  
  
-   Une instruction CASE recherchée qui évalue un jeu d'expressions booléennes pour retourner des valeurs spécifiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Simple Case Statement  
CASE [input_expression]  
WHEN when_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
  
Search Case Statement  
CASE   
WHEN Boolean_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
```  
  
## <a name="arguments"></a>Arguments  
 *input_expression*  
 Expression MDX (Multidimensional Expressions) résolue en valeur scalaire.  
  
 *when_expression*  
 Valeur scalaire spécifiée par rapport à laquelle l' *input_expression* est évaluée, qui, lorsqu’elle est évaluée sur true, retourne la valeur scalaire du *else_result_expression*.  
  
 *when_true_result_expression*  
 Valeur scalaire retournée lorsque la clause WHEN prend la valeur True.  
  
 *else_result_expression*  
 Valeur scalaire retournée si aucune des clauses WHEN ne prend la valeur True.  
  
 *Boolean_expression*  
 Expression MDX qui prend une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 S'il n'existe aucune clause ELSE et si toutes les clauses WHEN prennent la valeur false, le résultat est une cellule vide.  
  
## <a name="simple-case-expression"></a>Expression CASE simple  
 MDX évalue une expression case simple en résolvant le *input_expression* à une valeur scalaire. Cette valeur scalaire est ensuite comparée à la valeur scalaire de l' *when_expression*. Si les deux valeurs scalaires correspondent, l’instruction CASE retourne la valeur de l' *when_true_expression*. Si aucune correspondance n'est relevée, la clause WHEN suivante est évaluée. Si toutes les clauses WHEN ont la valeur false, la valeur de *else_result_expression* de la clause Else, le cas échéant, est retournée.  
  
 Dans l'exemple ci-dessous, la mesure Reseller Order Count (nombre de commandes du revendeur) est évaluée par rapport à plusieurs clauses WHEN et retourne un résultat fondé sur la valeur de la mesure Reseller Order Count pour chaque année. Pour les valeurs du nombre de commandes du revendeur qui ne correspondent pas à une valeur scalaire spécifiée dans un *when_expression* dans une clause when, la valeur scalaire de la *else_result_expression* est retournée.  
  
```  
WITH MEMBER [Measures].x AS   
CASE [Measures].[Reseller Order Count]  
   WHEN 0 THEN 'NONE'  
   WHEN 1 THEN 'SMALL'  
   WHEN 2 THEN 'SMALL'  
   WHEN 3 THEN 'MEDIUM'  
   WHEN 4 THEN 'MEDIUM'  
   WHEN 5 THEN 'LARGE'  
   WHEN 6 THEN 'LARGE'  
      ELSE 'VERY LARGE'  
END  
SELECT Calendar.[Calendar Year] on 0  
, NON EMPTY [Geography].[Postal Code].Members ON 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="searched-case-expression"></a>Expression CASE recherchée  
 Pour procéder à des évaluations plus complexes à l'aide de l'expression CASE, optez pour l'expression CASE recherchée. Cette variante de l'expression de recherche vous permet d'évaluer si une expression d'entrée s'inscrit dans une plage de valeurs. MDX évalue les clauses WHEN dans l'ordre de leur apparition dans l'instruction CASE.  
  
 Dans l’exemple suivant, la mesure Reseller Order Count est évaluée par rapport à la *Boolean_expression* spécifiée pour chaque clause when. Un résultat basé sur la valeur de la mesure Reseller Order Count pour chaque année est retourné. Du fait que les clauses WHEN sont évaluées dans l'ordre dans lequel elles apparaissent, toutes les valeurs supérieures à 6 peuvent aisément être affectées à la valeur « VERY LARGE » sans avoir à spécifier explicitement chaque valeur. Pour les valeurs du nombre de commandes du revendeur qui ne sont pas spécifiées dans une clause WHEN, la valeur scalaire de l' *else_result_expression* est retournée.  
  
```  
WITH MEMBER [Measures].x AS   
CASE   
   WHEN [Measures].[Reseller Order Count] > 6 THEN 'VERY LARGE'  
   WHEN [Measures].[Reseller Order Count] > 4 THEN 'LARGE'  
   WHEN [Measures].[Reseller Order Count] > 2 THEN 'MEDIUM'  
   WHEN [Measures].[Reseller Order Count] > 0 THEN 'SMALL'  
   ELSE "NONE"  
END  
SELECT Calendar.[Calendar Year] on 0,  
NON EMPTY [Geography].[Postal Code].Members on 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de script MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
