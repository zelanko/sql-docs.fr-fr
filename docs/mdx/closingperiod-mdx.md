---
description: ClosingPeriod (MDX)
title: ClosingPeriod (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f457a941c8967ce6f3c6700760ff95d5c2999d0f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487632"
---
# <a name="closingperiod-mdx"></a>ClosingPeriod (MDX)


  Retourne le membre qui correspond au dernier frère parmi les descendants d'un membre spécifié à un niveau spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ClosingPeriod( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Cette fonction a principalement été conçue pour être exploitée dans une dimension de type Time (dimension de temps) mais peut également être utilisée avec n'importe quelle dimension.  
  
-   Si une expression de niveau est spécifiée, la fonction **ClosingPeriod** utilise la dimension qui contient le niveau spécifié et retourne le dernier frère parmi les descendants du membre par défaut au niveau spécifié.  
  
-   Si une expression de niveau et une expression de membre sont spécifiées, la fonction **ClosingPeriod** retourne le dernier frère parmi les descendants du membre spécifié au niveau spécifié.  
  
-   Si ni une expression de niveau, ni une expression de membre n’est spécifiée, la fonction **ClosingPeriod** utilise le niveau et le membre par défaut de la dimension (le cas échéant) dans le cube avec un type Time.  
  
 La fonction **ClosingPeriod** est équivalente à l’instruction MDX suivante :  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`.  
  
> [!NOTE]  
>  La fonction [OpeningPeriod](../mdx/openingperiod-mdx.md) est similaire à la fonction **ClosingPeriod** , à ceci près que la fonction **OpeningPeriod** retourne le premier frère au lieu du dernier frère.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne la valeur de la mesure par défaut pour le membre FY2007 de la dimension Date (doté d'un type sémantique Time). Ce membre est retourné parce que le niveau Fiscal Year (année fiscale) est le premier descendant du niveau [All], la hiérarchie Fiscal est la hiérarchie par défaut parce qu'elle est la première hiérarchie définie par l'utilisateur dans la collection des hiérarchies, et le membre FY2007 est le dernier frère de la hiérarchie à ce niveau.  
  
```  
SELECT ClosingPeriod() ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne la valeur de la mesure par défaut pour le membre du 30 novembre 2006 au niveau date. date. date pour la hiérarchie d’attribut date. date. Ce membre est le dernier frère du descendant du niveau [All] dans la hiérarchie d'attribut Date.Date.  
  
```  
SELECT ClosingPeriod ([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
```  
  
 L'exemple ci-après retourne la valeur de la mesure par défaut pour le membre December, 2003 (décembre 2003) qui est le dernier frère du descendant du membre 2003 au niveau Year (année) dans la hiérarchie définie par l'utilisateur Calendar (calendrier).  
  
```  
SELECT ClosingPeriod ([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
 L'exemple ci-après retourne la valeur de la mesure par défaut pour le membre June, 2003 (juin 2003) qui est le dernier frère du descendant du membre 2003 au niveau Year (année) dans la hiérarchie définie par l'utilisateur Fiscal.  
  
```  
SELECT ClosingPeriod ([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [OpeningPeriod&#41;MDX &#40;](../mdx/openingperiod-mdx.md)   
 [Référence des fonctions MDX &#40;&#41;MDX ](../mdx/mdx-function-reference-mdx.md)   
 [LastSibling&#41;MDX &#40;](../mdx/lastsibling-mdx.md)  
  
  
