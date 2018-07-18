---
title: Afficher les propriétés d’un groupe de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server]
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7c59f778735c524ca8b1d0b41469114b21e5b591
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312319"
---
# <a name="view-availability-group-properties-sql-server"></a>Afficher les propriétés d'un groupe de disponibilité (SQL Server)
  Cette rubrique explique comment afficher les propriétés d'un groupe de disponibilité pour un groupe de disponibilité AlwaysOn à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  

  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher et modifier les propriétés d'un groupe de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Cliquez avec le bouton droit sur le groupe de disponibilité dont vous souhaitez afficher les propriétés, puis sélectionnez la commande **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés du groupe de disponibilité**, utilisez les pages **Général** et **Préférences de sauvegarde** pour afficher et, dans certains cas, pour modifier les propriétés du groupe de disponibilité sélectionné. Pour plus d’informations, consultez [Propriétés du groupe de disponibilité et Nouveau groupe de disponibilité &#40;page Général&#41;](availability-group-properties-new-availability-group-general-page.md) et [Propriétés d’un groupe de disponibilité : nouveau groupe de disponibilité &#40;page Préférences de sauvegarde&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).  
  
     Utilisez la page **Autorisations** pour afficher les connexions, les rôles et les autorisations explicites actuellement associés au groupe de disponibilité. Pour plus d’informations, consultez la page [Autorisations ou Éléments sécurisables](../../../relational-databases/security/permissions-or-securables-page.md).  
  

  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher les propriétés et l'état d'un groupe de disponibilité**  
  
 Pour interroger les propriétés et les états des groupes de disponibilité pour lesquels l'instance de serveur héberge un réplica de disponibilité, utilisez les vues suivantes :  
  
 [sys.availability_groups](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 Retourne une ligne pour chaque groupe de disponibilité pour lequel l'instance locale d' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] héberge un réplica de disponibilité. Chaque ligne contient une copie mise en cache des métadonnées du groupe de disponibilité.  
  
 **Noms de colonne :** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.availability_groups_cluster](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 Retourne une ligne pour chaque groupe de disponibilité du cluster WSFC. Chaque ligne contient les métadonnées du groupe de disponibilité du cluster de clustering de basculement Windows Server (WSFC).  
  
 **Noms de colonne :** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 Retourne une ligne pour chaque groupe de disponibilité qui possède un réplica de disponibilité sur l'instance locale de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Chaque ligne affiche les états qui définissent l'intégrité d'un groupe de disponibilité donné.  
  
 **Noms de colonne :** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc  
  

  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour afficher des informations sur les groupes de disponibilité**  
  
-   [Afficher les propriétés d’un réplica de disponibilité &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)  
  
-   [Afficher les propriétés d’écouteur de groupe de disponibilité &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)  
  
-   [Les stratégies AlwaysOn pour les problèmes opérationnels avec des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)  
  
 **Pour configurer un groupe de disponibilité existant**  
  
-   [Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Ajouter une base de données à un groupe de disponibilité &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Supprimer une base de données secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Supprimer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](remove-an-availability-group-listener-sql-server.md)  
  
-   [Supprimer une base de données primaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Supprimer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)  
  
 **Pour basculer manuellement un groupe de disponibilité**  
  
-   [Effectuer un basculement manuel planifié d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41; ](overview-of-always-on-availability-groups-sql-server.md) [surveiller les groupes de disponibilité &#40;Transact-SQL&#41; ](monitor-availability-groups-transact-sql.md) [stratégies AlwaysOn pour les problèmes opérationnels avec AlwaysOn Groupes de disponibilité &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) 
  
  
