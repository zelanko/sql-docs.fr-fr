---
description: PredictCaseLikelihood (DMX)
title: PredictCaseLikelihood (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a08ec4809b281205386abad429afe339e0dbb1d1
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727698"
---
# <a name="predictcaselikelihood-dmx"></a>PredictCaseLikelihood (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Cette fonction retourne la probabilité qu'un cas d'entrée corresponde au modèle existant. Uniquement utilisée avec les modèles de clustering.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictCaseLikelihood([NORMALIZED|NONNORMALIZED])  
```  
  
## <a name="arguments"></a>Arguments  
 NORMALIZED  
 La valeur de retour contient la probabilité du cas au sein du modèle divisée par la probabilité du cas sans le modèle.  
  
 NONNORMALIZED  
 La valeur de retour contient la probabilité brute du cas, qui est le produit des probabilités des attributs de cas.  
  
## <a name="applies-to"></a>S'applique à  
 Modèles générés à l’aide des [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes de clustering et [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering.  
  
## <a name="return-type"></a>Type de retour  
 Nombre à virgule flottante double précision compris entre 0 et 1. Un nombre plus proche de 1 indique que le cas a une probabilité plus élevée de se produire dans ce modèle. Un nombre plus proche de 0 indique qu'il est moins probable que le cas se produise dans ce modèle.  
  
## <a name="remarks"></a>Notes  
 Par défaut, le résultat de la fonction **PredictCaseLikelihood** est normalisé. Les valeurs normalisées sont généralement plus utiles lorsque le nombre d'attributs d'un cas augmente et que les différences entre les probabilités brutes de deux cas deviennent beaucoup moins importantes.  
  
 L'équation suivante est utilisée pour calculer les valeurs normalisées pour des valeurs x et y données :  
  
-   x = probabilité du cas en fonction du modèle de clustering  
  
-   y = probabilité de cas marginale, calculée comme le logarithme du rapport de vraisemblance du cas en fonction des cas d'apprentissage  
  
-   Z = exp (log (x)-log (Y))  
  
 Normalized = (z/(1 + z))  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne la probabilité que le cas spécifié se produira dans le modèle de clustering, qui est basé sur la base de données [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW.  
  
```  
SELECT  
  PredictCaseLikelihood() AS Default_Likelihood,  
  PredictCaseLikelihood(NORMALIZED) AS Normalized_Likelihood,  
  PredictCaseLikelihood(NONNORMALIZED) AS Raw_Likelihood,  
FROM  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 Résultats attendus :  
  
|Default_Likelihood|Normalized_Likelihood|Raw_Likelihood|  
|-------------------------|----------------------------|---------------------|  
|6.30672792729321E-08|6.30672792729321E-08|9.5824454056846E-48|  
  
 La différence entre ces résultats montre l'effet de la normalisation. La valeur brute pour **CaseLikelihood** suggère que la probabilité de la casse est d’environ 20 pour cent ; Toutefois, lorsque vous normalisez les résultats, il devient évident que la probabilité de la casse est très faible.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX ](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX ](../dmx/general-prediction-functions-dmx.md)  
  
