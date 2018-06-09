---
title: PAS (DMX) | Documents Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 053eb905edb1379bfdc40ec010dc6d4efadcba26
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842842"
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
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui retourne FALSE si l'argument renvoie la valeur TRUE ; dans le cas contraire, elle retourne TRUE.  
  
## <a name="remarks"></a>Notes  
 L'argument est considéré comme une valeur booléenne (0 correspond à la valeur FALSE ; dans le cas contraire, TRUE) avant que l'opérateur effectue la négation logique. Si *Expression1* a la valeur TRUE, l’opérateur retourne FALSE. Si *Expression1* est FALSE, l’opérateur retourne TRUE. Le tableau ci-dessous explique comment s'effectue la conjonction logique.  
  
|Si Expression1 est|La valeur de retour est|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs logiques &#40;DMX&#41;](../dmx/operators-logical.md)   
 [Opérateurs &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
