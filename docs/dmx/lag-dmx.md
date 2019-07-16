---
title: Lag (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 170e2f8b565f8b3d9d5e385b2bba9f183e743ace
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008350"
---
# <a name="lag-dmx"></a>Lag (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la tranche horaire entre la date du cas en cours et la dernière date de l'ensemble d'apprentissage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>Type de retour  
 Valeur scalaire de type entier.  
  
## <a name="remarks"></a>Notes  
 Si le **Lag** fonction est utilisée sur un modèle où se trouve la colonne KEY TIME au sein d’une table imbriquée, la fonction doit se trouve dans l’expression Sub-SELECT de l’instruction.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les cas compris dans les données des 12 derniers mois qui ont servi à l'apprentissage du modèle.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
