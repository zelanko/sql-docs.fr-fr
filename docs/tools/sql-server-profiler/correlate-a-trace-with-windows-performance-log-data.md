---
title: "Mettre en corr&#233;lation une trace avec les donn&#233;es du journal de performances&#160;Windows | Microsoft Docs"
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
  - "mise en corrélation du suivi avec les données du journal"
  - "journaux [SQL Server], traces"
  - "Profiler [SQL Server Profiler], mise en corrélation du suivi avec les données du journal"
  - "traces [SQL Server], journaux"
  - "SQL Server Profiler, mise en corrélation du suivi avec les données du journal"
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Mettre en corr&#233;lation une trace avec les donn&#233;es du journal de performances&#160;Windows
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] permet d'ouvrir un journal de performances Microsoft Windows, de choisir les compteurs que vous voulez corréler avec une trace et d'afficher les compteurs de performances sélectionnés en même temps que la trace dans l'interface utilisateur graphique du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Lorsque vous sélectionnez un événement dans la fenêtre de trace, une barre verticale rouge dans le volet Moniteur système du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indique les données du journal de performances en corrélation avec l'événement de trace sélectionné.  
  
 Pour mettre en corrélation une trace avec des compteurs de performances, ouvrez un fichier de trace ou une table qui contient les colonnes **StartTime** et **EndTime** et cliquez sur **Importer les données de performances** dans le menu **Fichier** de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Vous pouvez ouvrir un journal de performances et sélectionner les objets et compteurs du Moniteur système que vous voulez mettre en corrélation avec la trace.  
  
## Voir aussi  
 [Corréler une trace aux données du journal de performances Windows &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  