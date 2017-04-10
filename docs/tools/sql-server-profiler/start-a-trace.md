---
title: "D&#233;marrer une trace | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server Profiler, arrêt de traces"
  - "suspension de traces"
  - "Profiler [SQL Server Profiler], arrêt de traces"
  - "Profiler [SQL Server Profiler], démarrage de traces"
  - "traces [SQL Server], démarrage"
  - "SQL Server Profiler, suspension de traces"
  - "traces [SQL Server], arrêt"
  - "Profiler [SQL Server Profiler], suspension de traces"
  - "traces [SQL Server], suspension"
  - "SQL Server Profiler, démarrage de traces"
  - "arrêt de traces"
  - "démarrage de traces"
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# D&#233;marrer une trace
  Après avoir défini une nouvelle trace ou créé un modèle en utilisant le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], vous pouvez démarrer, suspendre ou arrêter la capture des données en utilisant la définition de la nouvelle trace ou le modèle.  
  
## Démarrage d’une trace  
 Lorsque vous démarrez une trace et que la source définie est une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ou des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une file d'attente qui fournit un espace de stockage temporaire pour les événements serveur capturés.  
  
 Lorsque vous utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour accéder à Trace SQL, une nouvelle fenêtre de trace s'ouvre (si aucune n'est ouverte) au démarrage d'une trace et les données sont capturées immédiatement.  
  
 Lorsque vous utilisez des procédures stockées système [!INCLUDE[tsql](../../includes/tsql-md.md)] pour accéder à Trace SQL, vous devez démarrer une trace chaque fois qu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre pour capturer des données. Lorsqu’une trace est démarrée, vous pouvez modifier uniquement le nom de la trace.  
  
> [!NOTE]  
>  Lorsque vous utilisez des traces existantes, vous pouvez afficher les propriétés, mais pas les modifier. Pour modifier les propriétés, arrêtez ou suspendez la trace.  
  
## Voir aussi  
 [Démarrer automatiquement une trace après s’être connecté à un serveur &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Suspendre une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)   
 [Arrêter une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)   
 [Effacer une fenêtre de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)   
 [Exécuter une trace après qu’elle a été suspendue ou arrêtée &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  