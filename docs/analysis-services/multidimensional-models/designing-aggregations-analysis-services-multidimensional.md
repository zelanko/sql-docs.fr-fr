---
title: "Conception d’agrégations (Analysis Services - multidimensionnel) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 71e50fc874562cceddc91b454a246b29370cf7c7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="designing-aggregations-analysis-services---multidimensional"></a>Conception d'agrégations (Analysis Services - Multidimensionnel)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Les agrégations sont des résumés précalculés de données de cubes qui permettent [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de fournir des réponses rapides à des requêtes.  
  
 Pour définir des options de stockage et concevoir des agrégations pour une partition, utilisez l'Assistant Conception d'agrégation. Cet Assistant agit sur une seule partition d'un groupe de mesures à la fois, ce qui vous permet de sélectionner différentes options et configurations pour chaque partition. L'Assistant vous aide à configurer les options de stockage et à concevoir des agrégations pour une partition. Pour plus d'informations sur la configuration du stockage, consultez.  
  
 Sélectionnez une méthode pour contrôler le nombre d'agrégations que l'Assistant va concevoir, puis laissez celui-ci créer les agrégations.  
  
 L'objectif est de concevoir le nombre d'agrégations optimal. Non seulement ce nombre doit fournir un temps de réponse satisfaisant, mais il doit également empêcher la formation de partitions de trop grande taille. Un plus grand nombre d'agrégations permet des temps de réponse plus rapides, mais requiert aussi plus d'espace de stockage et peut mettre plus de temps à calculer. De plus, comme l'Assistant conçoit de plus en plus d'agrégations, les agrégations créées antérieurement produisent des gains de performance beaucoup plus importants par rapport à celles qui sont créées plus tard. La réduction des agrégations moins utiles augmente aussi les performances. Vous pouvez contrôler le nombre d'agrégations que l'Assistant conçoit à l'aide de l'une des méthodes suivantes :  
  
-   spécifiez une limite pour l'espace de stockage réservé aux agrégations ;  
  
-   spécifiez une limite pour les gains de performance ;  
  
-   arrêtez manuellement l'Assistant lorsque la courbe Performance/Taille affichée commence à présenter un niveau de gain de performance acceptable ;  
  
-   décidez de ne pas concevoir d'agrégations.  
  
 Pour configurer les options de stockage, l'Assistant doit être en mesure de se connecter à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur le serveur cible. L'Assistant renvoie un message d'erreur si [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] n'est pas en cours d'exécution sur le serveur cible ou si le processus de configuration du stockage ne parvient pas à se connecter au serveur cible.  
  
 L'étape finale de l'Assistant vous permet de lancer le traitement ou de le différer. Le traitement crée les agrégations conçues avec l'Assistant, tandis que l'ajournement du traitement enregistre les agrégations conçues en vue d'un traitement ultérieur, ce qui permet de poursuivre le travail de conception sans devoir effectuer le traitement. Selon la taille de la partition, le traitement peut durer très longtemps. Si vous le souhaitez, vous pouvez interrompre le traitement d'une partition.  
  
## <a name="see-also"></a>Voir aussi  
 [Agrégations et conceptions d'agrégation](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
