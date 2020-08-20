---
description: IsSibling (MDX)
title: IsSibling (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: dc43d132e9fca9f691ab76aa43851aadf6c52b47
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483972"
---
# <a name="issibling-mdx"></a>IsSibling (MDX)


  Retourne une valeur indiquant si un membre spécifié est un frère d'un autre membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsSibling(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Member_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **IsSibling** retourne la **valeur true** si le premier membre spécifié est un frère du deuxième membre spécifié. Dans le cas contraire, la fonction retourne **false**.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne TRUE si le membre actuel sur la hiérarchie Fiscal de la dimension Date est un frère de July 2002 :  
  
 `WITH MEMBER MEASURES.ISSIBLINGDEMO AS`  
  
 `IsSibling([Date].[Fiscal].CURRENTMEMBER, [Date].[Fiscal].[Month].&[2002]&[7])`  
  
 `SELECT {MEASURES.ISSIBLINGDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
