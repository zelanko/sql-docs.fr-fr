---
title: IsDescendant (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bab465fe98c9509eaa99999a321317ee8013a74d
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969760"
---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Indique si le nœud actuel provient du nœud spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Type de retour  
 Type booléen  
  
## <a name="remarks"></a>Notes  
 **IsDescendant** est utilisé uniquement dans les [&#62; de modèle Select from &#60;. CONTENU &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md) et [sélectionnez &#60;&#62; de modèle. DIMENSION_CONTENT &#40;des requêtes&#41;DMX](../dmx/select-from-model-dimension-content-dmx.md) .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne tous les cas qui descendent du nœud spécifié dans la fonction IsDescendant.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)  
  
  
