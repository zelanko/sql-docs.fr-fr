---
title: Sys.dm_resource_governor_resource_pools_history_ex (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_governor
- sys.resource_governor_TSQL
- resource_governor
- resource_governor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor catalog view
ms.assetid: ''
author: joesackmsft
ms.author: josack
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: 7b40d9afe54137fb31088aa8aa8b5664c90b715d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053304"
---
# <a name="sysdmresourcegovernorresourcepoolshistoryex-transact-sql"></a>Sys.dm_resource_governor_resource_pools_history_ex (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Statistiques des pools d’instantané renvoie à des intervalles de 15 secondes pour les 30 dernières minutes de ressource pour une base de données SQL Azure.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**pool_id**|int|ID du pool de ressources. N'accepte pas la valeur NULL.
|**name**|sysname|Le nom du pool de ressources. N'accepte pas la valeur NULL.|
|**snapshot_time**|datetime2|Date/heure de l’instantané de statistiques de pool de ressources réalisé|
|**duration_ms**|int|Durée entre l’instantané en cours et précédent|
|**statistics_start_time**|datetime2|Heure à laquelle les statistiques ont été réinitialisées pour ce pool. N'accepte pas la valeur NULL.|
|**active_session_count**|int|Nombre total de sessions actif dans l’instantané actuel|
|**active_worker_count**|int|Nombre total de workers dans l’instantané actuel|
|**delta_cpu_usage_ms**|int|Utilisation de l’UC en millisecondes depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_cpu_usage_preemptive_ms**|int|Appels win32 PreEmptive ne régissent pas par RG de processeur SQL, depuis la dernière capture instantanée|
|**used_data_space_kb**|bigint|Espace total utilisé dans les bases de données utilisateur associés au pool de l’utilisateur|
|**allocated_disk_space_kb**|bigint|Taille des bases de données utilisateur du fichier de données total dans associé avec le pool de l’utilisateur|
|**target_memory_kb**|bigint|Quantité de mémoire cible, en kilo-octets, que le pool de ressources tente d'atteindre. Cette valeur est basée sur les paramètres actuels et l'état du serveur. N'accepte pas la valeur NULL.|
|**used_memory_kb**|bigint|Quantité de mémoire utilisée, en kilo-octets, pour le pool de ressources. N'accepte pas la valeur NULL.|
|**cache_memory_kb**|bigint|Utilisation de la mémoire cache totale actuelle en kilo-octets. N'accepte pas la valeur NULL.|
|**compile_memory_kb**|bigint|Utilisation de la mémoire occultée totale actuelle en kilo-octets (Ko). Cette utilisation est essentiellement destinée à la compilation et l'optimisation, mais d'autres utilisations de la mémoire peuvent exister. N'accepte pas la valeur NULL.|
|**active_memgrant_count**|bigint|Nombre actuel d'allocations de mémoire. N'accepte pas la valeur NULL.|
|**active_memgrant_kb**|bigint|Somme, en kilo-octets (Ko), des allocations de mémoire actuelles. N'accepte pas la valeur NULL.|
|**used_memgrant_kb**|bigint|Quantité totale de la mémoire utilisée (occultée) actuelle provenant des allocations de mémoire. N'accepte pas la valeur NULL.|
|**delta_memgrant_timeout_count**|int|nombre de mémoire accorder des délais d’attente dans ce pool de ressources dans cette période. N'accepte pas la valeur NULL.|
|**delta_memgrant_waiter_count**|int|Nombre de requêtes actuellement en attente d'allocations de mémoire. N'accepte pas la valeur NULL.|
|**delta_out_of_memory_count**|int|Le nombre d’allocations de mémoire ayant échoué dans le pool depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_read_io_queued**|int|Le total de sorties de lecture empilées depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S.|
|**delta_read_io_issued**|int|Le total de sorties de lecture émises depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S.|
|**delta_read_io_completed**|int|Le total de sorties de lecture terminées depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_read_io_throttled**|int|Le total de sorties de lecture limitées depuis l’instantané. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S.|
|**delta_read_bytes**|bigint|Nombre total d’octets lus depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_read_io_stall_ms**|int|Durée totale (en millisecondes) entre l’arrivée d’e/s en lecture et l’achèvement depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_read_io_stall_queued_ms**|int|Durée totale (en millisecondes) entre la lecture d’arrivée des e/s et problème depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S. Valeur différente de zéro delta_read_io_stall_queued_ms signifie qu'e/s est affectée par RG.|
|**delta_write_io_queued**|int|Le total de sorties d’écriture empilées depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S.|
|**delta_write_io_issued**|int|Le total de sorties d’écriture émises depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S.|
|**delta_write_io_completed**|int|Le total de sorties d’écriture terminées depuis la dernière capture instantanée. N'accepte pas la valeur NULL|
|**delta_write_io_throttled**|int|L’écriture total IOs limitées depuis la dernière capture instantanée. N'accepte pas la valeur NULL|
|**delta_write_bytes**|bigint|Le nombre total d’octets écrits depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_write_io_stall_ms**|int|Durée totale (en millisecondes) entre l’arrivée de d’e/s d’écriture et de saisie semi-automatique depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_write_io_stall_queued_ms**|int|Durée totale (en millisecondes) entre l’arrivée de d’e/s d’écriture et leur émission depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S.|
|**delta_io_issue_delay_ms**|int|Durée totale (en millisecondes) entre l’émission planifiée et l’émission réelle des e/s depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S.|
|**max_iops_per_volume**|int|E/s maximales par seconde (IOPS) par le paramètre de volume de disque pour ce Pool. Autorise la valeur NULL. Null si le pool de ressources n'est pas régi pour les E/S.|
|**max_memory_kb**|bigint|Quantité maximale de mémoire, en kilo-octets, dont peut disposer le pool de ressources. Cette valeur est basée sur les paramètres actuels et l'état du serveur. N'accepte pas la valeur NULL.
|**max_log_rate_kb**|bigint|Taux de journal maximal (en kilo-octets par seconde) au niveau de pool de ressources.|
|**max_data_space_kb**|bigint|Paramètre pour ce pool élastique (en Ko) de la limite de stockage de max pool élastique.|
|**max_session**|int|Limite de session pour le pool|
|**max_worker**|int|Nombre maximal de threads pour le pool|
|**min_cpu_percent**|int|Configuration actuelle de la bande passante de l'UC moyenne garantie pour toutes les demandes dans le pool de ressources en cas de contention du processeur. N'accepte pas la valeur NULL.|
|**max_cpu_percent**|int|Configuration actuelle de la bande passante processeur moyenne maximale pour toutes les demandes dans le pool de ressources en cas de contention du processeur. N'accepte pas la valeur NULL.|
|**cap_cpu_percent**|int|Limite maximale d'utilisation fixe sur la bande passante de l'UC que toutes les demandes dans le pool de ressources recevront. Limite le niveau de la bande passante processeur maximal pour le niveau spécifié. La plage autorisée pour la valeur est comprise entre 1 et 100. N'accepte pas la valeur NULL.|
|**min_vcores**|decimal(5,2)|Configuration actuelle de la bande passante de l'UC moyenne garantie pour toutes les demandes dans le pool de ressources en cas de contention du processeur.  Dans les unités de vCores|
|**max_vcores**|decimal(5,2)|Configuration actuelle de la bande passante processeur moyenne maximale pour toutes les demandes dans le pool de ressources en cas de contention du processeur.  Dans l’unité de vCores|
|**cap_vcores**|decimal(5,2)|Limite maximale d'utilisation fixe sur la bande passante de l'UC que toutes les demandes dans le pool de ressources recevront.  Dans l’unité sur des vCores|
|**instance_cpu_count**|int|Nombre de processeurs configurés pour l’instance|
|** instance_cpu_percent|decimal(5,2)|Pourcentage d’UC configurés pour l’instance|
|**instance_vcores**|decimal(5,2)|Nombre de vCores configurés pour l’instance|
|**delta_log_bytes_used**|decimal(5,2)|Génération de journal total (en octets) au niveau du pool depuis la dernière capture instantanée|
|**avg_login_rate_percent**|decimal(5,2)|Nombre de connexions depuis la dernière capture instantanée, comparée au nombre maximal de connexions|
|**delta_vcores_used**|decimal(5,2)|Utilisation de calcul en nombre de vCores depuis la dernière capture instantanée.|
|**cap_vcores_used_percent**|decimal(5,2)|Utilisation de calcul moyenne en pourcentage de la limite du pool.|
|**instance_vcores_used_percent**|decimal(5,2)|Utilisation de calcul moyenne en pourcentage de la limite de l’instance SQL.|
|**avg_data_io_percent**|decimal(5,2)|Utilisation moyenne des e/s en pourcentage de la limite du pool.|
|**avg_log_write_percent**|decimal(5,2)|L’utilisation des ressources d’écriture moyenne en pourcentage de la limite du pool.|
|**avg_storage_percent**|decimal(5,2)|Utilisation de stockage moyen en pourcentage de la limite de stockage du pool.|
|**avg_allocated_storage_percent**|decimal(5,2)|Le pourcentage d’espace de données allouée par toutes les bases de données dans le pool élastique. C’est le rapport d’espace de données allouée à la taille maximale de données pour le pool élastique. Pour plus d’informations, consultez : Gestion de l’espace fichier dans la base de données SQL|
|**max_worker_percent**|decimal(5,2)|Nombre maximal d’ouvriers simultanés (demandes) en pourcentage de la limite du pool.|
|**max_session_percent**|decimal(5,2)|Nombre maximal de sessions simultané en pourcentage de la limite du pool.|
|||

## <a name="permissions"></a>Autorisations

Cette vue nécessite l’autorisation VIEW SERVER STATE.

## <a name="remarks"></a>Notes

Les utilisateurs peuvent accéder à cette vue de gestion dynamique pour surveiller de près de la consommation des ressources en temps réel pour le pool de charge de travail utilisateur, ainsi que des pools internes du système de l’instance de base de données SQL Azure.

> [!IMPORTANT]
> La plupart des données signalées par cette DMV est prévu pour une utilisation interne et est susceptible de changer.

## <a name="examples"></a>Exemples

L’exemple suivant retourne les données de taux de journal maximale et la consommation à chaque instantané par pool d’utilisateur  

```sql
select snapshot_time, name, max_log_rate_kb, delta_log_bytes_used from sys.dm_resource_governor_resource_pools_history_ex where name like 'UserPool%' order by snapshot_time desc
```

L’exemple suivant renvoie des informations similaires en tant que sys.elastic_pool_resource_stats sans avoir à se connecter à Master logique

```sql
select snapshot_time, name, cap_vcores_used_percent,
  avg_data_io_percent,  
  avg_log_write_percent,
  avg_storage_percent,
  avg_allocated_storage_percent,
  max_data_space_kb,
  max_worker_percent,
  max_session_percent
    from sys.dm_resource_governor_resource_pools_history_ex where name like 'UserPool%' order by snapshot_time desc
```

## <a name="see-also"></a>Voir aussi

- [Gouvernance de taux de journal de traduction](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Limites de ressources DTU de pool élastique](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [Limites de ressources de pool élastique vCore](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
