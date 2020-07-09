---
title: Planifier les traces | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bad2aedb9299eb53e4f98e62a5aa48158f9ec457
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750939"
---
# <a name="schedule-traces"></a>Planifier les traces
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Vous pouvez planifier les traces de deux façons dans Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez :  
  
-   Activer une heure d'arrêt de la trace.  
  
-   Utiliser l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour planifier la trace.  
  
## <a name="specifying-a-stop-time"></a>Spécification d'une heure d'arrêt  
 Vous pouvez spécifier une heure d'arrêt de la trace si vous utilisez des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] ou si vous utilisez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Vous devez définir l'heure d'arrêt lorsque vous configurez initialement la trace.  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>Planification des traces à l'aide de l'Agent SQL Server  
 La meilleure façon de planifier les traces consiste à utiliser l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour démarrer la trace, puis à spécifier une heure d’arrêt de la trace à l’aide de la procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)]**sp_trace_setstatus**ou du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Pour définir un filtre d'heure de fin pour une trace**  
  
 [Filtrer des événements en fonction de leur heure de fin &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches d’administration automatisée &#40;SQL Server Agent&#41;](https://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
