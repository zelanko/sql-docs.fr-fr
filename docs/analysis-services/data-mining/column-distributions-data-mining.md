---
title: Distributions de colonnes (exploration de données) | Documents Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d808627187029e971c8d07a9fc10ea93e8b8cb9e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="column-distributions-data-mining"></a>Distributions de colonnes (exploration de données)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez définir des distributions de colonnes dans une structure d’exploration de données pour affecter la manière dont les algorithmes traitent les données dans ces colonnes quand vous créez des modèles d’exploration de données. Pour certains algorithmes, il est judicieux de définir la distribution des colonnes continues avant de traiter le modèle, s'il est établi que les colonnes contiennent des distributions de valeurs communes. Si vous ne définissez pas de distributions, les modèles d'exploration de données obtenus risquent de générer des prévisions moins précises, car les algorithmes disposent dans ce cas d'une moins grande quantité d'informations pour interpréter les données.  
  
 Les algorithmes disponibles dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prennent en charge les types de distribution suivants :  
  
 **Normale**  
 Les valeurs pour la colonne continue forment un histogramme à distribution normale.  
  
 ![Histogramme avec distribution normale](../../analysis-services/data-mining/media/normal-distribution.gif "histogramme avec distribution normale")  
  
 **Log-normale**  
 Les valeurs pour la colonne continue forment un histogramme, dans lequel la courbe est allongée à son extrémité supérieure et est rétrécie vers son extrémité inférieure.  
  
 ![Histogramme avec distribution normale logarithmique](../../analysis-services/data-mining/media/log-normal-distribution.gif "histogramme avec distribution normale logarithmique")  
  
 **Uniforme**  
 Les valeurs de la colonne continue forment une courbe plate, dont toutes les valeurs sont sensiblement les mêmes.  
  
 ![Histogramme avec distribution uniforme](../../analysis-services/data-mining/media/uniform-distribution.gif "histogramme avec distribution uniforme")  
  
 Pour plus d’informations sur les algorithmes fournis par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu des Types de & #40 ; exploration de données & #41 ;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Les Structures d’exploration de données & #40 ; Analysis Services - Exploration de données & #41 ;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Méthodes de discrétisation & #40 ; exploration de données & #41 ;](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [Distributions & #40 ; DMX & #41 ;](../../dmx/distributions-dmx.md)   
 [Colonnes de Structure d’exploration de données](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
