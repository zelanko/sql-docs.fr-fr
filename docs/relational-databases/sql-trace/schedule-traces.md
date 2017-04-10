---
title: "Planifier les traces | Microsoft Docs"
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
  - "filtres [SQL Server], événements"
  - "traces [SQL Server]"
  - "traces [SQL Server], arrêt"
  - "événements [SQL Server], filtres"
  - "planification des traces [SQL Server]"
  - "traces [SQL Server], planification"
  - "arrêt de traces"
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Planifier les traces
  Vous pouvez planifier les traces de deux façons dans Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez :  
  
-   Activer une heure d'arrêt de la trace.  
  
-   Utiliser l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour planifier la trace.  
  
## Spécification d'une heure d'arrêt  
 Vous pouvez spécifier une heure d'arrêt de la trace si vous utilisez des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] ou si vous utilisez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Vous devez définir l'heure d'arrêt lorsque vous configurez initialement la trace.  
  
## Planification des traces à l'aide de l'Agent SQL Server  
 La meilleure façon de planifier les traces consiste à utiliser l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour démarrer la trace, puis à spécifier une heure d’arrêt de la trace à l’aide de la procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_trace_setstatus** ou du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Pour définir un filtre d'heure de fin pour une trace**  
  
 [Filtrer des événements en fonction de leur heure de fin &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## Voir aussi  
 [Tâches d’administration automatisée &#40;SQL Server Agent&#41;](../../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  