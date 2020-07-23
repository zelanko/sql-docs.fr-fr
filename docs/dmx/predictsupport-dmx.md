---
title: PredictSupport (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: da8673d58a6d1889017b0f79ea7cb4bf41c64466
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970697"
---
# <a name="predictsupport-dmx"></a>PredictSupport (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retourne la valeur de support pour un état spécifié.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>S'applique à  
 Colonne scalaire  
  
## <a name="return-type"></a>Type de retour  
 Valeur scalaire du type spécifié par *\<*scalar column reference*>* .  
  
## <a name="remarks"></a>Remarques  
 Si l'état prévisible est omis, c'est l'état doté de la probabilité de prévision la plus élevée qui est utilisé, à l'exception du compartiment des états manquants. Pour inclure le compartiment des États manquants, affectez à la valeur \<predicted state> **INCLUDE_NULL**.  
  
 Pour retourner la prise en charge des États manquants, affectez la valeur \<predicted state> null.  
  
> [!NOTE]  
>  Les valeurs de support sont calculées différemment ou peuvent avoir une interprétation différente selon le type de modèle que vous interrogez. Pour plus d’informations sur la façon dont la prise en charge est calculée pour un type de modèle particulier, consultez le type d’algorithme individuel dans [contenu du modèle d’exploration de données &#40;Analysis Services-exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise une requête singleton pour prévoir si un individu peut se révéler un acheteur potentiel de bicyclette et pour déterminer la prise en charge de la prévision selon le modèle d'exploration de données Arbre de décision TM.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictSupport([Bike Buyer]) AS [Support],  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)  
  
  
