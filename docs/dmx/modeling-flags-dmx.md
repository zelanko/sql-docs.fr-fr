---
description: Indicateurs de modélisation (DMX)
title: Indicateurs de modélisation (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 52b28158c59e12886f8058883c65654b23ece9e0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466537"
---
# <a name="modeling-flags-dmx"></a>Indicateurs de modélisation (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Vous pouvez utiliser des indicateurs de modélisation dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour fournir à un algorithme d'exploration de données des informations supplémentaires portant sur les données définies dans une table de cas. Ces informations permettent à l'algorithme de construire un modèle d'exploration de données plus précis. Les indicateurs de modélisation peuvent se définir sur des colonnes de structure d'exploration de données comme sur des colonnes de modèle d'exploration de données.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge les indicateurs de modélisation suivants :  
  
 **NON NULL**  
 Les valeurs de la colonne d'attribut ne doivent jamais contenir de valeur NULL. Une erreur est générée si [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] rencontre une valeur NULL pour la colonne d’attribut au cours du processus d’apprentissage du modèle. Cet indicateur est défini sur une colonne de structure d'exploration de données.  
  
 **RÉGRESSEUR**  
 Indique que l'algorithme peut utiliser la colonne spécifiée dans la formule de régression des algorithmes de régression. Cet indicateur est pris en charge par les algorithmes [!INCLUDE[msCoName](../includes/msconame-md.md)] Linear Regression et [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees. Il est défini sur une colonne de modèle d'exploration de données.  
  
 **MODEL_EXISTENCE_ONLY**  
 Les valeurs de la colonne d'attribut sont moins importantes que la présence de l'attribut. Cet indicateur est défini sur une colonne de modèle d'exploration de données.  
  
 Des algorithmes tiers peuvent prendre en charge des indicateurs de modélisation supplémentaires. Pour déterminer les indicateurs de modélisation pris en charge par un algorithme, utilisez l’ensemble de lignes de schéma **SUPPORTED_MODELING_FLAGS** . Vous pouvez également interroger les services d'exploration de données sur le serveur afin de déterminer les indicateurs de modélisation pris en charge pour un algorithme spécifique. Par exemple, la requête suivante retourne les indicateurs de modélisation pris en charge pour l'algorithme MLR (Microsoft Linear Regression) sur le serveur actuel :  
  
```  
SELECT SUPPORTED_MODELING_FLAGS  
FROM $SYSTEM.DMSCHEMA_MINING_SERVICES  
WHERE SERVICE_NAME = 'Microsoft_Linear_Regression'  
```  
  
 Résultats attendus :  
  
 NOT NULL,REGRESSOR  
  
## <a name="specifying-modeling-flags-on-a-mining-model"></a>Spécification d'indicateurs de modélisation sur un modèle d'exploration de données  
 Pour obtenir des exemples de la syntaxe [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prise en charge pour la spécification d’un indicateur sur une colonne de structure d’exploration de données, consultez [Create mining structure &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
 Pour obtenir un exemple de la syntaxe permettant de spécifier un indicateur de modélisation sur une colonne de modèle d’exploration de données, consultez [ALTER Mining STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
 Pour plus d’informations sur l’utilisation des colonnes du modèle d’exploration de données, consultez [colonnes du modèle d’exploration](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns)de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX ](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
