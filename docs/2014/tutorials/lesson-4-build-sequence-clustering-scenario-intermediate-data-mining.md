---
title: 'Leçon 4 : génération d’un scénario Sequence Clustering (didacticiel sur l’exploration de données intermédiaire) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d34125b7b750daa1da25c9e8788172b5d9ca2c35
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62710601"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>Leçon 4 : Génération d'un scénario Sequence Clustering (Didacticiel sur l'exploration de données intermédiaire)
  Le service marketing de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] souhaite comprendre comment les clients se déplacent sur le site web [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] . Cette société suppose que l'ordre dans lequel les clients ajoutent des produits dans leurs paniers obéit à un modèle. Il souhaite en effet analyser l'ordre des séquences d'achat afin de découvrir comment les clients ajoutent des articles associés à leurs paniers. Elle peut utiliser ces informations pour rationaliser le flux du site Web afin qu'il conduise les clients à acheter des produits supplémentaires.  
  
 Une fois que vous aurez terminé les tâches de cette leçon, vous aurez créé un modèle d'exploration de données qui utiliser l'algorithme MSC ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering) pour prévoir le prochain article que les clients ajouteront à leurs paniers d'achats. Vous allez expérimenter les deux versions du modèle : une qui analyse uniquement l'ordre des produits dans le panier et une qui contient d'autres caractéristiques démographiques des clients à des fins de regroupement. Enfin, vous allez utiliser les modèles pour créer des prédictions que vous pourrez utiliser pour recommander des produits aux clients.  
  
 Pour effectuer les tâches de la leçon, vous allez utiliser la structure d’exploration de données Market panier que vous avez créée au cours de la [leçon 3 : génération d’un scénario de panier de marché &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md). Cette leçon contient les tâches suivantes :  
  
-   [Création d’une structure de modèle d’exploration de données Sequence Clustering &#40;Didacticiel intermédiaire sur l’exploration de données&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [Traitement du modèle Sequence Clustering](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [Exploration du modèle Sequence Clustering &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Création d’un modèle de clustering séquencé associé &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Création de prédictions sur un modèle Sequence Clustering &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une structure de modèle d’exploration de données Sequence Clustering &#40;Didacticiel intermédiaire sur l’exploration de données&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Toutes les leçons  
 [Leçon 1 : création de la solution intermédiaire d’exploration de données &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Leçon 2 : génération d’un scénario de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Leçon 3 : Génération d’un scénario de panier d’achat &#40;Didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 Leçon 4 : Scénario Sequence Clustering (didacticiel sur l’exploration de données intermédiaire)  
  
 [Leçon 5 : Génération de modèles de réseau neuronal et de régression logistique &#40;Didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Didacticiel sur l’exploration de données intermédiaire &#40;Analysis Services d’exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
