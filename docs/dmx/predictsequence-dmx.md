---
title: PredictSequence (DMX) | Documents Microsoft
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
f1_keywords: PredictSequence
dev_langs: DMX
helpviewer_keywords: PredictSequence function
ms.assetid: c2992dfc-b99d-4430-8dcd-21ad3ffd4590
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 45d9652ed84fc8716029748c27d6be322dca57fd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Prédit les valeurs de séquence pour un ensemble spécifié de données de séquence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Type de retour  
 A \<expression de table >.  
  
## <a name="remarks"></a>Notes  
 Si le  *n*  paramètre est spécifié, il retourne les valeurs suivantes :  
  
-   Si  *n*  est supérieure à zéro, les valeurs de séquence le plus probables dans la prochaine  *n*  étapes.  
  
-   Si les deux *n-start* et *n-end* sont spécifiés, les valeurs de séquence à partir de *n-start* à *n-fin*.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne une séquence des cinq produits les plus susceptibles d'être achetés par un client dans la base de données [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], selon le modèle d'exploration de données Sequence Clustering.  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
