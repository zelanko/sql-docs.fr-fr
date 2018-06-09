---
title: Var (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14caf6e96b41fdf2e7f8b4d20f16852e890bd166
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743918"
---
# <a name="var-mdx"></a>Var (MDX)


  Retourne la variance d’une expression numérique évaluée sur un jeu, à l’aide de la formule de remplissage non biaisée (division par *n*).  
  
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
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
