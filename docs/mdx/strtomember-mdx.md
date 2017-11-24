---
title: StrToMember (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: STRTOMEMBER
dev_langs: kbMDX
helpviewer_keywords: StrToMember function
ms.assetid: eb8a3dc0-5ae4-434e-b321-680a81a59e67
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: c706110946bae4176bd217288a185e977c846e90
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="strtomember-mdx"></a>StrToMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le membre spécifié par une chaîne au format MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Name*  
 Expression de chaîne valide qui spécifie, directement ou indirectement, un membre.  
  
## <a name="remarks"></a>Notes  
 Le **StrToMember** fonction retourne le membre spécifié dans l’expression de chaîne. Le **StrToMember** fonction est généralement utilisée avec les fonctions définies par l’utilisateur pour retourner un membre spécifié à partir d’une fonction externe vers une instruction MDX, ou lorsqu’une requête MDX est paramétrable.  
  
-   Lorsque vous utilisez l'indicateur CONSTRAINED, le nom du membre doit pouvoir être directement résolu à un nom de membre qualifié ou non qualifié. Cet indicateur est employé pour réduire les risques d'attaques par injection au travers de la chaîne spécifiée. Si une chaîne qui ne peut être directement résolue à un nom de membre qualifié ou non qualifié est fournie, l'erreur suivante s'affiche : « Les restrictions imposées par l'indicateur CONSTRAINED dans la fonction STRTOMEMBER n'ont pas été respectées. »  
  
-   Si l'indicateur CONSTRAINED n'est pas utilisé, vous pouvez résoudre le membre spécifié soit directement à un nom de membre, soit à une expression MDX elle-même résolue à un nom.  
  
-   Pour mieux comprendre les différences entre jeux et membres, consultez Utilisation d'expressions de jeu et Utilisation d'expressions de membre.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne la mesure Reseller Sales Amount du membre Bayern dans la hiérarchie d’attribut State-Province à l’aide de la **StrToMember** (fonction). Le nom de membre qualifié est fourni par la chaîne spécifiée.  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 L’exemple suivant retourne la mesure Reseller Sales Amount du membre Bayern à l’aide de la **StrToMember** (fonction). Du fait que la chaîne du nom de membre n'a fourni qu'un nom de membre non qualifié, la requête retourne la première instance du membre spécifié qui se trouve d'ailleurs dans la hiérarchie Customer Geography de la dimension Customer qui ne rejoint pas Reseller Sales. Les méthodes conseillées préconisent la définition d'un nom qualifié afin de garantir les résultats attendus.  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 L’exemple suivant retourne la mesure Reseller Sales Amount du membre Bayern dans la hiérarchie d’attribut State-Province à l’aide de la **StrToMember** (fonction). La chaîne du nom de membre fournie est résolue à un nom de membre qualifié.  
  
```  
SELECT {StrToMember('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-dessous retourne une erreur liée à l'indicateur CONSTRAINED. Tandis que la chaîne de nom de membre fournie contient une expression de membre MDX valide qui est résolue à un nom de membre qualifié, l'indicateur CONSTRAINED exige l'usage de noms de membres qualifiés ou non qualifiés dans cette même chaîne.  
  
```  
SELECT StrToMember ('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
