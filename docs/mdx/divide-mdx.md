---
title: Division (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6184aa9d932355cd935a9131848ec27895faea5f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68049300"
---
# <a name="divide-mdx"></a>Diviser (MDX)


  Effectue une division et retourne un autre résultat ou BLANK() lors d'une division par 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Arguments  
 *monnaie*  
 Dividende ou nombre à diviser.  
  
 *dénominateur*  
 Diviseur ou nombre par lequel diviser.  
  
 *alternateresult*  
 (Facultatif) Valeur retournée quand la division par zéro provoque une erreur. Lorqu'elle n'est pas fournie, la valeur par défaut est BLANK().  
  
## <a name="remarks"></a>Notes  
 Le résultat de remplacement lors de la division par 0 doit être une constante.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
