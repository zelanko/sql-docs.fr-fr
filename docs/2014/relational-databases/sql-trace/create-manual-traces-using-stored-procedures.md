---
title: Créer des traces manuelles à l’aide de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 247548de6f3a89afac2143347d987a6f6d638c55
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62714817"
---
# <a name="create-manual-traces-using-stored-procedures"></a>Créer des traces manuelles à l'aide de procédures stockées
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des procédures stockées système [!INCLUDE[tsql](../../includes/tsql-md.md)] pour créer des traces sur une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Ces procédures stockées système permettent, à partir de vos propres applications, de créer des traces manuellement au lieu d'utiliser le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Vous pouvez ainsi écrire des applications personnalisées spécifiques des besoins de votre entreprise.  
  
## <a name="in-this-section"></a>Dans cette section  
 Le tableau suivant répertorie les procédures stockées système pour tracer une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
|Procédure stockée|Tâche réalisée|  
|----------------------|--------------------|  
|[sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql)|Retourne des informations sur les événements inclus dans une trace.|  
|[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)|Retourne des informations sur une trace spécifiée ou toutes les traces existantes.|  
|[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)|Crée une définition de trace. La nouvelle trace est à l'état arrêté.|  
|[sp_trace_generateevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)|Crée un événement défini par l'utilisateur.|  
|[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)|Ajoute une classe d'événements ou une colonne de données à une trace ou en supprime une.|  
|[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|Démarre, arrête ou ferme une trace.|  
|[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)|Retourne des informations relatives aux filtres appliqués à une trace.|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|Applique un nouveau filtre ou un filtre modifié à une trace.|  
  
 **Pour définir votre propre trace à l'aide de procédures stockées**  
  
1.  Spécifiez les événements à capturer à l’aide de **sp_trace_setevent**.  
  
2.  Spécifiez les filtres d'événements, le cas échéant. Pour plus d’informations, consultez [Définir un filtre de trace &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md).  
  
3.  Spécifiez la destination des données d’événement capturées à l’aide de **sp_trace_create**.  
  
 Pour obtenir un exemple d’utilisation de procédures stockées de trace, consultez [Créer une trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).  
  
 **Pour définir les valeurs par défaut des définitions de trace**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
 **Pour définir les valeurs par défaut de l'affichage des traces**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **Pour créer une trace**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [Transact-SQL](../sql-trace/create-a-trace-transact-sql.md)  
  
 **Pour ajouter ou supprimer des événements à un modèle de trace**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
