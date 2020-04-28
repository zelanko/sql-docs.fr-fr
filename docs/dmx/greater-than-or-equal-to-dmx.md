---
title: '&gt;= (Supérieur ou égal à) (DMX) | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3615dc8b5de0e5057e2dedaa0077aae51ed87ebe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68074787"
---
# <a name="gt-greater-than-or-equal-to-dmx"></a>&gt;= (Supérieur ou égal à) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Effectue une opération de comparaison qui détermine si la valeur d'une expression DMX (Data Mining Extensions) est supérieure ou égale à la valeur d'une autre expression DMX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DMX_Expression >= DMX_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DMX_Expression*  
 Expression DMX valide  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne contenant la valeur TRUE si les deux paramètres ont la valeur Non NULL et si la valeur du premier paramètre est supérieure ou égale à la valeur du deuxième paramètre. La valeur booléenne contient FALSE si les deux paramètres ont la valeur Non NULL et si la valeur du premier paramètre est inférieure à la valeur du deuxième paramètre. La valeur booléenne contient une valeur NULL si l'un des deux ou les deux paramètres donnent comme résultat une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs de comparaison &#40;&#41;DMX](../dmx/operators-comparison.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40;&#41;DMX](../dmx/operators-dmx.md)  
  
  
