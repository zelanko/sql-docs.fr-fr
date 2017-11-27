---
title: "SELECT FROM &lt;modèle&gt; (DMX) | Documents Microsoft"
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
f1_keywords:
- SELECT
- FROM
dev_langs: DMX
helpviewer_keywords:
- empty prediction joins [DMX]
- SELECT FROM <model> statement
ms.assetid: dc5b9a01-e308-4ee8-84fc-ba4b991c60aa
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 589ab76ad5ffeb415366c545a4b00a8be2a9d63b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
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
 Ce paramètre est facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *model*  
 Identificateur du modèle  
  
 *liste des conditions*  
 Ce paramètre est facultatif. Conditions pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Ce paramètre est facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les colonnes dans le *liste d’expressions* doit être défini comme predict ou predict only, ou associée à une colonne prévisible.  
  
## <a name="naive-bayes-example"></a>Exemple de modèle Naive Bayes  
 L'exemple suivant réalise une prédiction de jointure vide sur la colonne Bike Buyer (Acheteur de bicyclette), en retournant l'état le plus probable du modèle d'exploration TM Naive Bayes.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Exemple de modèle Time Series  
 L'exemple suivant effectue une prédiction sur la colonne Amount (Quantité) du modèle Forecasting (Prévisions), en retournant les quatre étapes suivantes. La colonne Model Region (Région Modèle) combine des modèles de bicyclette et des régions en un seul identificateur. La requête utilise le [PredictTimeSeries &#40; DMX &#41;](../dmx/predicttimeseries-dmx.md) (fonction) pour effectuer la prédiction.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNEZ &#40; DMX &#41;](../dmx/select-dmx.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
