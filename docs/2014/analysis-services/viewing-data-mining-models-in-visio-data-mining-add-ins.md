---
title: Affichage des modèles d’exploration de données dans Visio (compléments d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- diagram, modifying
- templates [Visio]
- shapes, data mining
- diagram
ms.assetid: 5841adea-6650-4fae-8526-26af33edbede
author: minewiskan
ms.author: owend
ms.openlocfilehash: fe6baff391f108e14a401a0d3b9dcacefa6da406
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938140"
---
# <a name="viewing-data-mining-models-in-visio-data-mining-add-ins"></a>Affichage de modèles d'exploration de données dans Visio (Compléments d'exploration de données)
  Les formes Visio pour l'exploration de données vous permettent de vous connecter à un serveur et de créer un diagramme représentant un modèle d'exploration de données existant. Les diagrammes peuvent alors être personnalisés à l'aide de contrôles Visio, mais vous pouvez également explorer plus en détail les données, exposer une partie des statistiques sous-jacentes et utiliser le modèle sous-jacent.  
  
## <a name="building-a-model-diagram"></a>Génération d'un diagramme de modèle  
 Lorsque vous ouvrez le fichier contenant les formes Visio pour l’exploration de données, le volet **formes** affiche les formes suivantes.  
  
 Si vous ne voyez pas les formes d'exploration de données en ouvrant Visio, ouvrez le fichier modèle dans le dossier d'installation.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Pour utiliser une forme, faites-la glisser vers la page. Chaque forme ouvre un Assistant différent qui vous permet de sélectionner des données sources, de définir des options pour le type de graphique spécifique et de spécifier l'ombrage et d'autres options d'affichage.  
  
 Le tableau ci-dessous répertorie les types de modèles qu'il est possible d'utiliser avec chaque type de diagramme.  
  
|Forme Visio|Modèles pris en charge|  
|-----------------|----------------------|  
|Arbre de décision|Utilisez cette forme pour les modèles basés sur les algorithmes d'arbre de décision ou de régression linéaire.|  
|Réseau de dépendances|Utilisez cette forme pour les modèles basés sur l'un des algorithmes suivants : Naive Bayes, Decision Trees ou Association Rules.|  
|Cluster|Utilisez cette forme pour les modèles basés sur les algorithmes de clustering.|  
  
 Selon le type de données figurant dans votre modèle d'exploration de données, l'Assistant peut proposer des options différentes. Par exemple, les colonnes qui contiennent des nombres continus sont visualisées différemment des variables catégorielles.  
  
## <a name="working-with-completed-shapes"></a>Utilisation des formes achevées  
 Une fois le diagramme terminé, utilisez-le pour parcourir le modèle d'exploration de données ou améliorez-le pour l'utiliser dans des présentations.  
  
### <a name="visio-menus"></a>Menus Visio  
 Visio fournit une variété de contrôles de rendu, de thèmes et de menus contextuels pour vous aider à améliorer un diagramme.  
  
-   Utilisez les thèmes Visio pour modifier les couleurs d'un diagramme.  
  
-   Modifiez les connecteurs ou la disposition du diagramme.  
  
### <a name="data-mining-menus"></a>Menus d'exploration de données  
 Ces barres d'outils et éléments de menu sont fournis par les compléments qui sont spécifiques à chaque forme ou type de modèle  
  
-   Chaque type de diagramme possède un menu contextuel pour la forme qui vous permet d'accéder aux options spéciales. Même si la plupart des options de ce menu sont communes à toutes les formes Visio, certaines sont spécifiques aux modèles d'exploration de données  
  
     Par exemple, dans un diagramme Arbre de décision, vous pouvez cliquer sur un nœud individuel puis réduire les nœuds enfants pour simplifier le diagramme ou déplacer les nœuds enfants vers une page séparée.  
  
-   Dans la mesure où la forme est liée aux données de modèle, vous pouvez également procéder à une exploration à l'aide du diagramme :  
  
     Filtrer les nœuds affichés, ou modifier le niveau de l'arbre ou la profondeur du graphique.  
  
     Effectuer un zoom avant sur des sections spécifiques, rechercher les nœuds qui contiennent un attribut, ou filtrer un graphique de dépendances par ses bords (probabilité).  
  
## <a name="walkthroughs"></a>Procédures pas à pas  
 Pour obtenir des exemples d'utilisation et d'interprétation d'un diagramme fini, consultez les rubriques suivantes :  
  
 [Procédure pas à pas Diagramme de cluster](cluster-diagram-walkthrough-data-mining-add-ins.md)  
  
 [Procédure pas à pas Diagramme de réseau de dépendances](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
 [Procédure pas à pas Diagramme d'arbre de décision](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;SQL Server les compléments d’exploration de données&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
