---
title: ParallelPeriod (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b4122c13a5371cc0ffe1c5c6235ad750e7fdadad
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68020700"
---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (MDX)


  Retourne un membre d'une période antérieure dans la même position relative que le membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ParallelPeriod( [ Level_Expression [ ,Index [ , Member_Expression ] ] ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Évaluer*  
 Expression numérique valide qui spécifie le nombre de périodes parallèles à décaler.  
  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Bien que similaire à la fonction [cousin](../mdx/cousin-mdx.md) , la fonction **ParallelPeriod** est plus étroitement liée à la série chronologique. La fonction **ParallelPeriod** prend l’ancêtre du membre spécifié au niveau spécifié, recherche le frère de l’ancêtre avec le décalage spécifié, puis retourne la période parallèle du membre spécifié parmi les descendants du frère.  
  
 La fonction **ParallelPeriod** a les valeurs par défaut suivantes :  
  
-   Si aucune expression de niveau, ni aucune expression de membre n’est spécifiée, la valeur de membre par défaut est le membre actuel de la première hiérarchie sur la première dimension avec un type de *temps* dans le groupe de mesures.  
  
-   Si une expression de niveau est spécifiée, mais qu’une expression de membre n’est pas spécifiée, la valeur de membre par défaut est *Level_Expression*. **Hierarchy. CurrentMember**.  
  
-   La valeur d'index par défaut est 1.  
  
-   Le niveau par défaut est celui du parent du membre spécifié.  
  
 La fonction **ParallelPeriod** est équivalente à l’instruction MDX suivante :  
  
 `Cousin(Member_Expression, Ancestor(Member_Expression, Level_Expression) .Lag(Numeric_Expression))`  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la période parallèle du mois d'octobre 2003 avec un décalage de trois périodes en se basant sur le niveau du trimestre, ce qui retourne le mois de janvier 2003.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Quarter]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 L'exemple ci-dessous retourne la période parallèle du mois d'octobre 2003 avec un décalage de trois périodes en se basant sur le niveau du semestre, ce qui retourne le mois d'avril 2002.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Semester]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
