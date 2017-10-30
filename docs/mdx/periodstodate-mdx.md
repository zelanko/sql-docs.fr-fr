---
title: PeriodsToDate (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PERIODSTODATE
dev_langs:
- kbMDX
helpviewer_keywords:
- PeriodsToDate function
ms.assetid: 43b9f69c-7b8c-4de0-9c4b-778ae766f74e
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bc87b6be3a34f106784a8113eccb5dc5e75bd32c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="periodstodate-mdx"></a>PeriodsToDate (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne un jeu des membres frères de même niveau qu'un membre donné, commençant par le premier frère et se terminant par le membre donné, conformément à la contrainte du niveau spécifié de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PeriodsToDate( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Dans l’étendue du niveau spécifié, le **PeriodsToDate** fonction retourne le jeu de périodes au même niveau que le membre spécifié, en commençant par la première période et se terminant par un membre spécifié.  
  
-   Si un niveau est spécifié, le membre actuel de la hiérarchie est inféré *hiérarchie*. **CurrentMember**, où *hiérarchie*correspond à la hiérarchie du niveau spécifié.  
  
-   Si ni un niveau ni un membre n'est spécifié, le niveau est le niveau parent du membre actuel de la première hiérarchie sur la première dimension de type Time dans le groupe de mesures.  
  
 `PeriodsToDate( Level_Expression, Member_Expression )` est fonctionnellement équivalent à l'expression MDX suivante :  
  
 `TopCount(Descendants(Ancestor(Member_Expression, Level_Expression), Member_Expression.Level), 1):Member_Expression`  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne la somme de la `Measures.[Order Quantity]` membre, agrégé sur les huit premiers mois de l’année civile 2003 qui sont contenus dans le `Date` dimension, à partir de la **Adventure Works** cube.  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 L'exemple ci-après est agrégé sur les deux premiers mois du deuxième semestre de l'annéé civile 2003.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
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
 [TopCount &#40; MDX &#41;](../mdx/topcount-mdx.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

