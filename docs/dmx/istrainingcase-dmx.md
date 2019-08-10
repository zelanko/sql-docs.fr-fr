---
title: IsTrainingCase (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 23f36181d0ee4902f56aa4acb8163f7f43af8b31
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68889023"
---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indique si un cas est utilisé comme cas d'apprentissage pour le modèle d'exploration de données ou la structure d'exploration de données spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>Type de résultat  
 Retourne la **valeur true** si le cas fait partie du jeu de données d’apprentissage; sinon, false.  
  
## <a name="remarks"></a>Notes  
 Si vous utilisez l'Assistant Exploration de données pour créer une structure d'exploration de données et un modèle d'exploration de données connexe, 30 % des cas sont, par défaut, réservés pour une utilisation en tant que jeu de données de test. Les cas restants de la source de données que vous spécifiez sont utilisés pour l'apprentissage du modèle. Toutefois, si vous utilisez DMX (Data Mining Extensions) pour créer le modèle d'exploration de données, toutes les données sont, par défaut, utilisées pour l'apprentissage du modèle, et aucun jeu de test n'est créé. Pour permettre la création d'un jeu de données de test, vous devez définir les paramètres de la clause WITH HOLDOUT.  
  
 Vous pouvez déterminer si les données d'une structure d'exploration de données particulière ont été partitionnées en jeux de test et d'apprentissage en consultant la valeur des propriétés <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> et <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  L’extraction doit être activée sur le modèle si vous souhaitez utiliser les fonctions IsTrainingCase ou IsTestCase pour retourner des détails sur les cas dans le modèle. Pour plus d’informations, consultez [Activer l’extraction pour un modèle d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/enable-drillthrough-for-a-mining-model).  
  
 Pour retourner les cas qui font partie du jeu de données de test, utilisez [la &#40;fonction&#41;IsTestCase DMX](../dmx/istestcase-dmx.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise le modèle d’exploration de données de clustering du scénario de publipostage ciblé dans le didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). La requête retourne uniquement les cas qui sont utilisés pour l'apprentissage du modèle d'exploration de données. De plus, les cas d'apprentissage sont limités aux clients âgés de moins de 40 ans.  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 Pour obtenir d’autres exemples d’interrogation des cas utilisés dans l’exploration de données, consultez [Select from &#60;Model&#62;. Les &#40;cas&#41; DMX](../dmx/select-from-model-cases-dmx.md) et sélectionnent la [ &#60;structure&#62;. CAS](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Jeux de données d’apprentissage et de test](https://docs.microsoft.com/analysis-services/data-mining/training-and-testing-data-sets)   
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Requêtes d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-mining-queries)  
  
  
