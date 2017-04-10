---
title: "Ajouter une table (SSAS Tabulaire) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# Ajouter une table (SSAS Tabulaire)
  Cette rubrique explique comment ajouter une table à partir d'une source de données dans laquelle vous avez précédemment importé des données dans votre modèle. Pour ajouter une table à partir de la même source de données, vous pouvez utiliser la connexion à la source de données existante. Il est recommandé d'utiliser toujours une connexion unique lorsque vous importez plusieurs tables à partir d'une source de données unique.  
  
### Pour ajouter une table à partir d'une source de données existante  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Connexions existantes**.  
  
2.  Dans la page **Connexions existantes**, sélectionnez la connexion à la source de données qui contient la table à ajouter, puis cliquez sur **Ouvrir**.  
  
3.  Dans la page **Sélectionner des tables et des vues**, sélectionnez la table à partir de la source de données à ajouter à votre modèle.  
  
    > [!NOTE]  
    >  La page **Sélectionner des tables et des vues** n’affiche pas les tables précédemment importées comme vérifiées.  Si vous sélectionnez une table qui a été précédemment importées au moyen de cette connexion, et si vous ne donnez pas à la table un nom convivial différent, un « 1 » sera ajouté au nom convivial. Vous n'avez pas besoin de resélectionner les tables qui ont été précédemment importées à l'aide de cette connexion.  
  
4.  Si nécessaire, utilisez **Afficher un aperçu et filtrer** pour sélectionner uniquement certaines colonnes ou appliquer des filtres aux données à importer.  
  
5.  Cliquez sur **Terminer** pour importer la nouvelle table.  
  
> [!NOTE]  
>  Lorsque vous importez plusieurs tables simultanément à partir d'une seule source de données, les relations entre ces tables à la source sont automatiquement créées dans le modèle. Si vous ajoutez une table ultérieurement, toutefois, vous devrez peut-être créer manuellement des relations dans le modèle entre les tables récemment ajoutées et les tables précédemment importées.  
  
## Voir aussi  
 [Importer des données &#40;SSAS Tabulaire&#41;](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)   
 [Supprimer une table &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/delete-a-table-ssas-tabular.md)  
  
  