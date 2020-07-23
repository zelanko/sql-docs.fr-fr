---
title: Types de contenu (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a0c44e0ea90b253cee5564a327d49c34c1ae78a
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969890"
---
# <a name="content-types-dmx"></a>Types de contenu (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Pour fonctionner correctement, les algorithmes d'exploration de données ont besoin, outre le type de données, d'autres informations telles que le type de contenu.  Le type de contenu permet à l'algorithme de déterminer la manière d'utiliser les données de la colonne.  
  
 Chaque algorithme prend en charge des types de contenu spécifiques. Par exemple, l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes ne peut pas utiliser des colonnes continues. Pour utiliser une colonne continue dans un modèle [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes, vous devez discrétiser les données de la colonne. Certains algorithmes nécessitent certains types de contenu afin de fonctionner correctement. Par exemple, l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series nécessite une colonne temps clé pour identifier la durée de la collecte des données.  
  
 Pour obtenir une description complète des types de contenu [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pris en charge par, consultez [types de contenu &#40;&#41;d’exploration de données ](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining).  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
