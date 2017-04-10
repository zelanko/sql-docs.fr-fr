---
title: "T&#226;che Ex&#233;cuter le travail de l&#39;Agent SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.executesqlserveragentjobtask.f1"
helpviewer_keywords: 
  - "tâche d'exécution de travail d'Agent SQL Server [Integration Services]"
  - "travaux [Integration Services]"
  - "Agent SQL Server [Integration Services]"
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
caps.latest.revision: 44
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 44
---
# T&#226;che Ex&#233;cuter le travail de l&#39;Agent SQL Server
  La tâche Exécuter le travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécute des travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent est un service Windows [!INCLUDE[msCoName](../../includes/msconame-md.md)] qui exécute des travaux définis dans une instance de SQL Server. Vous pouvez créer des travaux qui exécutent des instructions Transact-SQL et des scripts ActiveX, réalisent des tâches de maintenance des services [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et de réplication ou exécutent des packages. Vous pouvez également configurer une tâche pour surveiller [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et déclencher des alertes. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les travaux de l’Agent sont généralement utilisés pour automatiser des tâches à caractère répétitif. Pour plus d’informations, consultez [Implémenter des travaux](../../ssms/agent/implement-jobs.md).  
  
 Grâce à la tâche Exécuter le travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un package peut effectuer des tâches d'administration liées aux composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, un travail d’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut exécuter une procédure stockée système telle que **sp_enum_dtspackages** pour obtenir la liste des packages stockés dans un dossier.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être en cours d’exécution pour que les travaux d’administration locale ou multiserveur puissent être exécutés automatiquement.  
  
 Cette tâche encapsule la procédure système **sp_start_job** et transmet le nom du travail d’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à la procédure en guise d’argument. Pour plus d’informations, consultez [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).  
  
## Configuration de la tâche d'exécution de travail d'Agent SQL Server  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Exécuter le travail de l’Agent SQL Server &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
  