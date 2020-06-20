---
title: 'Mise en miroir de bases de données : interopérabilité et coexistence (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 85b1f5eccc96e4ba1685a6e8d2ec8a5c428e2c8c
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934310"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>Mise en miroir de bases de données : interopérabilité et coexistence (SQL Server)
  Vous pouvez utiliser la mise en miroir de bases de données avec les fonctionnalités et les composants suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [Instances de cluster de basculement AlwaysOn (clustering de basculement SQL Server)](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [Capture de données modifiées (et suivi des modifications)](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [Instantanés de base de données](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [Catalogues de texte intégral](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [Copie des journaux de transaction](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [Réplication](database-mirroring-and-replication-sql-server.md)  
  
 La mise en miroir de bases de données n'interopère pas avec les opérations suivantes :  
  
-   Transactions entre bases de données/transactions distribuées  
  
     Pour plus d’informations sur les raisons pour lesquelles de telles transactions ne sont pas prises en charge, consultez [Transactions entre bases de données non prises en charge pour la mise en miroir de bases de données ou les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
