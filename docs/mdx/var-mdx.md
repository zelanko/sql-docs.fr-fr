---
description: Var (MDX)
title: Var (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 46aad9a9b7c328d23680df3c74bcf09a465b868d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483712"
---
# <a name="var-mdx"></a>Var (MDX)


  Retourne l’échantillon de variance d’une expression numérique évaluée sur un jeu, à l’aide de la formule de remplissage non biaisée (division par *n*).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 La fonction **var** retourne la variance non biaisée d’une expression numérique spécifiée évaluée sur un jeu spécifié.  
  
 La fonction **var** utilise la formule de remplissage non biaisée, tandis que la fonction [VarP](../mdx/varp-mdx.md) utilise la formule de remplissage biaisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
