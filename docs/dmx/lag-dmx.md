---
title: Lag (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: LAG
dev_langs: DMX
helpviewer_keywords: Lag function
ms.assetid: 2da6df1a-5506-4871-a0f0-83292f1df41e
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 91c86f45191c9e68774d2a787499a169de8d919c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
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
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
