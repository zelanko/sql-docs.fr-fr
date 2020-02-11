---
title: Utilisation d’expressions scalaires | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b87fad1b9c568f4ebd5f65ef3705001b12d26693
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038040"
---
# <a name="using-scalar-expressions"></a>Utilisation d'expressions scalaires


  Dans la syntaxe MDX (Multidimensional Expressions), une expression scalaire est un élément qui, lorsqu'il est évalué, retourne une valeur unique au sein du contexte d'évaluation.  
  
 Dans la syntaxe MDX, les expressions scalaires comprennent des expressions de chaîne, numériques et de date.  
  
 Les expressions scalaires sont utilisées en général dans les définitions de membre calculé, étant donné que les membres calculés doivent renvoyer une valeur scalaire. La requête suivante affiche des exemples de membres calculés sur la dimension de mesures qui utilise différents types d'expression scalaire :  
  
 `WITH`  
  
 `MEMBER MEASURES.NumericValue AS 10`  
  
 `MEMBER MEASURES.NumericExpression AS 10 + 10`  
  
 `MEMBER MEASURES.NumericExpressionBasedOnMeasure AS [Measures].[Internet Sales Amount] + 10`  
  
 `MEMBER MEASURES.StringValue AS "10"`  
  
 `MEMBER MEASURES.ConcatenatedString AS "10" + "10"`  
  
 `MEMBER MEASURES.StringFunction AS MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.TodaysDate AS NOW()`  
  
 `SELECT`  
  
 `{MEASURES.NumericValue,MEASURES.NumericExpression,MEASURES.NumericExpressionBasedOnMeasure,`  
  
 `MEASURES.StringValue, MEASURES.ConcatenatedString, MEASURES.StringFunction, MEASURES.TodaysDate}`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 Le seul type de données que peut retourne une mesure, calculée ou autre, est le type OLE Variant. Par conséquent, vous devrez parfois effectuer un cast d'une valeur de mesure en un type particulier pour obtenir le comportement attendu. La requête suivante en donne une illustration :  
  
```  
WITH  
//Two calculated measures that return strings  
MEMBER MEASURES.NumericString1 AS "10"  
MEMBER MEASURES.NumericString2 AS "10"  
//In this case, the + operator acts to concatenate the strings  
MEMBER MEASURES.Concatenation AS MEASURES.NumericString1 + MEASURES.NumericString2  
//Casting one value to an integer with the CINT function causes the second measure  
//to be treated as an integer too, so that the + operator now acts to add the values  
MEMBER MEASURES.Addition AS CINT(MEASURES.NumericString1) + MEASURES.NumericString2  
SELECT  
{MEASURES.NumericString1,MEASURES.NumericString2,MEASURES.Concatenation,MEASURES.Addition }  
ON COLUMNS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
