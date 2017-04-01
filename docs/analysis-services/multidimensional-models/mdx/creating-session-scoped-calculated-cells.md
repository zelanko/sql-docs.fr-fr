---
title: "Cr&#233;ation de cellules calcul&#233;es au niveau de la session | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "membres calculés au niveau de la session [MDX]"
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Cr&#233;ation de cellules calcul&#233;es au niveau de la session
    
> [!IMPORTANT]  
>  Cette syntaxe est déconseillée. Il est conseillé d'utiliser plutôt les assignations MDX. Pour plus d’informations sur les assignations, consultez [Script MDX de base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Pour créer des cellules calculées mises à la disposition de l'ensemble des requêtes au cours de la même session, vous pouvez utiliser l'instruction [CREATE CELL CALCULATION](../Topic/CREATE%20CELL%20CALCULATION%20Statement%20\(MDX\).md) ou l'instruction [ALTER CUBE](../Topic/ALTER%20CUBE%20Statement%20\(MDX\).md) . Ces deux instructions génèrent le même résultat.  
  
## Syntaxe de l'instruction CREATE CELL CALCULATION  
  
> [!IMPORTANT]  
>  Cette syntaxe est déconseillée. Il est conseillé d'utiliser plutôt les assignations MDX. Pour plus d’informations sur les assignations, consultez [Script MDX de base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Utilisez la syntaxe suivante pour définir une cellule calculée au niveau de la session à l'aide de l'instruction CREATE CELL CALCULATION :  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## Syntaxe de l'instruction ALTER CUBE  
  
> [!IMPORTANT]  
>  Cette syntaxe est déconseillée. Il est conseillé d'utiliser plutôt les assignations MDX. Pour plus d’informations sur les assignations, consultez [Script MDX de base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Utilisez la syntaxe suivante pour définir une cellule calculée au niveau de la session à l'aide de l'instruction ALTER CUBE :  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 La valeur `String_Expression` contient une liste d'expressions de jeu MDX unidimensionnelles et orthogonales dont chacune doit prendre la valeur de l'une des catégories de jeux répertoriées dans le tableau suivant.  
  
|Catégorie|Description|  
|--------------|-----------------|  
|Jeu vide|Expression de jeu MDX qui prend la valeur d'un ensemble vide. Dans ce cas, la portée de la cellule calculée est l'intégralité du cube.|  
|Jeu à un seul membre|Expression de jeu MDX qui prend la valeur d'un seul membre.|  
|Jeu de membres de niveau|Expression de jeu MDX qui prend la valeur des membres d'un même niveau. La fonction MDX *Level_Expression*.**Members** en est un exemple. Pour inclure des membres calculés, utilisez la fonction MDX *Level_Expression*.**AllMembers**.<br /><br /> Pour plus d’informations, consultez [AllMembers &#40;MDX&#41;](../../../mdx/allmembers-mdx.md).|  
|Jeu de descendants|Expression de jeu MDX qui prend la valeur des descendants d'un membre spécifié. La fonction MDX **Descendants**(*Member_Expression*, *Level_Expresion*, *Desc_Flag*) en est un exemple.<br /><br /> Pour plus d’informations, consultez [Descendants &#40;MDX&#41;](../../../mdx/descendants-mdx.md).|  
  
## Voir aussi  
 [Création de calculs de cellules à l’aide de la syntaxe MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-cell-calculations-in-mdx-mdx.md)  
  
  