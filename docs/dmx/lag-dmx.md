---
title: Décalage (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 170e2f8b565f8b3d9d5e385b2bba9f183e743ace
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
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
 Si la fonction **lag** est utilisée sur un modèle où la colonne Key Time se trouve dans une table imbriquée, la fonction doit se trouver dans la sous-sélection de l’instruction.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les cas compris dans les données des 12 derniers mois qui ont servi à l'apprentissage du modèle.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)  
  
  
