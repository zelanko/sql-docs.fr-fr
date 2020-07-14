---
title: 'Mise en miroir de bases de données : Interopérabilité et coexistence'
description: Découvrez-en plus sur l’interopérabilité et la coexistence de la mise en miroir de bases de données SQL Server et d’autres fonctionnalités de SQL Server, telles que les catalogues de texte intégral et les captures instantanées de base de données.
ms.custom: seo-lt-2019
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b70007c2beaa26d93107f167013a240fe0fa5864
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751908"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>Mise en miroir de bases de données : interopérabilité et coexistence (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Vous pouvez utiliser la mise en miroir de bases de données avec les fonctionnalités et les composants suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [Instances de cluster de basculement Always On (clustering de basculement SQL Server)](../../database-engine/database-mirroring/database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [Capture de données modifiées (et suivi des modifications)](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [Instantanés de base de données](../../database-engine/database-mirroring/database-mirroring-and-database-snapshots-sql-server.md)  
  
-   [Catalogues de texte intégral](../../database-engine/database-mirroring/database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [Copie des journaux de transaction](../../database-engine/database-mirroring/database-mirroring-and-log-shipping-sql-server.md)  
  
-   [Réplication](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)  
  
 La mise en miroir de bases de données n'interopère pas avec les opérations suivantes :  
  
-   Transactions entre bases de données/transactions distribuées  
  
     Pour plus d’informations sur les raisons pour lesquelles de telles transactions ne sont pas prises en charge, consultez [Transactions entre bases de données et transactions distribuées pour des groupes de disponibilité Always On et la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
