---
title: Onglet Profils du cluster Sequence Clustering (visionneuse de modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.profiles.f1
ms.assetid: 44230895-0a42-4032-8d6c-0cdb8a2dbb8c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f277abea585715f6a3656fffe7672f347233507
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66069094"
---
# <a name="sequence-clustering-cluster-profiles-tab-mining-model-viewer"></a>Onglet Profils du cluster du modèle Sequence Clustering (Visionneuse de modèle d'exploration de données)
  L’onglet **Profils du cluster** dans la **Visionneuse de l’algorithme MSC** (Microsoft Sequence Clustering) fournit une vue à code de couleurs des séquences incluses dans chaque cluster.  
  
 Utilisez cette vue d'un modèle Sequence Clustering pour obtenir une vue rapide de la façon dont les séquences trouvées par le modèle sont regroupées. Vous pouvez voir d'un coup d'œil le nombre de séquences qui sont longues et celles qui sont courtes. Vous pouvez également cliquer sur un cluster et afficher la **Légende d’exploration de données** pour voir exactement les états représentés par les couleurs dans chaque séquence.  
  
 **Pour plus d’informations :**  [algorithme de clustering de séquences Microsoft](data-mining/microsoft-sequence-clustering-algorithm.md), [Parcourir un modèle à l’aide de Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l'observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d’exploration de données**  
 Choisissez un modèle d'exploration de données pour afficher le contenu de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour consulter le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée ou la **Visionneuse de l'arborescence de contenu générique Microsoft**. Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Afficher la légende**  
 Sélectionnez cette option pour afficher une légende qui montre la corrélation entre les couleurs affichées dans les profils du cluster et les valeurs textuelles des états.  
  
 **Barres de l'histogramme**  
 Utilisez cette option pour modifier le nombre de barres de couleur incluses dans l'histogramme. S’il existe davantage de barres que le nombre que vous choisissez d’afficher, les barres de la plus grande importance sont conservées et les barres restantes sont regroupées dans **Autre**.  
  
 **Attributs** et **profils de cluster**  
 Cette section du graphique répertorie les clusters des séquences trouvées dans le modèle.  
  
 Chaque cluster de séquence s’affiche avec le nombre d’états que vous avez sélectionné dans l’option **Barres de l’histogramme**.  
  
 Deux ensembles d'histogrammes sont affichés pour chaque cluster du modèle, chacun sur une ligne différente dans le graphique :  
  
-   **nom de l’attribut>. Samples : les histogrammes de cette ligne affichent les séquences d’éléments qui sont représentatives de chaque cluster. \<** En termes DMX, ce sont les cas d'exemple pour chaque cluster.  
  
-   nom de l’attribut> : les histogrammes de cette ligne décrivent tous les éléments que le cluster contient et leur distribution globale. ** \< ** Cliquez sur un histogramme quand la **Légende d’exploration de données** est visible et que vous pouvez voir les valeurs numériques de chacun.  
  
 **États**  
 Cette colonne du graphique est facultative et peut être affichée ou supprimée en sélectionnant l’option **Afficher la légende** . La colonne **États** fournit un guide indiquant l’état représenté par chacune des couleurs dans l’histogramme de clusters correspondant.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Algorithme Microsoft Sequence Clustering](data-mining/microsoft-sequence-clustering-algorithm.md)   
 [Visionneuses de modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèles d’exploration de données](data-mining/data-mining-model-viewers.md)   
 [Explorer un modèle à l'aide de la visionneuse de l'algorithme MSC (Microsoft Sequence Cluster)](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
  
