---
title: 'Leçon 5 : Génération de réseau neuronal et modèles de régression logistique (didacticiel d’exploration de données intermédiaire) | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- data mining [Analysis Services], tutorials
- neural networks
- tutorials [Data Mining]
- neural network model [Analysis Services]
ms.assetid: 42c3701a-1fd2-44ff-b7de-377345bbbd6b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1bbfd2344b46e015e26d2dba393aea689329949c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108819"
---
# <a name="lesson-5-building-neural-network-and-logistic-regression-models-intermediate-data-mining-tutorial"></a>Leçon 5 : Génération de modèles de réseau neuronal et de régression logistique (Didacticiel sur l'exploration de données intermédiaire)
  
  
 Le département des opérations de [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] est engagé dans un projet pour améliorer la satisfaction des clients avec leur centre d’appels. Il a embauché un fournisseur pour gérer le centre d'appels et signaler des mesures de l'efficacité du centre d'appels, et vous a demandé d'analyser certaines données préliminaires fournies par ce fournisseur. Il veut savoir si des découvertes intéressantes ont été faites. En particulier, il veut savoir si les données suggèrent des problèmes de personnel ou des façons d'améliorer la satisfaction de la clientèle.  
  
 Le jeu de données est peu volumineux et couvre uniquement une période de 30 jours du fonctionnement du centre d'appels. Les données suivent le nombre des opérateurs nouveaux et expérimentés dans chaque équipe, le nombre d'appels entrants, le nombre de commandes, ainsi que les problèmes qui doivent être résolus et la durée moyenne d'attente d'un client avant que quelqu'un ne réponde à un appel. Les données incluent également une niveau mesure de qualité de service basée sur *le taux d'abandon*qui est un indicateur de la frustration des clients.  
  
 Puisque vous n'avez pas d'attente préalable par rapport à ce que les données indiqueront, vous décidez d'utiliser un modèle de réseau neuronal pour explorer les corrélations possibles. Les modèles de réseau neuronal sont souvent utilisés pour l'exploration car ils peuvent analyser des relations complexes entre de nombreuses entrées et sorties.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Dans cette leçon, vous allez utiliser l'algorithme MNN (Microsoft Neural Network) pour générer un modèle que vous et l'équipe Opérations pouvez utiliser pour comprendre les tendances des données. Dans le cadre de cette leçon, vous allez essayer de répondre aux questions suivantes :  
  
-   Quels facteurs affectent la satisfaction des clients ?  
  
-   Qu'est-ce que le centre d'appels peut faire pour améliorer la qualité du service ?  
  
 Sur la base des résultats, vous générerez ensuite un modèle de régression logistique que vous pouvez utiliser pour des prédictions. Les prédictions seront utilisées par l'équipe d'exploitation comme une aide dans la planification du fonctionnement du centre d'appels.  
  
 Cette leçon contient les rubriques suivantes :  
  
-   [Ajout d’une données vue de Source pour les données de centre d’appels &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
-   [Création d’une Structure de réseau neuronal et un modèle &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Exploration du modèle de centre d’appels &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
-   [Ajout d’un modèle de régression logistique à la Structure de centre d’appels &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
-   [Création de prédictions pour les modèles de centre d’appels &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Ajout d’une données vue de Source pour les données de centre d’appels &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Toutes les leçons  
 [Leçon 1 : Création de la Solution d’exploration de données intermédiaire &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Leçon 2 : Création d’un scénario de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Leçon 3 : Génération d’un scénario de panier &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Leçon 4 : Création d’un scénario Sequence Clustering &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 Leçon 5 : Scénario de réseau neuronal et de régression logistique (didacticiel sur l’exploration de données intermédiaire)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Didacticiel d’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
