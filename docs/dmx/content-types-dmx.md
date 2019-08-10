---
title: Types de contenu (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: da8a5e5602b877c12284d8410f6b2a1c7da6bc58
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68889145"
---
# <a name="content-types-dmx"></a>Types de contenu (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Pour fonctionner correctement, les algorithmes d'exploration de données ont besoin, outre le type de données, d'autres informations telles que le type de contenu. Le type de contenu permet à l'algorithme de déterminer la manière d'utiliser les données de la colonne.  
  
 Chaque algorithme prend en charge des types de contenu spécifiques. Par exemple, l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes ne peut pas utiliser des colonnes continues. Pour utiliser une colonne continue dans un modèle [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes, vous devez discrétiser les données de la colonne. Certains algorithmes nécessitent certains types de contenu afin de fonctionner correctement. Par exemple, l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series nécessite une colonne temps clé pour identifier la durée de la collecte des données.  
  
 Pour obtenir une description complète des types de contenu [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pris en charge par, consultez [ &#40;exploration&#41;de données des types de contenu](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining).  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Référence DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Éléments de syntaxe &#40;DMX&#41; des extensions d’exploration de données](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Référence des fonctions &#40;DMX&#41; des extensions d’exploration de données](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Référence des opérateurs &#40;DMX&#41; Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Référence des instructions &#40;DMX&#41; Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de la &#40;syntaxe&#41; DMX des extensions d’exploration de données](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Fonctions &#40;de prédiction générales DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
