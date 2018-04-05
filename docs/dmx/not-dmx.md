---
title: PAS (DMX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- NOT
dev_langs:
- DMX
helpviewer_keywords:
- NOT operator [DMX]
ms.assetid: 6d91b3d9-270c-4a68-b41f-169cff5faa0e
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c242a6767e60b04249d69d340806d0cf78a374e2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Opérateur logique qui effectue une négation logique sur une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression DMX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur booléenne qui retourne FALSE si l'argument renvoie la valeur TRUE ; dans le cas contraire, elle retourne TRUE.  
  
## <a name="remarks"></a>Notes   
 L'argument est considéré comme une valeur booléenne (0 correspond à la valeur FALSE ; dans le cas contraire, TRUE) avant que l'opérateur effectue la négation logique. Si *Expression1* a la valeur TRUE, l’opérateur retourne FALSE. Si *Expression1* est FALSE, l’opérateur retourne TRUE. Le tableau ci-dessous explique comment s'effectue la conjonction logique.  
  
|Si Expression1 est|La valeur de retour est|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logique opérateurs &#40; DMX &#41;](../dmx/operators-logical.md)   
 [Opérateurs &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  
