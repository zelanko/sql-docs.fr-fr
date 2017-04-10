---
title: "Modifier un mod&#232;le de trace (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles [SQL Server], traces"
  - "modèles de trace [SQL Server]"
  - "modification des traces"
ms.assetid: b81df2a1-e202-43d8-92b0-0beb145f0116
caps.latest.revision: 26
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 26
---
# Modifier un mod&#232;le de trace (SQL Server Profiler)
  Cette rubrique explique comment modifier un modèle de trace avec le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### Pour modifier un modèle de trace  
  
1.  Dans le menu **Fichier**, pointez sur **Modèles**, puis cliquez sur **Modifier le modèle**.  
  
2.  Dans la boîte de dialogue **Propriétés du modèle de trace**, sous l’onglet **Général**, vous pouvez modifier le type de serveur et le nom de modèle, ou utiliser un modèle par défaut pour le type de serveur.  
  
3.  Sous l’onglet **Sélection des événements**, utilisez le contrôle de la grille pour ajouter ou supprimer des événements et des colonnes de données dans le fichier de trace comme suit :  
  
    -   Pour ajouter un événement, développez la catégorie d’événements appropriée dans la colonne **Événements**, puis sélectionnez le nom de l’événement.  
  
    -   Lorsque vous ajoutez un événement, toutes les colonnes de données sont incluses par défaut. Pour supprimer une colonne de données d'un événement dans une trace, désactivez la case à cocher dans la colonne de données de l'événement.  
  
    -   Pour ajouter des filtres, cliquez sur le nom de la colonne de données et définissez les critères de filtrage dans la boîte de dialogue **Modifier le filtre**. Vous pouvez également cliquer avec le bouton droit sur le nom de la colonne de données et cliquer sur **Modifier le filtre des colonnes** pour ouvrir la boîte de dialogue **Modifier le filtre**. Cliquez sur **OK** pour ajouter le filtre.  
  
4.  Cliquez sur **Enregistrer** ou **Enregistrer sous** pour enregistrer le modèle de trace sous un autre nom.  
  
## Voir aussi  
 [Spécifier les événements et les colonnes de données d’un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Dériver un modèle à partir d’une trace en cours d’exécution &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)   
 [Dériver un modèle à partir d’un fichier de trace ou d’une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)   
 [Modèles et autorisations du générateur de SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  