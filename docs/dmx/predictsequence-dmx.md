---
description: PredictSequence (DMX)
title: PredictSequence (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 31f99205f3e23db23c5c2a38750f75212763e8de
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426101"
---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Prédit les valeurs de séquence pour un ensemble spécifié de données de séquence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Type de retour  
 \<table expression>  
  
## <a name="remarks"></a>Notes  
 Si le paramètre *n* est spécifié, les valeurs suivantes sont renvoyées :  
  
-   Si *n* est supérieur à zéro, les valeurs de séquence les plus probables dans les *n* étapes suivantes.  
  
-   Si *n-Start* et *n-end* sont spécifiés, les valeurs de séquence de *n-Start* à *n-end*.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne une séquence des cinq produits les plus susceptibles d'être achetés par un client dans la base de données [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], selon le modèle d'exploration de données Sequence Clustering.  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX ](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX ](../dmx/general-prediction-functions-dmx.md)  
  
  
