---
title: sys.dm_user_db_resource_governance (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governance
- sys.resource_governance_TSQL
- resource_governance
- resource_governance_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governance catalog view
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: bb4c43fa4193d9254d7f06f24bd903f974739e87
ms.sourcegitcommit: a9a03f9a7ec4dad507d2dfd5ca33571580114826
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58567635"
---
# <a name="sysdmuserdbresourcegovernance-transact-sql"></a>sys.dm_user_db_resource_governance (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Retourne la gouvernance des ressources des paramètres de configuration et de la capacité pour une base de données de base de données SQL Azure.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|INT|ID de la base de données unique au sein d’un serveur de base de données SQL Azure.|
|**logical_database_guid**|UNIQUEIDENTIFIER|Guid logique pour la base de données utilisateur et reste tout au long de la base de données utilisateur.  Renommer ou une base de données vers un autre SLO ne modifie pas le GUID. |
|**physical_database_guid**|UNIQUEIDENTIFIER|Guid physique pour une base de données utilisateur qui reste tout au long de l’instance physique de la base de données utilisateur. Paramètre pour un SLO différents entraîne cette colonne à modifier.|
|**server_name**|NVARCHAR|Nom du serveur logique.|
|**database_name**|NVARCHAR|Nom de la base de données logique.|
|**slo_name**|NVARCHAR|Service objectif génération et au niveau matériel.|
|**dtu_limit**|INT|Limite DTU de base de données (NULL pour vCore).|
|**cpu_limit**|INT|limite de vCore de base de données (NULL pour les bases de données DTU).|
|**min_cpu**|TINYINT|Pourcentage d’UC minimale qui peut être utilisé par les charges de travail utilisateur.|
|**max_cpu**|TINYINT|Pourcentage d’UC maximal qui peut être utilisé par les charges de travail utilisateur.|
|**cap_cpu**|TINYINT|Limite de pourcentage d’UC pour les groupes de charges de travail utilisateur.|
|**min_cores**|SMALLINT|Nombre d’unités centrales utilisées par SQL.|
|**max_dop**|SMALLINT|Degré maximal de parallélisme utilisé par les charges de travail utilisateur.|
|**min_memory**|INT|Pourcentage de mémoire minimale qui peut être utilisé par les charges de travail utilisateur.|
|**max_memory**|INT|Pourcentage de mémoire maximale qui peut être utilisé par les charges de travail utilisateur.|
|**max_sessions**|INT|Limite de session pour le groupe d’utilisateurs.|
|**max_memory_grant**|INT|Allocation de la mémoire maximale pour chaque requête de charge de travail utilisateur, en pourcentage.|
|**max_db_memory**|INT|Limite de mémoire de pool de mémoire tampon maximale pour la charge de travail de base de données utilisateur|
|**govern_background_io**|bit|Indique si les écritures en arrière-plan sont facturés au groupe d’utilisateurs.|
|**min_db_max_size_in_mb**|BIGINT|Taille de fichier de base de données Max minimale, en Mo.|
|**max_db_max_size_in_mb**|BIGINT|Nombre maximal de base de données fichier maximale, en Mo.|
|**default_db_max_size_in_mb**|BIGINT|Valeur par défaut de la taille de fichier de base de données maximale, en Mo.|
|**db_file_growth_in_mb**|BIGINT|Croissance par défaut du fichier de base de données azure, en Mo.|
|**initial_db_file_size_in_mb**|BIGINT|Taille de fichier de base de données par défaut, en Mo.|
|**log_size_in_mb**|BIGINT|Par défaut taille du fichier journal, en Mo.|
|**instance_cap_cpu**|INT|Limite du processeur au niveau de l’instance.|
|**instance_max_log_rate**|BIGINT|Génération d’enregistrement limite de taux au niveau de l’instance, en octets par seconde.|
|**instance_max_worker_threads**|INT|Nombre de threads de travail au niveau de l’instance.|
|**replica_type**|INT|Type de réplica, où 0 est primaire, et 1 secondaire.|
|**max_transaction_size**|BIGINT|Espace de journal maximale utilisée par une transaction, en Ko.|
|**checkpoint_rate_mbps**|INT|Bande passante du point de contrôle, en Mbits/s.|
|**checkpoint_rate_io**|INT|Point de contrôle d’e/s taux en e/s par seconde.|
|**last_updated_date_utc**|DATETIME|Date et heure de la dernière modification du paramètre ou de reconfiguration.|
|**primary_group_id**|INT|ID de groupe de charge de travail d’utilisateur principal.|
|**primary_group_max_workers**|INT|Limite de travail au niveau de groupe de charge de travail utilisateur principal.|
|**primary_min_log_rate**|BIGINT|Taux de journalisation minimum (octets par seconde) au niveau de groupe de charge de travail utilisateur principal.|
|**primary_max_log_rate**|BIGINT|Taux de journal maximale (octets par seconde) au niveau de groupe de charge de travail utilisateur principal.|
|**primary_group_min_io**|INT|E/s minimale au niveau de groupe de charge de travail utilisateur principal.|
|**primary_group_max_io**|INT|E/s maximales au niveau de groupe de charge de travail utilisateur principal.|
|**primary_group_min_cpu**|FLOAT|Limite de pourcentage processeur minimale au niveau de groupe de charge de travail utilisateur principal.|
|**primary_group_max_cpu**|FLOAT|Limite maximale de pourcentage de l’UC au niveau de groupe de charge de travail utilisateur principal.|
|**primary_log_commit_fee**|INT|Journal taux gouvernance validation frais au niveau de groupe de charge de travail utilisateur principal.|
|**primary_pool_max_workers**|INT|Limite de travail au niveau du pool principal d’utilisateur.
|**pool_max_io**|INT|Limite d’e/s maximale au niveau du pool principal d’utilisateur.|
|**govern_db_memory_in_resource_pool**|bit|Indique si la taille maximale du pool de mémoires tampons est régie au niveau du pool de ressources. Définissez généralement des bases de données dans les pools élastiques.|
|**volume_local_iops**|INT|E/s par seconde plafond de volume local (par exemple, C:, D:).|
|**volume_managed_xstore_iops**|INT|E/s par seconde plafond pour le compte de stockage à distance.|
|**volume_external_xstore_iops**|INT|E/s par limite de deuxième compte de stockage à distance utilisé par les données de télémétrie et les sauvegardes de base de données SQL Azure.|
|**volume_type_local_iops**|INT|E/s par seconde cap pour tous les volumes locaux.|
|**volume_type_managed_xstore_iops**|INT|E/s par seconde cap pour tous les comptes de stockage distant utilisé par l’instance.|
|**volume_type_external_xstore_iops**|INT|E/s par seconde cap pour tous les comptes de stockage distant utilisé par les sauvegardes de base de données SQL Azure et les données de télémétrie pour l’instance.|
|**volume_pfs_iops**|INT|E/s par deuxième extrémité premium stockage de fichiers.|
|**volume_type_pfs_iops**|INT|E/s par seconde cap pour tout le stockage fichier premium utilisé par l’instance.|
|||

## <a name="permissions"></a>Autorisations

Cette vue nécessite l'autorisation VIEW DATABASE STATE.

## <a name="remarks"></a>Notes

Les utilisateurs peuvent accéder à cette vue de gestion dynamique pour la configuration de gouvernance des ressources et les paramètres de capacité pour une base de données de base de données SQL Azure. 

> [!IMPORTANT]
> La plupart des données signalées par cette DMV est prévu pour une utilisation interne et est susceptible de changer.

## <a name="examples"></a>Exemples

L’exemple suivant retourne l’instance maximale journal taux données classées par nom de la base de données au sein du serveur de base de données pour une base de données unique ou regroupée.

```
SELECT database_name,
       primary_max_log_rate
FROM sys.dm_user_db_resource_governance
ORDER BY database_name DESC;  
```

## <a name="see-also"></a>Voir aussi

- [Gouvernance de taux de journaux de transaction](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Limites de ressources DTU de base de données unique](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-single-databases)
- [Limites de ressources vCore de base de données unique](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)
