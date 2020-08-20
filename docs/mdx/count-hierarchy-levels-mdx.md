---
description: Count (Hierarchy Levels) (MDX)
title: Nombre (niveaux hiérarchiques) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a5ebf525df144b0fd1dd81ba5b223045b2ecfd88
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461641"
---
# <a name="count-hierarchy-levels-mdx"></a>Count (Hierarchy Levels) (MDX)


  Retourne le nombre de niveaux dans la hiérarchie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchy_Expression.Levels.Count  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Retourne le nombre de niveaux dans une hiérarchie, notamment le niveau `[All]` (le cas échéant).  
  
> [!IMPORTANT]  
>  Lorsqu'une dimension contient uniquement une hiérarchie visible unique, cette hiérarchie peut être désignée soit par le nom de dimension, soit par le nom de la hiérarchie, puisque le nom de dimension est résolu à son unique hiérarchie visible. Par exemple, `Measures.Levels.Count` est une expression MDX valide parce qu'elle est résolue à la seule hiérarchie de la dimension de mesures.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne et comptabilise le nombre de niveaux dans la hiérarchie définie par l'utilisateur Product Categories du cube Adventure Works.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Product Categories].Levels.Count   
Select Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;dimension&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Nombre &#40;Tuple&#41; &#40;&#41;MDX ](../mdx/count-tuple-mdx.md)   
 [Nombre &#40;défini&#41; &#40;&#41;MDX ](../mdx/count-set-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
