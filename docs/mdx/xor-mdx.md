---
title: XOR (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: XOR
dev_langs: kbMDX
helpviewer_keywords: XOR operator
ms.assetid: 17280f36-df0e-477e-9342-e8129ed5cc3c
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 38a352662bb1209096502953b96b4c3ad5e8bc0f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="xor-mdx"></a>XOR (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Effectue une exclusion logique sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
 *Expression2*  
 Expression MDX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur booléenne qui retourne **true** si un seul et unique argument prend la valeur **true**; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Le **XOR** opérateur traite les deux paramètres comme des valeurs booléennes (zéro, 0, comme **false**; sinon, **true**) avant que l’opérateur effectue l’exclusion logique. Le tableau suivant illustre comment la **XOR** opérateur effectue l’exclusion logique.  
  
|*Expression1*|*Expression2*|Valeur retournée|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
