---
description: StrToSet (MDX)
title: StrToSet (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 882ab646af51d4b1edbe0a1240eaaed7cbfa5422
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386775"
---
# <a name="strtoset-mdx"></a>StrToSet (MDX)


  Retourne le jeu spécifié par une chaîne au format MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Specification*  
 Expression de chaîne valide spécifiant, directement ou indirectement, un jeu.  
  
## <a name="remarks"></a>Notes  
 La fonction **StrToSet** retourne le jeu spécifié dans l’expression de chaîne. La fonction **StrToSet** est généralement utilisée avec des fonctions définies par l’utilisateur pour renvoyer une spécification Set d’une fonction externe vers une instruction MDX, ou lorsqu’une requête MDX est paramétrable.  
  
-   Lorsque l’indicateur constressed est utilisé, la spécification set doit contenir des noms de membres qualifiés ou non qualifiés ou un ensemble de tuples contenant des noms de membres qualifiés ou non qualifiés, placés entre accolades {} . Cet indicateur est employé pour réduire les risques d'attaques par injection au travers de la chaîne spécifiée. Si une chaîne qui ne peut être directement résolue à des noms de membres qualifiés ou non qualifiés est fournie, l'erreur suivante s'affiche : restrictions imposées par l'indicateur CONSTRAINED dans la fonction STRTOSET n'ont pas été respectées. »  
  
-   Si l'indicateur CONSTRAINED n'est pas utilisé, vous pouvez résoudre le jeu spécifié à une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
-   Pour mieux comprendre les différences entre jeux et membres, consultez Utilisation d'expressions de jeu et Utilisation d'expressions de membre.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne l’ensemble des membres de la hiérarchie d’attribut State-Province à l’aide de la fonction **StrToSet** . La spécification Set fournit une expression d’ensemble MDX valide.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-dessous retourne une erreur liée à l'indicateur CONSTRAINED. Tandis que le jeu spécifié fournit une expression d'ensemble MDX valide, l'indicateur CONSTRAINED exige l'usage de noms de membres qualifiés ou non qualifiés dans le jeu spécifié.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-après retourne la mesure Reseller Sales Amount (montant des ventes du revendeur) pour l'Allemagne et le Canada. Le jeu spécifié fourni dans la chaîne spécifiée contient des noms de membres qualifiés, conformément aux exigences de l'indicateur CONSTRAINED.  
  
```  
SELECT StrToSet ('{[Geography].[Geography].[Country].[Germany],[Geography].[Geography].[Country].[Canada]}', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
