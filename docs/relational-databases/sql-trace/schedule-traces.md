---
title: Planifier les traces | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: sql-trace
ms.reviewer: ''
ms.suite: sql
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
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 18f833b64b24ebcba50003b46f036fdc854235b3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="schedule-traces"></a>Planifier les traces
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vous pouvez planifier les traces de deux façons dans Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez :  
  
-   Activer une heure d'arrêt de la trace.  
  
-   Utiliser l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour planifier la trace.  
  
## <a name="specifying-a-stop-time"></a>Spécification d'une heure d'arrêt  
 Vous pouvez spécifier une heure d'arrêt de la trace si vous utilisez des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] ou si vous utilisez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Vous devez définir l'heure d'arrêt lorsque vous configurez initialement la trace.  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>Planification des traces à l'aide de l'Agent SQL Server  
 La meilleure façon de planifier les traces consiste à utiliser l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour démarrer la trace, puis à spécifier une heure d’arrêt de la trace à l’aide de la procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_trace_setstatus**ou du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Pour définir un filtre d'heure de fin pour une trace**  
  
 [Filtrer des événements en fonction de leur heure de fin &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Tâches d’administration automatisée &#40;SQL Server Agent&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
