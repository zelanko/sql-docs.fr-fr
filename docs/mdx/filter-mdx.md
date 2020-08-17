---
description: Filter (MDX)
title: Filtre (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 026e4720803d828ae9ba96a4d3df7f5a72d59e8d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387505"
---
# <a name="filter-mdx"></a>Filter (MDX)


  Retourne le jeu résultant du filtrage d'un jeu spécifié selon une condition de recherche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Logical_Expression*  
 Expression logique MDX (Multidimensional Expressions) valide qui prend la valeur True ou False.  
  
## <a name="remarks"></a>Notes  
 La fonction **Filter** évalue l’expression logique spécifiée par rapport à chaque tuple dans le jeu spécifié. La fonction retourne un jeu qui se compose de chaque tuple dans le jeu spécifié, où l’expression logique prend la **valeur true**. Si aucun tuple ne prend la **valeur true**, un jeu vide est retourné.  
  
 La fonction **Filter** fonctionne de manière similaire à celle de la fonction [IIf](../mdx/iif-mdx.md) . La fonction **IIf** retourne une seule des deux options en fonction de l’évaluation d’une expression logique MDX, tandis que la fonction **Filter** retourne un jeu de tuples qui répondent à la condition de recherche spécifiée. En effet, la fonction de **filtre** s’exécute `IIf(Logical_Expression, Set_Expression.Current, NULL)` sur chaque tuple du jeu et retourne le jeu résultant.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre l'utilisation de la fonction Filter sur l'axe des lignes d'une requête afin de retourner uniquement les dates où le Montant des ventes sur Internet est supérieur à $10 000 :  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 La fonction Filter peut également s'utiliser à l'intérieur des définitions de membre calculées. L’exemple suivant retourne la somme du `Measures.[Order Quantity]` membre, agrégée sur les neuf premiers mois de 2003 contenus dans la `Date` dimension, à partir du cube **Adventure Works** . La fonction **PeriodsToDate** définit les tuples dans le jeu sur lequel opère la fonction d' **agrégation** . La fonction **Filter** limite les tuples qui sont retournés à ceux dont les valeurs sont inférieures pour la mesure Reseller Sales Amount pour la période précédente.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
