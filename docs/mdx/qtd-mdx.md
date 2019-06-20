---
title: Qtd (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 182a86a05cd0dae6adf85d2168fe884ace910a82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63278421"
---
# <a name="qtd-mdx"></a>Qtd (MDX)


  Retourne un jeu des frères membres d’un même niveau qu’un membre donné, en commençant par le premier frère et se terminant par le membre donné, en tant que contrainte par la *trimestre* au niveau de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si un membre expressionis sauf indication contraire, la valeur par défaut est le membre actuel de la première hiérarchie avec un niveau de type *trimestres* dans la première dimension de type *temps* dans le groupe de mesures.  
  
 Le **Qtd** fonction est un raccourci pour le [PeriodsToDate &#40;MDX&#41; ](../mdx/periodstodate-mdx.md) dont l’argument expression de niveau a la valeur de fonction *trimestre*. Ce qui signifie que `Qtd(Member_Expression)` est fonctionnellement équivalent à `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne la somme de la `Measures.[Order Quantity]` membre, agrégé sur les deux premiers mois du troisième trimestre de l’année civile 2003 qui figurent dans le `Date` dimension, à partir de la **Adventure Works** cube.  
  
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
  
  
