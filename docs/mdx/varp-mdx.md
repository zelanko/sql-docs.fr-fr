---
title: VarP (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VARP
dev_langs:
- kbMDX
helpviewer_keywords:
- VarP function [MDX]
ms.assetid: feca648d-bbc8-44c8-9a0e-38f66d914c72
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4f0d30afa0147f62bea4b58661ee735deb61a429
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="varp-mdx"></a>VarP (MDX)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne la variance de remplissage d’une expression numérique évaluée sur un jeu, à l’aide de la formule de remplissage biaisée (division par  *n* -1).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Le **VarP** fonction retourne la variance biaisée d’une expression numérique spécifiée évaluée sur un jeu spécifié.  
  
 Le **VarP** fonction utilise le remplissage biaisée formule lors de la [Var](../mdx/var-mdx.md) fonction utilise la formule de remplissage non biaisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

