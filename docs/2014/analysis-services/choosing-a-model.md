---
title: Choix d’un modèle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining algorithms
- mining models
- mining structures
- data mining models
- data mining structures
ms.assetid: 444bbf9c-cec8-460e-881d-38784fb146fa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d91e282ebfe0299fd6015530e8af1b6d10e6547
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52400512"
---
# <a name="choosing-a-model"></a>Choix d'un modèle
  **Algorithme d’exploration de données :** L’exploration de données *algorithme* est un mécanisme qui crée des modèles de données. L'algorithme définit la façon dont les données sont comptées, les relations dérivées et les séquences stockées. La sélection d'un algorithme dépend en partie du type de données à analyser. Par exemple, certains algorithmes peuvent uniquement utiliser des nombres continus, tandis que d'autres peuvent être plus efficaces avec un nombre limité de valeurs distinctes.  
  
 **Modèle d’exploration de données :** Le résultat d’analyse de données par un algorithme est enregistré dans un *modèle d’exploration de*. Un modèle d'exploration de données est une collection de règles, de statistiques et de schémas. Le *contenu* du modèle d’exploration de données dépend de l’algorithme que vous permettent de traiter les données, mais pouvez inclure les éléments suivants :  
  
-   des règles Si-alors qui décrivent la manière dont les produits sont regroupés dans une transaction ;  
  
-   Un arbre de décision qui trace les chemins d'accès conduisant à un résultat, avec des probabilités d'occurrence de chaque chemin d'accès.  
  
-   Un modèle mathématique avec des équations pour l'ensemble du modèle ou uniquement pour des segments du modèle.  
  
-   Collections d’éléments similaires (appelé *clusters* ou *segments*) qui sont définies par les caractéristiques elles partagent et par un score de similarité.  
  
-   *Nœuds* dans un réseau, connecté par *bords*. Les nœuds représentent des éléments ou des groupes d'éléments. Les arêtes sont notées en fonction de la puissance des relations entre les nœuds.  
  
 **À l’aide du modèle :** Une fois que vous avez créé un modèle, vous pouvez utiliser les visionneuses fournies pour l’Explorer, ou vous pouvez créer une requête sur le modèle. Les requêtes peuvent être utilisées pour :  
  
-   Prédire des valeurs futures.  
  
-   Générer un ensemble de produits connexes ou de produits recommandés.  
  
-   Retourner des règles, des schémas ou des formules dans le modèle.  
  
-   Obtenir des métadonnées à partir du modèle.  
  
-   Spécifier la probabilité et prendre en charge les scores pour tout ou partie des prédictions.  
  
## <a name="types-of-machine-learning-algorithms"></a>Types d'algorithmes d'apprentissage automatique  
 Dans la mesure où différents types d'algorithmes utilisent les données différemment, vous devez sélectionner l'algorithme adapté à vos objectifs et aux données que vous voulez analyser lorsque vous créez un modèle.  
  
 Les compléments d'exploration de données pour Excel incluent les types étendus d'algorithmes suivants :  
  
-   *Les algorithmes de classification*.  
  
     Prévoyez une ou plusieurs variables discrètes, en fonction des autres attributs du dataset.  
  
-   *Algorithmes de régression*  
  
     Prévoyez une ou plusieurs variables continues, telles que les bénéfices ou les pertes, en fonction d'autres attributs du dataset.  
  
-   *Algorithmes de segmentation*  
  
     Répartissez les données dans des groupes, ou clusters, d'éléments possédant des propriétés similaires.  
  
-   *Algorithmes d’association*  
  
     Recherchez des corrélations entre différents attributs d'un dataset. Ce type d'algorithme est principalement utilisé pour créer des règles d'association. Vous pouvez utiliser des règles d'association pour l'analyse du panier d'achat.  
  
-   *Algorithmes d’analyse de séquence*  
  
     Synthétisez les séquences ou épisodes fréquents dans les données, tels que les chemins suivis par les utilisateurs lors de la navigation sur un site Web.  
  
 Les algorithmes qu'utilisent les compléments d'exploration de données SQL Server pour Office reposent sur les algorithmes fournis par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Vous pouvez également utiliser des algorithmes tiers conformes à la spécification OLE DB pour l’exploration de données, si l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à laquelle vous êtes connecté a été configuré pour autoriser des algorithmes tiers.  
  
## <a name="requirements"></a>Configuration requise  
 Chaque algorithme diffère au niveau des types des données avec lesquels il peut s'exécuter.  
  
-   Un modèle de régression linéaire ne peut modéliser que des valeurs numériques. Les variables d'entrée et les résultats cibles doivent être des types de nombres continus. Utilisez un arbre de décision ou un modèle d'estimation si vous devez combiner des variables discrètes et continues.  
  
-   Un modèle Naïve Bayes impose que tous les nombres soient placés dans un conteneur. Si vous utilisez l'un des assistants basés sur cet algorithme, le placement dans un conteneur est effectué automatiquement.  
  
-   Un modèle d'arbre de décision peut contenir à la fois des variables discrètes et continues. Toutefois, les nombres seront placés dans un conteneur automatiquement en fonction des divisions dans l'arbre.  
  
-   Les réseaux neuronaux et les modèles de régression logistique placent automatiquement dans un conteneur les nombres utilisés soit comme résultats, soit comme variables d'entrée. Si vous souhaitez regrouper les nombres en fonction d'autres critères, vous devez utiliser l'outil de réétiquetage pour créer des regroupements avant la modélisation. Par exemple, vous pouvez souhaiter regrouper des valeurs dans une **âge** colonne par déciles (10-20, 21 à 30 et ainsis de suite), plutôt qu’aux regroupements statistiquement significatifs détectés par le modèle (un exemple peut être 35,6 – 41,8 ans).  
  
-   Un modèle d'association nécessite que les données soient regroupées au sein de transactions, chacune faisant référence à plusieurs éléments ou lignes. Si vous utilisez le [Assistant associer &#40;Client d’exploration de données pour Excel&#41; ](associate-wizard-data-mining-client-for-excel.md) Assistant ou la [analyse de panier d’achat &#40;outils d’analyse de Table pour Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) outil, les données doivent être présentées comme indiqué dans le **associer** onglet de l’exemple de classeur.  
  
     Si vous souhaitez utiliser des tables imbriquées dans une source de données externe, vous devez utiliser le [avancés de modélisation &#40;des compléments d’exploration de données pour Excel&#41; ](advanced-modeling-data-mining-add-ins-for-excel.md) options pour créer une structure d’exploration de données et le modèle d’exploration de données qui est enregistré sur le serveur de modélisation. Excel ne prend pas en charge les tables imbriquées.  
  
## <a name="feature-selection"></a>Sélection des fonctionnalités  
 Selon le jeu de données, l’algorithme peut appliquer *sélection des fonctionnalités*, afin d’éliminer les colonnes qui ne sont pas utiles et pour déterminer quelles colonnes de données sont statistiquement significatives en relation avec le résultat.  
  
 Chaque algorithme utilise des méthodes de sélection des fonctionnalités légèrement différentes (entropie ou différents scores) pour déterminer quelles tendances sont importantes et quelles différences peuvent être ignorées.  
  
 Dans les compléments d'exploration de données pour Excel, la sélection des fonctionnalités est appliquée automatiquement, en utilisant la méthode de calcul de score appropriée pour chaque algorithme. Si vous souhaitez affecter les résultats de la sélection des fonctionnalités, utilisez les Assistants dans le **d’exploration de données** ruban, puis cliquez sur **avancé** pour définir les paramètres à l’aide de la **paramètres d’algorithme**boîte de dialogue.  
  
 Pour obtenir la liste de la sélection de fonctionnalité méthodes utilisées par chaque algorithme consultez la rubrique sur [sélection des fonctionnalités &#40;d’exploration de données&#41; ](data-mining/feature-selection-data-mining.md) dans la documentation en ligne de SQL Server.  
  
## <a name="list-of-supported-algorithms"></a>Liste d'algorithmes pris en charge  
 Les algorithmes suivants sont fournis par défaut.  
  
|Nom de l’algorithme|Description|Utilisé dans|  
|--------------------|-----------------|-------------|  
|Microsoft Association Rules|Cet algorithme crée des règles qui décrivent les éléments susceptibles d'apparaître ensemble dans une transaction.|[Assistant association &#40;Client d’exploration de données pour Excel&#41;](associate-wizard-data-mining-client-for-excel.md)<br /><br /> [Analyse de panier d’achat &#40;outils d’analyse de Table pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)|  
|Microsoft Clustering|Cet algorithme identifie les relations dans un jeu de données que vous ne pourriez pas forcément déduire d'une observation informelle. Il utilise des techniques itératives pour regrouper les enregistrements en clusters possédant des caractéristiques similaires.|[Détecter les catégories &#40;outils d’analyse de Table pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)<br /><br /> [Assistant cluster &#40;les données des compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)|  
|Microsoft Decision Trees|Cet algorithme effectue des prédictions en fonction des relations entre les colonnes du jeu de données, et modélise les relations sous forme d'une série de fractionnements de type arbre sur des valeurs spécifiques.<br /><br /> Il prend en charge la prédiction des attributs discrets et continus.|[Assistant classification &#40;les données des compléments d’exploration de données pour Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)<br /><br /> [Assistant estimation &#40;les données des compléments d’exploration de données pour Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)|  
|Microsoft Linear Regression|S'il existe une dépendance linéaire entre la variable cible et les variables en cours d'examen, cet algorithme recherche la relation la plus efficace entre la cible et ses entrées.<br /><br /> Il prend en charge la prédiction d'attributs continus.|Cet algorithme est disponible dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Dans les compléments d'exploration de données pour Office, vous pouvez créer un modèle qui utilise cet algorithme en créant une structure, puis en ajoutant manuellement un modèle.<br /><br /> Pour plus d’informations, consultez [avancés de modélisation &#40;des compléments d’exploration de données pour Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Logistic Regression|Cet algorithme analyse les facteurs qui contribuent à un résultat, le résultat étant limité à deux valeurs, généralement l'occurrence ou la non-occurrence d'un événement.<br /><br /> Il prend en charge la prédiction des attributs discrets et continus.|[Remplir à partir de l’exemple &#40;outils d’analyse de Table pour Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)<br /><br /> [Scénario valeur cible &#40;outils d’analyse de Table pour Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)<br /><br /> [Scénario de simulation &#40;outils d’analyse de Table pour Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)<br /><br /> [Calcul de prédiction &#40;outils d’analyse de Table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)|  
|Microsoft Naive Bayes|Cet algorithme recherche la probabilité de la relation entre toutes les colonnes d'entrée et les colonnes prévisibles. Il est utile pour générer rapidement des modèles d'exploration de données permettant de découvrir des relations.<br /><br /> Il prend uniquement en charge les attributs discrets ou discrétisés.<br /><br /> Cet algorithme traite tous les attributs d'entrée de manière indépendante.|[Analyser les facteurs d’influence clés &#40;outils d’analyse de Table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)|  
|Microsoft Neural Network|Cet algorithme analyse des données d'entrée ou des problèmes d'entreprise complexes pour lesquels une importante quantité de données d'apprentissage est disponible, mais pour lesquels il n'est pas facile de dériver des règles à l'aide d'autres algorithmes.<br /><br /> Il peut prédire plusieurs attributs.<br /><br /> Il peut être utilisé pour classer des attributs discrets et la régression d'attributs continus.|Cet algorithme est disponible dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Dans les compléments d'exploration de données pour Office, vous pouvez créer un modèle qui utilise cet algorithme en créant une structure, puis en ajoutant manuellement un modèle.<br /><br /> Pour plus d’informations, consultez [avancés de modélisation &#40;des compléments d’exploration de données pour Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Sequence Clustering|Cet algorithme identifie les clusters d'événements ordonnés de manière similaire dans une séquence.<br /><br /> Il associe l'analyse de séquence et le clustering.|Cet algorithme n'est disponible que dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Toutefois, dans les compléments d'exploration de données pour Office, vous pouvez créer un modèle qui utilise cet algorithme en créant une structure, puis en ajoutant manuellement un modèle.<br /><br /> Pour plus d’informations, consultez [avancés de modélisation &#40;des compléments d’exploration de données pour Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Time Series|Cet algorithme analyse les données chronologiques au moyen d'un arbre de décision linéaire.<br /><br /> Il est possible d'utiliser des séquences pour prévoir les valeurs futures dans la série chronologique.|[Prévision &#40;outils d’analyse de Table pour Excel&#41;](forecast-table-analysis-tools-for-excel.md)<br /><br /> [Assistant prévisions &#40;les données des compléments d’exploration de données pour Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments inclus dans les compléments d’exploration de données pour Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
