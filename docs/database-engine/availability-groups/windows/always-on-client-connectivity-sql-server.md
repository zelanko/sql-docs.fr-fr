---
title: "Connectivit&#233; client Always On (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Groupes de disponibilité [SQL Server], écouteurs"
  - "Groupes de disponibilité [SQL Server], configuration requise et restrictions"
  - "Groupes de disponibilité [SQL Server], connectivité client"
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
caps.latest.revision: 22
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 21
---
# Connectivit&#233; client Always On (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique décrit les considérations relatives à la connectivité client aux groupes de disponibilité Always On, notamment les conditions préalables requises, les restrictions et les recommandations concernant les paramètres et les configurations de clients.  
  
 **Dans cette rubrique :**  
  
-   [Prise en charge de la connectivité client](#ClientConnSupport)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="ClientConnSupport"></a> Prise en charge de la connectivité client  
 La section ci-dessous fournit des informations sur la prise en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] de la connectivité client.  
  
 **Prise en charge de pilote**  
  
 Le tableau suivant récapitule les pilotes pris en charge pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] :  
  
|Pilote|Basculement de sous-réseaux multiples|Intention de l'application|Routage en lecture seule|Basculement de sous-réseaux multiples : basculement plus rapide du point de terminaison d'un sous-réseau unique|Basculement de sous-réseaux multiples : résolution d'instance nommée pour des instances de cluster SQL|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Oui|Oui|Oui|Oui|Oui|  
|SQL Native Client 11.0 OLEDB|Non|Oui|Oui|Non|Non|  
|ADO.NET avec .NET Framework 4.0 et correctif logiciel de connectivité*|Oui|Oui|Oui|Oui|Oui|  
|ADO.NET avec .NET Framework 3.5 SP1 et correctif logiciel de connectivité**|Oui|Oui|Oui|Oui|Oui|  
|Microsoft JDBC Driver 4.0 pour SQL Server|Oui|Oui|Oui|Oui|Oui|  
  
 *Téléchargez le correctif logiciel de connectivité pour ADO .NET avec .NET Framework 4.0 : [http://support.microsoft.com/kb/2600211](http://support.microsoft.com/kb/2600211).  
  
 **Téléchargez le correctif logiciel de connectivité pour ADO .NET avec .NET Framework 3.5 SP1 : [http://support.microsoft.com/kb/2654347](http://support.microsoft.com/kb/2654347).  
  
> [!IMPORTANT]  
>  Pour se connecter à un écouteur de groupe de disponibilité, un client doit utiliser une chaîne de connexion TCP.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Création et configuration des groupes de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
## Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Clustering de basculement et groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)   
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners, client connectivity, application failover.md)   
 [À propos de l’accès de la connexion client aux réplicas de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery (Guide de solutions Microsoft SQL Server Always On pour la haute disponibilité et la récupération d’urgence)](http://go.microsoft.com/fwlink/?LinkId=227600)   
 [Blog de l’équipe de SQL Server Always On : Blog officiel de l’équipe de SQL Server Always On](http://blogs.msdn.com/b/sqlAlways%20On/)   
 [Un long délai se produit lorsque vous vous reconnectez à une connexion IPSec à partir d’un ordinateur qui exécute Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 ou Windows Server 2008 R2](http://support.microsoft.com/kb/980915)   
 [Il faut environ 30 secondes au service de cluster pour basculer des adresses IP IPv6 dans Windows Server 2008 R2](http://support.microsoft.com/kb/2578113)   
 [Ralentissez l'opération de basculement s'il n'existe aucun routeur entre le cluster et un serveur d'applications](http://support.microsoft.com/kb/2582281)  
  
  