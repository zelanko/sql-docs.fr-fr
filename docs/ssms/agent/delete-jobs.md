---
title: Supprimer des travaux | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f5e08e59ade5619787882695f6183bf1526dc557
ms.lasthandoff: 04/11/2017

---
# <a name="delete-jobs"></a>Supprimer des travaux
Un travail est constitué d'une série d'opérations spécifiques exécutées de manière séquentielle par l'Agent SQL Server. Par défaut, les travaux ne sont pas supprimés lorsque l'exécution se termine. Vous pouvez supprimer un ou plusieurs travaux [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent indépendamment de la réussite ou de l'échec du travail. Vous pouvez également configurer l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pour supprimer automatiquement des travaux quand ils réussissent, échouent ou s'achèvent.  
  
Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter la procédure stockée système [sp_delete_job (Transact-SQL)](http://msdn.microsoft.com/en-us/b85db6e4-623c-41f1-9643-07e5ea38db09) pour supprimer un travail. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_delete_job** pour supprimer un travail. Un utilisateur qui n'est pas membre du rôle serveur fixe **sysadmin** n'a le droit de supprimer que les travaux dont il est propriétaire.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Description**|**Rubrique**|  
|Explique comment supprimer un ou plusieurs travaux de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Supprimer un ou plusieurs travaux](../../ssms/agent/delete-one-or-more-jobs.md)|  
|Explique comment configurer l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pour supprimer automatiquement des travaux quand ils réussissent, échouent ou s'achèvent.|[Automatically Delete a Job](../../ssms/agent/automatically-delete-a-job.md)|  
  

