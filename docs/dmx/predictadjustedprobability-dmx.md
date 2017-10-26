---
title: PredictAdjustedProbability (DMX) | Documents Microsoft
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
- PredictAdjustedProbability
dev_langs:
- DMX
helpviewer_keywords:
- PredictAdjustedProbability function
ms.assetid: 9a1e2ec5-5a37-4df6-a78e-26a495cc9301
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0ced04fb08ab3896fa535a7c11b697f85d8395a6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="predictadjustedprobability-dmx"></a>PredictAdjustedProbability (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la probabilité ajustée d'un état spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictAdjustedProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>S'applique à  
 Colonne scalaire  
  
## <a name="return-type"></a>Type de retour  
 Une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Si l'état prévisible est omis, c'est l'état doté de la probabilité de prévision la plus élevée qui est utilisé, à l'exception du compartiment des états manquants. Pour inclure le compartiment des États manquants, définissez la \<état prédit > à **INCLUDE_NULL**.  
  
 Pour retourner la probabilité ajustée des États manquants, définissez la \<état prédit > sur la valeur NULL.  
  
 Le **PredictAdjustedProbability** fonction est un [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] extension pour le [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB pour l’exploration de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise une prédiction de jointure naturelle pour déterminer si un individu peut se révéler un acheteur potentiel de bicyclette selon le modèle d'exploration de données Arbre de décision TM et pour définir la probabilité ajustée de cette prévision.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictAdjustedProbability([Bike Buyer]) AS [Adjusted Probability]  
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
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

