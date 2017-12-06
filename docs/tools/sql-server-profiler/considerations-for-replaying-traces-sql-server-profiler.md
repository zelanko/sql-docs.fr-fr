---
title: "Considérations sur la relecture des Traces (SQL Server Profiler) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60fa1b34d95a427d802bd355dcb66c3794d4ea79
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a>Considérations sur la relecture des traces (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ne peut pas relire les types de traces suivants :  
  
-   Les traces qui contiennent une réplication transactionnelle et d'autres activités de journal de transactions. Ces événements sont ignorés. Les autres types de réplication ne sont pas affectés car ils ne font pas d'écritures dans le journal des transactions.  
  
-   Les traces qui contiennent des opérations impliquant des identificateurs globaux uniques (GUID). Ces événements sont ignorés.  
  
-   Les traces qui contiennent des opérations sur des colonnes **text**, **ntext**et **image** ayant recours à l’utilitaire **bcp** , aux instructions BULK INSERT, READTEXT, WRITETEXT et UPDATETEXT ainsi qu’aux opérations de texte intégral. Ces événements sont ignorés.  
  
-   Les traces contenant des liaisons de session : procédures stockées système **sp_getbindtoken** et **sp_bindsession** . Ces événements sont ignorés.  
  
> [!NOTE]  
>  Si vous n’utilisez pas le modèle de relecture préconfigurée (**TSQL_Replay**) et que vous ne capturez pas toutes les données requises, le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ne relit pas la trace. Pour plus d’informations, consultez [Conditions préalables à la relecture](../../tools/sql-server-profiler/replay-requirements.md).  
  
 Pour savoir quelles autorisations sont nécessaires pour relire une trace, consultez [Autorisations nécessaires pour exécuter SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_getbindtoken &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [sp_bindsession &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [WRITETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/writetext-transact-sql.md)   
 [UPDATETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
