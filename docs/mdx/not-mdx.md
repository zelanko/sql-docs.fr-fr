---
title: PAS (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NOT
dev_langs: kbMDX
helpviewer_keywords: NOT operator [MDX]
ms.assetid: c11bd3b0-54b3-4a6d-babc-6067722194db
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 513dcff2862aa024684702017b9281b6163fcf5f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="not-mdx"></a>NOT (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Effectue une négation logique sur une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur booléenne qui retourne **false** si l’argument a la valeur **true**; sinon, **true**.  
  
## <a name="remarks"></a>Notes  
 Le **pas** opérateur traite l’expression en tant que valeur booléenne (zéro, 0, comme **false**; sinon, **true**) avant que l’opérateur effectue la négation logique. Le tableau suivant illustre comment la **pas** opérateur effectue la négation logique.  
  
|*Expression1*|Valeur retournée|  
|-------------------|------------------|  
|**true**|**false**|  
|**false**|**true**|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
