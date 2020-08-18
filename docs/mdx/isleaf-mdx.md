---
description: IsLeaf (MDX)
title: IsLeaf (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1b7dd1d76b417633ff50a77b3f2822e6f7cfd462
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471821"
---
# <a name="isleaf-mdx"></a>IsLeaf (MDX)


  Retourne une valeur indiquant si un membre spécifié est un membre feuille.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsLeaf(Member_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **IsLeaf** retourne la **valeur true** si le membre spécifié est un membre feuille. Dans le cas contraire, la fonction retourne **false**.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la valeur TRUE si [Date].[Fiscal].CurrentMember est un membre feuille :  
  
 `WITH MEMBER MEASURES.ISLEAFDEMO AS`  
  
 `IsLeaf([Date].[Fiscal].CURRENTMEMBER)`  
  
 `SELECT {MEASURES.ISLEAFDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
