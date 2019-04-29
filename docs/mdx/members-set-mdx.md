---
title: Members (Set) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3bd4fe92c064f4665a4b397e47a45ae5bde50f39
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63048445"
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
 Si une expression de hiérarchie est spécifiée, le **Members (Set)** fonction retourne le jeu de tous les membres dans la hiérarchie spécifiée, sans les membres calculés. Pour obtenir le jeu de tous les membres, calculée ou dans le cas contraire, sur une hiérarchie utilisent les [AllMembers &#40;MDX&#41; ](../mdx/allmembers-mdx.md) (fonction)  
  
 Si une expression de niveau est spécifiée, le **Members (Set)** fonction retourne le jeu de tous les membres du niveau spécifié.  
  
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
  
 L'exemple suivant renvoie les quantités commandées de chaque membre au niveau `[Product].[Products].[Product Line]`. Le **membres** fonction retourne un jeu qui représente tous les membres du niveau.  
  
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
