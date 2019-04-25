---
title: Paramètres d’algorithme (SQL Server Data Mining Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MAXIMUM_STATES
- FORCED_REGRESSOR
- PERIODICITY_HINT
- HOLDOUT_SEED
- MAXIMUM_ITEMSET_SIZE
- HIDDEN_NODE_RATIO
- CLUSTERING_METHOD
- FORECAST_METHOD
- STOPPING_TOLERANCE
- MISSING_VALUE_SUBSTITUTION
- MINIMUM_IMPORTANCE
- HISTORIC_MODEL_COUNT
- SPLIT_METHOD
- MAXIMUM_OUTPUT_ATTRIBUTES
- HOLDOUT_PERCENTAGE
- MINIMUM_PROBABILITY
- SAMPLE_SIZE
- HISTORICAL_MODEL_GAP
- CLUSTER_SEED
- SCORE_METHOD
- INSTABILITY_SENSITIVITY
- AUTO_DETECT_PERIODICITY
- MAXIMUM_SEQUENCE_STATES
- MINIMUM_DEPENDENCY_PROBABILITY
- MINIMUM_SUPPORT
- MAXIMUM_SUPPORT
- MINIMUM_ITEMSET_SIZE
- PREDICTION_SMOOTHING
- algorithm parameters
- MAXIMUM_SERIES_VALUE
- MODELLING_CARDINALITY
- MAXIMUM_INPUT_ATTRIBUTES
- MINIMUM_SERIES_VALUE
- MAXIMUM_ITEMSET_COUNT
- CLUSTER_COUNT
- COMPLEXITY_PENALTY
ms.assetid: fcdc3f85-813d-4279-90b0-16e26edd008d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 555a92bf4131ee821fa70065cf02cada87f671ab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62635500"
---
# <a name="algorithm-parameters-sql-server-data-mining-add-ins"></a>Paramètres d'algorithme (Compléments d'exploration de données SQL Server)
  Lorsque vous effectuez l'exploration de données à l'aide des outils d'analyse de table pour Excel, vous n'avez pas besoin de configurer l'algorithme ou les paramètres d'exploration de données ; chaque outil analyse vos données et sélectionne automatiquement les paramètres optimums. Toutefois, si vous souhaitez modifier le modèle ou créer un modèle d'exploration de données de toutes pièces, le client d'exploration de données pour Excel vous propose plusieurs options de personnalisation.  
  
-   Créer un modèle d’exploration de données manuellement, en cliquant sur **avancé** , puis en cliquant sur **ajouter le modèle à la Structure**.  
  
-   Utiliser les Assistants de modélisation dans le Client d’exploration de données, puis cliquez sur **paramètres** pour contrôler le comportement de la [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes d’exploration de données.  
  
-   Cliquez sur **requête** pour ouvrir l’Assistant modèle de requête, puis cliquez sur **avancé** pour ouvrir le **éditeur de requêtes d’avancé d’exploration de données**. Dans cet éditeur, vous pouvez générer des modèles en utilisant les modèles DMX.  
  
 En outre, vous pouvez modifier le comportement des modèles d'exploration déjà créés, ou vous pouvez filtrer les résultats en définissant des paramètres dans la visionneuse de modèle d'exploration de données.  
  
## <a name="list-of-algorithm-parameters"></a>Liste des paramètres d'algorithme  
 Tous les algorithmes [!INCLUDE[msCoName](../includes/msconame-md.md)] peuvent être personnalisés en définissant des paramètres. Cette rubrique n'a pas pour objectif de fournir une explication complète des effets de la modification des paramètres, dans la mesure où les meilleurs paramètres dépendent de la composition de vos données.  
  
 Le tableau suivant répertorie les paramètres, décrit leurs fonctionnalités et fournit des liens vers des informations plus techniques.  
  
|Nom du paramètre|Utilisé dans|Description|  
|--------------------|-------------|-----------------|  
|AUTO_DETECT_PERIODICITY|Algorithme MTS (Microsoft Time Series)|Spécifie une valeur numérique comprise entre 0 et 1 utilisée pour détecter la périodicité. Une valeur proche de 1 favorise la découverte de nombreux modèles quasi-périodiques et la génération automatique d'indications de périodicité. Le traitement d'un grand nombre d'indications de périodicité est susceptible d'allonger de façon significative les durées d'apprentissage des modèles et de produire des modèles plus précis. Si la valeur est proche de 0, la périodicité n'est détectée que pour les données fortement périodiques.<br /><br /> La valeur par défaut est 0,6.|  
|CLUSTER_COUNT|Algorithme de clustering Microsoft<br /><br /> Algorithme MSC (Microsoft Sequence Clustering)|Spécifie le nombre approximatif de clusters que l'algorithme doit générer. S'il est impossible de générer ce nombre approximatif de clusters à partir des données, l'algorithme génère autant de clusters que possible. Si le paramètre CLUSTER_COUNT est défini à 0, l'algorithme utilise des valeurs heuristiques pour déterminer de manière optimale le nombre de clusters à générer.<br /><br /> La valeur par défaut est 10.|  
|CLUSTER_SEED|Algorithme de clustering Microsoft|Spécifie la valeur de départ utilisée pour générer de façon aléatoire des clusters pour le stade initial de construction d'un modèle.<br /><br /> La valeur par défaut est 0.|  
|CLUSTERING_METHOD|Algorithme de clustering Microsoft|Spécifie la méthode de clustering que doit utiliser l'algorithme. Les méthodes de clustering disponibles sont les suivantes : EM évolutif (1), EM non évolutif (2), K-means évolutif (3) ou K-means non évolutif (4).<br /><br /> La valeur par défaut est 1.|  
|COMPLEXITY_PENALTY|Algorithme MDT (Microsoft Decision Trees)<br /><br /> Algorithme MTS (Microsoft Time Series)|Contrôle la croissance de l'arbre de décision. Une valeur faible entraîne l'augmentation du nombre de fractionnements, alors qu'une valeur élevée entraîne la diminution du nombre de fractionnements. La valeur par défaut dépend du nombre d'attributs pour un modèle particulier, comme cela est décrit dans la liste suivante :<br /><br /> De 1 à 9 attributs, la valeur par défaut est égale à 0,5.<br /><br /> De 10 à 99 attributs, la valeur par défaut est égale à 0,9.<br /><br /> À partir de 100 attributs, la valeur par défaut est égale à 0,99.<br /><br /> Remarque : Dans les modèles de série chronologique, ce paramètre s’applique uniquement aux modèles qui sont générés à l’aide de l’algorithme ARTxp ou aux modèles mixtes.|  
|FORCED_REGRESSOR|Algorithme MDT (Microsoft Decision Trees)<br /><br /> Algorithme MLR (Microsoft Linear Regression)|Force l'algorithme à utiliser les colonnes indiquées comme régresseurs, quelle que soit leur importance, telle que calculée par l'algorithme.<br /><br /> Remarque : Ce paramètre est utilisé uniquement pour les arbres de décision qui prévoient un attribut continu. Par définition, un modèle de régression linéaire est un cas spécial d'arbres de décision qui prédit des attributs continus. Toutefois, un modèle d'arbre de décision peut contenir un nœud qui représente une formule de régression linéaire.|  
|FORECAST_METHOD|Algorithme MTS (Microsoft Time Series)|Indique si les prédictions doivent être faites à l'aide de l'algorithme ARTxp, de l'algorithme ARIMA ou d'une combinaison des deux.<br /><br /> La valeur par défaut MIXED.|  
|HIDDEN_NODE_RATIO|Microsoft Neural Network Algorithm|Spécifie le taux de neurones cachés par rapport aux neurones d'entrée et de sortie. La formule suivante détermine le nombre initial de neurones dans la couche masquée :<br /><br /> HIDDEN_NODE_RATIO * SQRT (total neurones d’entrée \* total neurones de sortie)<br /><br /> La valeur par défaut est 4,0.|  
|HISTORIC_MODEL_COUNT|Algorithme MTS (Microsoft Time Series)|Spécifie le nombre de modèles historiques qui seront construits.<br /><br /> La valeur par défaut est 1.|  
|HISTORICAL_MODEL_GAP|Algorithme MTS (Microsoft Time Series)|Spécifie le décalage dans le temps entre deux modèles historiques successifs. Par exemple, la valeur g produit des modèles historiques générés pour des données tronquées par tranches de temps à des intervalles de g, 2\*g, 3\*g et ainsi de suite.<br /><br /> La valeur par défaut est 10.|  
|HOLDOUT_PERCENTAGE|Algorithme MLR (Microsoft Logistic Regression)<br /><br /> Microsoft Neural Network Algorithm|Spécifie le pourcentage de cas extraits des données d'apprentissage pour calculer l'erreur d'exclusion, qui constitue l'un des critères d'arrêt pendant l'apprentissage du modèle d'exploration de données.<br /><br /> La valeur par défaut est 30.<br /><br /> Remarque : Ce paramètre est différent de la valeur de pourcentage d’exclusion qui s’applique à une structure d’exploration de données.|  
|HOLDOUT_SEED|Algorithme MLR (Microsoft Logistic Regression)<br /><br /> Microsoft Neural Network Algorithm|Spécifie un nombre qui est utilisé en tant que valeur de départ du générateur de nombres pseudo-aléatoires lorsque l'algorithme détermine de façon aléatoire les données d'exclusion. Si ce paramètre a la valeur 0, l'algorithme génère la valeur de départ en fonction du nom du modèle d'exploration de données, afin de garantir que le contenu du modèle reste inchangé pendant le retraitement.<br /><br /> La valeur par défaut est 0.<br /><br /> Remarque : Ce paramètre est différent de la valeur de départ d’exclusion qui s’applique à une structure d’exploration de données.|  
|INSTABILITY_SENSITIVITY|Algorithme MTS (Microsoft Time Series)|Contrôle le point où la variation de prédiction dépasse un certain seuil et l'algorithme ARTxp supprime les prédictions. La valeur par défaut est 1.<br /><br /> Remarque : Ce paramètre s’applique uniquement aux modèles mixtes ou aux modèles qui utilisent l’algorithme ARTxp.|  
|MAXIMUM_INPUT_ATTRIBUTES|Algorithme de clustering Microsoft<br /><br /> Algorithme MDT (Microsoft Decision Trees)<br /><br /> Algorithme MLR (Microsoft Linear Regression)<br /><br /> Algorithme MNB (Microsoft Naïve Bayes)<br /><br /> Microsoft Neural Network Algorithm<br /><br /> Algorithme MLR (Microsoft Logistic Regression)|Spécifie le nombre d'attributs d'entrée que l'algorithme peut traiter avant d'appeler la sélection des fonctionnalités. Attribuez à ce paramètre la valeur 0 pour désactiver la sélection des fonctionnalités.<br /><br /> La valeur par défaut est 255.|  
|MAXIMUM_ITEMSET_COUNT|Algorithme Microsoft Association|Spécifie le nombre maximal de jeux d'éléments à produire. Si aucun nombre n'est spécifié, l'algorithme génère tous les jeux d'éléments possibles.<br /><br /> La valeur par défaut est 200000.|  
|MAXIMUM_ITEMSET_SIZE|Algorithme Microsoft Association|Spécifie le nombre maximal d'éléments autorisés dans un jeu d'éléments. Une valeur de 0 spécifie qu'il n'y a pas de limite quant à la taille du jeu d'éléments.<br /><br /> La valeur par défaut est 3.|  
|MAXIMUM_OUTPUT_ATTRIBUTES|Algorithme MDT (Microsoft Decision Trees)<br /><br /> Algorithme MLR (Microsoft Linear Regression)<br /><br /> Algorithme MLR (Microsoft Logistic Regression)<br /><br /> Algorithme MNB (Microsoft Naïve Bayes)<br /><br /> Microsoft Neural Network Algorithm|Spécifie le nombre d'attributs de sortie que l'algorithme peut traiter avant d'appeler la sélection des fonctionnalités. Attribuez à ce paramètre la valeur 0 pour désactiver la sélection des fonctionnalités.<br /><br /> La valeur par défaut est 255.|  
|MAXIMUM_SEQUENCE_STATES|Algorithme MSC (Microsoft Sequence Clustering)|Spécifie le nombre maximal d'états qu'une séquence peut posséder. Si cette valeur est supérieure à 100, l'algorithme peut créer un modèle qui ne fournit pas d'informations significatives.<br /><br /> La valeur par défaut est 64.|  
|MAXIMUM_SERIES_VALUE|Algorithme MTS (Microsoft Time Series)|Spécifie la valeur maximale à utiliser pour les prédictions. Ce paramètre est utilisé, avec MINIMUM_SERIES_VALUE, pour limiter les prédictions à certaines plages attendues. Par exemple, vous pouvez spécifier que le volume de ventes prédites pour un jour ne doit jamais dépasser le nombre de produits dans l'inventaire.|  
|MAXIMUM_STATES|Algorithme de clustering Microsoft<br /><br /> Microsoft Neural Network Algorithm<br /><br /> Algorithme MSC (Microsoft Sequence Clustering)|Spécifie le nombre maximal d'états d'attribut que l'algorithme prend en charge. Si le nombre d’états d’un attribut est supérieur au nombre maximal d’états, l’algorithme emploie les États les plus utilisés de l’attribut et ignore les autres États.<br /><br /> La valeur par défaut est 100.|  
|MAXIMUM_SUPPORT|Algorithme Microsoft Association|Spécifie le nombre maximal de cas pour lesquels un jeu d'éléments peut bénéficier d'un support. Une valeur inférieure à 1 représente un pourcentage du nombre total de cas. Si cette valeur est supérieure à 1, elle représente le nombre absolu de cas pouvant contenir le jeu d'éléments.<br /><br /> La valeur par défaut est 1.|  
|MINIMUM_IMPORTANCE|Algorithme Microsoft Association|Spécifie le seuil d'importance pour les règles d'association. Les règles avec une importance inférieure à cette valeur sont filtrées.|  
|MINIMUM_ITEMSET_SIZE|Algorithme Microsoft Association|Spécifie le nombre minimal d'éléments autorisés dans un jeu d'éléments.<br /><br /> La valeur par défaut est 1.|  
|MINIMUM_DEPENDENCY_PROBABILITY|Algorithme MNB (Microsoft Naïve Bayes)|Spécifie la probabilité de dépendance minimale entre les attributs d'entrée et les attributs de sortie. Cette valeur sert à limiter la taille du contenu généré par l'algorithme. Cette propriété peut être définie entre 0 et 1. Les plus grandes valeurs réduisent le nombre d'attributs dans le contenu du modèle.<br /><br /> La valeur par défaut est 0.5.|  
|MINIMUM_PROBABILITY|Algorithme Microsoft Association|Spécifie la probabilité minimale qu'une règle ait la valeur True. Par exemple, la valeur 0,5 spécifie qu'aucune règle présentant une probabilité inférieure à 50 % n'est générée.<br /><br /> La valeur par défaut est 0,4.|  
|MINIMUM_SERIES_VALUE|Algorithme MTS (Microsoft Time Series)|Spécifie la contrainte inférieure pour toute prédiction de série chronologique. Les valeurs prédites ne seront jamais inférieures à cette contrainte.|  
|MINIMUM_SUPPORT|Algorithme Microsoft Association|Spécifie le nombre minimal de cas qui doivent contenir le jeu d'éléments avant que l'algorithme génère une règle. Attribuer à ce paramètre une valeur inférieure à 1 spécifie ce nombre minimal de cas comme un pourcentage du nombre total de cas. Attribuer à ce paramètre une valeur entière supérieure à 1 spécifie le nombre minimal de cas comme le nombre absolu de cas qui doivent contenir le jeu d'éléments. L'algorithme peut augmenter la valeur de ce paramètre, si la mémoire est limitée.<br /><br /> La valeur par défaut est 0,03.|  
|MINIMUM_SUPPORT|Algorithme de clustering Microsoft|Spécifie le nombre minimal de cas dans chaque cluster.<br /><br /> La valeur par défaut est 1.|  
|MINIMUM_SUPPORT|Algorithme MDT (Microsoft Decision Trees)|Spécifie le nombre minimal de cas de nœud terminal requis pour générer un fractionnement dans l'arbre de décision.<br /><br /> La valeur par défaut est 10.|  
|MINIMUM_SUPPORT|Algorithme MSC (Microsoft Sequence Clustering)|Spécifie le nombre minimal de cas dans chaque cluster.<br /><br /> La valeur par défaut est 10.|  
|MINIMUM_SUPPORT|Algorithme MTS (Microsoft Time Series)|Spécifie le nombre minimal de tranches de temps qui sont requises pour générer un fractionnement dans chaque arbre de série chronologique.<br /><br /> La valeur par défaut est 10.|  
|MISSING_VALUE_SUBSTITUTION|Algorithme MTS (Microsoft Time Series)|Spécifie la méthode employée pour combler les vides dans les données d'historique. Par défaut, les vides et les extrémités irréguliers ne sont pas autorisés dans les données. Les méthodes suivantes peuvent être utilisées pour combler les extrémités ou vides irréguliers : utiliser la valeur précédente, utiliser la valeur moyenne ou utiliser une constante numérique spécifique.|  
|MODELLING_CARDINALITY|Algorithme de clustering Microsoft|Spécifie le nombre d'exemples de modèles générés pendant le processus de clustering.<br /><br /> La valeur par défaut est 10.|  
|PERIODICITY_HINT|Algorithme MTS (Microsoft Time Series)|Fournit à l'algorithme une indication de la périodicité des données. Par exemple, si les ventes varient chaque année, et que l'unité de mesure de la série est le mois, la périodicité est égale à 12. Ce paramètre s'affiche sous la forme {n [, n]}, où n est un nombre positif. Le n entre crochets [] est facultatif et peut être répété aussi souvent que nécessaire.<br /><br /> La valeur par défaut est {1}.|  
|PREDICTION_SMOOTHING|Algorithme MTS (Microsoft Time Series)|Contrôle la fusion entre les algorithmes de série chronologique ARTXP et ARIMA. La valeur spécifiée n'est valide que lorsque le paramètre FORECAST_METHOD a la valeur MIXED. Les valeurs doivent être comprises entre 0 et 1. Si la valeur est 0, le modèle utilise uniquement ARTXP. Si la valeur est 1, le modèle utilise uniquement ARIMA. Une valeur plus proche à 0 indique une pondération plus importante pour ARTXP. Une valeur plus proche à 1 indique une pondération plus importante pour ARIMA.|  
|SAMPLE_SIZE|Algorithme de clustering Microsoft|Spécifie le nombre de cas que l'algorithme utilise à chaque passage si l'une des méthodes de clustering évolutif est définie pour le paramètre CLUSTERING_METHOD. Si la valeur 0 est attribuée au paramètre SAMPLE_SIZE, le jeu de données complet est organisé en clusters en un seul passage. Cela risque de créer des problèmes de mémoire et de performances.<br /><br /> La valeur par défaut est 50000.|  
|SAMPLE_SIZE|Algorithme MLR (Microsoft Logistic Regression)<br /><br /> Microsoft Neural Network Algorithm|Spécifie le nombre de cas à utiliser pour effectuer l'apprentissage du modèle. Le fournisseur d'algorithme utilise soit ce nombre, soit le pourcentage du nombre total de cas qui ne sont pas inclus dans le pourcentage d'exclusion conformément au paramètre HOLDOUT_PERCENTAGE : c'est la valeur la plus faible qui est retenue.<br /><br /> En d’autres termes, si HOLDOUT_PERCENTAGE a la valeur 30, l’algorithme utilise la valeur de ce paramètre ou une valeur égale à 70 % du nombre total de cas, en prenant la plus petite valeur des deux.<br /><br /> La valeur par défaut est 10000.|  
|SCORE_METHOD|Algorithme MDT (Microsoft Decision Trees)|Spécifie la méthode utilisée pour calculer le résultat de la division. Les options suivantes sont disponibles : (1) entropie, (2) bayésien avec a priori K2 avant, ou (3) bayésien de Dirichlet (BDE) avant.<br /><br /> La valeur par défaut est 3.|  
|SPLIT_METHOD|Algorithme MDT (Microsoft Decision Trees)|Spécifie la méthode utilisée pour fractionner le nœud. Les options suivantes sont disponibles : Binaire (1), complet (2) ou les deux (3).<br /><br /> La valeur par défaut est 3.|  
|STOPPING_TOLERANCE|Références techniques relatives à l'algorithme de gestion de clusters Microsoft|Spécifie la valeur utilisée pour déterminer quand une convergence est atteinte et quand l'algorithme a terminé la construction du modèle. La convergence est atteinte lorsque le changement global dans les probabilités de clusters est inférieur au rapport du paramètre STOPPING_TOLERANCE divisé par la taille du modèle.<br /><br /> La valeur par défaut est 10.|  
  
### <a name="comments"></a>Commentaires  
 Pour plus d'informations sur les algorithmes, consultez la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;compléments d’exploration de données SQL Server&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md)  
  
  
