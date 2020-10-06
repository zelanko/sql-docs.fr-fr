---
description: Distributions (DMX)
title: Distributions (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9deb3afaa6d0a4bc90281c2cc3998365eccb9838
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726220"
---
# <a name="distributions-dmx"></a>Distributions (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , vous pouvez définir le contenu des colonnes dans une structure d’exploration de données, pour affecter la façon dont les algorithmes traitent les données dans ces colonnes lorsque vous créez des modèles d’exploration de données. Pour certains algorithmes, il est judicieux de définir la distribution des colonnes continues avant de traiter le modèle, s'il est établi que les colonnes contiennent des distributions de valeurs communes. Si vous ne définissez pas de distributions, les modèles d'exploration de données obtenus risquent de générer des prévisions moins précises, car les algorithmes disposent dans ce cas d'une moins grande quantité d'informations pour interpréter les données.  
  
 Les algorithmes d'exploration de données [!INCLUDE[msCoName](../includes/msconame-md.md)] prennent en charge les types de distribution suivants :  
  
 **NORMAL**  
 Les valeurs de la colonne continue forment un histogramme à distribution gaussienne normale.  
  
 **Log-normale**  
 Les valeurs de la colonne continue forment un histogramme dans lequel le logarithme des valeurs est normalement distribué.  
  
 **UNIFORME**  
 Les valeurs de la colonne continue forment une courbe plate, dont toutes les valeurs sont sensiblement les mêmes.  
  
 Pour plus d’informations sur les [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes d’exploration de données, consultez algorithmes d’exploration de [données &#40;Analysis Services-exploration de données&#41;](/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining). Des algorithmes tiers peuvent prendre en charge des types de distribution supplémentaires. Pour déterminer les types de distribution pris en charge par un algorithme, utilisez l’ensemble de lignes de schéma **SUPPORTED_DISTRIBUTION_FLAGS** .  
  
 Pour plus d’informations sur les types de distribution, consultez [distributions de colonnes &#40;&#41;d’exploration de données ](/analysis-services/data-mining/column-distributions-data-mining).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;l’exploration de données&#41;](/analysis-services/data-mining/content-types-data-mining)   
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX ](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
