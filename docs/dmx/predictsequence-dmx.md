---
title: PredictSequence (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c6828b77af36b5dbbc50fbca0210961a7f2ed20c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041921"
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
 Un \<table expression >.  
  
## <a name="remarks"></a>Notes  
 Si le *n* paramètre est spécifié, il retourne les valeurs suivantes :  
  
-   Si *n* est supérieure à zéro, les valeurs de séquence probables dans le prochain *n* étapes.  
  
-   Si les deux *n-début* et *n-fin* sont spécifiés, les valeurs de séquence à partir de *n-début* à *n-fin*.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne une séquence des cinq produits les plus susceptibles d'être achetés par un client dans la base de données [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], selon le modèle d'exploration de données Sequence Clustering.  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
