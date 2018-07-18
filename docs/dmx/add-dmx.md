---
title: + (Ajouter) (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1cbb2714e9bc4f5d4944494c3b900bab737fe705
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37998801"
---
# <a name="-add-dmx"></a>+ (Add) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Effectue une opération arithmétique qui consiste à ajouter deux nombres ensemble.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric_Expression + Numeric_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Numeric_expression*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur qui possède le type de données du paramètre doté de la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si une expression s'évalue à NULL, l'opérateur retourne le résultat de l'autre expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs arithmétiques &#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
