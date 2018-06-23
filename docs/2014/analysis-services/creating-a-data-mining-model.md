---
title: Création d’un modèle d’exploration de données | Documents Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining models, creating
- forecasting [data mining]
- mining models, creating
- clustering [data mining]
- association [data mining]
- data modeling [data mining]
- estimation
- classification [data mining]
ms.assetid: 804b7db3-1f6a-4f73-a81d-bbe02520d7c6
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3c08737f07db68bd0e598844325d82172c3b1b44
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142589"
---
# <a name="creating-a-data-mining-model"></a>Création d'un modèle d'exploration de données
  Modélisation des données est l’étape d’exploration de données où vous générez des modèles et les tendances en appliquant *algorithmes* aux données. Ultérieurement, utilisez ces séquences pour l'analyse, ou pour faire des prédictions.  
  
 Les compléments d'exploration de données pour Office prennent en charge l'exploration de données au moyen d'Assistants qui facilitent la création de modèles. Les Assistants analysent les données, identifient des corrélations, calculent l'importance statistique de toutes les variables et sélectionnent automatiquement le meilleur modèle.  
  
 Bien que cette fonctionnalité soit en tous points aussi puissant que les données fournies par des outils d’exploration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], la combinaison des Assistants et l’interface familière d’Excel permet de facilement créer, modifier et utiliser l’exploration de données.  
  
## <a name="advanced-data-mining"></a>Avancés (Exploration de données)  
 Les Assistants avancés vous permettent de créer de nouveaux modèles d’exploration de données, en fonction des données stockées dans Excel, à l’aide d’un des algorithmes d’exploration de données de données dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
### <a name="create-mining-structure"></a>Créer une Structure d’exploration de données  
 L'Assistant Création d'une structure d'exploration de données vous aide à générer une nouvelle structure d'exploration de données, que vous pouvez utiliser comme base pour plusieurs modèles d'exploration de données. L'Assistant vous permet de mettre de côté une partie des données à utiliser comme un jeu de test, afin que vous puissiez évaluer tous les modèles qui utilisent les mêmes données selon un standard de test cohérent.  
  
 [Créer une Structure d’exploration de données &#40;compléments d’exploration de données SQL Server&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a>Ajouter un modèle à une structure  
 L'Assistant Ajout d'un modèle à une structure vous permet de choisir une structure d'exploration de données existante et de créer un nouveau modèle d'exploration de données pour cette structure. Vous pouvez ajouter plusieurs modèles d'exploration de données à une structure, en modifiant les paramètres ou choisissant des algorithmes d'exploration de données différents et personnaliser la sortie.  
  
 [Ajouter un modèle à Structure &#40;les données des compléments d’exploration de données pour Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a>Analyser les facteurs d'influence clés (Analyse)  
 Vous choisissez une colonne ou une valeur de sortie d'intérêt, puis l'algorithme analyse les données d'entrée pour identifier les facteurs qui ont le plus d'influence sur la cible. Éventuellement, créez un rapport qui compare deux valeurs quelconques, afin que vous puissiez voir comment les facteurs d'influence changent.  
  
 Le **analyser les facteurs d’influence clés** outil utilise l’algorithme Microsoft Naïve Bayes.  
  
 [Analyser les facteurs d’influence clés &#40;outils d’analyse de Table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a>Association (Exploration de données)  
 Le **associer** Assistant crée un modèle d’association qui détecte des associations entre des éléments qui apparaissent dans plusieurs transactions : par exemple, dans l’analyse de panier d’achat.  
  
 [Assistant association &#40;Client d’exploration de données pour Excel&#41;](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a>Classification (Exploration de données)  
 Le **classifier** Assistant crée un modèle de classification qui analyse les facteurs qui ont contribué au résultat cible. Utilisez plusieurs algorithmes avec cet Assistant, y compris d'arbre de décision, Naive Bayes, et de réseaux neuronaux.  
  
 [Assistant classification &#40;les données des compléments d’exploration de données pour Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a>Cluster (Exploration de données)  
 Le **Cluster** Assistant crée un modèle de clustering qui détecte les groupes de lignes qui partagent des caractéristiques similaires. Clustering (parfois appelé *segmentation*) est une technique d’apprentissage qui est très utile lorsque vous tentez de comprendre les séquences et des regroupements dans les nouvelles données.  
  
 L'algorithme de gestion de clusters Microsoft prend en charge le clustering K-means et EM (Expectation maximization)  
  
 [Assistant cluster &#40;les données des compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md).  
  
## <a name="detect-categories-analyze"></a>Détecter les catégories (Analyse)  
 Le **détecter les catégories** outil vous permet d’ajouter n’importe quel jeu de données et appliquer le clustering pour rechercher des regroupements de données. Il est utile pour rechercher des similitudes et pour créer des groupes à analyser.  
  
 Le **détecter les catégories** outil utilise l’algorithme Microsoft Clustering.  
  
 [Détecter les catégories &#40;outils d’analyse de Table pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a>Estimation (Exploration de données)  
 L'Assistant Estimation crée un modèle d'estimation qui extrait les séquences de données remarquables et les utilise pour prédire des valeurs continues de type numérique, date ou heure. Il utilise l'algorithme MDT ([!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees).  
  
 [Assistant estimation &#40;les données des compléments d’exploration de données pour Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a>Remplir à partir de l'exemple (Analyse)  
 Le **remplir à partir de l’exemple** outil vous aide à imputer les valeurs manquantes. Vous fournissez des exemples de valeurs manquantes, et l'outil crée des modèles basés sur toutes les données de la table, puis recommande de nouvelles valeurs en fonction des séquences dans les données.  
  
 Le **remplir à partir de l’exemple** outil utilise l’algorithme Microsoft Logistic Regression.  
  
 [Remplir à partir de l’exemple &#40;outils d’analyse de Table pour Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a>Prévision (Analyse)  
 Le **prévision** outil prend des données qui changent au fil du temps, puis prédit des valeurs futures.  
  
 Le **prévision** outil utilise l’algorithme MTS.  
  
 [Prévision &#40;outils d’analyse de Table pour Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a>Prévision (Exploration de données)  
 Le **prévision** Assistant crée un modèle de prévision qui détecte des séquences dans une série de cellules, puis prédit des valeurs supplémentaires.  
  
 [Assistant prévisions &#40;les données des compléments d’exploration de données pour Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a>Mettre en surbrillance les exceptions (Analyse)  
 Le **mettre en surbrillance les Exceptions** outil analyse les séquences dans une table de données et recherche les lignes et les valeurs qui ne correspondent pas au modèle. Vous pouvez les examiner et les corriger, puis réexécuter le modèle, ou marquer les valeurs avec un indicateur pour une action ultérieure.  
  
 Le **mettre en surbrillance les Exceptions** outil utilise l’algorithme Microsoft Clustering.  
  
 [Mettez en surbrillance les Exceptions &#40;outils d’analyse de Table pour Excel&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a>Calcul de prédiction (Analyse)  
 Cet outil crée un modèle d'analyse des facteurs qui mènent aux résultats, puis prédit un résultat pour toute nouvelle entrée, en fonction de critères dérivés de ces modèles. Il génère également une feuille de calcul interactive pour la prise de décision qui vous permet d'établir le score de nouvelles entrées. Vous pouvez également créer une version imprimée de la feuille de calcul que vous pouvez utiliser hors connexion pour l'établissement du score.  
  
 Le **calcul de prédiction** outil utilise l’algorithme Microsoft Logistic Regression.  
  
 [Calcul de prédiction &#40;outils d’analyse de Table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a>Scénario : valeur cible (Analyse)  
 Dans le **valeur cible** outil, vous spécifiez une valeur cible et l’outil identifie les facteurs sous-jacents qui doivent changer pour atteindre cette cible. Par exemple, si vous savez que vous devez augmenter la satisfaction des appels de 20 %, demandez au modèle de prédire les facteurs qui doivent changer pour obtenir cet objectif.  
  
 Le **valeur cible** outil utilise l’algorithme Microsoft Logistic Regression.  
  
 détails  
  
 [Scénario valeur cible &#40;outils d’analyse de Table pour Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a>Scénario : Scénario (Analyse)  
 Le **analyse de scénarios** outil complète la **valeur cible** outil. Avec cet outil, vous entrez la valeur que vous souhaitez modifier, puis le modèle prédit si cette modification est suffisante pour obtenir les résultats souhaités. Par exemple, demandez au modèle de déterminer si l'ajout d'un opérateur augmenterait la satisfaction des clients d'un point.  
  
 Le **simulation** outil utilise l’algorithme Microsoft Logistic Regression.  
  
 [Scénario de simulation &#40;outils d’analyse de Table pour Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a>Analyse du panier d'achat (Analyse)  
 Le **analyse du panier** outil crée des groupes de produits qui sont souvent achetés ensemble pour identifier des modèles qui peuvent être utilisés dans la vente croisée ou la vente incitative. Il génère également des rapports basés sur le prix et le coût de paquets de produits connexes, pour aider à la prise de décision.  
  
 Utilisez également cet outil pour les événements qui se produisent fréquemment ensemble, les facteurs conduisant à un diagnostic, ou tout autre ensemble de causes et résultats potentiels.  
  
 Le **analyse du panier** outil utilise l’algorithme Microsoft Association.  
  
 [Analyse du panier &#40;outils d’analyse de Table pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration et nettoyage des données](exploring-and-cleaning-data.md)   
 [Validation des modèles et à l’aide de modèles pour la prédiction &#40;les données des compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les données des compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  