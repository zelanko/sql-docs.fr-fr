---
description: sys.dm_db_xtp_index_stats (Transact-SQL)
title: sys. dm_db_xtp_index_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_index_stats
- dm_db_xtp_index_stats
- sys.dm_db_xtp_index_stats_TSQL
- dm_db_xtp_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_index_stats dynamic management view
ms.assetid: 8d0a50b8-2015-4576-930f-e3307dfc888e
author: CarlRabeler
ms.author: carlrab
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 096398c66e43ae36a9d2565394a7621ad45a4260
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475054"
---
# <a name="sysdm_db_xtp_index_stats-transact-sql"></a>sys.dm_db_xtp_index_stats (Transact-SQL)
[!INCLUDE[sql-asdb-asdbmi](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

  Contient les statistiques collectées depuis le dernier redémarrage de la base de données.  
  
 Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md) et [instructions pour l’utilisation d’index sur des tables optimisées en mémoire](https://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b).  

  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|ID de l'objet auquel appartient cet index.|  
|xtp_object_id|**bigint**|ID interne correspondant à la version actuelle de l’objet.<br /><br /> Remarque : s’applique à [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] .|  
|index_id|**bigint**|Identificateur de l'index. L'index_id n'est unique qu'à l'intérieur de l'objet.|  
|scans_started|**bigint**|Nombre d'analyses d'index de l'OLTP en mémoire effectuées. Chaque sélection, insertion, mise à jour ou suppression nécessite une analyse d'index.|  
|scans_retries|**bigint**|Nombre d'analyses d'index qui doivent être retentées.|  
|rows_returned|**bigint**|Nombre cumulatif de lignes retournées depuis la création de la table ou le démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rows_touched|**bigint**|Nombre cumulatif de lignes auxquelles il a été possible d'accéder depuis la création de la table ou le démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rows_expiring|**bigint**|À usage interne uniquement|  
|rows_expired|**bigint**|À usage interne uniquement|  
|rows_expired_removed|**bigint**|À usage interne uniquement|  
|phantom_scans_started|**bigint**|À usage interne uniquement|  
|phatom_scans_retries|**bigint**|À usage interne uniquement|  
|phantom_rows_touched|**bigint**|À usage interne uniquement|  
|phantom_expiring_rows_encountered|**bigint**|À usage interne uniquement|  
|phantom_expired_rows_encountered|**bigint**|À usage interne uniquement|  
|phantom_expired_removed_rows_encountered|**bigint**|À usage interne uniquement|  
|phantom_expired_rows_removed|**bigint**|À usage interne uniquement|  
|object_address|**varbinary (8)**|À usage interne uniquement|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation VIEW DATABASE STATE sur la base de données active.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique des tables à mémoire optimisée &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
