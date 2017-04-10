---
title: "Modifier la discr&#233;tisation d&#39;une colonne dans un mod&#232;le d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "discrétisation [Analysis Services]"
  - "structures d'exploration de données [Analysis Services], rubriques de procédures"
  - "colonnes discrétisées [exploration de données]"
  - "problèmes de création de compartiments [Analysis Services]"
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 14
---
# Modifier la discr&#233;tisation d&#39;une colonne dans un mod&#232;le d&#39;exploration de donn&#233;es
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] discrétise automatiquement les valeurs, autrement dit, il place les données dans une colonne numérique, dans certains scénarios. Par exemple, si vos données contiennent des données numériques continues et que vous créez un modèle d'arbre de décision, chaque colonne de données continues est intégrée automatiquement, selon la distribution des données. Si vous souhaitez contrôler la discrétisation des données, vous devez modifier les propriétés de la colonne de structure d'exploration de données, qui contrôle l'utilisation des données dans le modèle.  
  
 Pour obtenir des informations générales sur la façon de définir des propriétés dans un modèle d’exploration de données, consultez [Colonnes de modèle d’exploration de données](../../analysis-services/data-mining/mining-model-columns.md).  
  
### Pour afficher les propriétés d'une colonne de modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur l’en-tête de colonne contenant le nom du modèle d’exploration de données ou sur la ligne dans la grille qui contient le nom de l’algorithme d’exploration de données, puis sélectionnez **Propriétés**.  
  
     La fenêtre **Propriétés** affiche les propriétés associées au modèle d'exploration de données dans son ensemble.  
  
2.  Dans la colonne **Structure** près du côté gauche de l'écran, cliquez sur la colonne qui contient les données numériques continues que vous souhaitez discrétiser.  
  
     L'affichage de la fenêtre **Propriétés** se modifie et affiche uniquement les propriétés associées à cette colonne.  
  
### Pour modifier la méthode de discrétisation  
  
1.  Dans la fenêtre **Propriétés d'exploration de données** , cliquez sur la zone de texte en regard de **Contenu**, et sélectionnez **Discretized** dans la liste déroulante.  
  
     Les propriétés <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> et <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> sont maintenant activées.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur la zone de texte en regard de <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> et sélectionnez l’une des valeurs suivantes : **Automatic**, **EqualAreas** ou **Cluster**.  
  
    > [!NOTE]  
    >  Si l’utilisation de la colonne a la valeur **Ignore**, la fenêtre **Propriétés** pour la colonne est vide.  
  
     La nouvelle valeur est appliquée lorsque vous sélectionnez un élément différent dans le concepteur.  
  
3.  Dans la fenêtre **Propriétés**, cliquez sur la zone de texte en regard de <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> et tapez une valeur numérique.  
  
    > [!NOTE]  
    >  Si vous modifiez ces propriétés, la structure doit être traitée à nouveau, avec tous les modèles auxquels s'applique le nouveau paramètre.  
  
## Voir aussi  
 [Tâches du modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  