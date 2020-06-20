---
title: Supprimer des travaux | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
author: stevestein
ms.author: sstein
ms.openlocfilehash: f66387a1334f91c29b8edddad293d76064430b39
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995472"
---
# <a name="delete-jobs"></a>travaux, supprimer
  Un travail est constitué d'une série d'opérations spécifiques exécutées de manière séquentielle par l'Agent SQL Server. Par défaut, les travaux ne sont pas supprimés lorsque l'exécution se termine. Vous pouvez supprimer un ou plusieurs travaux [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent indépendamment de la réussite ou de l'échec du travail. Vous pouvez également configurer l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour supprimer automatiquement des travaux quand ils réussissent, échouent ou s'achèvent.  
  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter la procédure stockée système [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql) pour supprimer un travail. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](sql-server-agent-fixed-database-roles.md).  
  
 Les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_delete_job** pour supprimer un travail. Un utilisateur qui n'est pas membre du rôle serveur fixe **sysadmin** n'a le droit de supprimer que les travaux dont il est propriétaire.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Description**|**Rubrique**|  
|Explique comment supprimer un ou plusieurs travaux de l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Supprimer un ou plusieurs travaux](delete-one-or-more-jobs.md)|  
|Explique comment configurer l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour supprimer automatiquement des travaux quand ils réussissent, échouent ou s'achèvent.|[Automatically Delete a Job](automatically-delete-a-job.md)|  
  
  
