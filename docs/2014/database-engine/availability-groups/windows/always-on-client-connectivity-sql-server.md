---
title: Connectivité client Always On (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1368d29801a414de866003b86c63fb4823c4a7b8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62790658"
---
# <a name="always-on-client-connectivity-sql-server"></a>Connectivité client Always On (SQL Server)
  Cette rubrique décrit les considérations relatives à la connectivité client aux groupes de disponibilité AlwaysOn, y compris les conditions préalables requises, les restrictions et les recommandations concernant les paramètres et les configurations de clients.  
  
 
  
##  <a name="ClientConnSupport"></a> Prise en charge de la connectivité client  
 La section ci-dessous fournit des informations sur la prise en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] de la connectivité client.  
  
 **Prise en charge de pilote**  
  
 Le tableau suivant récapitule les pilotes pris en charge pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]:  
  
|Pilote|Basculement de sous-réseaux multiples|Intention de l'application|Routage en lecture seule|Basculement de sous-réseaux multiples : Basculement de point de terminaison de sous-réseau unique plus rapide|Basculement de sous-réseaux multiples : Résolution d’Instance nommée de SQL en cluster des Instances|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Oui|Oui|Oui|Oui|Oui|  
|SQL Native Client 11.0 OLEDB|Non|Oui|Oui|Non|Non|  
|ADO.NET avec .NET Framework 4.0 et correctif logiciel de connectivité **<sup>*</sup>**|Oui|Oui|Oui|Oui|Oui|  
|ADO.NET avec .NET Framework 3.5 SP1 et correctif logiciel de connectivité **<sup>** </sup>**|Oui|Oui|Oui|Oui|Oui|  
|Microsoft JDBC Driver 4.0 pour SQL Server|Oui|Oui|Oui|Oui|Oui|  
  
 **<sup>*</sup>**  Télécharger le correctif logiciel de connectivité pour ADO .NET avec .NET Framework 4.0 : [ https://support.microsoft.com/kb/2600211 ](https://support.microsoft.com/kb/2600211).  
  
 **<sup>** </sup>** Téléchargez le correctif logiciel de connectivité pour ADO .NET avec .NET Framework 3.5 SP1 : [ https://support.microsoft.com/kb/2654347 ](https://support.microsoft.com/kb/2654347).  
  
> [!IMPORTANT]  
>  Pour se connecter à un écouteur de groupe de disponibilité, un client doit utiliser une chaîne de connexion TCP.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Création et configuration des groupes de disponibilité &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Clustering de basculement et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [À propos de l’accès de la connexion client aux réplicas de disponibilité &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Guide de Solutions Microsoft SQL Server AlwaysOn pour une haute disponibilité et récupération d’urgence](https://go.microsoft.com/fwlink/?LinkId=227600)   
 [Blog de l’équipe AlwaysOn SQL Server : Blog officiel de SQL Server AlwaysOn Team](https://blogs.msdn.com/b/sqlalwayson/)   
 [Un long délai se produit quand vous vous reconnectez à une connexion IPSec à partir d’un ordinateur qui exécute Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 ou Windows Server 2008 R2](https://support.microsoft.com/kb/980915)   
 [Il faut environ 30 secondes au service de cluster pour basculer des adresses IP IPv6 dans Windows Server 2008 R2](https://support.microsoft.com/kb/2578113)   
 [Ralentissez l’opération de basculement s’il n’existe aucun routeur entre le cluster et un serveur d’applications](https://support.microsoft.com/kb/2582281)  
  
  
