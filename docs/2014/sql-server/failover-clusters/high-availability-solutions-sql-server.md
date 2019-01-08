---
title: Solutions haute disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], solutions
- Database Engine [SQL Server], availability
- database availability [SQL Server]
- availability [SQL Server]
- server availability [SQL Server]
ms.assetid: b2eda634-0f8e-4703-801b-7ba895544ff5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 15e75dd27ca447eaab326ff50cc67614d442e096
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52543593"
---
# <a name="high-availability-solutions-sql-server"></a>Solutions haute disponibilité (SQL Server)
  Cette rubrique présente plusieurs solutions haute disponibilité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui améliorent la disponibilité des serveurs ou des bases de données. Une solution à haute disponibilité masque l'impact d'une défaillance matérielle ou logicielle et gère la disponibilité des applications pour réduire au maximum le temps mort que perçoit l'utilisateur.  
  
> [!NOTE]  
>  Pour plus d’informations sur les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui prennent en charge une solution haute disponibilité donnée, consultez la section « Haute disponibilité (AlwaysOn) » de l’article [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
(#RecommendedSolutions)  
  
##  <a name="TermsAndDefinitions"></a> Présentation des solutions haute disponibilité SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit plusieurs options permettant de garantir un haut niveau de disponibilité pour un serveur ou une base de données. Les options de haute disponibilité sont les suivantes :  
  
 Instances de cluster de basculement AlwaysOn  
 Dans le cadre de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn offre, les Instances de Cluster de basculement AlwaysOn exploitent la fonctionnalité de Clustering de basculement Windows Server (WSFC) pour fournir une haute disponibilité locale grâce à la redondance à l’instance de serveur un niveau  *instance de cluster de basculement* (ICF). Une instance FCI est une instance unique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installée sur plusieurs nœuds WSFC (clustering de basculement Windows Server) et, éventuellement, sur plusieurs sous-réseaux. Sur le réseau, une instance de cluster de basculement FCI apparaît en tant qu'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutant sur un ordinateur unique, mais elle permet le basculement d'un nœud WSFC vers un autre en cas d'indisponibilité du nœud actuel.  
  
 Pour plus d’informations, consultez [ Instances de Cluster de basculement AlwaysOn (SQL Server)](windows/always-on-failover-cluster-instances-sql-server.md).  
  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] est une solution haute disponibilité et de récupération d’urgence au niveau de l’entreprise introduite dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour vous permettre d’optimiser la disponibilité d’une ou de plusieurs bases de données utilisateur. [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] exige que les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] résident sur des nœuds de clustering de basculement Windows Server (WSFC). Pour plus d’informations, consultez [ groupes de disponibilité AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md).  
  
> [!NOTE]  
>  Une instance FCI peut tirer parti de [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] pour permettre une récupération d'urgence à distance au niveau de la base de données. Pour plus d’informations, consultez [Clustering de basculement et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).  
  
 Mise en miroir de bases de données  
 > [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Nous vous recommandons d'utiliser [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] à la place.  
  
 La mise en miroir de base de données est une solution qui permet d'optimiser la disponibilité d'une base de données en utilisant presque instantanément le basculement. La mise en miroir de base de données peut être utilisée pour gérer une base de données de secours ou une *base de données miroir*pour une base de données de production correspondante désignée sous le nom de *base de données principale*. Pour plus d’informations, consultez [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Envoi des journaux de transaction  
 Comme [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] et la mise en miroir de bases de données, la copie des journaux de transaction fonctionne au niveau de la base de données. Vous pouvez utiliser la copie des journaux de transactions pour gérer une ou plusieurs bases de données de secours semi-automatique (appelées *bases de données secondaires*) pour une base de données de production unique correspondante appelée *base de données primaire*. Pour plus d’informations sur la copie des journaux de transactions, consultez [À propos de la copie des journaux de transaction &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
##  <a name="RecommendedSolutions"></a> Solutions recommandées pour l'utilisation de SQL Server pour protéger des données  
 Nous vous recommandons ce qui suit pour assurer une protection des données pour votre environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Pour la protection des données via une solution tierce de disque partagé (réseau SAN), nous vous recommandons d'utiliser les instances de cluster de basculement AlwaysOn.  
  
-   Pour la protection des données via [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nous vous recommandons d'utiliser [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
    > [!NOTE]  
    >  Si vous exécutez une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ne prend pas en charge [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], nous vous recommandons la copie des journaux de transaction. Pour plus d’informations sur les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui prennent en charge [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], consultez la section « Haute disponibilité (AlwaysOn) » de l’article [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server](windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Mise en miroir de base de données : Interopérabilité et Coexistence &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md)   
 [Fonctionnalités dépréciées du moteur de base de données dans SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
