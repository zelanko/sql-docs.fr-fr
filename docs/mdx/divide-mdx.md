---
title: Divide (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 86b4d8c97996733396e3062e134b2e31d2819ec0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471310"
---
# <a name="divide-mdx"></a>Diviser (MDX)


  Effectue une division et retourne un autre résultat ou BLANK() lors d'une division par 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Arguments  
 *numerator*  
 Dividende ou nombre à diviser.  
  
 *denominator*  
 Diviseur ou nombre par lequel diviser.  
  
 *alternateresult*  
 (Facultatif) Valeur retournée quand la division par zéro provoque une erreur. Lorqu'elle n'est pas fournie, la valeur par défaut est BLANK().  
  
## <a name="remarks"></a>Notes  
 Le résultat de remplacement lors de la division par 0 doit être une constante.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
