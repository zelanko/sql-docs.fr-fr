---
title: Objet système de mise en miroir de bases de données | Microsoft Docs
description: 'Consultez les informations sur les objets système de mise en miroir de bases de données : affichages catalogue système, vues de gestion dynamique du système et tables système.'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c37c75f9824f85705f92d1fabb6519303a76fafb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754717"
---
# <a name="database-mirroring-system-object-reference"></a>Objet système de mise en miroir de bases de données
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="system-catalog-views"></a>Vues de catalogue système

| Vue de catalogue système | Description|
| :------ | :----------------------------- |
| [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   | Contient une ligne pour chaque rôle de témoin qu'un serveur utilise dans un partenariat de mise en miroir de base de données. |
| &nbsp; | &nbsp; |

## <a name="system-dynamic-management-views"></a>Vues de gestion dynamique système

| Vue de gestion dynamique système | Description|
| :------ | :----------------------------- |
| [sys.dm_db_mirroring_auto_page_repair](../../relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-auto-page-repair.md)   | Retourne une ligne pour chaque tentative de réparation de page automatique sur toute base de données mise en miroir sur l'instance de serveur.  |
| [sys.dm_db_mirroring_connections](../../relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections.md)    | Retourne une ligne pour chaque connexion établie pour une mise en miroir de base de données. |
| &nbsp; | &nbsp; |

## <a name="system-tables"></a>Tables système

| Table système | Description|
| :------ | :----------------------------- |
| [sysdbmaintplan_databases](../../relational-databases/system-tables/sysdbmaintplan-databases-transact-sql.md)   | Retourne des informations sur les plans de maintenance de la mise en miroir de bases de données. |
| [sysdbmaintplan_history](../../relational-databases/system-tables/sysdbmaintplan-history-transact-sql.md)    | Retourne des informations sur l’historique des plans de maintenance de la mise en miroir de bases de données. |
| [sysdbmaintplan_jobs](../../relational-databases/system-tables/sysdbmaintplan-jobs-transact-sql.md)    |Retourne des informations sur les tâches liées aux plans de maintenance de la mise en miroir de bases de données.  |
| [sysdbmaintplans](../../relational-databases/system-tables/sysdbmaintplans-transact-sql.md)    | Retourne des informations sur les plans de mise en miroir de bases de données.  |
| &nbsp; | &nbsp; |


## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   

  
  
