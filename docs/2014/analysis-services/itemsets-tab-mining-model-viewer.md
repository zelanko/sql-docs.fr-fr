---
title: Onglet jeux d’éléments (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.itemsets.f1
ms.assetid: 95b2b805-b142-4064-9c80-4b1b3fe2fe63
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b34031f0554fd9743ba036c9ce0f1bebe2c3d44d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66079557"
---
# <a name="itemsets-tab-mining-model-viewer"></a>Onglet Jeux d'éléments (Visionneuse de modèle d'exploration de données)
  Vous pouvez utiliser le volet **Jeux d’éléments** pour afficher les jeux d’éléments fréquents contenus dans un modèle d’exploration de données de règles d’association. Étant donné qu'un modèle d'association peut contenir un grand nombre de jeux d'éléments, des contrôles sont fournis dans la visionneuse pour vous aider à filtrer les jeux d'éléments affichés dans la visionneuse.  
  
 **Pour plus d’informations :** [Algorithme Microsoft Association](data-mining/microsoft-association-algorithm.md), [Explorer un modèle à l’aide de la visionneuse de règles Microsoft Association](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données pour afficher le contenu de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour afficher le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée pour les modèles d'association ou la visionneuse de l'arborescence de contenu générique [!INCLUDE[msCoName](../includes/msconame-md.md)] . Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Prise en charge minimale**  
 Modifiez cette valeur pour définir la prise en charge minimale que doit contenir un jeu d'éléments pour être affiché dans la visionneuse. La valeur par défaut affichée à l'ouverture du modèle est calculée par le modèle, mais vous pouvez la modifier pour afficher plus ou moins de jeux d'éléments.  
  
 **Taille minimale de jeu d’éléments**  
 Modifiez cette valeur pour définir le nombre minimal d'éléments qui doivent être inclus dans un jeu d'éléments avant que ce dernier puisse être affiché dans la visionneuse.  
  
 **Filtrer le jeu d’éléments**  
 Tapez une valeur de chaîne pour filtrer le nombre de jeux d'éléments affichés dans la visionneuse.  
  
 Vous pouvez également taper des expressions régulières .NET comme critères de filtre. Par exemple, l'expression suivante retourne tous les jeux d'éléments qui contiennent « Road Bottle Cage » :  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*`  
  
 Notez que vous devrez peut-être actualiser la vue pour voir les critères de filtre appliqués. Vous pouvez également activer et désactiver l'option **Afficher le nom long** afin d'actualiser la liste.  
  
 Par défaut, les critères de filtre s'appliquent au nom complet de la combinaison attribut-valeur ; par conséquent, si vous affichez le nom de l'attribut uniquement, il n'est pas évident de savoir si les critères de filtre ont été appliqués correctement. Utilisez la liste déroulante **Afficher** pour sélectionner **Afficher le nom et la valeur de l'attribut**et vérifiez que la liste des jeux d'éléments est filtrée correctement.  
  
 **Afficher**  
 Ajustez le mode d'affichage du jeu d'éléments dans la visionneuse. Vous pouvez sélectionner l'une des trois options suivantes :  
  
-   Afficher le nom et la valeur de l'attribut  
  
-   Afficher la valeur de l'attribut uniquement  
  
-   Afficher le nom de l'attribut uniquement  
  
 Notez que cette option n'interroge pas de nouveau le modèle ; elle filtre uniquement les attributs ou les valeurs qui sont affichés.  
  
 **Afficher le nom long**  
 Sélectionnez cette option pour afficher le nom complet du jeu d'éléments tel qu'il apparaît dans le contenu du modèle d'exploration de données.  
  
 **Nombre maximal de lignes**  
 Limitez le nombre de jeux d'éléments affichés dans la visionneuse. Par défaut, les jeux d'éléments sont classés selon la prise en charge, par ordre décroissant ; une valeur plus faible limite ainsi la liste aux jeux d'éléments les plus courants.  
  
 **Prise en charge**  
 Affiche la prise en charge de chaque jeu d'éléments.  
  
 **Taille**  
 Affiche le nombre d'éléments présents dans chaque jeu d'éléments.  
  
 **Itemset**  
 Affiche la description de chaque jeu d'éléments. Par défaut, les jeux d'éléments sont présentés sous forme de liste d'attributs et de leurs valeurs séparés par des virgules. Vous pouvez modifier la façon dont ils sont affichés à l’aide de l’option **Afficher** .  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
