---
title: Onglet Profils du cluster (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.profiles.f1
ms.assetid: 1ebafa1f-74e9-4c05-b278-a690fa8543bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ebed4b2b7cc5c6496ab0c681450897a477e4707a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087869"
---
# <a name="cluster-profiles-tab-mining-model-viewer"></a>Onglet Profils du cluster (Visionneuse de modèle d'exploration de données)
  Utilisez l’onglet **Profils du cluster** pour obtenir une vue globale des clusters détectés par l’algorithme au sein d’un modèle de clustering. L'onglet affiche chaque attribut, accompagné de sa répartition dans chaque cluster.  
  
 **Pour plus d’informations :** [algorithme de clustering Microsoft](data-mining/microsoft-clustering-algorithm.md), [Parcourir un modèle à l’aide de Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l'observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d’exploration de données**  
 Choisissez un modèle d'exploration de données parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour afficher le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée pour le modèle d'exploration de données, ou la visionneuse de contenu d'exploration de données ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer). Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Afficher la légende**  
 Sélectionnez cette option pour afficher une clé qui indique le mappage de couleurs dans la visionneuse aux valeurs de la colonne **États** .  
  
 **Barres de l'histogramme**  
 Modifiez cette valeur pour contrôler le nombre d'états inclus dans chaque histogramme. S’il existe davantage d’états que le nombre que vous choisissez d’afficher, les états avec la plus grande probabilité sont affichés dans l’histogramme et les états restants sont regroupés dans **Autre**.  
  
 **Attributs**  
 Répertorie les colonnes figurant dans le modèle de clustering. Les histogrammes de chaque attribut montrent la manière dont l'attribut est distribué entre les clusters identifiés par l'algorithme.  
  
 **États**  
 Fournit une clé qui indique quelle couleur représente chaque état dans la ligne correspondante de clusters, ou un curseur avec un losange qui indique la distribution des valeurs numériques continues. Vous pouvez afficher ou masquer cette colonne en utilisant la case à cocher **Afficher la légende** .  
  
 **Profils de cluster**  
 Cette section contient une colonne pour chaque cluster du modèle. Pour chaque attribut, l'histogramme affiche la distribution des valeurs de l'attribut uniquement pour ce cluster. Le graphique contient également une colonne pour **Remplissage**, qui utilise également les histogrammes pour afficher la distribution des valeurs pour chaque attribut, mais pour tous les cas du modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
