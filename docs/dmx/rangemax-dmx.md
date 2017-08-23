---
title: RangeMax (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RangeMax
dev_langs:
- DMX
helpviewer_keywords:
- RangeMax function
ms.assetid: 6798d9d7-c3dc-40fb-bd8e-56cb1a6d0e5f
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8b8cb363e9d5db767ed172206f497ff300bb29a6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la limite supérieure du compartiment prédit qui est découvert pour une colonne discrétisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Colonnes scalaires.  
  
## <a name="return-type"></a>Type de retour  
 Une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Le **RangeMax** fonction peut être utilisée dans [SELECT DISTINCT FROM &#60; modèle &#62; &#40; DMX &#41;](../dmx/select-distinct-from-model-dmx.md) requêtes. Utilisée avec ce type de requête, la référence de colonne scalaire peut contenir des colonnes continues ou discrètes qui sont soit prédictibles, soit d'entrée.  
  
 Lorsqu’il est utilisé avec [SELECT FROM &#60; modèle &#62; JOINTURE de prédiction &#40; DMX &#41; ](../dmx/select-from-model-prediction-join-dmx.md), le **RangeMin**, **RangeMid**, et **RangeMax** fonctions retournent les valeurs limites réelles du compartiment spécifié. Par exemple, si vous effectuez une prévision sur une colonne discrétisée, la requête retourne le numéro du compartiment prédit dans la colonne discrétisée. Le **RangeMin**, **RangeMid**, et **RangeMax** fonctions décrivent le compartiment que la prévision spécifie. Lorsque le **RangeMax** fonction est utilisée avec une instruction PREDICTION JOIN, la référence de colonne scalaire peut contenir uniquement des colonnes discrètes, prédictibles.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les valeurs minimales, maximales et moyennes de la colonne de données continues Yearly Income du modèle d'exploration de données Arbre de décision.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40; DMX &#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40; DMX &#41;](../dmx/rangemin-dmx.md)  
  
  

