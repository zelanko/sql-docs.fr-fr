---
title: Types (DMX) de contenu | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ec3b618e83fff2915ec7d1dac0f25ea82c60912c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071023"
---
# <a name="content-types-dmx"></a>Types de contenu (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Pour fonctionner correctement, les algorithmes d'exploration de données ont besoin, outre le type de données, d'autres informations telles que le type de contenu. Le type de contenu permet à l'algorithme de déterminer la manière d'utiliser les données de la colonne.  
  
 Chaque algorithme prend en charge des types de contenu spécifiques. Par exemple, l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes ne peut pas utiliser des colonnes continues. Pour utiliser une colonne continue dans un modèle [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes, vous devez discrétiser les données de la colonne. Certains algorithmes nécessitent certains types de contenu afin de fonctionner correctement. Par exemple, l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series nécessite une colonne temps clé pour identifier la durée de la collecte des données.  
  
 Pour une description complète du contenu types que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge, consultez [des Types de contenu &#40;d’exploration de données&#41;](../analysis-services/data-mining/content-types-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Référence DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
