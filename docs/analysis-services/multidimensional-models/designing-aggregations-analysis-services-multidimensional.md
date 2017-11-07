---
title: "Conception d’agrégations (Analysis Services - multidimensionnel) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7fef45841f28152dfed66aa95f670e8a21a3d903
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="designing-aggregations-analysis-services---multidimensional"></a>Conception d'agrégations (Analysis Services - Multidimensionnel)
  Les agrégations sont des résumés précalculés de données de cubes qui permettent à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de fournir des réponses rapides à des requêtes.  
  
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
  
  

