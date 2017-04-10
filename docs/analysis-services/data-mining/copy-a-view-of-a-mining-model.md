---
title: "Copier une vue d&#39;un mod&#232;le d&#39;exploration de donn&#233;es | Microsoft Docs"
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
  - "Presse-papiers [exploration de données]"
  - "visionneuse de modèle d’exploration de données [Analysis Services], Presse-papiers"
  - "copie d'un modèle d'exploration de données vers le Presse-papiers"
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 38
---
# Copier une vue d&#39;un mod&#232;le d&#39;exploration de donn&#233;es
  L’onglet **Visionneuse de modèle d’exploration de données** du Concepteur d’exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise une visionneuse distincte pour chaque type de modèle d’exploration de données. Plusieurs des visionneuses ont des composants à partir desquels vous pouvez copier le contenu vers le Presse-papiers, puis coller le contenu dans un document ou un logiciel de manipulation d'image. Cette fonctionnalité est disponible avec les composants suivants :  
  
-   Diagramme de cluster dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer et la Visionneuse de l'algorithme MSC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster)  
  
-   Arbre de décision dans la Visionneuse d’arborescence [!INCLUDE[msCoName](../../includes/msconame-md.md)] et la Visionneuse de l’algorithme MTS ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series)  
  
-   Transitions d'état dans la Visionneuse de l'algorithme MSC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster)  
  
-   Réseau de dépendances dans la Visionneuse de l'algorithme MAR ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules), la Visionneuse de l'algorithme MNB ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes) et la Visionneuse d'arborescence [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Contenu du modèle d’exploration de données à partir du volet Détails du nœud de la Visionneuse de l’arborescence de contenu générique [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
 Vous pouvez copier la représentation complète du modèle d'exploration de données ou simplement la partie visible dans la visionneuse.  
  
> [!WARNING]  
>  Lorsque vous copiez un modèle à l'aide de la visionneuse, il ne crée pas de nouvel objet de modèle. Pour créer un modèle, vous devez utiliser l'Assistant, ou le Concepteur d'exploration de données. Pour plus d’informations, consultez [Créer une copie d’un modèle d’exploration de données](../../analysis-services/data-mining/make-a-copy-of-a-mining-model.md).  
  
### Pour copier le modèle complet dans le Presse-papiers  
  
1.  Dans la liste **Modèle d’exploration de données** sous l’onglet **Visionneuse de modèle d’exploration de données**, sélectionnez le modèle d’exploration de données à afficher.  
  
2.  Sélectionnez l’onglet approprié, tel que l’onglet **Réseau de dépendances**, puis cliquez sur **Copier le graphique entier** dans la barre d’outils de l’onglet.  
  
### Pour copier la partie visible du modèle vers le Presse-papiers  
  
1.  Dans la liste **Modèle d’exploration de données** sous l’onglet **Visionneuse de modèle d’exploration de données**, sélectionnez le modèle d’exploration de données à afficher.  
  
2.  Sélectionnez l’onglet approprié, tel que l’onglet **Réseau de dépendances**, puis effectuez un zoom avant ou arrière sur le modèle au niveau approprié.  
  
3.  Cliquez sur **Copier la vue du graphique** dans la barre d’outils de l’onglet sélectionné.  
  
### Pour copier le contenu du modèle d'exploration de données dans le Presse-papiers  
  
1.  Dans la liste **Modèle d’exploration de données** sous l’onglet **Visionneuse de modèle d’exploration de données**, sélectionnez le modèle d’exploration de données à afficher.  
  
2.  Dans la liste déroulante **Visionneuse**, sélectionnez **Visionneuse de l’arborescence de contenu générique Microsoft**.  
  
3.  Dans le volet **Légende du nœud (ID unique)**, cliquez sur un nœud.  
  
4.  Cliquez avec le bouton droit sur le volet **Détails du nœud**, puis sélectionnez **Sélectionner tout**.  
  
5.  Cliquez de nouveau avec le bouton droit sur le volet **Détails du nœud**, puis sélectionnez **Copier**.  
  
## Voir aussi  
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  