---
title: SELECT FROM &lt;modèle&gt; (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aac800e225eb5323b1bffeafda77d059f0a837e2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989901"
---
# <a name="select-from-ltmodelgt-dmx"></a>SELECT FROM &lt;modèle&gt; (DMX)
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
 Facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *model*  
 Identificateur du modèle  
  
 *liste de conditions*  
 Facultatif. Conditions pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les colonnes dans le *liste d’expressions* doit être défini comme predict ou predict only, ou liés à une colonne prédictible.  
  
## <a name="naive-bayes-example"></a>Exemple de modèle Naive Bayes  
 L'exemple suivant réalise une prédiction de jointure vide sur la colonne Bike Buyer (Acheteur de bicyclette), en retournant l'état le plus probable du modèle d'exploration TM Naive Bayes.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Exemple de modèle Time Series  
 L'exemple suivant effectue une prédiction sur la colonne Amount (Quantité) du modèle Forecasting (Prévisions), en retournant les quatre étapes suivantes. La colonne Model Region (Région Modèle) combine des modèles de bicyclette et des régions en un seul identificateur. La requête utilise le [PredictTimeSeries &#40;DMX&#41; ](../dmx/predicttimeseries-dmx.md) (fonction) pour effectuer la prédiction.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNEZ &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
