---
description: OR (DMX)
title: OU (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 86a9aede9f1b9b12f465fa52b0343cf22c04b295
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88395435"
---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Opérateur logique qui effectue une disjonction logique sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
 *Expression2*  
 Expression DMX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui retourne TRUE si l'un ou l'autre ou les deux arguments donnent comme résultat la valeur TRUE ; dans le cas contraire, elle retourne FALSE.   
  
## <a name="remarks"></a>Notes  
 Les deux arguments sont considérés comme valeurs booléennes (0 correspond à la valeur FALSE ; sinon TRUE) avant que l'opérateur effectue la disjonction logique. Si l'un ou l'autre ou les deux arguments donnent comme résultat la valeur TRUE, l'opérateur retourne TRUE. Si *expression1* prend la valeur true et que *Expression2* a la valeur false, l’opérateur retourne true.  
  
 Le tableau ci-dessous explique comment s'effectue la disjonction logique.  
  
|Si Expression1 est|Si Expression2 est|La valeur de retour est|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|false|true|  
|false|VRAI|TRUE|  
|false|false|false|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs logiques &#40;&#41;DMX ](../dmx/operators-logical.md)   
 [Opérateurs &#40;&#41;DMX ](../dmx/operators-dmx.md)  
  
  
