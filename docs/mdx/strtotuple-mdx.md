---
title: StrToTuple (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 232d1e94892165430867ec5217f8c87ccd625b48
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036716"
---
# <a name="strtotuple-mdx"></a>StrToTuple (MDX)


  Retourne le tuple spécifié par une chaîne au format MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Arguments  
 *Tuple_Specification*  
 Expression de chaîne valide qui spécifie, directement ou indirectement, un tuple.  
  
## <a name="remarks"></a>Notes  
 La fonction **StrToTuple** retourne le jeu spécifié. La fonction **StrToTuple** est généralement utilisée avec des fonctions définies par l’utilisateur pour retourner une spécification de tuple d’une fonction externe à une instruction MDX.  
  
-   En cas d'utilisation de l'indicateur CONSTRAINED, le tuple spécifié doit contenir des noms de membres qualifiés ou non qualifiés. Cet indicateur est employé pour réduire les risques d'attaques par injection au travers de la chaîne spécifiée. Si une chaîne qui ne peut être directement résolue à des noms de membres qualifiés ou non qualifiés est fournie, l'erreur suivante s'affiche : « Les restrictions imposées par l'indicateur CONSTRAINED dans la fonction STRTOTUPLE n'ont pas été respectées. »  
  
-   Si l'indicateur CONSTRAINED n'est pas utilisé, vous pouvez résoudre le tuple spécifié à une expression MDX valide qui retourne un tuple.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne la mesure Reseller Sales Amount du membre Bayern à l'aide de la fonction pour l'année civile 2004. Le tuple spécifié fourni contient une expression de tuple MDX valide.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-dessous retourne la mesure Reseller Sales Amount du membre Bayern à l'aide de la fonction pour l'année civile 2004. Le tuple spécifié fourni contient des noms de membres qualifiés, conformément aux exigences de l'indicateur CONSTRAINED.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-dessous retourne la mesure Reseller Sales Amount du membre Bayern à l'aide de la fonction pour l'année civile 2004. Le tuple spécifié fourni contient une expression de tuple MDX valide.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-dessous retourne une erreur liée à l'indicateur CONSTRAINED. Tandis que le tuple spécifié fournit une expression de tuple MDX valide, l'indicateur CONSTRAINED exige l'usage de noms de membres qualifiés ou non qualifiés dans le tuple spécifié.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
