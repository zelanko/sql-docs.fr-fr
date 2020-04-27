---
title: 'Groupes de disponibilité Always On : interopérabilité (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3f6123f66d687327ba56601419328e44fd920a2a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62815745"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Groupes de disponibilité Always On : interopérabilité (SQL Server)
  Cette rubrique documente l'interopérabilité de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] avec d'autres fonctionnalités de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a>Fonctionnalités qui interopèrent avec groupes de disponibilité AlwaysOn  
 Le tableau suivant répertorie les fonctionnalités de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui interopèrent avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un lien dans la colonne **Informations supplémentaires** indique que des observations relatives à l'interopérabilité existent pour une fonctionnalité.  
  
|Fonctionnalité|Informations complémentaires|  
|-------------|----------------------|  
|Capture des données modifiées|[Réplication, Change Tracking, capture de données modifiées et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Suivi des modifications|[Réplication, Change Tracking, capture de données modifiées et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Bases de données autonomes|[Bases de données autonomes avec les groupes de disponibilité AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)|  
|Chiffrement de base de données|[Bases de données chiffrées avec groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|Instantanés de base de données|[Instantanés de base de données avec groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM et FileTable|[FILESTREAM et filetable avec groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|Recherche en texte intégral|Remarque : les index de recherche en texte intégral sont synchronisés avec les bases de données secondaires AlwaysOn.|  
|Copie des journaux de transaction|[Conditions préalables à la migration de la copie des journaux de session vers groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|Magasin d'objets blob distants (RBS)|[Magasin d’objets BLOB distants &#40;&#41; RBS et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|Réplication[configurer la réplication pour groupes de disponibilité AlwaysOn (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [Maintenance d’une base de données de publication AlwaysOn &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [Réplication, Change Tracking, capture de données modifiées et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [Abonnés de réplication et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[Analysis Services avec les groupes de disponibilité AlwaysOn](analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|Utilisez des réplicas secondaires en lecture seule comme source de données de création de rapports et réduisez la charge sur votre réplica principal en lecture-écriture.<br /><br /> [Reporting Services groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[Service Broker groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|SQL Server Agent||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a>Fonctionnalités qui n’interagissent pas avec groupes de disponibilité AlwaysOn  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] n'interagit pas avec les fonctionnalités suivantes :  
  
-   Transactions entre bases de données/transactions distribuées  
  
     Pour plus d’informations sur les raisons pour lesquelles de telles transactions ne sont pas prises en charge, consultez [Transactions entre bases de données non prises en charge pour la mise en miroir de bases de données ou les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).  
  
-   Mise en miroir de bases de données  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [Guide de migration : Migration vers le clustering de basculement SQL Server 2012 et les groupes de disponibilité à partir des déploiements de mise en miroir et de clustering antérieurs](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [Blogs de l'équipe de SQL Server AlwaysOn : Blog officiel de l'équipe de SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Livres blancs :**  
  
     [Guide de migration : Migration vers les groupes de disponibilité AlwaysOn à partir des déploiements antérieurs combinant la mise en miroir de bases de données et la copie des journaux de transaction](https://msdn.microsoft.com/library/jj635217)  
  
     [Guide de solutions Microsoft SQL Server AlwaysOn pour la haute disponibilité et la récupération d'urgence](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Livres blancs de Microsoft pour SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Livres blancs de l'équipe de consultants clients de SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
