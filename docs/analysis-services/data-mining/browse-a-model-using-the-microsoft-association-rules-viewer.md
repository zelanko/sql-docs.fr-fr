---
title: "Explorer un mod&#232;le &#224; l&#39;aide de la visionneuse de l&#39;algorithme MAR (Microsoft Association Rules) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "jeux d'éléments [Analysis Services]"
  - "modèles d'exploration de données [Analysis Services], associations"
  - "contenu du modèle d'exploration de données, affichage"
  - "règles [Exploration de données]"
  - "visionneuse de l'algorithme MAR (Microsoft Association Rules) [Analysis Services]"
  - "analyse du panier d'achats [Analysis Services]"
  - "associations [Analysis Services]"
  - "visionneuse de l'algorithme MAR (Microsoft Association Rules)"
  - "dépendances [Analysis Services]"
ms.assetid: 538fc01b-8eb1-467a-9b66-3cd57cf7489f
caps.latest.revision: 39
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 39
---
# Explorer un mod&#232;le &#224; l&#39;aide de la visionneuse de l&#39;algorithme MAR (Microsoft Association Rules)
  La Visionneuse de l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] affiche les modèles d'exploration de données qui sont générés avec l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules). L'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules) est un algorithme d'association conçu pour la création de modèles d'exploration de données permettant d'effectuer des analyses de panier d'achat. Pour plus d'informations sur cet algorithme, consultez [Microsoft Association Algorithm](../../analysis-services/data-mining/microsoft-association-algorithm.md).  
  
 Voici les principales raisons pour lesquelles vous utilisez l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules) :  
  
-   pour rechercher des jeux d'éléments décrivant des éléments qui se trouvent généralement ensemble dans une transaction ;  
  
-   Pour découvrir les règles prédisant la présence d'autres éléments dans une transaction en fonction d'éléments existants  
  
> [!NOTE]  
>  La visionneuse de l'arborescence de contenu générique [!INCLUDE[msCoName](../../includes/msconame-md.md)] permet de consulter des informations détaillées relatives aux équations utilisées dans le modèle et les motifs découverts. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) ou [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](../Topic/Microsoft%20Generic%20Content%20Tree%20Viewer%20\(Data%20Mining\).md).  
  
 Pour plus d’informations sur la création, l’exploration et l’utilisation d’un modèle d’exploration de données Association, consultez [Leçon 3 : Génération d’un scénario de panier d’achat &#40;Didacticiel d’exploration de données intermédiaire&#41;](../Topic/Lesson%203:%20Building%20a%20Market%20Basket%20Scenario%20\(Intermediate%20Data%20Mining%20Tutorial\).md).  
  
##  <a name="BKMK_ViewerTabs"></a> Onglets de la visionneuse  
 Lorsque vous parcourez un modèle d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le modèle s'affiche sous l'onglet **Visionneuse de modèle d'exploration de données** du Concepteur d'exploration de données, à l'aide de la visionneuse appropriée pour ce modèle. La Visionneuse de l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules) contient les onglets suivants :  
  
-   [Jeux d'éléments](#BKMK_Itemsets)  
  
-   [Règles](#BKMK_Rules)  
  
-   [Réseau de dépendances](#BKMK_Dependency)  
  
 Chaque onglet contient la case à cocher **Afficher le nom long** qui vous permet d'afficher ou de masquer, dans la règle ou le jeu d'éléments, la table d'où provient le jeu d'éléments.  
  
###  <a name="BKMK_Itemsets"></a> Jeux d'éléments  
 L'onglet **Jeux d'éléments** affiche la liste des jeux d'éléments que le modèle a identifiés comme apparaissant fréquemment ensemble. L'onglet contient une grille comportant les colonnes suivantes : **Prise en charge**, **Taille**et **Jeu d'éléments**. Pour plus d'informations sur la prise en charge, consultez [Microsoft Association Algorithm](../../analysis-services/data-mining/microsoft-association-algorithm.md). La colonne **Taille** affiche le nombre d'éléments présents dans le jeu d'éléments. La colonne **Jeu d'éléments** affiche le jeu d'éléments actuel que le modèle a découvert. Vous pouvez contrôler le format du jeu d'éléments à l'aide de la liste **Afficher** , en choisissant parmi les options suivantes :  
  
-   **Afficher le nom et la valeur de l'attribut**  
  
-   **Afficher la valeur de l'attribut uniquement**  
  
-   **Afficher le nom de l'attribut uniquement**  
  
 Vous pouvez filtrer le nombre de jeux d'éléments affichés sous cet onglet en utilisant **Prise en charge minimale** et **Taille minimale du jeu d'éléments**. Vous pouvez limiter encore plus le nombre de jeux d'éléments affichés à l'aide de **Filtrer le jeu d'éléments** en définissant une caractéristique de jeu d'éléments qui doit exister. Par exemple, si vous tapez « Water Bottle = existing », vous limitez les jeux d'éléments à ceux qui contiennent une bouteille d'eau. L'option **Filtrer le jeu d'éléments** affiche également une liste des filtres que vous avez utilisés précédemment.  
  
 Vous pouvez trier les lignes de la grille en cliquant sur un en-tête de colonne.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a> Règles  
 L'onglet **Règles** affiche les règles découvertes par l'algorithme d'association. L'onglet **Règles** comprend une grille qui contient les colonnes suivantes : **Probabilité**, **Importance**et **Règle**. La probabilité indique la probabilité du résultat d'une règle. L'importance sert à mesurer l'utilité d'une règle. Même si la probabilité d'une règle est élevée, son utilité peut être sans importance. La colonne Importance permet de préciser ce point. Par exemple, si tous les jeux d'éléments contiennent un état spécifique d'un attribut, une règle prédisant l'état est insignifiante même si sa probabilité est très élevée. Plus l'importance est élevée, plus la règle est importante.  
  
 Vous pouvez utiliser les options **Probabilité minimale** et **Importance minimale** pour effectuer un filtrage des règles, similaire au filtrage que vous pouvez effectuer sous l'onglet **Jeux d'éléments** . Vous pouvez également utiliser **Filtrer la règle** pour filtrer une règle en fonction des états d'attribut qu'elle contient.  
  
 Vous pouvez trier les lignes de la grille en cliquant sur un en-tête de colonne.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a> Réseau de dépendances  
 L'onglet **Réseau de dépendances** contient une visionneuse du réseau de dépendances. Chaque nœud figurant dans la visionneuse représente un élément, par exemple « state = WA ». La flèche entre les nœuds représente l'association entre les éléments. Le sens de la flèche détermine l'association entre les éléments conformément aux règles découvertes par l'algorithme. Par exemple, si la visionneuse contient les trois éléments A, B et C, et que C est prédit par A et B, lorsque vous sélectionnez le nœud C, deux flèches pointent vers ce nœud : A vers C et B vers C.  
  
 Le curseur situé à gauche de la visionneuse agit comme un filtre lié à la probabilité des règles. Si vous déplacez le curseur vers le bas, seuls les liens les plus forts sont affichés.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
## Voir aussi  
 [Algorithme Microsoft Association](../../analysis-services/data-mining/microsoft-association-algorithm.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Outils d'exploration de données](../../analysis-services/data-mining/data-mining-tools.md)   
 [Visionneuses de modèle d’exploration de données](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  