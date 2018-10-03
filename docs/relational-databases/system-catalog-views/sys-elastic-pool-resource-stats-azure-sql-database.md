---
title: Sys.elastic_pool_resource_stats (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
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
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 210e051088539920ad9c26e8036c7d9a911a2e4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47653127"
---
# <a name="syselasticpoolresourcestats-azure-sql-database"></a>Sys.elastic_pool_resource_stats (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne les statistiques d’utilisation de ressources pour tous les pools de bases de données élastiques dans un serveur logique. Pour chaque pool de base de données élastique, il existe une ligne pour chaque fenêtre (quatre lignes par minute) de création de rapports de 15 secondes. Cela inclut l’utilisation du processeur, e/s, journal, la consommation de stockage et session/requête simultanée par toutes les bases de données dans le pool. Ces données sont conservées pendant 14 jours. 
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12.|  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Heure UTC indiquant le début de l’intervalle de rapport de 15 secondes.|  
|**end_time**|**datetime2**|Heure UTC indiquant la fin de l’intervalle de rapport de 15 secondes.|  
|**elastic_pool_name**|**nvarchar(128)**|Nom du pool élastique de base de données.|  
|**avg_cpu_percent**|**décimale (5,2)**|Utilisation de calcul moyenne en pourcentage de la limite du pool.|  
|**avg_data_io_percent**|**décimale (5,2)**|Utilisation moyenne des e/s en pourcentage de la limite du pool.|  
|**avg_log_write_percent**|**décimale (5,2)**|L’utilisation des ressources d’écriture moyenne en pourcentage de la limite du pool.|  
|**avg_storage_percent**|**décimale (5,2)**|Utilisation de stockage moyen en pourcentage de la limite de stockage du pool.|  
|**max_worker_percent**|**décimale (5,2)**|Nombre maximal d’ouvriers simultanés (demandes) en pourcentage de la limite du pool.|  
|**max_session_percent**|**décimale (5,2)**|Nombre maximal de sessions simultané en pourcentage de la limite du pool.|  
|**elastic_pool_dtu_limit**|**Int**|Max pool élastique DTU paramètre actuel de ce pool élastique pendant cet intervalle.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Limite de stockage maximale du pool élastique actuel définition pour ce pool élastique en mégaoctets pendant cet intervalle.|
|**avg_allocated_storage_percent**|**décimale (5,2)**|Le pourcentage d’espace de données allouée par toutes les bases de données dans le pool élastique.  C’est le rapport d’espace de données allouée à la taille maximale de données pour le pool élastique.  Pour plus d’informations, consultez : [gestion de l’espace de fichier dans la base de données SQL](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|  
  
## <a name="remarks"></a>Notes  
 Cette vue existe dans la base de données master du serveur logique. Vous devez être connecté à la base de données master pour la requête **sys.elastic_pool_resource_stats**.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **dbmanager** rôle.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne les données d’utilisation de ressources classées par l’heure la plus récente pour tous les pools élastiques de base de données sur le serveur logique actuels.  
  
```  
SELECT * FROM sys.elastic_pool_resource_stats   
ORDER BY end_time DESC;  
```  
  
 L’exemple suivant calcule le pourcentage DTU moyen utilisé pour un pool donné.  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.elastic_pool_resource_stats   
WHERE elastic_pool_name = '<your pool name>'   
ORDER BY end_time DESC;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Maîtriser une croissance explosive avec des bases de données élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Créer et gérer un pool de base de données élastique SQL Database (version préliminaire)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [Sys.resource_stats &#40;base de données SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Sys.dm_db_resource_stats &#40;base de données SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
