---
title: "À l’aide d’Expressions de Dimension | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- expressions [MDX], dimensions
- dimensions [Analysis Services], MDX
ms.assetid: 1d40cffb-e88f-4284-93cf-d62ab4f08395
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 1417fd747df92c84fe66e2c69996f57ab51875e1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="using-dimension-expressions"></a>Utilisation d'expressions de dimension
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Vous utilisez généralement des expressions de dimension et de hiérarchie lorsque vous passez des paramètres à des fonctions dans MDX (Multidimensional Expressions) pour retourner des membres, des jeux ou des tuples à partir d'une hiérarchie.  
  
 Les expressions de dimension peuvent être uniquement des expressions simples car elles sont des identificateurs d'objet. Consultez [Expressions &#40; MDX &#41; ](../mdx/expressions-mdx.md) pour une explication des expressions simples et complexes.  
  
## <a name="dimension-expressions"></a>Expressions de dimension  
 Une expression de dimension contient un identificateur de dimension ou une fonction de dimension.  
  
 Les expressions de dimension sont rarement utilisées seules. À la place, il est souhaitable généralement de spécifier une hiérarchie sur une dimension. La seule exception est lorsque vous travaillez avec la dimension de mesures qui n'ont pas de hiérarchies.  
  
 L'exemple ci-dessous présente un membre calculé qui utilise conjointement l'expression [Measures] avec les fonctions Members et Count() pour retourner le nombre de membres dans la dimension Measures :  
  
 `WITH MEMBER [Measures].[MeasureCount] AS`  
  
 `COUNT([Measures].MEMBERS)`  
  
 `SELECT [Measures].[MeasureCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Un identificateur de dimension apparaît comme *Dimension_Name* dans la notation BNF utilisée pour décrire des instructions MDX.  
  
## <a name="hierarchy-expressions"></a>Expressions de hiérarchie  
 De même, une expression de hiérarchie contient un identificateur de hiérarchie ou une fonction de hiérarchie. L'exemple ci-dessous illustre l'utilisation de l'expression de hiérarchie [Date].[Calendar] conjointement avec les fonctions .Levels et .Count pour retourner le nombre de niveaux dans la hiérarchie Calendar de la dimension Date :  
  
 `WITH MEMBER [Measures].[CalendarLevelCount] AS`  
  
 `[Date].[Calendar].Levels.Count`  
  
 `SELECT [Measures].[CalendarLevelCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Le scénario le plus courant où les expressions de hiérarchie sont utilisées a lieu conjointement avec la fonction .Members, pour retourner tous les membres sur une hiérarchie. L'exemple suivant retourne toutes les membres de [Date].[Calendar] sur l'axe des lignes :  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Un identificateur de hiérarchie apparaît sous la forme *Dimension_Name**.* *Hierarchy_Name* dans la notation BNF utilisée pour décrire des instructions MDX.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40; MDX &#41;](../mdx/expressions-mdx.md)  
  
  
