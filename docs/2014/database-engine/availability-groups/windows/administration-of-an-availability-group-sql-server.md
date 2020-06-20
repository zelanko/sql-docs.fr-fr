---
title: Administration d’un groupe de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], managing
ms.assetid: 0b7542fa-235e-413d-81bf-3eff9ee07480
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1bc670d47362f2e4170c9ae9a85b0588d07f1e4
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937219"
---
# <a name="administration-of-an-availability-group-sql-server"></a>Administration d'un groupe de disponibilité (SQL Server)
  La gestion d'un groupe de disponibilité AlwaysOn existant dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] implique une ou plusieurs des tâches suivantes :  
  
-   Modification des propriétés d'un réplica de disponibilité existant, par exemple pour modifier l'accès de connexion du client (pour configurer les réplicas secondaires lisibles), modification de son mode de basculement, mode de disponibilité ou paramètre de délai d'expiration de session.  
  
-   Ajout ou suppression de réplicas secondaires.  
  
-   Ajout ou suppression d'une base de données.  
  
-   Interruption ou reprise d'une base de données.  
  
-   Exécution d’un basculement manuel planifié ( *basculement manuel*) ou d’un basculement manuel forcé ( *basculement forcé*).  
  
-   Création ou configuration d'un écouteur de groupe de disponibilité.  
  
-   Gestion des [réplicas secondaires lisibles](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) pour un groupe de disponibilité donné. Cela implique la configuration d'un ou plusieurs réplicas pour l'accès en lecture seule en cas d'exécution sous le rôle secondaire, et la configuration du routage en lecture seule.  
  
-   Gestion des [sauvegardes sur des réplicas secondaires](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) pour un groupe de disponibilité donné. Cela implique la configuration de l'emplacement d'exécution des travaux de sauvegarde, puis la création d'un script pour les travaux de sauvegarde pour implémenter vos préférences de sauvegarde. Vous devez créer un script de travaux de sauvegarde pour chaque base de données dans le groupe de disponibilité sur chaque instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge un réplica de disponibilité.  
  
-   Suppression d'un groupe de disponibilité.  
  
-   Migration entre clusters de groupes de disponibilité AlwaysOn pour la mise à niveau du système d'exploitation  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
 **Pour configurer un groupe de disponibilité existant**  
  
-   [Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Ajouter une base de données à un groupe de disponibilité &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Supprimer une base de données secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Supprimer une base de données primaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Configurez la stratégie de basculement flexible pour contrôler les conditions du basculement automatique &#40;groupes de disponibilité AlwaysOn&#41;](configure-flexible-automatic-failover-policy.md)  
  
 **Pour gérer un groupe de disponibilité**  
  
-   [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Effectuer un basculement manuel planifié d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Supprimer un groupe de disponibilité &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)  
  
 **Pour gérer un réplica de disponibilité**  
  
-   [Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Modifier le mode de disponibilité d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modifier le mode de basculement d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Configurer le routage en lecture seule pour un groupe de disponibilité &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Modifier le délai d’expiration de session pour un réplica de disponibilité &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Pour gérer une base de données de disponibilité**  
  
-   [Ajouter une base de données à un groupe de disponibilité &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Supprimer une base de données primaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Supprimer une base de données secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Interrompre une base de données de disponibilité &#40;SQL Server&#41;](suspend-an-availability-database-sql-server.md)  
  
-   [Reprendre une base de données de disponibilité &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md)  
  
 **Pour surveiller un groupe de disponibilité**  
  
-   [Outils pour superviser les groupes de disponibilité Always On](monitoring-of-availability-groups-sql-server.md)  
  
 **Pour prendre en charge la migration des groupes de disponibilité vers un nouveau cluster WSFC (migration entre clusters)**  
  
-   [Changer le contexte de cluster HADR de l’instance de serveur &#40;SQL Server&#41;](change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
-   [Placer un groupe de disponibilité hors connexion &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [Blogs de l'équipe de SQL Server AlwaysOn : Blog officiel de l'équipe de SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Vidéos :**  
  
     [Microsoft SQL Server, nom de code « Denali », série AlwaysOn, Partie 1 : Présentation de la solution haute disponibilité de la prochaine génération](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server, nom de code « Denali », série AlwaysOn, Partie 2 : Génération d'une solution haute disponibilité critique à l'aide d'AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Livres blancs :**  
  
     [Livres blancs de Microsoft pour SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Livres blancs de l'équipe de consultants clients de SQL Server](http://sqlcat.com/)  
  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md)   
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Configuration d’une instance de serveur pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)  
 [Création et configuration des groupes de disponibilité &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Secondaires actifs : réplicas secondaires accessibles en lecture &#40;groupes de disponibilité AlwaysOn&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [Secondaires actifs : sauvegarde sur les réplicas secondaires &#40;groupes de disponibilité AlwaysOn&#41;](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Stratégies AlwaysOn pour les problèmes opérationnels avec groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Surveillance des groupes de disponibilité &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Groupes de disponibilité AlwaysOn : interopérabilité &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md)   
 [Vue d’ensemble des instructions Transact-SQL pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Vue d’ensemble des applets de commande PowerShell pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
