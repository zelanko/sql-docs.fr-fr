---
description: MemberToStr (MDX)
title: MemberToStr (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6217120c7e6d5ee55670be3d902a9ea99333273f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483802"
---
# <a name="membertostr-mdx"></a>MemberToStr (MDX)


  Retourne une chaîne au format MDX (Multidimensional Expressions) qui correspond à un membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MemberToStr(Member_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Cette fonction retourne une chaîne qui contient le nom unique d'un membre. Il est généralement utilisé pour passer le UniqueName d’un membre à une fonction externe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne la chaîne [Geography]. [Geography]. [Country]. & [États-Unis] :  
  
 `WITH MEMBER Measures.x AS MemberToStr`  
  
 `([Geography].[Geography].[Country].[United States])`  
  
 `SELECT Measures.x ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
