---
title: "Explorer un mod&#232;le &#224; l&#39;aide de Microsoft Sequence Cluster | Microsoft Docs"
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
  - "clusters [Analysis Services]"
  - "discrimination [Analysis Services]"
  - "noms [Analysis Services], clusters"
  - "Microsoft Cluster Viewer"
  - "contenu du modèle d'exploration de données, affichage"
  - "comparaison de clusters"
  - "visualisation des clusters"
  - "affichage des clusters"
  - "exploration de données [Analysis Services], clusters"
  - "Cluster Viewer [Analysis Services]"
  - "modèles d’exploration de données [Analysis Services], clusters"
ms.assetid: 591fe30b-d88f-4a71-94d4-4a3907fc275d
caps.latest.revision: 42
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 42
---
# Explorer un mod&#232;le &#224; l&#39;aide de Microsoft Sequence Cluster
  Le composant [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] affiche les modèles d'exploration de données qui sont générés à l'aide de l'algorithme MC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering). L'algorithme MC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering) est un algorithme de segmentation conçu pour explorer les données afin d'identifier d'éventuelles anomalies et de créer des prédictions. Pour plus d’informations sur cet algorithme, consultez [Microsoft Clustering Algorithm](../../analysis-services/data-mining/microsoft-clustering-algorithm.md).  
  
> [!NOTE]  
>  La visionneuse de l'arborescence de contenu générique [!INCLUDE[msCoName](../../includes/msconame-md.md)] permet de consulter des informations détaillées relatives aux équations utilisées dans le modèle et les motifs découverts. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) ou [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](../Topic/Microsoft%20Generic%20Content%20Tree%20Viewer%20\(Data%20Mining\).md).  
  
##  <a name="BKMK_ViewerTabs"></a> Onglets de la visionneuse  
 Lorsque vous parcourez un modèle d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le modèle s'affiche sous l'onglet **Visionneuse de modèle d'exploration de données** du Concepteur d'exploration de données, à l'aide de la visionneuse appropriée pour ce modèle. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer fournit les onglets suivants pour explorer les modèles d'exploration de données de clustering :  
  
-   [Diagramme de cluster](#BKMK_Diagram)  
  
-   [Profils du cluster](#BKMK_Profile)  
  
-   [Caractéristiques du cluster](#BKMK_Characteristics)  
  
-   [Discrimination de cluster](#BKMK_Discrimination)  
  
###  <a name="BKMK_Diagram"></a> Diagramme de cluster  
 L'onglet **Diagramme de cluster** du composant [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer affiche tous les clusters se trouvant dans un modèle d'exploration de données. L'ombrage de la ligne reliant un cluster à un autre représente le niveau de similarité des clusters. Si l'ombrage est clair ou inexistant, les clusters ne sont pas très similaires. Plus la ligne est sombre, plus la similarité des liens est grande. Vous pouvez modifier le nombre de lignes affichées par la visionneuse à l'aide du curseur situé à droite des clusters. Si vous déplacez le curseur vers le bas, seuls les liens les plus forts sont affichés.  
  
 Par défaut, l'ombre représente le remplissage du cluster. À l’aide des options **Variable d’ombrage** et **État**, vous pouvez sélectionner la paire attribut-état que l’ombrage représente. Plus l'ombrage est sombre, plus la distribution d'attribut est grande pour un état spécifique. Inversement, plus l'ombrage est clair, plus la distribution diminue.  
  
 Pour renommer un cluster, cliquez avec le bouton droit sur son nœud et sélectionnez **Renommer le cluster**. Le nouveau nom est enregistré sur le serveur.  
  
 Pour copier la partie visible du diagramme dans le Presse-papiers, cliquez sur **Copier la vue du graphique**. Pour copier l'intégralité du diagramme, cliquez sur **Copier le graphique entier**. Vous pouvez également faire un zoom avant et arrière à l'aide des boutons **Zoom avant** et **Zoom arrière**ou vous pouvez ajuster le diagramme à la taille de l'écran à l'aide de **Ajuster le diagramme à la fenêtre**.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Profile"></a> Profils du cluster  
 L'onglet **Profils du cluster** fournit une vue d'ensemble des clusters créés par l'algorithme de votre modèle. Cette vue montre chaque attribut ainsi que la distribution de l'attribut dans chaque cluster. Une info-bulle pour chaque cellule affiche les statistiques de distribution et une info-bulle pour chaque en-tête de colonne affiche le remplissage du cluster. Les attributs discrets sont représentés sous la forme de barres de couleur tandis que les attributs continus prennent la forme d'un graphique en losange qui représente l'écart type et moyen dans chaque cluster. L’option **Barres de l’histogramme** contrôle le nombre de barres qui sont visibles dans l’histogramme. Si le nombre réel de barres est supérieur au nombre de barres à afficher, les barres les plus importantes sont conservées et le reste des barres est regroupé dans un compartiment gris.  
  
 Vous pouvez modifier le nom par défaut des clusters afin de définir des noms plus descriptifs. Pour renommer un cluster, cliquez avec le bouton droit sur son en-tête de colonne et sélectionnez **Renommer le cluster**. Vous pouvez également masquer les clusters en sélectionnant **Masquer la colonne**.  
  
 Pour ouvrir une fenêtre qui offre une vue plus détaillée et plus grande des clusters, double-cliquez sur une cellule de la colonne **États** ou sur un histogramme dans la visionneuse.  
  
 Cliquez sur un en-tête de colonne pour trier les attributs par ordre d'importance pour ce cluster. Vous pouvez également faire glisser les colonnes pour les réorganiser dans la visionneuse.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> Caractéristiques du cluster  
 Pour utiliser l’onglet **Caractéristiques du cluster** , sélectionnez un cluster dans la liste **Cluster** . Après avoir sélectionné un cluster, vous pouvez examiner les caractéristiques qui composent ce cluster spécifique. Les attributs contenus dans le cluster sont répertoriés dans les colonnes **Variables** et l'état de l'attribut répertorié est répertorié dans la colonne **Valeurs** . Les états d'attribut apparaissent par ordre d'importance, en fonction de leur probabilité d'apparition dans le cluster. La probabilité est indiquée dans la colonne **Probabilité** .  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Discrimination"></a> Discrimination de cluster  
 Vous pouvez utiliser l'onglet **Discrimination de cluster** pour comparer les attributs entre deux clusters. Utilisez les listes **Cluster 1** et **Cluster 2** pour sélectionner les clusters à comparer. La visionneuse détermine les différences les plus importantes entre les clusters et affiche, par ordre d'importance, les états d'attribut associés à ces différences. Une barre à droite de l'attribut indique quel cluster est privilégié par l'état et la taille de la barre indique à quel point l'état privilégie le cluster.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
## Voir aussi  
 [Algorithme de gestion de clusters Microsoft](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Outils d'exploration de données](../../analysis-services/data-mining/data-mining-tools.md)   
 [Visionneuses de modèle d’exploration de données](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  