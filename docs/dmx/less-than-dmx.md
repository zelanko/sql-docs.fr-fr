---
description: '&lt; (Inférieur à) DMR'
title: '&lt; (Inférieur à) (DMX) | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9e57072bd8742d2d0da6fad11043c104297ab4f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466530"
---
# <a name="lt-less-than-dmx"></a>&lt; (Inférieur à) DMR
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Effectue une opération de comparaison qui détermine si la valeur d'une expression DMX (Data Mining Extensions) est inférieure à la valeur d'une autre expression DMX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DMX_Expression < DMX_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DMX_Expression*  
 Expression DMX valide  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne contenant la valeur TRUE si les deux paramètres ont la valeur Non NULL et si le premier paramètre a une valeur inférieure à la valeur du deuxième paramètre. La valeur booléenne contient FALSE si les deux paramètres ont la valeur Non NULL et si le premier paramètre a une valeur qui est égale à ou supérieure à la valeur du deuxième paramètre. La valeur booléenne contient une valeur NULL si l'un des deux ou les deux paramètres donnent comme résultat une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs de comparaison &#40;&#41;DMX ](../dmx/operators-comparison.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40;&#41;DMX ](../dmx/operators-dmx.md)  
  
  
