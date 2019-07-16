---
title: Distributions (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f4789a0e312decb2a46a9a1ba656fc5e4d3e9d47
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070751"
---
# <a name="distributions-dmx"></a>Distributions (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous pouvez définir le contenu des colonnes dans une structure d’exploration de données pour affecter la façon dont les algorithmes traitent les données dans ces colonnes lorsque vous créez des modèles d’exploration de données. Pour certains algorithmes, il est judicieux de définir la distribution des colonnes continues avant de traiter le modèle, s'il est établi que les colonnes contiennent des distributions de valeurs communes. Si vous ne définissez pas de distributions, les modèles d'exploration de données obtenus risquent de générer des prévisions moins précises, car les algorithmes disposent dans ce cas d'une moins grande quantité d'informations pour interpréter les données.  
  
 Les algorithmes d'exploration de données [!INCLUDE[msCoName](../includes/msconame-md.md)] prennent en charge les types de distribution suivants :  
  
 **NORMAL**  
 Les valeurs de la colonne continue forment un histogramme à distribution gaussienne normale.  
  
 **Log-normale**  
 Les valeurs de la colonne continue forment un histogramme dans lequel le logarithme des valeurs est normalement distribué.  
  
 **GLYPHES DE LARGEURS UNIFORMES**  
 Les valeurs de la colonne continue forment une courbe plate, dont toutes les valeurs sont sensiblement les mêmes.  
  
 Pour plus d’informations sur [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes d’exploration de données, consultez [algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md). Des algorithmes tiers peuvent prendre en charge des types de distribution supplémentaires. Pour déterminer les types de distribution un algorithme prend en charge, utilisez le **SUPPORTED_DISTRIBUTION_FLAGS** ensemble de lignes de schéma.  
  
 Pour plus d’informations sur les types de distribution, consultez [Distributions de colonnes &#40;d’exploration de données&#41;](../analysis-services/data-mining/column-distributions-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;Exploration de données&#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [Référence DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
