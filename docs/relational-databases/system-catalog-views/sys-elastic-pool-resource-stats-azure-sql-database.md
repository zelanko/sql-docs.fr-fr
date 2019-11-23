---
title: sys.elastic_pool_resource_stats
titleSuffix: Azure SQL Database
ms.date: 01/28/2019
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: reference
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
author: stevestein
ms.author: sstein
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 0712785a5af3e8cc3c606a597ba02e0075c88dd9
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73843872"
---
# <a name="syselastic_pool_resource_stats-azure-sql-database"></a>sys. elastic_pool_resource_stats (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne les statistiques d’utilisation des ressources pour tous les pools élastiques dans un serveur de SQL Database. Pour chaque pool élastique, il y a une ligne pour chaque fenêtre de création de rapports de 15 secondes (quatre lignes par minute). Cela comprend le processeur, les e/s, le journal, la consommation de stockage et l’utilisation simultanée des demandes/sessions par toutes les bases de données du pool. Ces données sont conservées pendant 14 jours. 
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] v12.|  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Heure UTC indiquant le début de l’intervalle de création de rapports de 15 secondes.|  
|**end_time**|**datetime2**|Heure UTC indiquant la fin de l’intervalle de création de rapports de 15 secondes.|  
|**elastic_pool_name**|**nvarchar(128)**|Nom du pool de bases de données élastiques.|  
|**avg_cpu_percent**|**decimal(5,2)**|Utilisation moyenne du calcul en pourcentage de la limite du pool.|  
|**avg_data_io_percent**|**decimal(5,2)**|Utilisation moyenne des e/s en pourcentage en fonction de la limite du pool.|  
|**avg_log_write_percent**|**decimal(5,2)**|Utilisation moyenne des ressources d’écriture en pourcentage de la limite du pool.|  
|**avg_storage_percent**|**decimal(5,2)**|Utilisation moyenne du stockage en pourcentage de la limite de stockage du pool.|  
|**max_worker_percent**|**decimal(5,2)**|Nombre maximal de threads de travail simultanés (demandes) en pourcentage en fonction de la limite du pool.|  
|**max_session_percent**|**decimal(5,2)**|Nombre maximal de sessions simultanées en pourcentage en fonction de la limite du pool.|  
|**elastic_pool_dtu_limit**|**int**|Paramètre DTU du pool élastique maximal actuel pour ce pool élastique au cours de cet intervalle.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Paramètre de limite de stockage du pool élastique maximal actuel pour ce pool élastique en mégaoctets pendant cet intervalle.|
|**avg_allocated_storage_percent**|**decimal(5,2)**|Pourcentage d’espace de données alloué par toutes les bases de données dans le pool élastique.  Il s’agit du rapport entre l’espace de données alloué et la taille maximale des données pour le pool élastique.  Pour plus d’informations [, consultez Gestion de l’espace de fichiers dans la base de données SQL](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management) .|  
  
## <a name="remarks"></a>Notes

 Cette vue existe dans la base de données Master du serveur SQL Database. Vous devez être connecté à la base de données Master pour interroger **sys. elastic_pool_resource_stats**.  
  
## <a name="permissions"></a>Autorisations

 Requiert l’appartenance au rôle **dbmanager** .  
  
## <a name="examples"></a>Exemples

 L’exemple suivant retourne les données d’utilisation des ressources classées par l’heure la plus récente pour tous les pools de bases de données élastiques du serveur de SQL Database actuel.  
  
```sql
SELECT * FROM sys.elastic_pool_resource_stats
ORDER BY end_time DESC;  
```

 L’exemple suivant calcule la consommation moyenne en pourcentage de DTU pour un pool donné.  

```sql
SELECT start_time, end_time,
  (SELECT Max(v)
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]
FROM sys.elastic_pool_resource_stats
WHERE elastic_pool_name = '<your pool name>'
ORDER BY end_time DESC;  
```

## <a name="see-also"></a>Voir aussi

 [Maîtriser la croissance explosive avec les bases de données élastiques](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Créer et gérer un pool de bases de données élastiques SQL Database (version préliminaire)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [sys. resource_stats &#40;Azure SQL Database&#41; ](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [sys. dm_db_resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
