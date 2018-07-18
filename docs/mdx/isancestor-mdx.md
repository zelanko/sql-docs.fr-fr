---
title: IsAncestor (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8aacd6825a81ff172d8fdf79373f5b251d6e18b9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740619"
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)


  Retourne une valeur indiquant si un membre spécifié est un ancêtre d'un autre membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Arguments  
 *Expression_membre1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Expression_membre2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Le **IsAncestor** fonction renvoie **true** si le premier membre spécifié est un ancêtre du deuxième membre spécifié. Sinon, la fonction retourne **false**.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant renvoie **true** si [Date]. [ Fiscal]. CurrentMember est un ancêtre de January 2003 :  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Ancêtre &#40;MDX&#41;](../mdx/ancestor-mdx.md)   
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
