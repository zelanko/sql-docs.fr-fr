---
title: WTD (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eee40829c72394bf95a1bc06540a434a1c74e166
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125812"
---
# <a name="wtd-mdx"></a>Wtd (MDX)


  Retourne un jeu des membres frères de même niveau qu'un membre donné, commençant par le premier frère et se terminant par le membre donné, conformément à la contrainte du niveau Week de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si une expression de membre n’est pas spécifiée, la valeur par défaut est le membre actuel de la première hiérarchie avec un niveau de type weeks dans la première dimension de type Time (**Time. CurrentMember**) dans le groupe de mesures.  
  
 La fonction **WTD** est une fonction de raccourci pour la fonction [PeriodsToDate](../mdx/periodstodate-mdx.md) dans laquelle le niveau est défini sur *weeks*. Ce qui signifie que `Wtd(Member_Expression)` est équivalent à `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>Voir aussi  
 [Taj &#40;&#41;MDX](../mdx/qtd-mdx.md)   
 [&#41;MDX &#40;](../mdx/mtd-mdx.md)   
 [Cumul &#40;&#41;MDX](../mdx/ytd-mdx.md)   
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
