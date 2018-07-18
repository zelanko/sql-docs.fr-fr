---
title: (Diviser) (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ab2b355c551b868cec3ee4329460f8bb0532236
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37972665"
---
# <a name="divide-dmx"></a>(Diviser) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Exécute une opération arithmétique qui divise un nombre par un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Dividende*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
 *Diviseur*  
 Expression DMX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur qui possède le type de données du paramètre doté de la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par cet opérateur représente le quotient de la première expression divisée par la seconde expression.  
  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si l'expression Divisor renvoie une valeur NULL, l'opérateur génère une erreur. Si les expressions Divisor et Dividend renvoient toutes les deux une valeur NULL, l'opérateur retourne une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs arithmétiques &#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [Diviser &#40;SSIS Expression&#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;Diviser&#41; &#40;Transact-SQL&#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  
