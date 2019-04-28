---
title: Distributions de colonnes (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a4969e3665aca4ed5aef588fa9595e96b846e98
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62715408"
---
# <a name="column-distributions-data-mining"></a>Distributions de colonnes (exploration de données)
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez définir des distributions de colonnes dans une structure d’exploration de données pour affecter la manière dont les algorithmes traitent les données dans ces colonnes quand vous créez des modèles d’exploration de données. Pour certains algorithmes, il est judicieux de définir la distribution des colonnes continues avant de traiter le modèle, s'il est établi que les colonnes contiennent des distributions de valeurs communes. Si vous ne définissez pas de distributions, les modèles d'exploration de données obtenus risquent de générer des prévisions moins précises, car les algorithmes disposent dans ce cas d'une moins grande quantité d'informations pour interpréter les données.  
  
 Les algorithmes disponibles dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prennent en charge les types de distribution suivants :  
  
 `Normal`  
 Les valeurs pour la colonne continue forment un histogramme à distribution normale.  
  
 ![Histogramme avec distribution normale](../media/normal-distribution.gif "histogramme avec distribution normale")  
  
 `Log Normal`  
 Les valeurs pour la colonne continue forment un histogramme, dans lequel la courbe est allongée à son extrémité supérieure et est rétrécie vers son extrémité inférieure.  
  
 ![Histogramme avec distribution normale logarithmique](../media/log-normal-distribution.gif "histogramme avec distribution normale logarithmique")  
  
 `Uniform`  
 Les valeurs de la colonne continue forment une courbe plate, dont toutes les valeurs sont sensiblement les mêmes.  
  
 ![Histogramme avec distribution uniforme](../media/uniform-distribution.gif "histogramme avec distribution uniforme")  
  
 Pour plus d’informations sur les algorithmes fournis par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;Exploration de données&#41;](content-types-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)   
 [Méthodes de discrétisation &#40;exploration de données&#41;](discretization-methods-data-mining.md)   
 [Distributions &#40;DMX&#41;](/sql/dmx/distributions-dmx)   
 [Colonnes de structure d’exploration de données](mining-structure-columns.md)  
  
  
