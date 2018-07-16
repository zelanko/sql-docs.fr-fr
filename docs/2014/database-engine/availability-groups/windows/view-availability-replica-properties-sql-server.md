---
title: Afficher les propriétés d’un réplica de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ', policies'
ms.assetid: 14fed3c4-8ecc-4e1c-931d-a7ec1e9f9e90
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9c8ce45ca1ae4efdb65d8d1aae44261be80a0a5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282198"
---
# <a name="view-availability-replica-properties-sql-server"></a>Afficher les propriétés d'un réplica de disponibilité (SQL Server)
  Cette rubrique explique comment afficher les propriétés d'un réplica de disponibilité pour un groupe de disponibilité AlwaysOn à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher et modifier les propriétés d'un réplica de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Développez le groupe de disponibilité auquel appartient le réplica de disponibilité, puis développez le nœud **Réplicas de disponibilité**.  
  
4.  Cliquez avec le bouton droit sur le réplica de disponibilité dont vous souhaitez afficher les propriétés, puis sélectionnez la commande **Propriétés** .  
  
5.  Dans la boîte de dialogue **Propriétés du réplica de disponibilité** , utilisez la page **Général** pour afficher les propriétés de ce réplica. Si vous êtes connecté au réplica principal, vous pouvez modifier les propriétés suivantes : mode de disponibilité, mode de basculement, accès à la connexion pour le rôle principal, accès en lecture pour le rôle secondaire (secondaire lisible) et valeur de délai d'expiration de session. Pour plus d’informations, consultez [propriétés du réplica de disponibilité &#40;Général Page&#41;](availability-replica-properties-general-page.md).  
  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher les propriétés et les états des réplicas de disponibilité**  
  
 Pour afficher les propriétés et les états des réplicas de disponibilité, utilisez les vues et fonctions système suivantes :  
  
 [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 Retourne une ligne pour chaque réplica de disponibilité dans chaque groupe de disponibilité pour lequel l'instance locale de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] héberge un réplica de disponibilité.  
  
 **Noms de colonne :** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url  
  
 [sys.availability_read_only_routing_lists](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 Retourne une ligne pour la liste de routage en lecture seule de chaque réplica de disponibilité d'un groupe de disponibilité AlwaysOn dans le cluster de basculement WSFC.  
  
 **Noms de colonnes :** replica_id, routing_priority, read_only_replica_id  
  
 [sys.dm_hadr_availability_replica_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 Retourne une ligne pour chaque réplica de disponibilité (indépendamment de l'état de jointure) des groupes de disponibilité AlwaysOn dans le cluster de clustering de basculement Windows Server (WSFC).  
  
 **Noms de colonnes :** group_name, replica_server_name, node_name  
  
 [sys.dm_hadr_availability_replica_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 Retourne une ligne pour chaque réplica (indépendamment de l'état de jointure) de tous les groupes de disponibilité AlwaysOn (indépendamment de l'emplacement du réplica) dans le cluster WSFC (clustering de basculement Windows Server).  
  
 **Noms de colonnes :** replica_id, replica_server_name, group_id, join_state, join_state_desc  
  
 [sys.dm_hadr_availability_replica_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 Retourne une ligne montrant l'état de chaque réplica de disponibilité local et une ligne pour chaque réplica de disponibilité distant au sein du même groupe de disponibilité.  
  
 **Noms de colonnes :** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description et last_connect_error_timestamp  
  
 [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 Détermine si le réplica actuel est le réplica de sauvegarde par défaut. Retourne 1 si la base de données sur l'instance de serveur actuelle est le réplica par défaut. Sinon, retourne 0.  
  
> [!NOTE]  
>  Pour plus d’informations sur les compteurs de performances pour les réplicas de disponibilité (l’objet de performances **SQLServer:Availability Replica**  ), consultez [SQL Server, réplica de disponibilité](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).  
  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour afficher des informations sur les groupes de disponibilité**  
  
-   [Afficher les propriétés d’un groupe de disponibilité &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)  
  
-   [Afficher les propriétés d’écouteur de groupe de disponibilité &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)  
  
-   [Les stratégies AlwaysOn pour les problèmes opérationnels avec des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)  
  
 **Pour gérer des réplicas de disponibilité**  
  
-   [Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Modifier le mode de disponibilité d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modifier le mode de basculement d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modifier le délai d’expiration de session pour un réplica de disponibilité &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
 **Pour gérer une base de données de disponibilité**  
  
-   [Ajouter une base de données à un groupe de disponibilité &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Interrompre une base de données de disponibilité &#40;SQL Server&#41;](suspend-an-availability-database-sql-server.md)  
  
-   [Reprendre une base de données de disponibilité &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md)  
  
-   [Supprimer une base de données secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Supprimer une base de données primaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)   
 [Les stratégies AlwaysOn pour les problèmes opérationnels avec des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Administration d’un groupe de disponibilité &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)  
  
  
