---
description: Qtd (MDX)
title: Taj (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea3bd80fa85d95dd3adf52793d5895425b40b9fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500452"
---
# <a name="qtd-mdx"></a>Qtd (MDX)


  Retourne un jeu de membres frères du même niveau qu’un membre donné, en commençant par le premier frère et en terminant par le membre donné, conformément à la limite du niveau *Quarter* de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si une expression de membre n’est pas spécifiée, la valeur par défaut est le membre actuel de la première hiérarchie avec un niveau de type *trimestres* dans la première dimension de type *Time* dans le groupe de mesures.  
  
 La fonction **Taj** est une fonction de raccourci pour la fonction de [&#41;de PeriodsToDate &#40;MDX ](../mdx/periodstodate-mdx.md) dont l’argument d’expression de niveau est défini sur *Quarter*. Ce qui signifie que `Qtd(Member_Expression)` est fonctionnellement équivalent à `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne la somme du `Measures.[Order Quantity]` membre, agrégée sur les deux premiers mois du troisième trimestre de l’année civile 2003 qui sont contenus dans la `Date` dimension, à partir du cube **Adventure Works** .  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        QTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
