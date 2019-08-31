---
title: sys. DM _user_db_resource_governance (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-database
ms.reviewer: ''
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
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: ea07ba28efc4ac50fdeef04bb1b3643c359ead28
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176258"
---
# <a name="sysdm_user_db_resource_governance-transact-sql"></a>sys. DM _user_db_resource_governance (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Retourne les paramètres de capacité et de configuration de la gouvernance des ressources pour une base de données Azure SQL Database.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|int|ID de la base de données, unique au sein d’un serveur Azure SQL Database.|
|**logical_database_guid**|uniqueidentifier|Guid logique pour la base de données utilisateur et qui reste dans la durée de vie d’une base de données utilisateur.  Le renommage ou la définition d’une base de données sur un autre SLO ne modifie pas le GUID. |
|**physical_database_guid**|uniqueidentifier|Guid physique d’une base de données utilisateur qui reste dans la durée de vie de l’instance physique de la base de données utilisateur. Le fait de définir sur un SLO différent entraînera la modification de cette colonne.|
|**server_name**|nvarchar|Nom du serveur logique.|
|**database_name**|nvarchar|Nom de la base de données logique.|
|**slo_name**|nvarchar|L’objectif de niveau de service et la génération de matériel.|
|**dtu_limit**|int|Limite de DTU de la base de données (NULL pour vCore).|
|**cpu_limit**|int|limite vCore de base de données (NULL pour les bases de données DTU).|
|**min_cpu**|tinyint|Pourcentage de processeur minimal qui peut être utilisé par la charge de travail de l’utilisateur.|
|**max_cpu**|tinyint|Pourcentage processeur maximal qui peut être utilisé par la charge de travail de l’utilisateur.|
|**cap_cpu**|tinyint|Seuil de pourcentage d’UC pour les groupes de charges de travail utilisateur.|
|**min_cores**|smallint|Nombre d’UC utilisées par SQL.|
|**max_dop**|smallint|Degré maximal de parallélisme utilisé par la charge de travail de l’utilisateur.|
|**min_memory**|int|Pourcentage de mémoire minimal qui peut être utilisé par la charge de travail de l’utilisateur.|
|**max_memory**|int|Pourcentage de mémoire maximal qui peut être utilisé par la charge de travail de l’utilisateur.|
|**max_sessions**|int|Limite de session pour le groupe d’utilisateurs.|
|**max_memory_grant**|int|Allocation de mémoire maximale pour chaque requête dans la charge de travail utilisateur, en pourcentage.|
|**max_db_memory**|int|Limite maximale de mémoire du pool de mémoires tampons pour la charge de travail de la base de|
|**govern_background_io**|bit|Indique si les écritures en arrière-plan sont facturées au groupe d’utilisateurs.|
|**min_db_max_size_in_mb**|bigint|Taille maximale du fichier de base de données (en Mo).|
|**max_db_max_size_in_mb**|bigint|Nombre maximal de fichiers de base de données, en Mo.|
|**default_db_max_size_in_mb**|bigint|Taille maximale du fichier de base de données par défaut, en Mo.|
|**db_file_growth_in_mb**|bigint|Croissance par défaut du fichier de base de données Azure, en Mo.|
|**initial_db_file_size_in_mb**|bigint|Taille du fichier de base de données par défaut, en Mo.|
|**log_size_in_mb**|bigint|Taille du fichier journal par défaut, en Mo.|
|**instance_cap_cpu**|int|Limite de l’UC au niveau de l’instance.|
|**instance_max_log_rate**|bigint|Taux de génération de journaux limité au niveau de l’instance, en octets par seconde.|
|**instance_max_worker_threads**|int|Limite de threads de travail au niveau de l’instance.|
|**replica_type**|int|Type de réplica, où 0 est principal et 1 est secondaire.|
|**max_transaction_size**|bigint|Espace maximal du journal utilisé par une transaction, en Ko.|
|**checkpoint_rate_mbps**|int|Bande passante des points de contrôle, en Mbits/s.|
|**checkpoint_rate_io**|int|Taux d’e/s de point de contrôle en e/s par seconde.|
|**last_updated_date_utc**|datetime|Date et heure du dernier changement ou reconfiguration du paramètre.|
|**primary_group_id**|int|ID du groupe de charge de travail utilisateur principal.|
|**primary_group_max_workers**|int|Limite de Worker au niveau du groupe de charge de travail utilisateur principal.|
|**primary_min_log_rate**|bigint|Taux de journal minimal (octets par seconde) au niveau du groupe de charge de travail utilisateur principal.|
|**primary_max_log_rate**|bigint|Taux de journal maximal (octets par seconde) au niveau du groupe de charge de travail utilisateur principal.|
|**primary_group_min_io**|int|Nombre minimal d’e/s au niveau du groupe de charge de travail utilisateur principal.|
|**primary_group_max_io**|int|Nombre maximal d’e/s au niveau du groupe de charge de travail utilisateur principal.|
|**primary_group_min_cpu**|float|Limite de pourcentage d’UC minimale au niveau du groupe de charge de travail de l’utilisateur principal.|
|**primary_group_max_cpu**|float|Limite de pourcentage de processeur maximale au niveau du groupe de charge de travail de l’utilisateur principal.|
|**primary_log_commit_fee**|int|Frais de validation de la gouvernance de taux de journal au niveau du groupe de charge de travail utilisateur principal.|
|**primary_pool_max_workers**|int|Limite Worker au niveau du pool d’utilisateurs principal.
|**pool_max_io**|int|Limite maximale d’e/s au niveau du pool d’utilisateurs principal.|
|**govern_db_memory_in_resource_pool**|bit|Indique si la taille maximale du pool de mémoires tampons est régie au niveau du pool de ressources. Généralement défini pour les bases de données dans des pools élastiques.|
|**volume_local_iops**|int|Capacité d’e/s par seconde pour le volume local (par exemple, C:, D:).|
|**volume_managed_xstore_iops**|int|Capacité d’e/s par seconde pour le compte de stockage distant.|
|**volume_external_xstore_iops**|int|Capacité d’e/s par seconde pour le compte de stockage distant utilisé par les sauvegardes et la télémétrie Azure SQL DB.|
|**volume_type_local_iops**|int|Niveau d’autorisation d’e/s par seconde pour tous les volumes locaux.|
|**volume_type_managed_xstore_iops**|int|Capacité d’e/s par seconde pour tous les comptes de stockage distant utilisés par l’instance.|
|**volume_type_external_xstore_iops**|int|Capacité d’e/s par seconde pour tous les comptes de stockage à distance utilisés par les sauvegardes et la télémétrie d’Azure SQL DB pour l’instance.|
|**volume_pfs_iops**|int|Capacité d’e/s par seconde pour le stockage de fichiers Premium.|
|**volume_type_pfs_iops**|int|Capacité d’e/s par seconde pour l’ensemble du stockage de fichiers Premium utilisé par l’instance.|
|||

## <a name="permissions"></a>Autorisations

Cette vue nécessite l'autorisation VIEW DATABASE STATE.

## <a name="remarks"></a>Notes

Les utilisateurs peuvent accéder à cette vue de gestion dynamique pour la configuration de la gouvernance des ressources et les paramètres de capacité d’une base de données Azure SQL Database. 

> [!IMPORTANT]
> La plupart des données en surface par cette DMV sont destinées à la consommation interne et peuvent faire l’objet de modifications.

## <a name="examples"></a>Exemples

L’exemple suivant retourne les données de taux de journal maximales de l’instance classées par nom de base de données dans le serveur de base de données pour une base de données unique ou regroupée.

```
SELECT database_name,
       primary_max_log_rate
FROM sys.dm_user_db_resource_governance
ORDER BY database_name DESC;  
```

## <a name="see-also"></a>Voir aussi

- [Gouvernance du taux de journal des transactions](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Limites de ressources de base de données DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-single-databases)
- [Limites de ressources vCore de base de données unique](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)
