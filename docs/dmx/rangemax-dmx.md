---
title: RangeMax (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 417f92a00e396952218c6ef04d105245f1e3708e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62658972"
---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 Le **RangeMax** fonction peut être utilisée dans [SELECT DISTINCT FROM &#60;modèle &#62; &#40;DMX&#41; ](../dmx/select-distinct-from-model-dmx.md) requêtes. Utilisée avec ce type de requête, la référence de colonne scalaire peut contenir des colonnes continues ou discrètes qui sont soit prédictibles, soit d'entrée.  
  
 Lorsqu’il est utilisé avec [SELECT FROM &#60;modèle&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), le **RangeMin**, **RangeMid**, et **RangeMax**  fonctions retournent les valeurs limites réelles du compartiment spécifié. Par exemple, si vous effectuez une prévision sur une colonne discrétisée, la requête retourne le numéro du compartiment prédit dans la colonne discrétisée. Le **RangeMin**, **RangeMid**, et **RangeMax** fonctions décrivent le compartiment que la prévision spécifie. Lorsque le **RangeMax** fonction est utilisée avec une instruction PREDICTION JOIN, la référence de colonne scalaire peut contenir uniquement des colonnes discrètes, prédictibles.  
  
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
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
