---
title: Distributions de colonnes (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 6c7eab32f251b9622c6ac77febf2c004806c024b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78174548"
---
# <a name="column-distributions-data-mining"></a>Distributions de colonnes (exploration de données)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez définir des distributions de colonnes dans une structure d’exploration de données, pour affecter la façon dont les algorithmes traitent les données dans ces colonnes lorsque vous créez des modèles d’exploration de données. Pour certains algorithmes, il est judicieux de définir la distribution des colonnes continues avant de traiter le modèle, s'il est établi que les colonnes contiennent des distributions de valeurs communes. Si vous ne définissez pas de distributions, les modèles d'exploration de données obtenus risquent de générer des prévisions moins précises, car les algorithmes disposent dans ce cas d'une moins grande quantité d'informations pour interpréter les données.

 Les algorithmes disponibles dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prennent en charge les types de distribution suivants :

 `Normal`Les valeurs de la colonne continue forment un histogramme avec une distribution normale.

 ![Histogramme avec distribution normale](../media/normal-distribution.gif "Histogramme avec distribution normale")

 `Log Normal`Les valeurs de la colonne continue forment un histogramme, dans lequel la courbe est allongée à l’extrémité supérieure et est inclinée vers l’extrémité inférieure.

 ![Histogramme avec distribution normale logarithmique](../media/log-normal-distribution.gif "Histogramme avec distribution normale logarithmique")

 `Uniform`Les valeurs de la colonne continue forment une courbe plate, dans laquelle toutes les valeurs sont également probables.

 ![Histogramme avec distribution uniforme](../media/uniform-distribution.gif "Histogramme avec distribution uniforme")

 Pour plus d’informations sur les algorithmes fournis par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md).

## <a name="see-also"></a>Voir aussi
 [Les types de contenu &#40;](content-types-data-mining.md) les structures d’exploration de données&#41;l’exploration [de données &#40;les méthodes de discrétisation d’exploration de données Analysis Services](mining-structures-analysis-services-data-mining.md)&#41;d' [exploration](discretization-methods-data-mining.md) de données &#40;les distributions&#41;les colonnes [DMX &#40;](/sql/dmx/distributions-dmx) [exploration](mining-structure-columns.md) de données


