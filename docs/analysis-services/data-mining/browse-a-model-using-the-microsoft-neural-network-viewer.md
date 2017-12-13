---
title: "Parcourir un modèle à l’aide de la visionneuse de réseau neuronal de Microsoft | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining model content, viewing
- classification mining model [Analysis Services]
- Microsoft Neural Network Viewer
- regression algorithms [Analysis Services]
- Neural Network Viewer [Analysis Services]
- neural network model [Analysis Services]
ms.assetid: 2343d746-c4f4-499b-9d3c-17d63310a9a3
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bf3960aa4308b921cb0c9da01ddfdb1bb52e6f0d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="browse-a-model-using-the-microsoft-neural-network-viewer"></a>Explorer un modèle à l'aide de la visionneuse de l'algorithme MNN (Microsoft Neural Network)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] visionneuse de réseau neuronal dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] affiche les modèles d’exploration de données qui sont générés avec le [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithme de réseau neuronal. L'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) crée des modèles d'exploration de données de classification et de régression qui peuvent analyser plusieurs entrées et sorties, et est très utile pour les analyses et l'exploration de durée indéterminée. Pour plus d'informations sur cet algorithme, consultez [Microsoft Neural Network Algorithm](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md).  
  
 Lorsque vous explorez un modèle à l'aide de la Visionneuse de l'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network), vous choisissez généralement des attributs et des états cibles, puis vous utilisez la visionneuse pour voir comment les attributs d'entrée affectent le résultat  
  
 Par exemple, supposons que vous connaissez ces faits relatifs à une classe de clients potentiels :  
  
-   Âge moyen (40 à 50 ans).  
  
-   Propriétaire d'une maison.  
  
-   Deux enfants encore à charge.  
  
 Comment pouvez-vous mettre en corrélation ces attributs avec la probabilité que le client effectue un achat ?  
  
 Lors de la création d'un modèle de réseau neuronal à l'aide du comportement d'achat comme résultat cible, vous pouvez explorer plusieurs combinaisons sur les attributs de client, tels que les revenus élevés, et découvrir quelle combinaison d'attributs est la plus susceptible d'influencer le comportement d'achat. Par exemple, vous pouvez découvrir que le facteur déterminant est la distance domicile-travail.  
  
 Si vous avez besoin d'informations plus détaillées, telles que les équations qui représentent chaque modèle qui a été découvert, vous pouvez basculer les vues et utiliser la visionneuse de l'arborescence de contenu générique [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) ou [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c).  
  
##  <a name="BKMK_ViewerTabs"></a> Onglets de la visionneuse  
 Lorsque vous parcourez un modèle d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le modèle s'affiche sous l'onglet **Visionneuse de modèle d'exploration de données** du Concepteur d'exploration de données, à l'aide de la visionneuse appropriée pour ce modèle. La Visionneuse de l'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) fournit les onglets suivants pour explorer les modèles d'exploration de données de réseau neuronal :  
  
-   [Entrées](#BKMK_Inputs)  
  
-   [Sorties](#BKMK_Outputs)  
  
-   [Variables](#BKMK_Characteristics)  
  
###  <a name="BKMK_Inputs"></a> Entrées  
 Utilisez l’onglet **Entrées** pour choisir les attributs et les valeurs que le modèle a utilisé comme entrées. Par défaut, la visionneuse s'ouvre avec tous les attributs inclus. Dans cette vue par défaut, le modèle choisit les valeurs d'attribut les plus importantes pour l'affichage.  
  
 Pour sélectionner un attribut d’entrée, cliquez à l’intérieur de la colonne **Attribut** de la grille **Entrée** et sélectionnez un attribut dans la liste déroulante. (Seuls les attributs figurant dans le modèle sont inclus dans la liste.)  
  
 La première valeur distincte apparaît sous la colonne **Valeur** . En cliquant sur la valeur par défaut, vous affichez une liste contenant tous les états possibles de l'attribut associé. Vous pouvez sélectionner l'état que vous voulez analyser. Vous pouvez sélectionner autant d'attributs que vous le souhaitez.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Outputs"></a> Sorties  
 Utilisez l’onglet **Sorties** pour choisir l’attribut de résultats à étudier. Vous pouvez choisir deux états quelconques de résultats à comparer, en supposant que les colonnes ont été définies comme attributs prédictibles lorsque le modèle a été créé.  
  
 Utilisez la liste **Attribut de sortie** pour sélectionner un attribut. Vous pouvez ensuite sélectionner deux états qui sont associés à l’attribut dans les listes **Valeur 1** et **Valeur 2** . Ces deux états de l’attribut de sortie seront comparés dans le volet **Variables** .  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> Variables  
 La grille sous l’onglet **Variables** contient les colonnes suivantes : **Attribut**, **Valeur**, **Privilèges [Valeur 1]**et **Privilèges [Valeur 2]**. Par défaut, les colonnes sont triées en fonction de la valeur de **Privilèges [Valeur 1]**. En cliquant sur un en-tête de colonne, vous modifiez l'ordre de tri de la colonne sélectionnée.  
  
 Une barre à droite de l'attribut indique quel état de l'attribut de sortie est privilégié par l'état d'attribut d'entrée spécifié. La taille de la barre indique à quel degré l'état de sortie favorise l'état d'entrée.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft Neural Network Algorithm](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Outils d'exploration de données](../../analysis-services/data-mining/data-mining-tools.md)   
 [Visionneuses de modèle d’exploration de données](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
