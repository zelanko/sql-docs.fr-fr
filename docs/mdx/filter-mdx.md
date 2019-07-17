---
title: Filtre (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3a70bceed4cdccf6a22f0cfea4e5093634f88f1f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132689"
---
# <a name="filter-mdx"></a>Filter (MDX)


  Retourne le jeu résultant du filtrage d'un jeu spécifié selon une condition de recherche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Logical_Expression*  
 Expression logique MDX (Multidimensional Expressions) valide qui prend la valeur True ou False.  
  
## <a name="remarks"></a>Notes  
 Le **filtre** fonction évalue l’expression logique spécifiée par rapport à chaque tuple dans le jeu spécifié. La fonction retourne un jeu composé de chaque tuple dans le jeu spécifié où l’expression logique prend la valeur **true**. Si aucun tuple donnent comme résultat **true**, un ensemble vide est retourné.  
  
 Le **filtre** fonction fonctionne de manière similaire à celle de la [IIf](../mdx/iif-mdx.md) (fonction). Le **IIf** fonction retourne uniquement une des deux options en fonction de l’évaluation d’une expression logique MDX, tandis que le **filtre** fonction retourne un jeu de tuples qui remplissent la condition de recherche spécifié. En effet, le **filtre** fonction exécute `IIf(Logical_Expression, Set_Expression.Current, NULL)` sur chaque tuple du jeu et retourne le jeu obtenu.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre l'utilisation de la fonction Filter sur l'axe des lignes d'une requête afin de retourner uniquement les dates où le Montant des ventes sur Internet est supérieur à $10 000 :  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 La fonction Filter peut également s'utiliser à l'intérieur des définitions de membre calculées. L’exemple suivant retourne la somme de la `Measures.[Order Quantity]` membre, agrégé sur les neuf premiers mois de 2003 contenus dans le `Date` dimension, à partir de la **Adventure Works** cube. Le **PeriodsToDate** fonction définit les tuples dans le jeu sur lequel le **agrégation** fonction s’exécute. Le **filtre** fonction limite les tuples retournés à ceux ayant des valeurs inférieures de la mesure Reseller Sales Amount pour la période précédente.  
  
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
  
  
