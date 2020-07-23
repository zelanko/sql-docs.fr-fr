---
title: RangeMid (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e3f13f1d110c26ee590df3a09296f6d861e34e37
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970657"
---
# <a name="rangemid-dmx"></a>RangeMid (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retourne le point milieu du compartiment prédit qui est découvert pour une colonne discrétisée.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RangeMid(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Colonnes scalaires discrétisées  
  
## <a name="return-type"></a>Type de retour  
 Valeur scalaire.  
  
## <a name="remarks"></a>Remarques  
 En cas d’utilisation avec [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), les fonctions **RangeMin**, **RangeMid**et **RangeMax** retournent les valeurs limites réelles du compartiment spécifié. Par exemple, si vous effectuez une prévision sur une colonne discrétisée, la requête retourne le numéro du compartiment prédit dans la colonne discrétisée. Les fonctions **RangeMin**, **RangeMid**et **RangeMax** décrivent le compartiment que spécifie la prédiction. Lorsque la fonction **RangeMid** est utilisée avec une instruction PREDICTION JOIN, la référence de colonne scalaire peut contenir uniquement des colonnes discrètes et prévisibles.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les valeurs minimales, maximales et moyennes de la colonne de données continues Yearly Income dans un modèle d'exploration de données Arbre de décision TM.  
  
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
 [RangeMax&#41;DMX &#40;](../dmx/rangemax-dmx.md)   
 [RangeMin&#41;DMX &#40;](../dmx/rangemin-dmx.md)  
  
  
