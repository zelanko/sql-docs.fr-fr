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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68049300"
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
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
