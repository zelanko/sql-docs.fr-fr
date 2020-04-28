---
title: IsAncestor (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5cc8352b0d087b54a623cce892a05dfed29258b5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105261"
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)


  Retourne une valeur indiquant si un membre spécifié est un ancêtre d'un autre membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Member_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **IsAncestor** retourne la **valeur true** si le premier membre spécifié est un ancêtre du deuxième membre spécifié. Dans le cas contraire, la fonction retourne **false**.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne la **valeur true** si [date]. [Fiscal]. CurrentMember est un ancêtre de janvier 2003 :  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [&#41;MDX &#40;MDX](../mdx/ancestor-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
