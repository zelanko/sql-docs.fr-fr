---
title: SÉLECTIONNER à partir du &lt; modèle &gt; (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6f6371df8d1ab987bf1f49d149ff7856ba2d111c
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83666664"
---
# <a name="select-from-ltmodelgt-dmx"></a>SÉLECTIONNER à partir du &lt; modèle &gt; (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Effectue une jointure de prédiction vide, retournant la ou les valeurs les plus probables pour les colonnes spécifiées. Seul le contenu provenant du modèle d'exploration de données est utilisé pour créer la prédiction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT <expression list> [TOP <n>] FROM <model>   
[WHERE <condition list>]   
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *liste d’expressions*  
 Liste séparée par des virgules des expressions, ou des colonnes de type Predict ou Predict only.   
  
 *n*  
 facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *model*  
 Identificateur du modèle  
  
 *liste de conditions*  
 facultatif. Conditions pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les colonnes de la *liste d’expressions* doivent être définies comme prédiction ou prédire uniquement ou associées à une colonne prévisible.  
  
## <a name="naive-bayes-example"></a>Exemple de modèle Naive Bayes  
 L'exemple suivant réalise une prédiction de jointure vide sur la colonne Bike Buyer (Acheteur de bicyclette), en retournant l'état le plus probable du modèle d'exploration TM Naive Bayes.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Exemple de modèle Time Series  
 L'exemple suivant effectue une prédiction sur la colonne Amount (Quantité) du modèle Forecasting (Prévisions), en retournant les quatre étapes suivantes. La colonne Model Region (Région Modèle) combine des modèles de bicyclette et des régions en un seul identificateur. La requête utilise la fonction [PredictTimeSeries &#40;DMX&#41;](../dmx/predicttimeseries-dmx.md) pour effectuer la prédiction.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNER &#40;&#41;DMX](../dmx/select-dmx.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
