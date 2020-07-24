---
title: '&lt;= (Inférieur ou égal à) (DMX) | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ee38c26240392e634ce4ffa9644313a43f90bf16
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971647"
---
# <a name="lt-less-than-or-equal-to-dmx"></a>&lt;= (Inférieur ou égal à) (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Effectue une opération de comparaison qui détermine si la valeur d'une expression DMX (Data Mining Extensions) est inférieure ou égale à la valeur d'une autre expression DMX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DMX_Expression <= DMX_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DMX_Expression*  
 Expression DMX valide  
  
## <a name="return-value"></a>Valeur renvoyée  
 Valeur booléenne contenant la valeur TRUE si les deux paramètres ont la valeur Non NULL et si la valeur du premier paramètre est inférieure ou égale à la valeur du deuxième paramètre. La valeur booléenne contient FALSE si les deux paramètres ont la valeur Non NULL et si la valeur du premier paramètre est supérieure à la valeur du deuxième paramètre. La valeur booléenne contient une valeur NULL si l'un des deux ou les deux paramètres donnent comme résultat une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs de comparaison &#40;&#41;DMX](../dmx/operators-comparison.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40;&#41;DMX](../dmx/operators-dmx.md)  
  
  
