---
title: OU (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OR
dev_langs:
- DMX
helpviewer_keywords:
- OR operator
ms.assetid: 727a38a9-7f75-4963-8e8a-aa703c129d30
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 41cdd1638dc31eefa9cb034db33ef9d30162d617
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Un opérateur logique qui effectue une disjonction logique sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
 *Expression2*  
 Expression DMX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur booléenne qui retourne TRUE si l'un ou l'autre ou les deux arguments donnent comme résultat la valeur TRUE ; dans le cas contraire, elle retourne FALSE.   
  
## <a name="remarks"></a>Notes  
 Les deux arguments sont considérés comme valeurs booléennes (0 correspond à la valeur FALSE ; sinon TRUE) avant que l'opérateur effectue la disjonction logique. Si l'un ou l'autre ou les deux arguments donnent comme résultat la valeur TRUE, l'opérateur retourne TRUE. Si *Expression1* a la valeur TRUE et *Expression2* a la valeur FALSE, l’opérateur retourne TRUE.  
  
 Le tableau ci-dessous explique comment s'effectue la disjonction logique.  
  
|Si Expression1 est|Si Expression2 est|La valeur de retour est|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|TRUE|  
|FALSE|TRUE|TRUE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logique opérateurs &#40; DMX &#41;](../dmx/operators-logical.md)   
 [Opérateurs &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  

