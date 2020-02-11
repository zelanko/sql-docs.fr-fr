---
title: ET (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0c727e6a6f981dd2862575bfb4943b104196080
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67913745"
---
# <a name="and-dmx"></a>AND (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
|TRUE|FALSE|FALSE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs logiques &#40;&#41;DMX](../dmx/operators-logical.md)   
 [Opérateurs &#40;&#41;DMX](../dmx/operators-dmx.md)  
  
  
