---
description: Utilisation (DMX)
title: Utilisation (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3886cd500282d34ef07145913e036a6ab4ad4852
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88394855"
---
# <a name="usage-dmx"></a>Utilisation (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Lorsque vous utilisez les extensions DMX (Data Mining Extensions) pour définir un nouveau modèle d’exploration de données dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , vous devez spécifier comment l’algorithme d’exploration de données qui génère le modèle utilisera chaque colonne. Vous pouvez spécifier une colonne comme étant l'un des types suivants :  
  
-   **Clé**  
  
-   **Séquence clé**  
  
-   **Temps clé**  
  
-   **Présentation**  
  
-   **PredictOnly**  
  
 En langage DMX, les colonnes non spécifiées sont considérées comme des colonnes d'entrée.  
  
 Pour traiter correctement un modèle, l'algorithme doit savoir quelle est la colonne clé qui identifie de manière unique chaque ligne, quelle est la colonne cible pour la création des prédictions si vous créez un modèle prévisible et quelles colonnes utiliser comme colonnes d'entrée pour créer les relations qui prévoient la colonne cible.  
  
 Les colonnes spécifiées en tant que type de **prédiction** sont utilisées comme colonnes d’entrée et de sortie. Les colonnes spécifiées en tant que **PredictOnly** sont utilisées uniquement comme colonnes de sortie. Il est possible que des algorithmes spécifiques considèrent les colonnes de type Predict différemment.  
  
 Pour plus d’informations sur les types d’utilisation de colonne [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pris en charge par, consultez [colonnes de modèle d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
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
  
  
