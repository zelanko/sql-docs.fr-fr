---
title: Sys.dm_db_log_stats (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_log_stats_TSQL
- sys.dm_db_log_stats
- sys.dm_db_log_stats_TSQL
- dm_db_log_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_stats dynamic management function
ms.assetid: 
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba933bad47beead99ea5f645a910b1783caa280e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdblogstats-transact-sql"></a>Sys.dm_db_log_stats (Transact-SQL)   
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Retourne les attributs de niveau résumés et des informations sur les fichiers journaux des transactions de bases de données. Utilisez ces informations pour la surveillance et de diagnostics de contrôle d’intégrité des journaux de transaction.   
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 sys.dm_db_log_stats ( database_id )
```  
  
## <a name="arguments"></a>Arguments  

*database_id* | NULL | **Par défaut**

Est l’ID de la base de données. `database_id` a la valeur `int`. Les entrées valides sont le numéro d’ID de base de données, `NULL`, ou `DEFAULT`. La valeur par défaut est `NULL`. `NULL`et `DEFAULT` sont des valeurs équivalentes dans le contexte de base de données actuelle.  
La fonction intégrée `DB_ID` peut être spécifié. Lorsque vous utilisez `DB_ID` sans spécifier un nom de base de données, le niveau de compatibilité de la base de données en cours doit être supérieur ou égal à 90.

  
## <a name="tables-returned"></a>Tables retournées  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|database_id    |**int**    |ID de la base de données |  
|recovery_model |**nvarchar (60)**   |   Mode de récupération de la base de données. Les valeurs possibles sont : <br /> SIMPLE<br /> BULK_LOGGED <br /> FULL |  
|log_min_lsn    |**nvarchar(24)**   |   LSN de début dans le journal des transactions en cours. |  
|log_end_lsn    |**nvarchar(24)**   |   LSN du dernier enregistrement du journal dans le journal des transactions. |  
|current_vlf_sequence_number    |**bigint** |   Fichier journal virtuel numéro de séquence actuel au moment de l’exécution. |  
|current_vlf_size_mb    |**float**  |   Taille actuelle du fichier journal virtuel en Mo. |   
|total_vlf_count    |**bigint** |   Nombre total de fichiers journaux virtuels dans le journal des transactions. |  
|total_log_size_mb  |**float**  |   Taille du journal des transactions totale en Mo. |  
|active_vlf_count   |**bigint** |   Nombre total de fichier journal virtuel actif dans le journal des transactions. |  
|active_log_size_mb |**float**  |   Taille du journal des transactions actif total en Mo. |  
|log_truncation_holdup_reason   |**nvarchar (60)**   |   Raison de retard de troncation du journal. La valeur est identique à `log_reuse_wait_desc` colonne de `sys.databases`.  (Pour plus d’explications de ces valeurs, consultez [du journal des transactions](../../relational-databases/logs/the-transaction-log-sql-server.md)). <br />Les valeurs possibles sont : <br />NOTHING<br />CHECKPOINT<br />LOG_BACKUP<br />ACTIVE_BACKUP_OR_RESTORE<br />ACTIVE_TRANSACTION<br />DATABASE_MIRRORING<br />REPLICATION<br />DATABASE_SNAPSHOT_CREATION<br />LOG_SCAN<br />AVAILABILITY_REPLICA<br />OLDEST_PAGE<br />XTP_CHECKPOINT<br />AUTRE TEMPORAIRE |  
|log_backup_time    |**datetime**   |   Transaction sauvegarde heure du dernier journal. |   
|log_backup_lsn |**nvarchar(24)**   |   Dernière sauvegarde de journal LSN. |   
|log_since_last_log_backup_mb   |**float**  |   Taille du journal en Mo depuis la dernière sauvegarde du journal des transactions LSN. |  
|log_checkpoint_lsn |**nvarchar(24)**   |   Dernier point de contrôle LSN. |  
|log_since_last_checkpoint_mb   |**float**  |   Taille du journal en Mo depuis le dernier LSN de point de contrôle. |  
|log_recovery_lsn   |**nvarchar(24)**   |   LSN de la base de données de récupération. Si `log_recovery_lsn` se produit avant le point de contrôle LSN, `log_recovery_lsn` est la plus ancienne transaction active LSN, sinon `log_recovery_lsn` est le LSN de point de contrôle. |  
|log_recovery_size_mb   |**float**  |   Taille du journal en Mo depuis le LSN de récupération de journal. |  
|recovery_vlf_count |**bigint** |   Nombre total de fichiers journaux virtuels à restaurer, s’il y avait le redémarrage du serveur ou de basculement. |  


## <a name="permissions"></a>Permissions  
Nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
  
## <a name="examples"></a>Exemples  

### <a name="a-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-high-number-of-vlfs"></a>A. Détermination des bases de données dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance avec un grand nombre de fichiers journaux virtuels   
La requête suivante retourne les bases de données avec les fichiers journaux virtuels plus de 100 dans les fichiers journaux. Grand nombre de fichiers journaux virtuels peut affecter le temps de démarrage, de restauration et de récupération de base de données.

``` t-sql  
SELECT name AS 'Database Name', total_vlf_count AS 'VLF count' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id) 
WHERE total_vlf_count  > 100;
```   

### <a name="b-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-transaction-log-backups-older-than-4-hours"></a>B. Détermination des bases de données dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance avec les sauvegardes de journaux de transactions plus de 4 heures   
La requête suivante détermine les derniers temps de sauvegarde de journal pour les bases de données dans l’instance.

``` t-sql  
SELECT name AS 'Database Name', log_backup_time AS 'last log backup time' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id); 
```

## <a name="see-also"></a>Voir aussi  
[Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Base de données associés des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)  

  
