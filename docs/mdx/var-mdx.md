---
title: Var (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VAR
dev_langs: kbMDX
helpviewer_keywords: Var function [MDX]
ms.assetid: 5575b68e-ebc1-4eaf-9547-1321d495ea62
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2c4afff9b93886e3b8ed0bcca2e564685ac00ea4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="var-mdx"></a>Var (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la variance d’une expression numérique évaluée sur un jeu, à l’aide de la formule de remplissage non biaisée (division par  *n* ).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Le **Var** fonction renvoie la variance non biaisée d’une expression numérique spécifiée évaluée sur un jeu spécifié.  
  
 Le **Var** fonction utilise la formule de remplissage non biaisée et la [VarP](../mdx/varp-mdx.md) fonction utilise la formule de remplissage biaisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
