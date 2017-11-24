---
title: "Cette requête (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: THIS
dev_langs: kbMDX
helpviewer_keywords: This function [MDX]
ms.assetid: 87acddee-ae54-49ee-8923-1b760606e8b7
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a02f5db6f24923b320361b6682954c59984db87e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="this-mdx"></a>This (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le sous-cube actuel pour l'utiliser avec des assignations dans le script de calcul MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
This   
```  
  
## <a name="remarks"></a>Notes  
 Le **cela** fonction peut être utilisée à la place de n’importe quelle expression de sous-cube pour fournir le sous-cube actuel dans la portée actuelle dans le script de calcul MDX. Le **cela** fonction doit être utilisée sur le côté gauche d’une assignation.  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Calculs](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
