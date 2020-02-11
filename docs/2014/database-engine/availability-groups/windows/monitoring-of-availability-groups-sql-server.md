---
title: Surveillance des groupes de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 1d5e3291-0d0a-45a1-88e5-1fc242d17210
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1793032a72ae1dd150caa5ddd1739f7f5620bce1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62790193"
---
# <a name="monitoring-of-availability-groups-sql-server"></a>Surveillance des groupes de disponibilité (SQL Server)
  Pour surveiller les propriétés et l'état d'un groupe de disponibilité AlwaysOn, vous pouvez utiliser les outils suivants.  
  
|Outil|Brève description|Liens|  
|----------|-----------------------|-----------|  
|Pack d'analyse System Center pour SQL Server|Le pack d'analyse pour SQL Server (SQLMP) est la solution recommandée pour la surveillance des groupes de disponibilité, des réplicas de disponibilité et des bases de données de disponibilité pour les administrateurs informatiques. Les fonctionnalités d'analyse particulièrement appropriées pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] incluent les suivantes :<br /><br /> Découverte automatique des groupes de disponibilité, des réplicas de disponibilité et des bases de données de disponibilité entre des centaines d'ordinateurs. Cette opération vous permet de suivre facilement votre inventaire [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .<br /><br /> Fonctionnalités complètes d'alertes et tickets System Center Operations Manager (SCOM). Ces fonctionnalités offrent des connaissances détaillées qui permettent de résoudre plus rapidement un problème.<br /><br /> Extension personnalisée à l'analyse d'intégrité AlwaysOn à l'aide de la gestion basée sur des stratégies.<br /><br /> Intégrité regroupée des bases de données de disponibilité aux réplicas de disponibilité.<br /><br /> Tâches personnalisées qui gèrent [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans la console System Center Operations Manager.|Pour télécharger le pack d’analyse (SQLServerMP.msi) et *le Guide SQL Server Management Pack pour System Center Operations Manager* (SQLServerMPGuide.doc), consultez :<br /><br /> [Pack d'analyse System Center pour SQL Server](https://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] fournissent une quantité d'informations sur vos groupes de disponibilité et leurs réplicas, bases de données, écouteurs et environnement de cluster WSFC.|[Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Le volet **Détails de l'Explorateur d'objets** affiche des informations de base sur les groupes de disponibilité hébergés sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à laquelle vous êtes connecté.<br /><br /> Conseil : utilisez ce volet pour sélectionner plusieurs groupes de disponibilité, réplicas ou bases de données et effectuer des tâches d’administration courantes sur les objets sélectionnés, comme la suppression de plusieurs réplicas de disponibilité ou bases de données dans un groupe de disponibilité.|[Utiliser les détails de l’Explorateur d’objets pour surveiller les groupes de disponibilité &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Les boîtes de dialogue**Propriétés** vous permettent d'afficher les propriétés des groupes de disponibilité, les réplicas ou les écouteurs et, dans certains cas, de modifier leurs valeurs.|[Afficher les propriétés d’un groupe de disponibilité &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)<br /><br /> [Afficher les propriétés d’un réplica de disponibilité &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)<br /><br /> [Afficher les propriétés d’écouteur de groupe de disponibilité &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)|  
|Moniteur système|L’objet de performance **SQLServer:Availability Replica** intègre des compteurs de performances chargés de fournir des informations sur les réplicas de disponibilité.|[SQL Server, réplica de disponibilité](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|Moniteur système|L’objet de performance **SQLServer:Database Replica** contient des compteurs de performances qui signalent des informations concernant les bases de données secondaires sur un réplica secondaire donné.<br /><br /> L'objet **SQLServer:Databases** dans SQL Server contient des compteurs de performances pour surveiller les activités du journal des transactions, entre autres choses. Les compteurs suivants sont particulièrement appropriés pour surveiller l’activité des journaux des transactions sur des bases de données de disponibilité : **Temps d’attente de vidage du journal (ms)** , **Vidages du journal/s**, **Journaliser les absences dans le cache/s du pool**, **Journaliser les lectures du disque/s du pool**et **Journaliser les requêtes/s du pool**.|[SQL Server, réplica de base de données](../../../relational-databases/performance-monitor/sql-server-database-replica.md) et [SQL Server, objet Databases](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [Modèle d'intégrité AlwaysOn Partie 1 -- Architecture du modèle d'intégrité](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/09/overview-of-the-alwayson-manageability-health-model.aspx)  
  
     [Modèle d'intégrité AlwaysOn Partie 2 - Extension du modèle d'intégrité](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
     [Surveillance de l'intégrité AlwaysOn avec PowerShell - Partie 1 : Vue d'ensemble des applets de commande de base](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-1.aspx)  
  
     [Surveillance de l'intégrité AlwaysOn avec PowerShell - Partie 2 : Utilisation des applets de commande avancées](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-2.aspx)  
  
     [Surveillance de l'intégrité AlwaysOn avec PowerShell - Partie 3 : Application de surveillance simple](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/monitoring-alwayson-health-with-powershell-part-3.aspx)  
  
     [Surveillance de l'intégrité AlwaysOn avec PowerShell - Partie 4 : Intégration à l'Agent SQL Server](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
     [Blogs de l'équipe de SQL Server AlwaysOn : Blog officiel de l'équipe de SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Livres blancs :**  
  
     [Livres blancs de Microsoft pour SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Livres blancs de l'équipe de consultants clients de SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue groupes de disponibilité AlwaysOn &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql)   
 [Groupes de disponibilité AlwaysOn les fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions)   
 [Stratégie flexible pour le basculement automatique d’un groupe de disponibilité &#40;Transact-SQL&#41;](flexible-automatic-failover-policy-availability-group.md)   
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [&#40;de réparation de page automatique pour les groupes de disponibilité et la mise en miroir de bases de données&#41;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [Utilisez le tableau de bord AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
