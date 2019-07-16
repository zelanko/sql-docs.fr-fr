---
title: OpeningPeriod (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 07f94c3ed850af10120b1de7d95941bc5c90e826
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088222"
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (MDX)


  Retourne le premier frère parmi les descendants d'un niveau spécifié, éventuellement à un membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Cette fonction a principalement été conçue pour être exploitée avec la dimension Time (dimension de temps) mais peut également être utilisée avec n'importe quelle dimension.  
  
-   Si une expression de niveau est spécifiée, le **OpeningPeriod** fonction utilise la hiérarchie qui contient le niveau spécifié et retourne le premier frère parmi les descendants du membre par défaut au niveau spécifié.  
  
-   Si une expression de niveau et une expression de membre sont spécifiés, le **OpeningPeriod** fonction retourne le premier frère parmi les descendants du membre spécifié au niveau spécifié dans la hiérarchie contenant le texte spécifié niveau.  
  
-   Si une expression de niveau, ni une expression de membre est spécifiée, le **OpeningPeriod** fonction utilise le niveau par défaut et le membre de la dimension avec un type de temps.  
  
> [!NOTE]  
>  Le [ClosingPeriod](../mdx/closingperiod-mdx.md) fonction est similaire à la **OpeningPeriod** fonctionner, à ceci près que le **ClosingPeriod** fonction retourne le dernier frère au lieu du premier frère.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne la valeur de la mesure par défaut pour le membre FY2002 de la dimension Date (dimension de type Time). Ce membre est retourné parce que le niveau Fiscal Year (année fiscale) est le premier descendant du niveau [All], la hiérarchie Fiscal est la hiérarchie par défaut parce qu'elle est la première hiérarchie définie par l'utilisateur dans la collection des hiérarchies, et le membre FY2002 est le premier frère de cette hiérarchie à ce niveau.  
  
```  
SELECT OpeningPeriod() ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple suivant retourne la valeur de la mesure par défaut pour le membre July 1, 2001 (1er juillet 2001) au niveau Date.Date.Date de la hiérarchie d'attribut Date.Date. Ce membre est le premier frère du descendant du niveau [All] dans la hiérarchie d'attribut Date.Date.  
  
```  
SELECT OpeningPeriod([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-après retourne la valeur de la mesure par défaut pour le membre January, 2003 (janvier 2003) qui est le premier frère du descendant du membre 2003 au niveau Year (année) dans la hiérarchie définie par l'utilisateur Calendar (calendrier).  
  
```  
SELECT OpeningPeriod([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-après retourne la valeur de la mesure par défaut pour le membre July, 2002 (juillet 2002) qui est le premier frère du descendant du membre 2003 au niveau Year (année) dans la hiérarchie définie par l'utilisateur Fiscal.  
  
```  
SELECT OpeningPeriod([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [TopCount &#40;MDX&#41;](../mdx/topcount-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40;MDX&#41;](../mdx/firstsibling-mdx.md)  
  
  
