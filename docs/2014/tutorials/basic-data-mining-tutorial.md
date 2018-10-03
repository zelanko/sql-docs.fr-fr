---
title: Didacticiel d’exploration de données de base | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: db5b4fcded48a711fc1c8e8c8ffdebdd36562282
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150299"
---
# <a name="basic-data-mining-tutorial"></a>Didacticiel d’exploration de données de base
  Bienvenue dans le [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] didacticiel d’exploration de données de base de données. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournit un environnement intégré pour la création des modèles d’exploration de données et élaborer des prédictions. Dans ce didacticiel, vous allez réaliser un scénario pour une campagne de publipostage ciblé dans laquelle vous allez utiliser l'apprentissage automatique pour analyser et prédire le comportement d'achat des clients. Le didacticiel montre comment utiliser trois des algorithmes d'exploration de données les plus importants : clustering, arbres de décision et Naive Bayes. Vous allez également apprendre à analyser vos résultats à l’aide des visionneuses de modèle d’exploration de données et à créer des prédictions et des graphiques de précision en utilisant les outils d’exploration de données qui sont inclus dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La société fictive, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], est utilisée pour tous les exemples.  
  
 Lorsque vous êtes habitué à utiliser les outils d’exploration de données, nous recommandons de suivre également le [didacticiel d’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md). Les leçons illustrent l'utilisation des prévisions, de l'analyse du panier d'achat, des séries chronologiques, des modèles d'association, des tables imbriquées et du modèle Sequence Clustering.  
  
## <a name="tutorial-scenario"></a>Scénario du didacticiel  
 Dans ce didacticiel, vous êtes un employé de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] qui a été demandé d’en savoir plus sur les clients de la société en fonction des historiques d’achat et ensuite ces données d’historique pour effectuer des prédictions qui peuvent être utilisées dans marketing. La société n'a jamais effectué d'exploration de données auparavant. Vous devez donc créer spécifiquement une base de données pour l'exploration de données et définir plusieurs modèles d'exploration de données.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel apprend à créer et à utiliser différents types de méthodes d'apprentissage automatique. Vous allez également apprendre comment créer une copie d'un modèle d'exploration de données, puis appliquer un filtre aux données d'entrée pour obtenir des résultats différents. Ensuite, comparez les résultats des deux modèles à l'aide d'un graphique de courbes d'élévation. Pour finir, vous allez utiliser l'extraction pour extraire des données supplémentaires de la structure d'exploration de données sous-jacente.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Exploration de données inclut les éléments suivants fonctionnalités qui vous permettent de facilement développer et comparer plusieurs modèles prévisionnels et puis effectuez les actions sur les résultats :  
  
-   *Jeux de tests de données d'exclusion*: lorsque vous créez une structure d'exploration de données, vous pouvez à présent diviser les données de la structure d'exploration de données en jeux d'apprentissage et de test. Cela vous permet de tester les modèles sur des jeux de données semblables, puis de comparer la précision des modèles associés.  
  
-   *Filtres de modèles d'exploration de données*: vous pouvez à présent joindre des filtres à un modèle d'exploration de données et appliquer le filtre pendant l'apprentissage et le test. Cela vous permet de générer facilement des modèles associés sur des sous-ensembles de données.  
  
-   *Extraction dans des cas de structure et des colonnes de structure* : vous pouvez maintenant déplacer facilement des modèles généraux dans le modèle d'exploration de données vers des détails utilisables dans la source de données.  
  
 Ce didacticiel contient les leçons suivantes :  
  
 [Leçon 1 : Préparation de l’analyse des Services de base de données &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 Au cours de cette leçon, vous allez apprendre à créer une nouvelle base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], à ajouter une source de données et une vue de source de données, ainsi qu'à préparer la nouvelle base de données qu'il sera possible d'utiliser avec l'exploration de données.  
  
 [Leçon 2 : Création d’une Structure de publipostage ciblé &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 Au cours de cette leçon, vous allez apprendre à créer une structure de modèle d'exploration de données qu'il sera possible d'utiliser dans un scénario de publipostage ciblé.  
  
 [Leçon 3 : Ajout et traitement des modèles](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 Dans cette leçon, vous apprendrez à ajouter des modèles à une structure. Les modèles que vous créez sont générés à l'aide des algorithmes suivants :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes  
  
 [Leçon 4 : Exploration des modèles de publipostage ciblé &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 Dans cette leçon, vous apprendrez à explorer et interpréter les conclusions de chaque modèle à l'aide des visionneuses.  
  
 [Leçon 5 : Test des modèles &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 Dans cette leçon, vous faites une copie de l'un des modèles de publipostage ciblé, vous ajoutez un filtre de modèle d'exploration de données afin de restreindre les données d'apprentissage à un jeu particulier de clients, puis vous évaluez la viabilité du modèle.  
  
 [Leçon 6 : Création et utilisation de prédictions &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 Dans cette dernière leçon du didacticiel sur l'exploration de données de base, vous utilisez le modèle pour prédire quels clients sont les plus susceptibles d'acheter un vélo. Vous allez ensuite effectuer une extraction dans les cas sous-jacents pour obtenir des informations de contact.  
  
## <a name="requirements"></a>Spécifications  
 Assurez-vous que les éléments suivants sont installés sur votre système :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en mode multidimensionnel  
  
-   La base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].  
  
 Pour des raisons de sécurité, les bases de données exemples ne sont pas installées avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour installer les bases de données officielles pour [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visitez le [Microsoft SQL Sample Databases](http://go.microsoft.com/fwlink/?LinkId=88417) page et sélectionnez [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Lorsque vous suivez un didacticiel, vous pouvez trouver la navigation entre les étapes plus aisée en ajoutant les boutons **Rubrique suivante** et **Rubrique précédente** à la barre d'outils de la visionneuse de document.  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions d’exploration de données](../../2014/analysis-services/data-mining/data-mining-solutions.md)   
 [Tâches du modèle d’exploration de données et procédures](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Création et l’interrogation des modèles d’exploration de données avec DMX : didacticiels &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  
