---
title: Créer des travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 986e38ef42fe1af2aba8ba1625225a336f29158d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52751311"
---
# <a name="create-jobs"></a>Créer des travaux
  Un travail est constitué d'une série d'opérations spécifiques exécutées de manière séquentielle par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Un travail peut effectuer diverses activités, notamment exécuter des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] , des applications d'invite de commandes, des scripts Microsoft ActiveX, des packages Integration Services, des commandes et des requêtes Analysis Services ou des tâches de réplication. Les travaux peuvent exécuter des tâches répétitives ou planifiables, et même notifier automatiquement les utilisateurs de l'état d'un travail en déclenchant des alertes, ce qui simplifie de manière significative l'administration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour créer un travail, l'utilisateur doit être membre de l'un des rôles de base de données fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ou du rôle de serveur fixe **sysadmin**. Un travail ne peut être modifié que par son propriétaire ou par les membres du rôle **sysadmin** . Les membres du rôle **sysadmin** peuvent attribuer la propriété du travail à d’autres utilisateurs et peuvent exécuter n’importe quel travail, quel qu’en soit le propriétaire. Pour plus d’informations sur les rôles de base de données fixe de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Rôles de base de données fixe de SQL Server Agent](sql-server-agent-fixed-database-roles.md).  
  
 Les travaux peuvent être écrits de manière à s'exécuter sur l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou sur plusieurs instances à l'échelle d'une entreprise. Pour exécuter des travaux sur plusieurs serveurs, vous devez configurer au moins un serveur maître et un ou plusieurs serveurs cibles. Pour plus d’informations sur les serveurs maîtres et cibles, consultez [Administration automatisée à l’échelle d’une entreprise](automated-administration-across-an-enterprise.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent enregistre dans l’historique des travaux les informations relatives aux travaux et aux étapes de travail.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Description**|**Rubrique**|  
|Explique comment créer un travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|[Créer un travail](create-a-job.md)|  
|Explique comment réattribuer la propriété des travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à un autre utilisateur.|[Give Others Ownership of a Job](give-others-ownership-of-a-job.md)|  
|Décrit la façon de définir le journal de l'historique des travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|[Configurer le journal d’historique des travaux](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les étapes de travail](manage-job-steps.md)   
 [Administration automatisée à l'échelle d'une entreprise](automated-administration-across-an-enterprise.md)   
 [Créer des planifications et les attacher à des travaux](create-and-attach-schedules-to-jobs.md)   
 [Exécuter des tâches](run-jobs.md)   
 [Afficher ou modifier les travaux](view-or-modify-jobs.md)  
  
  
