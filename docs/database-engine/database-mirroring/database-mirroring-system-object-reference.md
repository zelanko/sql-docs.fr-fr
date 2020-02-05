---
title: Objet système de mise en miroir de bases de données | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e61f8d9df3cb6dcaf545819d630c70bc18709d15
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68041786"
---
# <a name="database-mirroring-system-object-reference"></a>Objet système de mise en miroir de bases de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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

  
  
