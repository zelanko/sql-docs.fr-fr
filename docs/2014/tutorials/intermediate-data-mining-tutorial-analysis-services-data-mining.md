---
title: Didacticiel d’exploration de données intermédiaire (Analysis Services - Exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 404b31d5-27f4-4875-bd60-7b2b8613eb1b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4c244701d8a58765061ef3bde1f918c8be5a941d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63017179"
---
# <a name="intermediate-data-mining-tutorial-analysis-services---data-mining"></a>Didacticiel sur l'exploration de données intermédiaire (Analysis Services - Exploration de données)
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit un environnement intégré pour créer et utiliser des modèles d’exploration de données. Vous pouvez facilement créer une liaison avec des sources de données, créer et tester plusieurs modèles sur les mêmes données et déployer des modèles à utiliser dans des analyses prédictives.  
  
 Dans le didacticiel sur l'exploration de données de base, vous avez appris à utiliser [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer une solution d'exploration de données et vous avez créé trois modèles pour une campagne de publipostage ciblé afin d'analyser le comportement d'achat des clients et de cibler des acheteurs potentiels.  
  
 Ce didacticiel intermédiaire se base sur cette expérience et introduit plusieurs nouveaux scénarios, notamment des exigences professionnelles courantes telles que la prévision et l'analyse du panier d'achat. Vous apprendrez à créer un modèle de série chronologique, un modèle d'association et un modèle Sequence Clustering. Enfin, vous allez apprendre à utiliser le réseau neuronal pour explorer les corrélations des données et appliquer des modèles de régression logistique pour réaliser des prédictions.  
  
 Les leçons sont indépendantes et peuvent être accomplies séparément.  
  
 Pour mener à bien ces didacticiels, vous devez connaître les outils d'exploration de données et les visionneuses de modèles d'exploration de données présentées dans le didacticiel sur l'exploration de données de base.  
  
 Tous les scénarios utilisent la source de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], mais vous allez créer des vues de source de données différentes pour les différents scénarios. Vous pouvez suivre les leçons dans l'ordre qui vous convient dans la mesure où vous créez d'abord la source de données.  
  
## <a name="lesson-scenarios"></a>Scénarios des leçons  
 Suite au succès de votre campagne de publipostage ciblé, il vous a été demandé d'appliquer vos connaissances sur l'exploration de données afin de développer plusieurs nouveaux modèles à des fins de planification commerciale. Ces tâches sont les suivantes :  
  
-   **Prévisions :** Vous allez créer un *série chronologique* modèle, afin de prévoir les ventes de produits dans différentes régions du monde. Vous allez développer des modèles individuels pour chaque région et découvrez comment utiliser *la prédiction croisée*.  
  
-   **Analyse du panier :** Vous allez créer un *modèle d’association*, pour analyser des regroupements de produits achetés lors de visites sur le [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] site de commerce électronique. Grâce à ce modèle de panier d'achat, vous pouvez recommander des produits aux clients.  
  
-   **Analyse de séquence :** Vous générez un *modèle sequence clustering*, pour analyser l’ordre dans lequel les clients achètent des produits. Grâce à ce modèle, vous pouvez planifier des modifications dans la conception du site Web ou de nouvelles offres de produits.  
  
-   **Analyse des facteurs :** Vous utilisez un *réseau neuronal* modèle pour Explorer les causes possibles de mauvaise qualité de service dans les données de centre d’appels. Selon les informations tirées du modèle préliminaire, vous allez créer un *modèle de régression logistique* pour prédire les stratégies possibles pour améliorer l’expérience client.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel vous apprend à créer et utiliser différents types d'algorithmes d'exploration de données. Ce didacticiel contient les leçons suivantes :  
  
 [Leçon 1 : Création de la Solution d’exploration de données intermédiaire &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
 Dans cette leçon, vous allez créer un projet basé sur la base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], afin de prendre en charge plusieurs nouvelles vues des sources de données et de nombreux autres modèles d'exploration de données.  
  
 [Leçon 2 : Création d’un scénario de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
 Dans cette leçon, vous allez créer un modèle d'exploration de données qu'il sera possible d'utiliser dans un scénario de prévision. Vous allez également découvrir les modèles d'exploration de données créés avec l'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series).  
  
 Vous allez générer des modèles pour des régions individuelles, puis générer un modèle général utilisable à des fins de prédiction croisée.  
  
 [Leçon 3 : Génération d’un scénario de panier &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
 Dans cette leçon, vous allez ajouter une nouvelle vue de source de données et apprendre à utiliser des tables imbriquées et des clés. En fonction de ces données, vous allez créer un modèle d'exploration de données qu'il sera possible d'utiliser dans un scénario d'analyse de panier d'achat. Vous allez également découvrir les modèles d'exploration de données créés avec l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association.  
  
 [Leçon 4 : Création d’un scénario Sequence Clustering &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
 Dans cette leçon, vous allez créer un modèle d'exploration de données qu'il sera possible d'utiliser dans un scénario Sequence Clustering. Vous apprendrez également à explorer des modèles d'exploration de données créés avec l'algorithme MSC ([!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering).  
  
 [Leçon 5 : Création de réseau neuronal et modèles de régression logistique &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
 Dans cette leçon, vous allez créer plusieurs modèles d'exploration de données connexes, à l'aide des algorithmes MNN (Microsoft Neural Network) et MLR (Microsoft Logistic Regression). Vous apprendrez également à utiliser des vues de sources de données pour explorer les données sous-jacentes des modèles.  
  
## <a name="requirements"></a>Configuration requise  
 Assurez-vous que les éléments suivants sont installés sur votre système :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)])  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec la base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] .  
  
 Pour des raisons de sécurité, les bases de données exemples ne sont pas installées par défaut. Pour installer les bases de données officielles pour [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visitez le [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page et sélectionnez la version appropriée de la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l'exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Didacticiel DMX Bike Buyer](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [Tutoriel DMX Market Basket](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
  
