---
title: "Supprimer un filtre d&#39;un mod&#232;le d&#39;exploration de donn&#233;es | Microsoft Docs"
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
  - "filtres [Analysis Services]"
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 13
---
# Supprimer un filtre d&#39;un mod&#232;le d&#39;exploration de donn&#233;es
  Lorsque vous créez un filtre sur un modèle d'exploration de données, vous pouvez créer des modèles sur un sous-ensemble des données contenues dans la vue de source de données. Les filtres sont également utiles pour tester la précision du modèle sur un sous-ensemble des données d'origine.  
  
 Toutefois, vous devez supprimer le filtre si vous souhaitez réafficher l'intégralité des cas. Cette procédure décrit comment supprimer des conditions sur un filtre ou supprimer complètement le filtre.  
  
### Pour supprimer une condition d'un filtre sur un modèle d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l'Explorateur de solutions, cliquez sur la structure d'exploration de données qui contient le modèle d'exploration de données à filtrer.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Sélectionnez le modèle et cliquez avec le bouton droit pour ouvrir le menu contextuel.  
  
     - ou -  
  
     Sélectionnez le modèle. Dans le menu **Modèle d'exploration de données** , sélectionnez **Définir le filtre de modèle**.  
  
4.  Dans la boîte de dialogue **Filtre de modèle**, cliquez avec le bouton droit sur la ligne dans la grille qui contient la condition que vous souhaitez supprimer.  
  
5.  Sélectionnez **Supprimer**.  
  
### Pour effacer le filtre sur un modèle d'exploration de données dans la boîte de dialogue Éditeur de filtre  
  
-   Dans la boîte de dialogue **Éditeur de filtre**, cliquez avec le bouton droit sur n’importe quelle ligne de la grille et sélectionnez **Supprimer tout**.  
  
## Utilisation des filtres de modèle à l'aide de la fenêtre Propriétés  
 Si vous souhaitez supprimer le filtre entier, vous n'avez pas besoin d'ouvrir les boîtes de dialogue de l'Éditeur de filtre. Les conditions de filtre que vous avez créées sont disponibles dans la propriété **Filter** du modèle d'exploration de données.  
  
> [!NOTE]  
>  Vous pouvez afficher les propriétés d'un modèle d'exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], mais pas dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Pour effacer le filtre sur un modèle d'exploration de données dans l'Explorateur de solutions  
  
1.  Dans l'Explorateur de solutions, cliquez sur le modèle d'exploration de données qui contient le filtre.  
  
2.  Dans la fenêtre **Propriétés**, cliquez avec le bouton droit sur le texte du filtre de la propriété **Filter**, puis sélectionnez **Sélectionner tout**.  
  
3.  Appuyez sur la touche Retour arrière ou Suppr.  
  
## Voir aussi  
 [Extraire des données de cas à partir d'un modèle d'exploration de données](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)   
 [Tâches du modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  