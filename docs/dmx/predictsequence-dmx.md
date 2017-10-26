---
title: PredictSequence (DMX) | Documents Microsoft
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
- PredictSequence
dev_langs:
- DMX
helpviewer_keywords:
- PredictSequence function
ms.assetid: c2992dfc-b99d-4430-8dcd-21ad3ffd4590
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e9ddd402be082937ec828a86d82a238d121e55dd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  

