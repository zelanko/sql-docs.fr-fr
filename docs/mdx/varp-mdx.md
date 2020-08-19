---
description: VarP (MDX)
title: VarP (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c850ba60ac9900228c6adaa03aa97b46b1abddf1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429721"
---
# <a name="varp-mdx"></a>VarP (MDX)


  Retourne la variance de remplissage d’une expression numérique évaluée sur un jeu, à l’aide de la formule de remplissage biaisée (division par *n*-1).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 La fonction **VarP** retourne la variance biaisée d’une expression numérique spécifiée, évaluée sur un jeu spécifié.  
  
 La fonction **VarP** utilise la formule de remplissage biaisée, tandis que la fonction [var](../mdx/var-mdx.md) utilise la formule de remplissage non biaisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
