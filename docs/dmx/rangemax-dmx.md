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
ms.openlocfilehash: 61552cd8e38f77d12d7f4da10e2bbe9281e6073d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041682"
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
 Valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 La fonction **RangeMax** peut être utilisée dans [Select distinct à partir de &#60;modèle &#62; &#40;des requêtes&#41;DMX](../dmx/select-distinct-from-model-dmx.md) . Utilisée avec ce type de requête, la référence de colonne scalaire peut contenir des colonnes continues ou discrètes qui sont soit prédictibles, soit d'entrée.  
  
 En cas d’utilisation avec [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), les fonctions **RangeMin**, **RangeMid**et **RangeMax** retournent les valeurs limites réelles du compartiment spécifié. Par exemple, si vous effectuez une prévision sur une colonne discrétisée, la requête retourne le numéro du compartiment prédit dans la colonne discrétisée. Les fonctions **RangeMin**, **RangeMid**et **RangeMax** décrivent le compartiment que spécifie la prédiction. Lorsque la fonction **RangeMax** est utilisée avec une instruction PREDICTION JOIN, la référence de colonne scalaire peut contenir uniquement des colonnes discrètes et prévisibles.  
  
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
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid&#41;DMX &#40;](../dmx/rangemid-dmx.md)   
 [RangeMin&#41;DMX &#40;](../dmx/rangemin-dmx.md)  
  
  
