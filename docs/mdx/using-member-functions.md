---
title: À l’aide des fonctions membres | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1c9979b6b9fcb04115695cbe8d9c224e1c6c1f57
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251591"
---
# <a name="using-member-functions"></a>Utilisation de fonctions de membre


  Une fonction de membre est une fonction MDX (Multidimensional Expressions) qui retourne un membre. Les fonctions de membre, comme les fonctions de tuple et les fonctions de définition, sont essentielles à la négociation des structures multidimensionnelles de la syntaxe MDX (Multidimensional Expressions) présentes dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 De nombreuses fonctions de membre dans MDX, la plus importante est la **CurrentMember** (fonction), qui est utilisée pour déterminer le membre actuel sur une hiérarchie. La requête suivante illustre comment l’utiliser, ainsi que la **Parent**, **ancêtre**, et **Prevmember** fonctions :  
  
 `WITH`  
  
 `//Returns the name of the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[CurrentMemberDemo] AS [Date].[Calendar].CurrentMember.Name`  
  
 `//Returns the name of the parent of the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[ParentDemo] AS [Date].[Calendar].CurrentMember.Parent.Name`  
  
 `//Returns the name of the ancestor of the currentmember on the Calendar hierarchy at the Year level`  
  
 `MEMBER MEASURES.[AncestorDemo] AS ANCESTOR([Date].[Calendar].CurrentMember, [Date].[Calendar].[Calendar Year]).Name`  
  
 `//Returns the name of the member before the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[PrevMemberDemo] AS [Date].[Calendar].CurrentMember.Prevmember.Name`  
  
 `SELECT{MEASURES.[CurrentMemberDemo],MEASURES.[ParentDemo],MEASURES.[AncestorDemo],MEASURES.[PrevMemberDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [À l’aide des fonctions de Tuple](../mdx/using-tuple-functions.md)   
 [Utilisation de fonctions de jeu](../mdx/using-set-functions.md)  
  
  
