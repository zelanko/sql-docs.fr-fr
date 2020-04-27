---
title: Réseau neuronal (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.neuralnet.f1
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05654d9206f09d151abd5557d0aa6aae90b1b9ff
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072317"
---
# <a name="neural-network-mining-model-viewer"></a>Neural Network (réseau neuronal) (Visionneuse du modèle d'exploration de données)
  Utilisez la visionneuse **Neural Net** pour consulter les modèles d’exploration de données basés sur l’algorithme MNN ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network) ou l’algorithme MLR ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression).  
  
 **Pour plus d’informations :** [Algorithme MNN (Microsoft Neural Network)](data-mining/microsoft-neural-network-algorithm.md), [Algorithme MLR (Microsoft Logistic Regression)](data-mining/microsoft-logistic-regression-algorithm.md),[Explorer un modèle à l’aide de la visionneuse de l’algorithme MNN (Microsoft Neural Network)](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l'observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données à afficher, parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée ou la **Visionneuse de l'arborescence de contenu générique Microsoft**. Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Input**  
 Utilisez cette zone pour choisir des valeurs et des attributs d'entrée, afin que vous puissiez ultérieurement explorer la manière dont ils affectent les résultats.  
  
|Value|Description|  
|-----------|-----------------|  
|**Attribut**|Choisissez un attribut d'entrée dans la liste. Si vous laissez la sélection comme valeur par défaut, ** \<toutes les>**, le graphique affiche une liste de tous les attributs d’entrée, classés en fonction de leur impact sur l’attribut prévisible.|  
|**Valeur**|Choisissez la valeur de l'attribut d'entrée.|  
  
 **Sortie**  
 Utilisez ces contrôles pour choisir un attribut prédictible et une valeur à analyser et comparer dans le graphique à barres. Si vous ne modifiez pas les sélections, le graphique à barres compare les deux états principaux de résultats.  
  
|Value|Description|  
|-----------|-----------------|  
|**Attribut de sortie**|Choisissez un attribut prédictible. Si vous ne définissez pas la colonne comme prédictible lors de la création du modèle, vous ne pouvez pas l'ajouter ici.|  
|**Valeur 1**|Choisissez l’état de l’attribut prédictible à comparer à l’état contenu dans **Valeur 2**.<br /><br /> Vous pouvez comparer deux valeurs discrètes ou discrétisées ; toutefois, vous ne pouvez pas comparer une valeur à son complément, comme c'est le cas dans d'autres visionneuses.|  
|**Valeur 2**|Choisissez l’état de l’attribut prédictible à comparer à l’état contenu dans **Valeur 1**.|  
  
 **Variables**  
 Cette partie de l’onglet **Réseau neuronal** contient un histogramme interactif, qui répond aux sélections que vous avez effectuées pour les attributs d’entrée et de résultat. Étant donné qu'un réseau neuronal calcule la probabilité qu'une valeur particulière influence un résultat particulier, vous pouvez choisir n'importe quelle combinaison d'entrées ; le graphique à barres affiche la manière dont cette combinaison affecte la paire de résultats que vous comparez.  
  
|Value|Description|  
|-----------|-----------------|  
|**Attribut**|Affiche le nom de l’attribut d’entrée que vous avez sélectionné dans **Attribut**.|  
|**Valeur**|Affiche la valeur de l'attribut d'entrée sélectionné.|  
|**Privilégie \<la valeur 1>**|Affiche une barre indiquant dans quelle proportion cette combinaison particulière attribut-valeur affecte les résultats cibles sélectionnés dans **Valeur 1**.|  
|**Privilégie \<la valeur 2>**|Affiche une barre indiquant dans quelle proportion cette combinaison particulière attribut-valeur affecte les résultats cibles sélectionnés dans **Valeur 2**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
