---
title: Distributions (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- column distributions [DMX]
- distributions [DMX]
- DMX [Analysis Services], distributions
- Data Mining Extensions [Analysis Services], distributions
ms.assetid: cfbb9f38-ae71-401e-867f-15c6a2b6fb97
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8d56f7ed56349f57484aa39511b1ab86607f4508
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="distributions-dmx"></a>Distributions (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous pouvez définir le contenu des colonnes dans une structure d’exploration de données, pour affecter la façon dont les algorithmes traitent les données de ces colonnes lorsque vous créez des modèles d’exploration de données. Pour certains algorithmes, il est judicieux de définir la distribution des colonnes continues avant de traiter le modèle, s'il est établi que les colonnes contiennent des distributions de valeurs communes. Si vous ne définissez pas de distributions, les modèles d'exploration de données obtenus risquent de générer des prévisions moins précises, car les algorithmes disposent dans ce cas d'une moins grande quantité d'informations pour interpréter les données.  
  
 Les algorithmes d'exploration de données [!INCLUDE[msCoName](../includes/msconame-md.md)] prennent en charge les types de distribution suivants :  
  
 **NORMAL**  
 Les valeurs de la colonne continue forment un histogramme à distribution gaussienne normale.  
  
 **Log-normale**  
 Les valeurs de la colonne continue forment un histogramme dans lequel le logarithme des valeurs est normalement distribué.  
  
 **UNIFORME**  
 Les valeurs de la colonne continue forment une courbe plate, dont toutes les valeurs sont sensiblement les mêmes.  
  
 Pour plus d’informations sur [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes d’exploration de données, consultez [algorithmes d’exploration de données &#40; Analysis Services - Exploration de données &#41; ](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md). Des algorithmes tiers peuvent prendre en charge des types de distribution supplémentaires. Pour déterminer les types de distribution un algorithme prend en charge, utilisez le **SUPPORTED_DISTRIBUTION_FLAGS** de lignes du schéma.  
  
 Pour plus d’informations sur les types de distribution, consultez [Distributions de colonnes &#40; exploration de données &#41;](../analysis-services/data-mining/column-distributions-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu des Types de &#40; exploration de données &#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence](../dmx/data-mining-extensions-dmx-reference.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
