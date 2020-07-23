---
title: IsInNode (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 063c436f2e0d76ca891f332f25be385c2f16fdfa
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969639"
---
# <a name="isinnode-dmx"></a>IsInNode (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Indique si le nœud spécifié contient le cas courant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsInNode(<NodeID>)  
```  
  
## <a name="return-type"></a>Type de retour  
 Type booléen  
  
## <a name="remarks"></a>Remarques  
 **IsInNode** est utilisé uniquement dans les [&#62; de modèle Select from &#60;. CAS &#40;&#41;DMX](../dmx/select-from-model-cases-dmx.md) et [sélectionner des&#62; de &#60;modèle. SAMPLE_CASES &#40;des requêtes&#41;DMX](../dmx/select-from-model-sample-cases-dmx.md) .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne tous les cas qui ont été utilisés pour créer le modèle qui est associé au nœud spécifié dans la fonction IsInNode.  
  
```  
Select * from [TM Decision Tree].Cases  
WHERE IsInNode('0')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)  
  
  
