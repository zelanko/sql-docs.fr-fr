---
title: Création et configuration des groupes de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: e7d93c8a1b85d663c5c1590b76c4bf98f5050b3c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141036"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a>Création et configuration des groupes de disponibilité (SQL Server)
  Les rubriques de cette section expliquent comment déployer une implémentation [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur les instances de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] qui résident sur des nœuds de clustering de basculement Windows Server différents dans un seul cluster de basculement WSFC.  
  
 Avant de créer votre premier groupe de disponibilité, il est fortement recommandé de vous familiariser avec les informations présentées dans les rubriques suivantes :  
  
 [Conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
 Cette rubrique décrit les conditions préalables requises, restrictions et recommandations applicables aux ordinateurs, les nœuds WSFC, les instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les groupes de disponibilité, les réplicas et les bases de données. Cette rubrique contient également des informations sur les questions de sécurité.  
  
 [Mise en route avec les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
 Contient des informations sur les étapes de configuration d'une instance de serveur, de création d'un groupe de disponibilité, de configuration du groupe de disponibilité pour les connexions clientes, de gestion des groupes de disponibilité et de surveillance des groupes de disponibilité.  
  
 
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour configurer une instance de serveur pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**  
  
-   [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [Créer une base de données mise en miroir du point de terminaison pour les groupes de disponibilité AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions sortantes &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 **Pour commencer à configurer des groupes de disponibilité AlwaysOn**  
  
-   [Mise en route avec les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 **Pour créer et configurer un groupe de disponibilité**  
  
-   [Utiliser l’Assistant Groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [Créer un groupe de disponibilité &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Spécifier l’URL de point de terminaison lors de l’ajout ou lors de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Configurer la stratégie de basculement Flexible pour contrôler les Conditions pour le basculement automatique (groupes de disponibilité AlwaysOn)](configure-flexible-automatic-failover-policy.md)  
  
-   [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Configurer le routage en lecture seule pour un groupe de disponibilité &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Démarrer un mouvement de données sur une base de données secondaire AlwaysOn &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Gestion des connexions et des travaux pour les bases de données d’un groupe de disponibilité &#40;SQL Server&#41;](../../logins-and-jobs-for-availability-group-databases.md)  
  
 **Pour dépanner**  
  
-   [Résoudre les problèmes de Configuration des groupes de disponibilité AlwaysOn (SQL Server) supprimé](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Résoudre une opération d’ajout de fichier &#40;groupes de disponibilité AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [AlwaysON - HADRON Learning Series : Worker Pool Usage for HADRON Enabled Databases](http://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Blogs de l’équipe AlwaysOn SQL Server : Le Blog officiel de SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **Vidéos :**  
  
     [Microsoft SQL Server nom de code « Denali », série AlwaysOn, partie 1 : Présentation de la Solution haute disponibilité de prochaine génération](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server nom de code « Denali », série AlwaysOn, partie 2 : Création d’une Solution de haute disponibilité maximale à l’aide d’AlwaysOn](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Livres blancs :**  
  
     [Guide de Solutions Microsoft SQL Server AlwaysOn pour une haute disponibilité et récupération d’urgence](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Livres blancs de Microsoft pour SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Livres blancs de l'équipe de consultants clients de SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Administration d’un groupe de disponibilité &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [Stratégies AlwaysOn pour les problèmes opérationnels avec des groupes de disponibilité AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Surveillance des groupes de disponibilité &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Groupes de disponibilité AlwaysOn : Interopérabilité (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)  
  
  