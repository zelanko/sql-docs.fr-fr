---
title: Algorithmes d’exploration de données (Analysis Services-exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation algorithms [Analysis Services]
- clustering [Data Mining]
- learning algorithms
- data mining [Analysis Services], models
- algorithms [data mining]
- mining models [Analysis Services], algorithms
- inductive learning
- mining models [Analysis Services], creating
- data mining [Analysis Services], algorithms
- machine learning algorithms [Analysis Services]
ms.assetid: ed1fc83b-b98c-437e-bf53-4ff001b92d64
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 082241af377c8817c3adbc394a46f1ebc7d6a4e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66085141"
---
# <a name="data-mining-algorithms-analysis-services---data-mining"></a>Algorithmes d'exploration de données (Analysis Services - Exploration de données)
  Un *algorithme d’exploration de données* est un ensemble d’heuristiques et de calculs qui crée un modèle d’exploration de données à partir de données. Pour créer un modèle, l'algorithme analyse d'abord les données que vous fournissez, à la recherche de types spécifiques de modèles ou de tendances. L'algorithme utilise les résultats de cette analyse afin de définir les paramètres optimaux pour la création du modèle d'exploration de données. Ensuite, ces paramètres sont appliqués au jeu de données entier pour extraire des modèles utilisables et des statistiques détaillées.  
  
 Le modèle d'exploration de données qu'un algorithme crée à partir de vos données peut prendre des formes variées, dont les suivantes :  
  
-   Un ensemble de clusters qui décrivent la manière dont les cas sont liés dans un dataset.  
  
-   Un arbre de décision qui prédit les résultats et décrit comment les différents critères affectent ces résultats.  
  
-   Un modèle mathématique permettant de prévoir les ventes.  
  
-   Un ensemble de règles qui décrivent la manière dont les produits sont regroupés dans une transaction et les probabilités que les produits soient achetés ensemble.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit plusieurs algorithmes à utiliser dans vos solutions d’exploration de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] données. Ces algorithmes sont des implémentations de certaines méthodologies les plus populaires utilisées dans l'exploration de données. Tous les algorithmes d'exploration de données Microsoft peuvent être personnalisés et sont entièrement programmables à l'aide des interfaces API fournies, ou en utilisant des composants d'exploration de données dans SQL Server Integration Services.  
  
 Vous pouvez également utiliser des algorithmes tiers qui sont conformes à la spécification OLE DB pour l'exploration de données, ou développer des algorithmes personnalisés qui peuvent être inscrits en tant que services, puis utilisés dans l'infrastructure d'exploration de données SQL Server.  
  
## <a name="choosing-the-right-algorithm"></a>Choix de l'algorithme adéquat  
 Le choix du meilleur algorithme à utiliser pour une tâche analytique spécifique peut être un véritable défi. Vous pouvez utiliser des algorithmes différents pour effectuer la même tâche professionnelle, mais chaque algorithme produit un résultat différent et certains algorithmes peuvent produire plusieurs types de résultats. Par exemple, vous pouvez utiliser l’algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) pas seulement pour des prédictions, mais aussi comme manière de réduire le nombre de colonnes dans un dataset, car l’arbre de décision peut identifier les colonnes qui n’affectent pas le modèle d’exploration de données final.  
  
### <a name="choosing-an-algorithm-by-type"></a>Choix d'un algorithme par type  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] inclut les types d'algorithmes suivants :  
  
-   Les**algorithmes de classification** prévoient une ou plusieurs variables discrètes, en fonction des autres attributs du jeu de données.  
  
-   Les **algorithmes de régression** prévoient une ou plusieurs variables continues, telles que les bénéfices ou les pertes, en fonction d’autres attributs du jeu de données.  
  
-   Les**algorithmes de segmentation** répartissent les données dans des groupes (ou clusters) d’éléments possédant des propriétés similaires.  
  
-   Les**algorithmes d’association** recherchent des corrélations entre différents attributs d’un jeu de données. L'application la plus courante de ce genre d'algorithme concerne la création de règles d'association, utilisables dans une analyse de panier d'achat.  
  
-   Les **algorithmes d’analyse de séquence** synthétisent les séquences fréquentes ou les épisodes de données, tels qu’un workflow de chemin Web.  
  
 Toutefois, il n'y a aucune raison pour laquelle vous devriez être limité à un algorithme dans vos solutions. Les analystes expérimentés utilisent parfois un algorithme pour déterminer les entrées les plus efficaces (autrement dit, les variables), puis appliquent un algorithme différent pour prédire un résultat spécifique en fonction de ces données. L'exploration de données SQL Server vous permet de générer plusieurs modèles sur une structure d'exploration de données unique ; ainsi, avec une seule solution d'exploration de données, vous pouvez utiliser un algorithme de clustering, un modèle d'arbres de décision et un modèle Bayes naïve pour obtenir des vues différentes de vos données. Vous pouvez également utiliser plusieurs algorithmes dans une seule solution afin d'effectuer des tâches distinctes : par exemple, vous pouvez utiliser la régression pour obtenir des prévisions financières et un algorithme de réseau neuronal pour effectuer une analyse des facteurs qui influencent les ventes.  
  
### <a name="choosing-an-algorithm-by-task"></a>Choix d'un algorithme par tâche  
 Pour vous aider à sélectionner un algorithme en vue d'une utilisation avec une tâche spécifique, le tableau suivant fournit des suggestions pour les types de tâches pour lesquelles chaque algorithme est traditionnellement utilisé.  
  
|Exemples de tâches|Algorithmes Microsoft à utiliser|  
|-----------------------|---------------------------------|  
|**Prédiction d’un attribut discret**<br /><br /> Signaler les clients dans une liste de prospects comme intéressants ou inintéressants.<br /><br /> Calculer la probabilité qu'un serveur échoue dans les 6 mois suivants.<br /><br /> Classer les résultats des patients et explorer les facteurs connexes.|[Algorithme MDT (Microsoft Decision Trees)](microsoft-decision-trees-algorithm.md)<br /><br /> [Algorithme MNB (Microsoft Naive Bayes)](microsoft-naive-bayes-algorithm.md)<br /><br /> [Algorithme de clustering Microsoft](microsoft-clustering-algorithm.md)<br /><br /> [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)|  
|**Prédiction d’un attribut continu**<br /><br /> Prévoir les ventes de l'année suivante.<br /><br /> Prédire les visiteurs du site compte tendu des tendances historiques et saisonnières passées.<br /><br /> Générer un score de risque en fonction de données démographiques.|[Algorithme MDT (Microsoft Decision Trees)](microsoft-decision-trees-algorithm.md)<br /><br /> [Algorithme MTS (Microsoft Time Series)](microsoft-time-series-algorithm.md)<br /><br /> [Algorithme MLR (Microsoft Linear Regression)](microsoft-linear-regression-algorithm.md)|  
|**Prédiction d’une séquence**<br /><br /> Effectuer une analyse des parcours de visite du site Web d'une société.<br /><br /> Analyser les facteurs conduisant à la défaillance d'un serveur.<br /><br /> Capturer et analyser les séquences d'activités pendant les visites de patients, afin de formuler les meilleures pratiques autour des activités courantes.|[Algorithme MSC (Microsoft Sequence Clustering)](microsoft-sequence-clustering-algorithm.md)|  
|**Recherche de groupes d’éléments communs dans des transactions**<br /><br /> Utiliser l'analyse du panier d'achat pour déterminer le placement d'un produit.<br /><br /> Suggérer des produits supplémentaires à acheter par un client.<br /><br /> Analyser les données d'enquête de participants à un événement afin de rechercher les activités qui ont été mises en corrélation, pour planifier de futures activités.|[Algorithme Microsoft Association](microsoft-association-algorithm.md)<br /><br /> [Algorithme MDT (Microsoft Decision Trees)](microsoft-decision-trees-algorithm.md)|  
|**Recherche de groupes d’éléments similaires**<br /><br /> Créer des groupes de patients avec profils à risque basés sur des attributs tels que des données démographiques et des comportements.<br /><br /> Analyser les utilisateurs par consultation des habitudes d'achat.<br /><br /> Identifier les serveurs qui ont des caractéristiques d'utilisation similaires.|[Algorithme de clustering Microsoft](microsoft-clustering-algorithm.md)<br /><br /> [Algorithme MSC (Microsoft Sequence Clustering)](microsoft-sequence-clustering-algorithm.md)|  
  
## <a name="related-content"></a>Contenu associé  
 Le tableau suivant fournit des liens vers des ressources d'apprentissage pour chacun des algorithmes d'exploration de données fournis dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :  
  
|||  
|-|-|  
|**Description de l'algorithme de base**|Explique le rôle de l'algorithme et son fonctionnement, et présente les scénarios d'entreprise possibles dans lesquels l'algorithme peut être utile.|  
||[Algorithme Microsoft Association](microsoft-association-algorithm.md)<br /><br /> [Algorithme de clustering Microsoft](microsoft-clustering-algorithm.md)<br /><br /> [Algorithme MDT (Microsoft Decision Trees)](microsoft-decision-trees-algorithm.md)<br /><br /> [Algorithme MLR (Microsoft Linear Regression)](microsoft-linear-regression-algorithm.md)<br /><br /> [Algorithme MLR (Microsoft Logistic Regression)](microsoft-logistic-regression-algorithm.md)<br /><br /> [Algorithme MNB (Microsoft Naive Bayes)](microsoft-naive-bayes-algorithm.md)<br /><br /> [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)<br /><br /> [Algorithme MSC (Microsoft Sequence Clustering)](microsoft-sequence-clustering-algorithm.md)<br /><br /> [Algorithme MTS (Microsoft Time Series)](microsoft-time-series-algorithm.md)|  
|**Référence technique**|Fournit des informations techniques sur l'implémentation de l'algorithme, à l'aide de références universitaires selon les besoins. Dresse la liste des paramètres que vous pouvez configurer pour contrôler le comportement de l'algorithme et personnaliser les résultats dans le modèle. Décrit les spécifications de données et fournit des conseils en matière de performances, si possible.|  
||[Références techniques relatives à l’algorithme Microsoft Association](microsoft-association-algorithm-technical-reference.md)<br /><br /> [Références techniques relatives à l'algorithme de gestion de clusters Microsoft](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Références techniques relatives à l'algorithme MDT (Microsoft Decision Trees)](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Références techniques relatives à l'algorithme MLR (Microsoft Linear Regression)](microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [Références techniques relatives à l’algorithme MLR (Microsoft Logistic Regression)](microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Références techniques relatives à l'algorithme MNB (Microsoft Naive Bayes)](microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [Références techniques relatives à l'algorithme MSC (Microsoft Sequence Clustering)](microsoft-sequence-clustering-algorithm-technical-reference.md)<br /><br /> [Informations techniques de référence sur l’algorithme MTS (Microsoft Time Series)](microsoft-time-series-algorithm-technical-reference.md)|  
|**Contenu de modèle**|Explique comment les informations sont structurées dans chaque type de modèle d'exploration de données et indique comment interpréter les informations stockées dans chacun des nœuds.|  
||[Contenu du modèle d’exploration de données pour les modèles d’association &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md)<br /><br /> [Contenu du modèle d’exploration de données pour les modèles de clustering &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md)<br /><br /> [Contenu du modèle d’exploration de données pour les modèles d’arbre de décision &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)<br /><br /> [Contenu du modèle d’exploration de données pour les modèles de régression linéaire &#40;Analysis Services – Exploration de données&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)<br /><br /> [Contenu du modèle d’exploration de données pour les modèles de régression logistique &#40;Analysis Services – Exploration de données&#41;](mining-model-content-for-logistic-regression-models.md)<br /><br /> [Contenu du modèle d’exploration de données pour les modèles Naive Bayes &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)<br /><br /> [Contenu du modèle d’exploration de données pour les modèles de réseau neuronal &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)<br /><br /> [Contenu du modèle d’exploration de données pour les modèles Sequence Clustering &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-sequence-clustering-models.md)<br /><br /> [Contenu du modèle d’exploration de données pour les modèles de séries chronologiques &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md)|  
|**Requêtes d’exploration de données**|Fournit plusieurs requêtes que vous pouvez utiliser avec chaque type de modèle. Les exemples incluent des requêtes de contenu qui vous permettent d'en savoir plus sur les schémas du modèle, ainsi que des requêtes de prédiction pour vous aider à établir des prédictions en fonction de ces schémas.|  
||[Exemples de requêtes de modèle d'association](association-model-query-examples.md)<br /><br /> [Exemples de requêtes de modèle de clustering](clustering-model-query-examples.md)<br /><br /> [Exemples de requêtes de modèle d’arbre de décision](decision-trees-model-query-examples.md)<br /><br /> [Exemples de requête de modèle de régression linéaire](linear-regression-model-query-examples.md)<br /><br /> [Exemples de requêtes de modèle de régression logistique](logistic-regression-model-query-examples.md)<br /><br /> [Exemples de requêtes de modèle Naive Bayes](naive-bayes-model-query-examples.md)<br /><br /> [Exemples de requêtes de modèle de réseau neuronal](neural-network-model-query-examples.md)<br /><br /> [Sequence Clustering Model Query Examples](sequence-clustering-model-query-examples.md)<br /><br /> [Time Series Model Query Examples](time-series-model-query-examples.md)|  
  
## <a name="related-tasks"></a>Tâches associées  
  
|**Rubrique**|**Description**|  
|---------------|---------------------|  
|Déterminer l'algorithme utilisé par un modèle d'exploration de données|[Interroger les paramètres utilisés pour créer un modèle d'exploration de données](query-the-parameters-used-to-create-a-mining-model.md)|  
|Créer un algorithme de plug-in personnalisé|[Algorithmes de plug-in](plugin-algorithms.md)|  
|Explorer un modèle à l'aide d'une visionneuse d'algorithme|[Visionneuses de modèle d’exploration de données](data-mining-model-viewers.md)|  
|Afficher le contenu d'un modèle à l'aide d'un format tabulaire générique|[Explorer un modèle à l'aide de la visionneuse de l'arborescence de contenu générique Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)|  
|En savoir plus sur la configuration de vos données et l'utilisation d'algorithmes pour créer des modèles|[Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)<br /><br /> [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-models-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d'exploration de données](data-mining-tools.md)  
  
  
