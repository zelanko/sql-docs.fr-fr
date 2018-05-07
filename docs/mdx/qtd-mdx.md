---
title: Qtd (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- QTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Qtd function
ms.assetid: c1fe47e0-9c2b-466f-8d6d-e2b1c16a69cb
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 016e41ebb0531fc37a9f74c40259ede376b99549
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="qtd-mdx"></a>Qtd (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne un jeu de frères membres d’un même niveau qu’un membre donné, en commençant par le premier frère et se terminant par le membre donné, en tant que contrainte par la *trimestre* au niveau de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si un membre expressionis ne pas spécifié, la valeur par défaut est le membre actuel de la première hiérarchie avec un niveau de type *trimestres* dans la première dimension de type *temps* dans le groupe de mesures.  
  
 Le **Qtd** fonction est un raccourci pour la [PeriodsToDate &#40;MDX&#41; ](../mdx/periodstodate-mdx.md) fonction dont l’argument expression de niveau a la valeur *trimestre*. Ce qui signifie que `Qtd(Member_Expression)` est fonctionnellement équivalent à `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne la somme de la `Measures.[Order Quantity]` membre, agrégé sur les deux premiers mois du troisième trimestre de l’année civile 2003 qui sont contenus dans le `Date` dimension, à partir de la **Adventure Works** cube.  
  
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
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
