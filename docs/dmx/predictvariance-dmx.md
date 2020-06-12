---
title: PredictVariance (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 13beb2a9a99ceea1d517e9ef2c77a071d7c72d30
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83666861"
---
# <a name="predictvariance-dmx"></a>PredictVariance (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la variance d'une colonne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictVariance(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Colonne scalaire  
  
## <a name="return-type"></a>Type de retour  
 Valeur scalaire du type qui est spécifié par la * \< référence de colonne scalaire>*.  
  
## <a name="remarks"></a>Remarques  
 Si la référence de colonne est discrète, la fonction **PredictVariance** retourne 0 car la variance ne peut être calculée à partir de valeurs discrètes.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise une prédiction de jointure naturelle pour déterminer si un individu peut se révéler un acheteur potentiel de bicyclette selon le modèle d'exploration de données Arbre de décision TM et pour définir la variance de cette prévision.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictVariance([Bike Buyer]) AS [Variance]  
FROM  
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
  
  
