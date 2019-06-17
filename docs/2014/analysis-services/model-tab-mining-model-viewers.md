---
title: Modèle d’onglet (visionneuses de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.timeseries.decisiontree.f1
ms.assetid: 50570bb4-fcac-411e-b530-0398437efda7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05c0a25ceded07264e4dbe10467e9dc6f093f6c0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66077620"
---
# <a name="model-tab-mining-model-viewers"></a>Onglet Modèle (Visionneuses de modèle d'exploration de données)
  L'onglet **Modèle** dans la visionneuse de l'algorithme MTS affiche une représentation de série chronologique en tant que nœud dans un graphique, comme celles utilisées dans les modèles d'arbre de décision.  
  
 Utilisez cette vue d'un modèle de série chronologique pour extraire des informations utiles sur l'analyse de série chronologique, y compris l'équation pour le graphique, les termes ARIMA et les coefficients.  
  
 **Pour plus d’informations :** [Algorithme de série chronologique de Microsoft](data-mining/microsoft-time-series-algorithm.md), [Explorer un modèle à l’aide de la visionneuse de la série Microsoft Time](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md), [algorithme de série chronologique de Microsoft](data-mining/microsoft-time-series-algorithm.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Sélectionne un modèle d'exploration de données à afficher. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée pour ce type de modèle ou la **visionneuse de l'arborescence de contenu générique Microsoft** . Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Zoom avant**  
 Permet d'effectuer un zoom avant sur le schéma.  
  
 **Effectuer un zoom arrière**  
 Permet d'effectuer un zoom arrière sur le schéma.  
  
 **Copier la vue du graphique**  
 Copie la partie visible du diagramme dans le Presse-papiers.  
  
 **Copier le graphique entier**  
 Copie la totalité du diagramme dans le Presse-papiers.  
  
 **Diagramme de mise à l’échelle à la fenêtre**  
 Réduit la taille du diagramme jusqu'à ce qu'il soit ajusté à l'écran.  
  
 **Arborescence**  
 Sélectionnez dans la liste déroulante une arborescence à afficher dans la visionneuse  
  
 Si le modèle de série chronologique inclut plusieurs séries, chaque série est représentée comme une arborescence distincte. Par exemple, si vous avez créé des prédictions au fil du temps pour [Quantity] et [Sales Amount], une série séparée est créée pour chaque attribut prédictible.  
  
 La longueur de la couleur en surbrillance dans la liste indique le nombre de niveaux dans l'arborescence. Autrement dit, un modèle de série chronologique qui peut être représenté par un seul nœud aurait une seule équation pour décrire la tendance et la barre de couleur serait très courte. (Bien entendu, si le modèle est de type MIXED, le nœud contient à la fois une équation ARTXP et ARIMA.)  
  
 Si l'arborescence affichée dans la liste déroulante comporte une barre de couleur plus longue, cela signifie que le modèle a de nombreuses branches dans l'arborescence. Un branchement indique une régression plus complexe et le modèle doit être divisé en plusieurs segments, avec une équation différente (ou une paire d'équations) dans chaque nœud.  
  
 **Arrière-plan**  
 Utilisez ce contrôle pour sélectionner l'état représenté par la couleur d'arrière-plan de chaque nœud.  
  
 **Expansion par défaut**  
 Ajustez le nombre de niveaux par défaut qui sont affichés pour toutes les arborescences du modèle.  
  
 **Afficher le niveau**  
 Modifiez le nombre de niveaux affichés dans l'arborescence.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
