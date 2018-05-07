---
title: XOR (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- XOR
dev_langs:
- kbMDX
helpviewer_keywords:
- XOR operator
ms.assetid: 17280f36-df0e-477e-9342-e8129ed5cc3c
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 17bebf33ae3cc5d08f51fe61ac7adbe0de875751
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="xor-mdx"></a>XOR (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
