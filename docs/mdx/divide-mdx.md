---
title: Diviser (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 9fe4a47b-d5e8-4dc7-ad4a-3e47ab463f03
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2f05c20a10b72b3c919672fd528a4222c6d204d7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="divide-mdx"></a>Diviser (MDX)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Effectue une division et retourne un autre résultat ou BLANK() lors d'une division par 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Arguments  
 *Numérateur*  
 Dividende ou nombre à diviser.  
  
 *dénominateur*  
 Diviseur ou nombre par lequel diviser.  
  
 *alternateresult*  
 (Facultatif) Valeur retournée quand la division par zéro provoque une erreur. Lorqu'elle n'est pas fournie, la valeur par défaut est BLANK().  
  
## <a name="remarks"></a>Notes  
 Le résultat de remplacement lors de la division par 0 doit être une constante.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

