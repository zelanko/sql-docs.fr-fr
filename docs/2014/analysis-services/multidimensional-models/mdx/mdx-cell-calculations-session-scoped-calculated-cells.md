---
title: Création de cellules calculées au niveau de la session | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 199de07778a153cd1bc40b5033d364e5e0055bd3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546431"
---
# <a name="creating-session-scoped-calculated-cells"></a>Création de cellules calculées au niveau de la session
    
> [!IMPORTANT]  
>  Cette syntaxe est déconseillée. Il est conseillé d'utiliser plutôt les assignations MDX. Pour plus d’informations sur les assignations, consultez [Script MDX de base &#40;MDX&#41;](the-basic-mdx-script-mdx.md).  
  
 Pour créer des cellules calculées mises à la disposition de l'ensemble des requêtes au cours de la même session, vous pouvez utiliser l'instruction [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) ou l'instruction [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) . Ces deux instructions génèrent le même résultat.  
  
## <a name="create-cell-calculation-syntax"></a>Syntaxe de l'instruction CREATE CELL CALCULATION  
  
> [!IMPORTANT]  
>  Cette syntaxe est déconseillée. Il est conseillé d'utiliser plutôt les assignations MDX. Pour plus d’informations sur les assignations, consultez [Script MDX de base &#40;MDX&#41;](the-basic-mdx-script-mdx.md).  
  
 Utilisez la syntaxe suivante pour définir une cellule calculée au niveau de la session à l'aide de l'instruction CREATE CELL CALCULATION :  
  
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
  
## <a name="alter-cube-syntax"></a>Syntaxe de l'instruction ALTER CUBE  
  
> [!IMPORTANT]  
>  Cette syntaxe est déconseillée. Il est conseillé d'utiliser plutôt les assignations MDX. Pour plus d’informations sur les assignations, consultez [Script MDX de base &#40;MDX&#41;](the-basic-mdx-script-mdx.md).  
  
 Utilisez la syntaxe suivante pour définir une cellule calculée au niveau de la session à l'aide de l'instruction ALTER CUBE :  
  
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
  
|Category|Description|  
|--------------|-----------------|  
|Jeu vide|Expression de jeu MDX qui prend la valeur d'un ensemble vide. Dans ce cas, la portée de la cellule calculée est l'intégralité du cube.|  
|Jeu à un seul membre|Expression de jeu MDX qui prend la valeur d'un seul membre.|  
|Jeu de membres de niveau|Expression de jeu MDX qui prend la valeur des membres d'un même niveau. L' *Level_Expression*en est un exemple.`Members` Fonction MDX. Pour inclure des membres calculés, utilisez l' *Level_Expression*.`AllMembers` Fonction MDX.<br /><br /> Pour plus d’informations, consultez [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).|  
|Jeu de descendants|Expression de jeu MDX qui prend la valeur des descendants d'un membre spécifié. Par exemple `Descendants` , la fonction MDX (*Member_Expression*, *Level_Expression*, *Desc_Flag*).<br /><br /> Pour plus d’informations, consultez [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).|  
  
## <a name="see-also"></a>Voir aussi  
 [Création de calculs de cellules à l’aide de la syntaxe MDX &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
