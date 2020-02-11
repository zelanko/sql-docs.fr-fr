---
title: Membres (Set) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d3e5bb14455d2d2ea67c4187e8e1a2a420031944
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138257"
---
# <a name="members-set-mdx"></a>Members (Set) (MDX)


  Retourne le jeu des membres d'une dimension, d'un niveau ou d'une hiérarchie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
## <a name="remarks"></a>Notes  
 Si une expression de hiérarchie est spécifiée, la fonction **Members (Set)** retourne le jeu de tous les membres dans la hiérarchie spécifiée, à l’exclusion des membres calculés. Pour obtenir le jeu de tous les membres, calculé ou autre, sur une hiérarchie, utilisez la fonction [AllMembers &#40;MDX&#41;](../mdx/allmembers-mdx.md)  
  
 Si une expression de niveau est spécifiée, la fonction **Members (Set)** retourne le jeu de tous les membres dans le niveau spécifié.  
  
> [!IMPORTANT]  
>  Lorsqu'une dimension contient uniquement une hiérarchie visible unique, cette hiérarchie peut être désignée soit par le nom de dimension, soit par le nom de la hiérarchie, puisque le nom de dimension dans ce scénario est résolu à son unique hiérarchie visible. Par exemple, Measures.Members est une expression MDX valide parce qu'elle est résolue à la seule hiérarchie de la dimension de mesures.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne l'ensemble de tous les membres de la hiérarchie Calendar Year dans le cube Adventure Works.  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 L'exemple suivant renvoie les quantités commandées de chaque membre au niveau `[Product].[Products].[Product Line]`. La fonction **members** retourne un jeu qui représente tous les membres du niveau.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)   
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
