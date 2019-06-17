---
title: Sequence Clustering onglet transition d’état de Cluster (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.transition.f1
ms.assetid: 40aef457-d69f-4905-a2d3-924c37bd3d97
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a236805ac047b351aa49c2486b8acac84818017
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66069077"
---
# <a name="sequence-clustering-cluster-transition-tab-mining-model-viewer"></a>Onglet Transition d'état du modèle Sequence Clustering (Visionneuse de modèle d'exploration de données)
  L’onglet **Transitions d’état** dans la **Visionneuse de l’algorithme MSC** (Microsoft Sequence Clustering) fournit une présentation détaillée des transitions entre des paires attribut-valeur, ou des états, dans le cluster sélectionné.  
  
 Utilisez cette vue d'un modèle Sequence Clustering pour afficher des schémas. Dans le diagramme, un lien représente la probabilité d'une transition et un nœud l'état d'une séquence.  
  
 **Pour plus d’informations :** [Algorithme Microsoft Sequence Clustering](data-mining/microsoft-sequence-clustering-algorithm.md), [Explorer un modèle à l’aide de la séquence de Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données pour afficher le contenu de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour consulter le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée ou la **Visionneuse de l'arborescence de contenu générique Microsoft**. Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Zoom avant**  
 Permet d'effectuer un zoom avant sur le schéma pour mieux voir les états.  
  
 **Effectuer un zoom arrière**  
 Permet d'effectuer un zoom arrière sur le schéma pour obtenir une vue d'ensemble des états du cluster.  
  
 **Copier la vue du graphique**  
 Copie la partie visible du diagramme dans le Presse-papiers.  
  
 **Copier le graphique entier**  
 Copie la totalité du diagramme dans le Presse-papiers.  
  
 **Cluster**  
 Choisissez un cluster à afficher dans la visionneuse. Par défaut, **Remplissage (tout)** est sélectionné, ce qui signifie que les états et transitions du modèle entier sont inclus dans le graphique. Lorsque vous choisissez un cluster particulier, seuls les états et transitions qui figurent dans ce cluster sont affichés.  
  
 **Conseil :** Vous pouvez renommer les clusters à l’aide de la **diagramme de Cluster** onglet. Il suffit de sélectionner un cluster, de cliquer avec le bouton droit et de choisir **Renommer**. Renommer les clusters avec un nom plus descriptif simplifie la comparaison des clusters sous l’onglet **Transitions d’état** .  
  
 **Afficher les étiquettes du bord**  
 Sélectionnez cette option pour afficher les nombres sur chaque bord du graphique qui délimitent la probabilité de la transition.  
  
 **Links**  
 Utilisez le curseur pour contrôler le nombre d'états et de transitions affichés dans le graphique. Abaisser le curseur permet d'afficher uniquement les états et les transitions ayant la probabilité la plus élevée.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
