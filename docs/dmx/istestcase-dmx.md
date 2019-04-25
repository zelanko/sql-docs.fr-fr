---
title: IsTestCase (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b7e80f8a9dfb82f13350b94b310690a081fae1de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62503731"
---
# <a name="istestcase-dmx"></a>IsTestCase (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indique si un cas est utilisé comme cas de test pour le modèle d'exploration de données ou la structure d'exploration de données spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>Type de résultat  
 Retourne **true** si le cas fait partie du jeu de données de test ; sinon **false**.  
  
## <a name="remarks"></a>Notes  
 Si vous utilisez l'Assistant Exploration de données pour créer une structure d'exploration de données et un modèle d'exploration de données connexe, 30 % des cas sont, par défaut, réservés pour une utilisation en tant que jeu de données de test. Les cas restants sont utilisés pour l'apprentissage du modèle d'exploration de données. Le même jeu de données de test peut être utilisé avec tous les modèles qui sont basés sur cette structure. Toutefois, si vous utilisez DMX pour créer le modèle d'exploration de données, toutes les données sont, par défaut, utilisées pour l'apprentissage du modèle, et aucun jeu de test n'est créé. Pour activer la création d’un jeu de données de test, vous devez définir les paramètres de la clause WITH HOLDOUT.  
  
 Vous pouvez déterminer si un jeu de test a été créé sur une structure d'exploration de données particulière en consultant la valeur des propriétés <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> et <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  Extraction doit être activée sur le modèle si vous souhaitez utiliser les fonctions IsTrainingCase ou IsTestCase pour retourner des détails sur les cas dans un modèle particulier. Pour plus d’informations, consultez [Activer l’extraction pour un modèle d’exploration de données](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md).  
  
 Pour retourner les cas qui font partie du jeu de données d’apprentissage, utilisez la fonction [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise le `Targeted Mailing` structure d’exploration de données qui est créé dans le [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). La requête retourne tous les cas de la structure qui sont utilisés pour le test.  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 Pour plus d’informations sur comment interroger les cas utilisés dans l’exploration de données, consultez [SELECT FROM &#60;modèle&#62;. CAS &#40;DMX&#41; ](../dmx/select-from-model-cases-dmx.md) et [SELECT FROM &#60;structure&#62;. CAS](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Requêtes d'exploration de données](../analysis-services/data-mining/data-mining-queries.md)   
 [Jeux de données d’apprentissage et de test](../analysis-services/data-mining/training-and-testing-data-sets.md)  
  
  
