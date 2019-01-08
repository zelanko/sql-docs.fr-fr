---
title: Explorer un modèle à l’aide de la visionneuse de règles d’Association de Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- mining models [Analysis Services], associations
- mining model content, viewing
- rules [Data Mining]
- Association Rules Viewer [Analysis Services]
- market basket analysis [Analysis Services]
- associations [Analysis Services]
- Microsoft Association Rules Viewer
- dependencies [Analysis Services]
ms.assetid: 538fc01b-8eb1-467a-9b66-3cd57cf7489f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 25fa0df8f0e3575b8767020721b56b4a19ac529d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538803"
---
# <a name="browse-a-model-using-the-microsoft-association-rules-viewer"></a>Explorer un modèle à l'aide de la visionneuse de l'algorithme MAR (Microsoft Association Rules)
  La Visionneuse de l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] affiche les modèles d'exploration de données qui sont générés avec l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules). L'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules) est un algorithme d'association conçu pour la création de modèles d'exploration de données permettant d'effectuer des analyses de panier d'achat. Pour plus d'informations sur cet algorithme, consultez [Microsoft Association Algorithm](microsoft-association-algorithm.md).  
  
 Voici les principales raisons pour lesquelles vous utilisez l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules) :  
  
-   pour rechercher des jeux d'éléments décrivant des éléments qui se trouvent généralement ensemble dans une transaction ;  
  
-   Pour découvrir les règles prédisant la présence d'autres éléments dans une transaction en fonction d'éléments existants  
  
> [!NOTE]  
>  La visionneuse de l'arborescence de contenu générique [!INCLUDE[msCoName](../../includes/msconame-md.md)] permet de consulter des informations détaillées relatives aux équations utilisées dans le modèle et les motifs découverts. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) ou [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).  
  
 Pour une procédure pas à pas montrant comment créer, Explorer et utiliser un modèle d’exploration de données d’association, consultez [leçon 3 : Génération d’un scénario de panier &#40;didacticiel d’exploration de données intermédiaire&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).  
  
##  <a name="BKMK_ViewerTabs"></a> Onglets de la visionneuse  
 Lorsque vous parcourez un modèle d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le modèle s'affiche sous l'onglet **Visionneuse de modèle d'exploration de données** du Concepteur d'exploration de données, à l'aide de la visionneuse appropriée pour ce modèle. La Visionneuse de l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules) contient les onglets suivants :  
  
-   [Jeux d'éléments](#BKMK_Itemsets)  
  
-   [Règles](#BKMK_Rules)  
  
-   [Réseau de dépendances](#BKMK_Dependency)  
  
 Chaque onglet contient la case à cocher **Afficher le nom long** qui vous permet d'afficher ou de masquer, dans la règle ou le jeu d'éléments, la table d'où provient le jeu d'éléments.  
  
###  <a name="BKMK_Itemsets"></a> Jeux d'éléments  
 L'onglet **Jeux d'éléments** affiche la liste des jeux d'éléments que le modèle a identifiés comme apparaissant fréquemment ensemble. L'onglet contient une grille comportant les colonnes suivantes : **Prise en charge**, **taille**, et **jeu d’éléments**. Pour plus d'informations sur la prise en charge, consultez [Microsoft Association Algorithm](microsoft-association-algorithm.md). La colonne **Taille** affiche le nombre d'éléments présents dans le jeu d'éléments. La colonne **Jeu d'éléments** affiche le jeu d'éléments actuel que le modèle a découvert. Vous pouvez contrôler le format du jeu d'éléments à l'aide de la liste **Afficher** , en choisissant parmi les options suivantes :  
  
-   **Afficher le nom et la valeur de l'attribut**  
  
-   **Afficher la valeur de l'attribut uniquement**  
  
-   **Afficher le nom de l'attribut uniquement**  
  
 Vous pouvez filtrer le nombre de jeux d'éléments affichés sous cet onglet en utilisant **Prise en charge minimale** et **Taille minimale du jeu d'éléments**. Vous pouvez limiter encore plus le nombre de jeux d'éléments affichés à l'aide de **Filtrer le jeu d'éléments** en définissant une caractéristique de jeu d'éléments qui doit exister. Par exemple, si vous tapez « Water Bottle = existing », vous limitez les jeux d'éléments à ceux qui contiennent une bouteille d'eau. L'option **Filtrer le jeu d'éléments** affiche également une liste des filtres que vous avez utilisés précédemment.  
  
 Vous pouvez trier les lignes de la grille en cliquant sur un en-tête de colonne.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a> Règles  
 L'onglet **Règles** affiche les règles découvertes par l'algorithme d'association. Le **règles** onglet comprend une grille qui contient les colonnes suivantes : **Probabilité**, **Importance**, et **règle**. La probabilité indique la probabilité du résultat d'une règle. L'importance sert à mesurer l'utilité d'une règle. Même si la probabilité d'une règle est élevée, son utilité peut être sans importance. La colonne Importance permet de préciser ce point. Par exemple, si tous les jeux d'éléments contiennent un état spécifique d'un attribut, une règle prédisant l'état est insignifiante même si sa probabilité est très élevée. Plus l'importance est élevée, plus la règle est importante.  
  
 Vous pouvez utiliser les options **Probabilité minimale** et **Importance minimale** pour effectuer un filtrage des règles, similaire au filtrage que vous pouvez effectuer sous l'onglet **Jeux d'éléments** . Vous pouvez également utiliser **Filtrer la règle** pour filtrer une règle en fonction des états d'attribut qu'elle contient.  
  
 Vous pouvez trier les lignes de la grille en cliquant sur un en-tête de colonne.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a> Réseau de dépendances  
 L'onglet **Réseau de dépendances** contient une visionneuse du réseau de dépendances. Chaque nœud figurant dans la visionneuse représente un élément, par exemple « state = WA ». La flèche entre les nœuds représente l'association entre les éléments. Le sens de la flèche détermine l'association entre les éléments conformément aux règles découvertes par l'algorithme. Par exemple, si la visionneuse contient les trois éléments A, B et C et C sont prédit par A et B, si vous sélectionnez le nœud C, deux flèches pointent vers le nœud C - A à C et B à C.  
  
 Le curseur situé à gauche de la visionneuse agit comme un filtre lié à la probabilité des règles. Si vous déplacez le curseur vers le bas, seuls les liens les plus forts sont affichés.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft Association Algorithm](microsoft-association-algorithm.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](mining-model-viewer-tasks-and-how-tos.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](mining-model-viewer-tasks-and-how-tos.md)   
 [Outils d'exploration de données](data-mining-tools.md)   
 [Visionneuses de modèle d’exploration de données](data-mining-model-viewers.md)  
  
  
