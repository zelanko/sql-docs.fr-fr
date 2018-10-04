---
title: Onglet réseau de dépendances (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.dependencynetwork.f1
ms.assetid: e58ce1b7-20d6-42cb-ade5-916da8471e09
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f907a03df66970d69fe4c6b0379d735af987102
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226169"
---
# <a name="dependency-network-tab-mining-model-viewer"></a>Onglet Réseau de dépendances (Visionneuse de modèle d'exploration de données)
  L'onglet **Réseau de dépendances** affiche sous forme graphique tous les attributs contenus dans le modèle d'exploration de données et illustre les relations qu'il existe entre eux.  
  
 L'onglet **Réseau de dépendances**  est utilisé pour plusieurs types de modèles d'exploration de données, y compris les modèles Naïve Bayes, les modèles d'arbre de décision et les modèles d'association. Pour plus d'informations sur la manière d'interpréter le contenu de l'onglet **Réseau de dépendances**  dans le contexte de ces modèles, consultez les liens suivants :  
  
 [Explorer un modèle à l’aide de la visionneuse d’arborescences Microsoft](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
 [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNB (Microsoft Naive Bayes)](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
 [Explorer un modèle à l’aide de la visionneuse de l’algorithme MAR (Microsoft Association Rules)](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données à afficher, parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre dans une visionneuse personnalisée. Le type de visionneuse personnalisée qui est utilisée pour chaque modèle est déterminé par l'algorithme que vous avez utilisé pour créer le modèle.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Pour chaque modèle, vous pouvez utiliser la visionneuse personnalisée fournie pour chaque modèle d'exploration de données ou la visionneuse de contenu d'exploration de données ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer). Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant. La visionneuse de l'arborescence de contenu Microsoft peut être utilisée avec tous les modèles, et représente le contenu du modèle dans une table HTML.  
  
 **Zoom avant**  
 Permet d'effectuer un zoom avant sur le schéma afin que vous puissiez voir les attributs plus en détail.  
  
 **Effectuer un zoom arrière**  
 Permet d'effectuer un zoom arrière sur le schéma, afin que vous puissiez voir plus d'attributs et les liens entre eux.  
  
 **Copier la vue du graphique**  
 Copie la partie visible du diagramme dans le Presse-papiers.  
  
 **Copier le graphique entier**  
 Copie la totalité du diagramme dans le Presse-papiers.  
  
 **Liens**  
 Ajustez le nombre de liens (arêtes) et de nœuds affichés par la visionneuse en déplaçant le curseur à droite des attributs. Faites glisser la barre de curseur vers le bas pour augmenter la valeur de seuil, afin que seuls les liens les plus forts soient affichés. Pour chaque type de modèle, une valeur légèrement différente est utilisée pour représenter les liens dans le graphique :  
  
-   Dans un modèle d' **arbre de décision** , les arêtes représentent la force prédictive de la connexion, déterminée en partie par le score de fractionnement.  
  
-   Dans un modèle **Naïve Bayes** , les liens entre deux nœuds peuvent s'appliquer dans l'une ou l'autre direction : autrement dit, le nœud A peut prédire le nœud B, et inversement. Le score associé à l'arête représente la force prédictive de la connexion.  
  
-   Dans un **modèle d'association**, les arêtes entre les nœuds représentent le score d'importance de la règle qui connecte deux jeux d'éléments.  
  
 Règle générale pour tous les types de modèle : plus le lien est fort, plus la relation prédictive entre les deux attributs est forte.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèle d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
