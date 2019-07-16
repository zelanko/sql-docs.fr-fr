---
title: Cette requête (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a2486f23170ec19f16dca31672696c09815a2e83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036639"
---
# <a name="this-mdx"></a>This (MDX)


  Retourne le sous-cube actuel pour l'utiliser avec des assignations dans le script de calcul MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
This   
```  
  
## <a name="remarks"></a>Notes  
 Le **cela** fonction peut être utilisée à la place de n’importe quelle expression de sous-cube pour fournir le sous-cube actuel au sein de la portée actuelle dans le script de calcul MDX. Le **cela** fonction doit être utilisée sur le côté gauche d’une assignation.  
  
## <a name="examples"></a>Exemples  
 Le fragment de script MDX suivant illustre l'utilisation du mot clé THIS avec les instructions SCOPE pour effectuer des affectations aux sous-cubes :  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2005],`  
  
 `[Date].[Fiscal].[Fiscal Quarter].Members,`  
  
 `[Measures].[Sales Amount Quota]`  
  
 `) ;`  
  
 `This = ParallelPeriod`  
  
 `(`  
  
 `[Date].[Fiscal].[Fiscal Year], 1,`  
  
 `[Date].[Fiscal].CurrentMember`  
  
 `) * 1.35 ;`  
  
 `/*-- Allocate equally to months in FY 2002 -----------------------------*/`  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2002],`  
  
 `[Date].[Fiscal].[Month].Members`  
  
 `) ;`  
  
 `This = [Date].[Fiscal].CurrentMember.Parent / 3 ;`  
  
 `End Scope ;`  
  
 `End Scope;`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Calculs](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
