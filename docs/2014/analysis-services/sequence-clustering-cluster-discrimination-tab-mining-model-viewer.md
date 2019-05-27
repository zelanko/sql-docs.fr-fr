---
title: Sequence Clustering onglet Discrimination de Cluster (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.discrimination.f1
ms.assetid: 7dd16479-2633-4f4b-83bf-cf55972a2241
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 914629fca09d4bcffb5ac931316331bbb7e7eebe
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66069134"
---
# <a name="sequence-clustering-cluster-discrimination-tab-mining-model-viewer"></a>Onglet Discrimination de cluster du modèle Sequence Clustering (Visionneuse de modèle d'exploration de données)
  L’onglet **Discrimination de cluster** de la **Visionneuse de l’algorithme MSC** (Microsoft Sequence Clustering) compare les clusters sélectionnés à partir d’un modèle Sequence Clustering.  
  
 Utilisez cette vue d'un modèle Sequence Clustering pour comparer deux clusters et déterminer les états et les transitions qui sont différents.  
  
 **Pour plus d’informations :** [Algorithme Microsoft Sequence Clustering](data-mining/microsoft-sequence-clustering-algorithm.md), [Explorer un modèle à l’aide de la séquence de Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données pour afficher le contenu de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour consulter le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée ou la **Visionneuse de l'arborescence de contenu générique Microsoft**. Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Cluster 1**  
 Sélectionnez un cluster parmi ceux du modèle.  
  
 **Cluster 2**  
 Sélectionnez un deuxième cluster dans le modèle d’exploration des données pour le comparer au **Cluster 1**.  
  
 Si vous ne sélectionnez pas un autre cluster, par défaut le cluster sélectionné est comparé à son complément, ce qui correspond à tous les cas du modèle qui ne figurent pas dans le cluster 1.  
  
 **Scores de discrimination pour \<cluster 1 > et \<cluster 2 >**  
 Ce graphique fournit la comparaison détaillée des clusters que vous avez sélectionnés. En général, un modèle de clustering affecte rarement des états ou des valeurs exclusivement à un seul cluster. Par conséquent, la visionneuse indique uniquement qu’un attribut ou un état particulier *privilégie* un cluster particulier.  
  
 De façon générale, un cluster particulier peut contenir plusieurs états : par exemple, un état courant peut être l'achat d'une bouteille d'eau et d'un porte-bidon, dans l'ordre. Toutefois, la séquence peut être présente dans d'autres clusters qui ont des caractéristiques de définition plus importantes. Par exemple, un autre cluster peut être caractérisé de manière plus importante par des temps de transaction très courts, et une analyse indiquerait que les éléments « bouteille d'eau » et « porte-bidon » sont positionnés de manière à pouvoir généralement, mais pas systématiquement, être regroupés dans ce cluster.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variables**|Attribut du modèle d'exploration de données.|  
|**Valeurs**|État de l’attribut répertorié dans **Variables**.|  
|**Privilégie \<cluster 1 >**|Contient une barre ombragée qui indique dans quelle proportion l’attribut et l’état répertoriés dans **Variables** et **Valeur** privilégient le cluster sélectionné dans **Cluster 1**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
