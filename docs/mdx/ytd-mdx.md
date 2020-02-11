---
title: AAJ (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2e3fcd823dea5d651cd7be9295fa4c6bba25380c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125761"
---
# <a name="ytd-mdx"></a>Ytd (MDX)


  Retourne un jeu de membres frères du même niveau qu’un membre donné, en commençant par le premier frère et en terminant par le membre donné, conformément à la limite du niveau *year* de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si une expression de membre n’est pas spécifiée, la valeur par défaut est le membre actuel de la première hiérarchie avec un niveau de type *years* dans la première dimension de type *Time* dans le groupe de mesures.  
  
 La fonction **AAJ** est une fonction de raccourci pour la fonction [PeriodsToDate](../mdx/periodstodate-mdx.md) dans laquelle la propriété type de la hiérarchie d’attribut sur laquelle le niveau est basé est définie sur *years*. Ce qui signifie que `Ytd(Member_Expression)` est équivalent à `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Notez que cette fonction ne fonctionnera pas lorsque la propriété type est définie sur *FiscalYears*.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne la somme du `Measures.[Order Quantity]` membre, agrégée sur les huit premiers mois de l’année civile 2003 qui sont contenus dans la `Date` dimension, à partir du cube **Adventure Works** .  
  
```  
WITH MEMBER [Date].[Calendar].[First8MonthsCY2003] AS  
    Aggregate(  
        YTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First8MonthsCY2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 **AAD** est fréquemment utilisé conjointement avec aucun paramètre spécifié, ce qui signifie que la fonction [CurrentMember &#40;MDX&#41;](../mdx/currentmember-mdx.md) affichera un total cumulé de cumul annuel jusqu’à ce jour dans un rapport, comme le montre la requête suivante :  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
