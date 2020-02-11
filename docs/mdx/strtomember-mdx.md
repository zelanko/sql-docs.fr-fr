---
title: StrToMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a78f0664ea561825bb279db47aa3c01fc98bf7dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036801"
---
# <a name="strtomember-mdx"></a>StrToMember (MDX)


  Retourne le membre spécifié par une chaîne au format MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Name*  
 Expression de chaîne valide qui spécifie, directement ou indirectement, un membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **StrToMember** retourne le membre spécifié dans l’expression de chaîne. La fonction **StrToMember** est généralement utilisée avec des fonctions définies par l’utilisateur pour renvoyer une spécification de membre d’une fonction externe vers une instruction MDX, ou lorsqu’une requête MDX est paramétrable.  
  
-   Lorsque vous utilisez l'indicateur CONSTRAINED, le nom du membre doit pouvoir être directement résolu à un nom de membre qualifié ou non qualifié. Cet indicateur est employé pour réduire les risques d'attaques par injection au travers de la chaîne spécifiée. Si une chaîne qui ne peut être directement résolue à un nom de membre qualifié ou non qualifié est fournie, l'erreur suivante s'affiche : « Les restrictions imposées par l'indicateur CONSTRAINED dans la fonction STRTOMEMBER n'ont pas été respectées. »  
  
-   Si l'indicateur CONSTRAINED n'est pas utilisé, vous pouvez résoudre le membre spécifié soit directement à un nom de membre, soit à une expression MDX elle-même résolue à un nom.  
  
-   Pour mieux comprendre les différences entre jeux et membres, consultez Utilisation d'expressions de jeu et Utilisation d'expressions de membre.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne la mesure Reseller Sales Amount pour le membre Bayern dans la hiérarchie d’attribut State-Province à l’aide de la fonction **StrToMember** . Le nom de membre qualifié est fourni par la chaîne spécifiée.  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 L’exemple suivant retourne la mesure Reseller Sales Amount pour le membre Bayern à l’aide de la fonction **StrToMember** . Du fait que la chaîne du nom de membre n'a fourni qu'un nom de membre non qualifié, la requête retourne la première instance du membre spécifié qui se trouve d'ailleurs dans la hiérarchie Customer Geography de la dimension Customer qui ne rejoint pas Reseller Sales. Les méthodes conseillées préconisent la définition d'un nom qualifié afin de garantir les résultats attendus.  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 L’exemple suivant retourne la mesure Reseller Sales Amount pour le membre Bayern dans la hiérarchie d’attribut State-Province à l’aide de la fonction **StrToMember** . La chaîne du nom de membre fournie est résolue à un nom de membre qualifié.  
  
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
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
