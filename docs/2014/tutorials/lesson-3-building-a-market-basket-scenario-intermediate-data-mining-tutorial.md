---
title: 'Leçon 3 : Génération d’un scénario de panier d’achat (didacticiel d’exploration de données intermédiaire) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c2f1c5a8ae897284f07c3fd6c65d9735099a41fa
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041400"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a>Leçon 3 : Génération d’un scénario de panier d’achat (didacticiel d’exploration de données intermédiaire)
  Le service marketing de la société [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] souhaite améliorer son site Web pour promouvoir la vente croisée. Dans le cadre de la mise à jour du site, il veut pouvoir prédire les produits que les clients sont susceptibles d'acheter en fonction des produits déjà présents dans leurs paniers d'achat en ligne. Le service marketing souhaite également mieux comprendre le comportement d'achat des clients, afin de pouvoir concevoir le site Web de façon à ce que les articles susceptibles d'être achetés ensemble apparaissent ensemble. Il a appris que l'exploration de données est particulièrement utile pour ce type d' *analyse du panier d'achat* et vous demandé de développer un modèle d'exploration de données.  
  
 Une fois les tâches de cette leçon terminées, vous disposerez d'un modèle d'exploration de données qui présentera les articles par groupe à partir de l'historique des transactions des clients. En outre, vous pourrez utiliser le modèle d'exploration de données pour prédire les articles supplémentaires qu'un client sera susceptible d'acheter.  
  
 Pour effectuer les tâches de cette leçon, vous allez utiliser la source de données et de la solution que vous avez créé dans la première leçon de la [didacticiel d’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md). Vous modifierez cette solution en ajoutant une vue de source de données qui contient des tables relatives au client, notamment une table imbriquée des achats des clients.  Vous générerez ensuite un modèle d'exploration de données qui utilise l'algorithme MAR (Microsoft Association Rules), adapté aux scénarios d'analyse de panier.  
  
 Cette leçon contient les rubriques suivantes :  
  
-   [Ajout d’un Data Source View avec des Tables imbriquées &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [Création d’un modèle et la Structure Market Basket &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Modification et traitement du modèle de panier &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [Exploration des modèles de panier &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [Filtrage d’une Table imbriquée dans un modèle d’exploration de données &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [Prédiction d’Associations &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Ajout d’un Data Source View avec des Tables imbriquées &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Toutes les leçons  
 [Leçon 1 : Création de la Solution d’exploration de données intermédiaire &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Leçon 2 : Création d’un scénario de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 Leçon 3 : Scénario de panier (didacticiel d’exploration de données intermédiaire)  
  
 [Leçon 4 : Création d’un scénario Sequence Clustering &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Leçon 5 : Création de réseau neuronal et modèles de régression logistique &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l'exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Leçon 2 : Création d’un scénario de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)   
 [Leçon 4 : Création d’un scénario Sequence Clustering &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
