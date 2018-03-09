---
title: '* (Multiplication) (DMX) | Documents Microsoft'
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: cfab1581-7818-427b-b8b2-cec0b5e3a0cd
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9fcd1cd05485a7b03590cc01da1ef7b755a87a37
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="-multiply-dmx"></a>* (Multiply) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Effectue l'opération arithmétique qui consiste à multiplier un nombre par un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Numeric_expression*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur qui possède le type de données du paramètre doté de la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes   
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si une expression donne comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Arithmétique opérateurs &#40; DMX &#41;](../dmx/operators-arithmetic.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  
