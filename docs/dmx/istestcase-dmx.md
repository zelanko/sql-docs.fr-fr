---
description: IsTestCase (DMX)
title: IsTestCase (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c0bc9e4ffe7da1f81bbd246e9cbfa7398bfec50e
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726143"
---
# <a name="istestcase-dmx"></a>IsTestCase (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Indique si un cas est utilisé comme cas de test pour le modèle d'exploration de données ou la structure d'exploration de données spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>Type de résultat  
 Retourne la **valeur true** si le cas fait partie du jeu de données de test ; Sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Si vous utilisez l'Assistant Exploration de données pour créer une structure d'exploration de données et un modèle d'exploration de données connexe, 30 % des cas sont, par défaut, réservés pour une utilisation en tant que jeu de données de test. Les cas restants sont utilisés pour l'apprentissage du modèle d'exploration de données. Le même jeu de données de test peut être utilisé avec tous les modèles qui sont basés sur cette structure. Toutefois, si vous utilisez DMX pour créer le modèle d'exploration de données, toutes les données sont, par défaut, utilisées pour l'apprentissage du modèle, et aucun jeu de test n'est créé. Pour permettre la création d’un jeu de données de test, vous devez définir les paramètres de la clause WITH exclusion.  
  
 Vous pouvez déterminer si un jeu de test a été créé sur une structure d'exploration de données particulière en consultant la valeur des propriétés <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> et <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  L’extraction doit être activée sur le modèle si vous souhaitez utiliser les fonctions IsTrainingCase ou IsTestCase pour retourner des détails sur les cas d’un modèle particulier. Pour plus d’informations, consultez [Activer l’extraction pour un modèle d’exploration de données](/analysis-services/data-mining/enable-drillthrough-for-a-mining-model).  
  
 Pour retourner les cas qui font partie du jeu de données d’apprentissage, utilisez la fonction [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise la `Targeted Mailing` structure d’exploration de données qui est créée dans le didacticiel sur l' [exploration de données de base](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130)). La requête retourne tous les cas de la structure qui sont utilisés pour le test.  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 Pour plus d’informations sur l’interrogation des cas utilisés dans l’exploration de données, consultez [SELECT FROM &#60;model&#62;. CAS &#40;&#41;DMX ](../dmx/select-from-model-cases-dmx.md) et [sélectionner des&#62; de la structure de &#60;. CAS](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;&#41;DMX ](../dmx/functions-dmx.md)   
 [Requêtes d’exploration de données](/analysis-services/data-mining/data-mining-queries)   
 [Jeux de données d'apprentissage et de test](/analysis-services/data-mining/training-and-testing-data-sets)  
  
