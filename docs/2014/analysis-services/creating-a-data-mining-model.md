---
title: Création d’un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a8893960b5177563ccf98dbd21cb528ce399ea3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086725"
---
# <a name="creating-a-data-mining-model"></a>Création d'un modèle d'exploration de données
  La modélisation des données est l’étape d’exploration de données dans laquelle vous créez des modèles et des tendances en appliquant des *algorithmes* aux données. Ultérieurement, utilisez ces séquences pour l'analyse, ou pour faire des prédictions.  
  
 Les compléments d'exploration de données pour Office prennent en charge l'exploration de données au moyen d'Assistants qui facilitent la création de modèles. Les Assistants analysent les données, identifient des corrélations, calculent l'importance statistique de toutes les variables et sélectionnent automatiquement le meilleur modèle.  
  
 Bien que cette fonctionnalité soit tout aussi puissante que les outils d’exploration de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournis [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]par et, la combinaison d’assistants et de l’interface Excel familière facilite la création, la modification et l’utilisation de l’exploration de données.  
  
## <a name="advanced-data-mining"></a>Avancés (Exploration de données)  
 Les assistants avancés vous permettent de créer des modèles d’exploration de données basés sur des données stockées dans Excel, à l’aide de l’un des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]algorithmes d’exploration de données de.  
  
### <a name="create-mining-structure"></a>Créer une structure d’exploration de données  
 L'Assistant Création d'une structure d'exploration de données vous aide à générer une nouvelle structure d'exploration de données, que vous pouvez utiliser comme base pour plusieurs modèles d'exploration de données. L'Assistant vous permet de mettre de côté une partie des données à utiliser comme un jeu de test, afin que vous puissiez évaluer tous les modèles qui utilisent les mêmes données selon un standard de test cohérent.  
  
 [Créer des &#40;de structure d’exploration de données SQL Server des compléments d’exploration de données&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a>Ajouter un modèle à une structure  
 L'Assistant Ajout d'un modèle à une structure vous permet de choisir une structure d'exploration de données existante et de créer un nouveau modèle d'exploration de données pour cette structure. Vous pouvez ajouter plusieurs modèles d'exploration de données à une structure, en modifiant les paramètres ou choisissant des algorithmes d'exploration de données différents et personnaliser la sortie.  
  
 [Ajouter un modèle à la structure &#40;compléments d’exploration de données pour Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a>Analyser les facteurs d'influence clés (Analyse)  
 Vous choisissez une colonne ou une valeur de sortie d'intérêt, puis l'algorithme analyse les données d'entrée pour identifier les facteurs qui ont le plus d'influence sur la cible. Éventuellement, créez un rapport qui compare deux valeurs quelconques, afin que vous puissiez voir comment les facteurs d'influence changent.  
  
 L’outil **analyser les influences clés** utilise l’algorithme Microsoft Naïve Bayes.  
  
 [Analyser les influenceurs clés &#40;les outils d’analyse de table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a>Association (Exploration de données)  
 L’Assistant **Association** crée un modèle d’association qui détecte des associations entre les éléments qui apparaissent dans plusieurs transactions : par exemple, dans l’analyse du panier d’marché.  
  
 [Assistant Association &#40;client d’exploration de données pour Excel&#41;](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a>Classification (Exploration de données)  
 L’Assistant **classification** crée un modèle de classification qui analyse les facteurs qui ont contribué à un résultat cible. Utilisez plusieurs algorithmes avec cet Assistant, y compris d'arbre de décision, Naive Bayes, et de réseaux neuronaux.  
  
 [Assistant classification &#40;compléments d’exploration de données pour Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a>Cluster (Exploration de données)  
 L’Assistant **cluster** crée un modèle de clustering qui détecte les groupes de lignes qui partagent des caractéristiques similaires. Le clustering (parfois appelé *segmentation*) est une technique d’apprentissage non supervisée qui est très utile lorsque vous tentez de comprendre des modèles et des regroupements dans de nouvelles données.  
  
 L'algorithme de gestion de clusters Microsoft prend en charge le clustering K-means et EM (Expectation maximization)  
  
 [Assistant de Cluster &#40;des compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md).  
  
## <a name="detect-categories-analyze"></a>Détecter les catégories (Analyse)  
 L’outil **détecter les catégories** vous permet d’ajouter n’importe quel jeu de données et d’appliquer le clustering pour rechercher des regroupements de données. Il est utile pour rechercher des similarités et pour créer des groupes à analyser plus en détail.  
  
 L’outil **détecter les catégories** utilise l’algorithme de clustering Microsoft.  
  
 [Détecter les catégories &#40;les outils d’analyse de table pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a>Estimation (Exploration de données)  
 L'Assistant Estimation crée un modèle d'estimation qui extrait les séquences de données remarquables et les utilise pour prédire des valeurs continues de type numérique, date ou heure. Il utilise l'algorithme MDT ([!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees).  
  
 [Assistant estimation &#40;des compléments d’exploration de données pour Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a>Remplir à partir de l'exemple (Analyse)  
 L’outil **remplir à partir de l’exemple** vous aide à imputer les valeurs manquantes. Vous fournissez des exemples de valeurs manquantes, et l'outil crée des modèles basés sur toutes les données de la table, puis recommande de nouvelles valeurs en fonction des séquences dans les données.  
  
 L’outil **remplir à partir de l’exemple** utilise l’algorithme de régression logistique de Microsoft.  
  
 [Remplir à partir de l’exemple &#40;les outils d’analyse de table pour Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a>Prévision (Analyse)  
 L’outil **prévision** prend des données qui changent au fil du temps et prédit des valeurs futures.  
  
 L’outil **prévision** utilise l’algorithme MTS (Microsoft Time Series).  
  
 [Outils d’analyse de table &#40;de prévision pour Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a>Prévision (Exploration de données)  
 L’Assistant **prévision** crée un modèle de prévision qui détecte les séquences dans une série de cellules, puis prédit des valeurs supplémentaires.  
  
 [Assistant Prévision &#40;des compléments d’exploration de données pour Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a>Mettre en surbrillance les exceptions (Analyse)  
 L’outil **mettre en surbrillance les exceptions** analyse les séquences dans une table de données et recherche les lignes et les valeurs qui ne correspondent pas au modèle. Vous pouvez les examiner et les corriger, puis réexécuter le modèle, ou marquer les valeurs avec un indicateur pour une action ultérieure.  
  
 L’outil **mettre en surbrillance les exceptions** utilise l’algorithme de clustering Microsoft.  
  
 [Mettre en surbrillance les exceptions &#40;les outils d’analyse de table pour Excel&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a>Calcul de prédiction (Analyse)  
 Cet outil crée un modèle d'analyse des facteurs qui mènent aux résultats, puis prédit un résultat pour toute nouvelle entrée, en fonction de critères dérivés de ces modèles. Il génère également une feuille de calcul interactive pour la prise de décision qui vous permet d'établir le score de nouvelles entrées. Vous pouvez également créer une version imprimée de la feuille de calcul que vous pouvez utiliser hors connexion pour l'établissement du score.  
  
 L’outil **calcul de prédiction** utilise l’algorithme de régression logistique de Microsoft.  
  
 [Calcul de prédiction &#40;les outils d’analyse de table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a>Scénario : valeur cible (Analyse)  
 Dans l’outil **recherche objectif** , vous spécifiez une valeur cible et l’outil identifie les facteurs sous-jacents qui doivent changer pour répondre à cette cible. Par exemple, si vous savez que vous devez augmenter la satisfaction des appels de 20 %, demandez au modèle de prédire les facteurs qui doivent changer pour obtenir cet objectif.  
  
 L’outil de **recherche d’objectif** utilise l’algorithme de régression logistique de Microsoft.  
  
 details  
  
 [Scénario de la recherche de l’objectif &#40;outils d’analyse de table pour Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a>Scénario : Scénario (Analyse)  
 L’outil d' **analyse de scénarios** complète l’outil de **recherche d’objectif** . Avec cet outil, vous entrez la valeur que vous souhaitez modifier, puis le modèle prédit si cette modification est suffisante pour obtenir les résultats souhaités. Par exemple, demandez au modèle de déterminer si l'ajout d'un opérateur augmenterait la satisfaction des clients d'un point.  
  
 L’outil **simulation** utilise l’algorithme de régression logistique de Microsoft.  
  
 [Scénario de simulation &#40;les outils d’analyse de table pour Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a>Analyse du panier d'achat (Analyse)  
 L’outil d' **analyse du panier d’achat** crée des groupes de produits qui sont fréquemment achetés ensemble, afin d’identifier les modèles qui peuvent être utilisés dans la vente croisée ou la vente incitative. Il génère également des rapports basés sur le prix et le coût de paquets de produits connexes, pour aider à la prise de décision.  
  
 Utilisez également cet outil pour les événements qui se produisent fréquemment ensemble, les facteurs conduisant à un diagnostic, ou tout autre ensemble de causes et résultats potentiels.  
  
 L’outil d' **analyse du panier d’achat** utilise l’algorithme Microsoft Association.  
  
 [Analyse du panier d’achat &#40;table outils pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration et nettoyage des données](exploring-and-cleaning-data.md)   
 [Validation des modèles et utilisation de modèles pour la prédiction &#40;compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
