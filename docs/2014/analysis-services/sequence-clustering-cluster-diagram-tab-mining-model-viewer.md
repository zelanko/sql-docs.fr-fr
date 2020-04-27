---
title: Onglet diagramme de cluster de séquence clustering (visionneuse de modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.diagrams.f1
ms.assetid: 4b705397-9af4-4678-9eda-149bc5d762fa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d8cff96e3ed2d36db93abb3583a08b5c9d8153d8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069111"
---
# <a name="sequence-clustering-cluster-diagram-tab-mining-model-viewer"></a>Onglet Diagramme de cluster du modèle Sequence Clustering (Visionneuse de modèle d'exploration de données)
  L’onglet **Diagramme de cluster** de la **visionneuse MSC** (Microsoft Sequence Clustering) affiche sous forme graphique tous les clusters contenus dans le modèle Sequence Clustering.  
  
 Utilisez cette vue d'un modèle Sequence Clustering pour procéder à une extraction depuis chaque cluster dans les cas de prise en charge, si l'extraction a été activée. Vous pouvez également affecter des noms descriptifs aux clusters et remplacer la variable d'ombrage afin d'évaluer la distribution des valeurs en un coup d'œil  
  
 **Pour plus d’informations :** [Algorithme MSC (Microsoft Sequence Clustering)](data-mining/microsoft-sequence-clustering-algorithm.md), [Explorer un modèle à l’aide de la visionneuse de l’algorithme MSC (Microsoft Sequence Cluster)](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l'observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données pour afficher le contenu de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour consulter le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée ou la **Visionneuse de l'arborescence de contenu générique Microsoft**. Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Zoom avant**  
 Permet d'effectuer un zoom avant sur le schéma et d'obtenir une vue plus détaillée des clusters.  
  
 **Zoom arrière**  
 Permet d'effectuer un zoom arrière sur le schéma, pour voir tous les clusters du modèle.  
  
 **Copier la vue du graphique**  
 Copie la partie visible du diagramme dans le Presse-papiers.  
  
 **Copier le graphique entier**  
 Copie la totalité du diagramme dans le Presse-papiers.  
  
 **Ajuster le diagramme à la fenêtre**  
 Réduit la taille du diagramme jusqu'à ce qu'il soit ajusté à l'écran.  
  
 **Rechercher un nœud**  
 Utilisez la boîte de dialogue **Rechercher un nœud** pour filtrer les clusters dans le graphique et ainsi faciliter la recherche d’un cluster spécifique. Pour plus d’informations, consultez [Boîte de dialogue Rechercher un nœud &#40;visionneuse de modèle d’exploration de données&#41;](find-node-dialog-box-mining-model-viewer.md).  
  
 Notez que dans ce contexte, vous recherchez uniquement le nom du cluster, pas les attributs du cluster ; par conséquent, cette option est très utile si vous avez affecté des noms descriptifs à votre cluster. Vous pouvez affecter des noms aux clusters dans la visionneuse en cliquant avec le bouton droit sur chaque cluster et en sélectionnant **Renommer**.  
  
 **Améliorer la disposition**  
 Réorganise les clusters du diagramme pour en améliorer la disposition.  
  
 **Masse**  
 L’apparence du graphique à barres de densité et les valeurs qu’il contient dépendent de l’attribut que vous sélectionnez dans **Variable d’ombrage**.  
  
-   Si aucun état d'attribut n'est sélectionné comme variable d'ombrage, par défaut l'ombrage de densité appliqué à chaque cluster représente la prise en charge du cluster, par comparaison à la population globale des cas.  
  
-   Quand vous sélectionnez un attribut pour **Variable d’ombrage**, vous devez ensuite sélectionner également une valeur pour **État** . Ce faisant, le graphique à barres de densité est actualisé afin d'afficher la probabilité de cet état. Vous pouvez placer la souris sur n'importe quel cluster individuel afin d'afficher la probabilité de l'état sélectionné pour ce cluster.  
  
 **Variable d’ombrage**  
 Sélectionnez un attribut du modèle d'exploration de données à utiliser lors de l'ombrage du schéma de cluster.  
  
 **State**  
 Sélectionnez un état qui correspond à **Variable d’ombrage**. Par exemple, si vous souhaitez consulter les séquences qui incluent un produit particulier, sélectionnez la colonne [Product] comme attribut pour **Variable d’ombrage**, ainsi que le nom de produit spécifique comme valeur pour **État** .  
  
 **Liens**  
 Les lignes du schéma indiquent des associations entre les clusters de séquence. Vous pouvez modifier le nombre de liens affichés par la visionneuse à l'aide du curseur situé à droite des clusters. Si vous déplacez le curseur vers le bas, seuls les liens les plus forts sont affichés.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
