---
description: AND (DMX)
title: ET (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 17dabee823323c63a2d36a21cd79b81e9a323803
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431201"
---
# <a name="and-dmx"></a>AND (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Effectue une conjonction logique sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
 *Expression2*  
 Expression DMX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui retourne TRUE si les deux paramètres donnent comme résultat la valeur TRUE ; dans le cas contraire, elle retourne FALSE.  
  
## <a name="remarks"></a>Notes  
 Les deux paramètres sont considérés comme valeurs booléennes (0 correspond à la valeur FALSE ; sinon TRUE) avant que l'opérateur effectue la conjonction logique. Le tableau ci-dessous affiche la liste des valeurs qui sont retournées selon les différentes combinaisons de valeurs des paramètres.  
  
|Si Expression1 est|Si Expression2 est|La valeur de retour est|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|false|false|  
|false|true|false|  
|false|false|false|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs logiques &#40;&#41;DMX ](../dmx/operators-logical.md)   
 [Opérateurs &#40;&#41;DMX ](../dmx/operators-dmx.md)  
  
  
