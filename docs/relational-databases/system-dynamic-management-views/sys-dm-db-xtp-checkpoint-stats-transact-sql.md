---
title: Sys.dm_db_xtp_checkpoint_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_checkpoint_stats
- dm_db_xtp_checkpoint_stats_TSQL
- sys.dm_db_xtp_checkpoint_stats
- sys.dm_db_xtp_checkpoint_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_checkpoint_stats dynamic management view
ms.assetid: 8d0b18ca-db4d-4376-9905-3e4457727c46
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 00a859096b0a816b24f858529365dd2d7568b2ee
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396126"
---
# <a name="sysdmdbxtpcheckpointstats-transact-sql"></a>sys.dm_db_xtp_checkpoint_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Retourne des statistiques sur les opérations de point de contrôle de l'OLTP en mémoire dans la base de données active. Si la base de données n'a pas d'objets OLTP en mémoire, retourne un ensemble de résultats vide.  
  
 Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
```  
SELECT * FROM db.sys.dm_db_xtp_checkpoint_stats;  
```  
  
**[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] diffère sensiblement de versions plus récentes et fait inférieure de la rubrique à [SQL Server 2014](#bkmk_2014).**
  
## <a name="includesssql15includessssql15-mdmd-and-later"></a>[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et versions ultérieures  
 Le tableau suivant décrit les colonnes de `sys.dm_db_xtp_checkpoint_stats`, en commençant par **[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]**.  
  
|Nom de colonne|Type|Description|  
|-----------------|----------|-----------------|  
|last_lsn_processed|**bigint**|Dernier NSE vu par le contrôleur.|  
|end_of_log_lsn|**numeric(38)**|Le LSN de la fin du journal.|  
|bytes_to_end_of_log|**bigint**|Non traités par le contrôleur, correspondant aux octets entre des octets de journal `last_lsn_processed` et `end_of_log_lsn`.|  
|log_consumption_rate|**bigint**|Taux de consommation de journal des transactions par le contrôleur (en Ko/s).|  
|active_scan_time_in_ms|**bigint**|Temps passé par le contrôleur dans analyse activement le journal des transactions.|  
|total_wait_time_in_ms|**bigint**|Temps d’attente cumulé pour le contrôleur lors de l’analyse ne pas le journal.|  
|waits_for_io|**bigint**|Nombre d’attentes pour le journal d’e/s générée par le thread du contrôleur.|  
|io_wait_time_in_ms|**bigint**|Durée cumulative d’attente sur les e/s de journal par le thread du contrôleur.|  
|waits_for_new_log_count|**bigint**|Nombre d’attentes induite par le thread du contrôleur pour un nouveau journal doit être généré.|  
|new_log_wait_time_in_ms|**bigint**|Durée cumulative d’attente sur un nouveau journal par le thread du contrôleur.|  
|idle_attempts_count|**bigint**|Nombre de fois que le contrôleur a basculé vers un état inactif.|  
|tx_segments_dispatched|**bigint**|Nombre de segments vu par le contrôleur et d’expédition les sérialiseurs. Segment est une partie contiguë de journal constituant une unité de sérialisation. Il est actuellement une taille de 1 Mo, mais peut changer dans les futures.|  
|segment_bytes_dispatched|**bigint**|Nombre total d’octets d’octets envoyés par le contrôleur de sérialiseurs, depuis le redémarrage de la base de données.|  
|bytes_serialized|**bigint**|Nombre total d’octets sérialisé, car le redémarrage de la base de données.|  
|serializer_user_time_in_ms|**bigint**|Temps passé par les sérialiseurs en mode utilisateur.|  
|serializer_kernel_time_in_ms|**bigint**|Temps passé par les sérialiseurs en mode noyau.|  
|xtp_log_bytes_consumed|**bigint**|Nombre total d’octets de journal consommés depuis le redémarrage de la base de données.|  
|checkpoints_closed|**bigint**|Nombre de points de contrôle fermés depuis le redémarrage de la base de données.|  
|last_closed_checkpoint_ts|**bigint**|Horodatage du dernier point de contrôle fermé.|  
|hardened_recovery_lsn|**numeric(38)**|Récupération démarre à partir de LSN.|  
|hardened_root_file_guid|**uniqueidentifier**|GUID du fichier racine qui renforcés à la suite du dernier point de contrôle terminé.|  
|hardened_root_file_watermark|**bigint**|**Interne uniquement**. La distance, il est valide pour lire le fichier racine jusqu'à (c’est un type pertinente en interne uniquement – appelé BSN).|  
|hardened_truncation_lsn|**numeric(38)**|LSN du point de troncation.|  
|log_bytes_since_last_close|**bigint**|Octets à partir du dernier fermer à la fin actuelle du journal.|  
|time_since_last_close_in_ms|**bigint**|Heure depuis la dernière fermeture du point de contrôle.|  
|current_checkpoint_id|**bigint**|Actuellement nouveaux segments sont assignées à ce point de contrôle. Le système de point de contrôle est un pipeline. Le point de contrôle actuel est celui qui sont assignées aux segments à partir du journal. Une fois qu’il a atteint une limite, le point de contrôle est libéré par le contrôleur et un autre créé comme en cours.|  
|current_checkpoint_segment_count|**bigint**|Nombre de segments dans le point de contrôle actuel.|  
|recovery_lsn_candidate|**bigint**|**En interne uniquement**. Candidat pour être sélectionnées en tant que recoverylsn lorsque current_checkpoint_id se ferme.|  
|outstanding_checkpoint_count|**bigint**|Nombre de points de contrôle dans le pipeline en attente d’être fermé.|  
|closing_checkpoint_id|**bigint**|ID du point de contrôle de fermeture.<br /><br /> Sérialiseurs sont exécutés en parallèle, par conséquent, une fois qu’ils ont fini le point de contrôle est un candidat pour être fermée par le thread de fermeture. Mais le thread de fermeture peut fermer uniquement à la fois et il doit être dans l’ordre, par conséquent, le point de contrôle de fermeture est celui qui fonctionne sur le thread de fermeture.|  
|recovery_checkpoint_id|**bigint**|ID du point de contrôle à utiliser dans la récupération.|  
|recovery_checkpoint_ts|**bigint**|Horodatage du point de contrôle de récupération.|  
|bootstrap_recovery_lsn|**numeric(38)**|LSN de récupération pour le programme d’amorçage.|  
|bootstrap_root_file_guid|**uniqueidentifier**|GUID du fichier racine pour le programme d’amorçage.|  
|internal_error_code|**bigint**|Erreur lors de la vue par le contrôleur, le sérialiseur, fermez, et le threads de fusion.|
|bytes_of_large_data_serialized|**bigint**|La quantité de données qui a été sérialisées. |  
  
##  <a name="bkmk_2014"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 Le tableau suivant décrit les colonnes de `sys.dm_db_xtp_checkpoint_stats`, pour **[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]**.  
  
|Nom de colonne|Type|Description|  
|-----------------|----------|-----------------|  
|log_to_process_in_bytes|**bigint**|Nombre d'octets du journal entre le numéro séquentiel dans le journal (LSN) actuel du thread et la fin du journal.|  
|total_log_blocks_processed|**bigint**|Nombre total de blocs de journal traités depuis le démarrage du serveur.|  
|total_log_records_processed|**bigint**|Nombre total d'enregistrements de journal traités depuis le démarrage du serveur.|  
|xtp_log_records_processed|**bigint**|Nombre total d'enregistrements de journal de l'OLTP en mémoire traités depuis le démarrage du serveur.|  
|total_wait_time_in_ms|**bigint**|Durée cumulative d'attente en ms.|  
|waits_for_io|**bigint**|Nombre d'attentes pour les E/S du journal.|  
|io_wait_time_in_ms|**bigint**|Durée cumulative d'attente des E/S du journal.|  
|waits_for_new_log|**bigint**|Nombre d'attentes pour le nouveau journal à générer.|  
|new_log_wait_time_in_ms|**bigint**|Durée cumulative d'attente du nouveau journal.|  
|log_generated_since_last_checkpoint_in_bytes|**bigint**|Nombre d'entrées de journal générées depuis le dernier point de contrôle de l'OLTP en mémoire.|  
|ms_since_last_checkpoint|**bigint**|Durée en millisecondes depuis le dernier point de contrôle de l'OLTP en mémoire.|  
|checkpoint_lsn|**numérique (38)**|Numéro séquentiel dans le journal (LSN) de récupération associé au dernier point de vérification de l'OLTP en mémoire terminé.|  
|current_lsn|**numérique (38)**|Numéro séquentiel dans le journal de l'enregistrement de journal en cours de traitement.|  
|end_of_log_lsn|**numérique (38)**|Numéro séquentiel dans le journal à la fin du journal.|  
|task_address|**varbinary(8)**|Adresse de SOS_Task. Jointure à sys.dm_os_tasks pour rechercher des informations supplémentaires.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation `VIEW DATABASE STATE` sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de Table optimisé en mémoire &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
