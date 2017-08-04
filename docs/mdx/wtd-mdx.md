---
title: Wtd (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Wtd function
ms.assetid: 41066e1b-e802-4582-be4b-3ed7807b033e
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1010b6d7aef59c5bb4eb18e93ba63bc972e8b7fa
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="wtd-mdx"></a>Wtd (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne un jeu des membres frères de même niveau qu'un membre donné, commençant par le premier frère et se terminant par le membre donné, conformément à la contrainte du niveau Week de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si une expression de membre n’est pas spécifiée, la valeur par défaut est le membre actuel de la première hiérarchie avec un niveau de type semaines dans la première dimension de type Time (**Time.CurrentMember**) dans le groupe de mesures.  
  
 Le **Wtd** fonction est un raccourci pour la [PeriodsToDate](../mdx/periodstodate-mdx.md) fonction où le niveau est défini sur *semaines*. Ce qui signifie que `Wtd(Member_Expression)` est équivalent à `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>Voir aussi  
 [Qtd &#40; MDX &#41;](../mdx/qtd-mdx.md)   
 [MTd &#40; MDX &#41;](../mdx/mtd-mdx.md)   
 [YTD &#40; MDX &#41;](../mdx/ytd-mdx.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

