---
title: Diviser (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 01d9c838e8b7a40d19a59997ae670eee19e6309b
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969850"
---
# <a name="divide-dmx"></a>(Diviser) (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Exécute une opération arithmétique qui divise un nombre par un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Détaché*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
 *Division*  
 Expression DMX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Valeur qui possède le type de données du paramètre doté de la priorité la plus élevée.  
  
## <a name="remarks"></a>Remarques  
 La valeur retournée par cet opérateur représente le quotient de la première expression divisée par la seconde expression.  
  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si l'expression Divisor renvoie une valeur NULL, l'opérateur génère une erreur. Si les expressions Divisor et Dividend renvoient toutes les deux une valeur NULL, l'opérateur retourne une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs arithmétiques &#40;&#41;DMX](../dmx/operators-arithmetic.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40;&#41;DMX](../dmx/operators-dmx.md)   
 [Diviser l’expression &#40;SSIS&#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;diviser&#41; &#40;&#41;Transact-SQL](../t-sql/language-elements/divide-transact-sql.md)  
  
  
