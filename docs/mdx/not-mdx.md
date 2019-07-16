---
title: NOT (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4031b887eb0a42580d6ae8debf6c9177ff67efc3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088236"
---
# <a name="not-mdx"></a>NOT (MDX)


  Effectue une négation logique sur une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Une valeur booléenne qui retourne **false** si l’argument prend la valeur **true**; sinon, **true**.  
  
## <a name="remarks"></a>Notes  
 Le **pas** opérateur traite l’expression comme une valeur booléenne (zéro, 0, comme **false**; sinon, **true**) avant que l’opérateur effectue la négation logique. Le tableau suivant illustre comment la **pas** opérateur effectue la négation logique.  
  
|*Expression1*|Valeur de retour|  
|-------------------|------------------|  
|**true**|**false**|  
|**false**|**true**|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
