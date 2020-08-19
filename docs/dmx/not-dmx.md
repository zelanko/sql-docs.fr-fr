---
description: NOT (DMX)
title: NON (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 03a8ea859160af36b9c822bf01c4197e8b4c3175
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426261"
---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

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
 L'argument est considéré comme une valeur booléenne (0 correspond à la valeur FALSE ; dans le cas contraire, TRUE) avant que l'opérateur effectue la négation logique. Si *expression1* a la valeur true, l’opérateur retourne false. Si *expression1* a la valeur false, l’opérateur retourne true. Le tableau ci-dessous explique comment s'effectue la conjonction logique.  
  
|Si Expression1 est|La valeur de retour est|  
|-----------------------|---------------------|  
|true|false|  
|false|true|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs logiques &#40;&#41;DMX ](../dmx/operators-logical.md)   
 [Opérateurs &#40;&#41;DMX ](../dmx/operators-dmx.md)  
  
  
