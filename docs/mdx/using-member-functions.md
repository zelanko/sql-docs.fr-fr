---
title: "À l’aide des fonctions membres | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- member functions [MDX]
ms.assetid: 094c443f-0daa-4af7-801c-d2e1d686d755
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9354c2e6a83918742f1c2de1dea943be4b21e844
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="using-member-functions"></a>Utilisation de fonctions de membre
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Une fonction de membre est une fonction MDX (Multidimensional Expressions) qui retourne un membre. Les fonctions de membre, comme les fonctions de tuple et les fonctions de définition, sont essentielles à la négociation des structures multidimensionnelles de la syntaxe MDX (Multidimensional Expressions) présentes dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 De nombreuses fonctions de membre dans MDX, la plus importante est la **CurrentMember** fonction, qui est utilisée pour déterminer le membre actuel sur une hiérarchie. La requête suivante illustre comment l’utiliser, ainsi que les **Parent**, **ancêtre**, et **Prevmember** fonctions :  
  
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
 [Fonctions &#40; La syntaxe MDX &#41;](../mdx/functions-mdx-syntax.md)   
 [À l’aide des fonctions de Tuple](../mdx/using-tuple-functions.md)   
 [À l’aide des fonctions de jeu](../mdx/using-set-functions.md)  
  
  

