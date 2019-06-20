---
title: '* (Multiplication) (DMX) | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f73e3e55045dd4ea9d4c2476540d2f7223d16eb0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62502073"
---
# <a name="-multiply-dmx"></a>* (Multiply) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Effectue l'opération arithmétique qui consiste à multiplier un nombre par un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Numeric_Expression*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur qui possède le type de données du paramètre doté de la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si une expression donne comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs arithmétiques &#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operators &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
