---
title: Utilisation (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b961282ba6bc25caa260a3e156f843a413a5ef1a
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893113"
---
# <a name="usage-dmx"></a>Utilisation (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Lorsque vous utilisez les extensions DMX (Data Mining Extensions) pour définir un nouveau modèle d' [!INCLUDE[msCoName](../includes/msconame-md.md)] exploration de données dans, vous devez spécifier comment l’algorithme d' [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]exploration de données qui génère le modèle utilisera chaque colonne. Vous pouvez spécifier une colonne comme étant l'un des types suivants :  
  
-   **Key**  
  
-   **Séquence de touches**  
  
-   **Temps clé**  
  
-   **Predict**  
  
-   **PredictOnly**  
  
 En langage DMX, les colonnes non spécifiées sont considérées comme des colonnes d'entrée.  
  
 Pour traiter correctement un modèle, l'algorithme doit savoir quelle est la colonne clé qui identifie de manière unique chaque ligne, quelle est la colonne cible pour la création des prédictions si vous créez un modèle prévisible et quelles colonnes utiliser comme colonnes d'entrée pour créer les relations qui prévoient la colonne cible.  
  
 Les colonnes spécifiées en tant que type de prédiction sont utilisées comme colonnes d’entrée et de sortie. Les colonnes spécifiées en tant que **PredictOnly** sont utilisées uniquement comme colonnes de sortie. Il est possible que des algorithmes spécifiques considèrent les colonnes de type Predict différemment.  
  
 Pour plus d’informations sur les types d’utilisation [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de colonne pris en charge par, consultez [colonnes de modèle d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
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
  
  
