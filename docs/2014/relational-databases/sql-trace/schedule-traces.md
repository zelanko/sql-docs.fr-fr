---
title: Planifier les traces | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3017f239b024bcab3d19b589be1ec189187a5d09
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043317"
---
# <a name="schedule-traces"></a>Planifier les traces
  Vous pouvez planifier les traces de deux façons dans Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez :  
  
-   Activer une heure d'arrêt de la trace.  
  
-   Utiliser l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour planifier la trace.  
  
## <a name="specifying-a-stop-time"></a>Spécification d'une heure d'arrêt  
 Vous pouvez spécifier une heure d'arrêt de la trace si vous utilisez des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] ou si vous utilisez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Vous devez définir l'heure d'arrêt lorsque vous configurez initialement la trace.  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>Planification des traces à l'aide de l'Agent SQL Server  
 La meilleure façon de planifier les traces consiste à utiliser l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour démarrer la trace, puis à spécifier une heure d’arrêt de la trace à l’aide de la procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_trace_setstatus**ou du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Pour définir un filtre d'heure de fin pour une trace**  
  
 [Filtrer des événements en fonction de leur heure de fin &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches d’administration automatisée &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md)  
  
  
