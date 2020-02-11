---
title: sys. dm_db_resource_stats (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1dd66834788896e6952a0352eb2a19fd1a828513
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75245962"
---
# <a name="sysdm_db_resource_stats-azure-sql-database"></a>sys.dm_db_resource_stats (base de données Azure SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne la consommation d'UC, d’E/S et de mémoire pour une base de données [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Il existe une ligne pour toutes les 15 secondes, même s’il n’existe aucune activité dans la base de données. Les données historiques sont conservées pendant environ une heure.  
  
|Colonnes|Type de données|Description|  
|-------------|---------------|-----------------|  
|end_time|**DATETIME**|Heure UTC indiquant la fin de l'intervalle de rapports actuel.|  
|avg_cpu_percent|**décimal (5, 2)**|Utilisation moyenne du calcul en pourcentage de la limite de la couche de service.|  
|avg_data_io_percent|**décimal (5, 2)**|Utilisation moyenne des e/s de données en pourcentage de la limite du niveau de service. Pour les bases de données Hyperscale, consultez [e/s de données dans statistiques d’utilisation des ressources](https://docs.microsoft.com/azure/sql-database/sql-database-hyperscale-performance-diagnostics#data-io-in-resource-utilization-statistics).|  
|avg_log_write_percent|**décimal (5, 2)**|Moyenne des écritures du journal des transactions (en Mbits/s) en pourcentage de la limite du niveau de service.|  
|avg_memory_usage_percent|**décimal (5, 2)**|Utilisation moyenne de la mémoire en pourcentage de la limite de la couche de service.<br /><br /> Cela comprend la mémoire utilisée pour les pages du pool de mémoires tampons et le stockage des objets OLTP en mémoire.|  
|xtp_storage_percent|**décimal (5, 2)**|Utilisation du stockage pour l’OLTP en mémoire en pourcentage de la limite du niveau de service (à la fin de l’intervalle de création de rapports). Cela comprend la mémoire utilisée pour le stockage des objets OLTP en mémoire suivants : les tables optimisées en mémoire, les index et les variables de table. Il comprend également la mémoire utilisée pour le traitement des opérations ALTER TABLE.<br /><br /> Retourne 0 si l’OLTP en mémoire n’est pas utilisé dans la base de données.|  
|max_worker_percent|**décimal (5, 2)**|Nombre maximal de threads de travail simultanés (demandes) en pourcentage de la limite du niveau de service de la base de données.|  
|max_session_percent|**décimal (5, 2)**|Nombre maximal de sessions simultanées en pourcentage de la limite du niveau de service de la base de données.|  
|dtu_limit|**int**|Paramètre DTU maximal de la base de données actuelle pour cette base de données au cours de cet intervalle. Pour les bases de données utilisant le modèle vCore, cette colonne a la valeur NULL.|
|cpu_limit|**décimal (5, 2)**|Nombre de vCores pour cette base de données au cours de cet intervalle. Pour les bases de données utilisant le modèle basé sur DTU, cette colonne a la valeur NULL.|
|avg_instance_cpu_percent|**décimal (5, 2)**|Utilisation moyenne du processeur de base de données en pourcentage du processus de base de données SQL.|
|avg_instance_memory_percent|**décimal (5, 2)**|Utilisation moyenne de la mémoire de la base de données en pourcentage du processus de base de données SQL.|
|avg_login_rate_percent|**décimal (5, 2)**|Identifié à titre d'information uniquement. Non pris en charge. La compatibilité future n'est pas garantie.|
|replica_role|**int**|Représente le rôle du réplica actuel avec 0 comme principal, 1 comme secondaire et 2 comme redirecteur (principal de géo-secondaire). La valeur « 1 » s’affiche lorsque vous êtes connecté avec l’intention de lecture seule pour tous les réplicas secondaires lisibles. Si vous vous connectez à une géo-secondaire sans spécifier d’intention en lecture seule, vous devez voir « 2 » (connexion au redirecteur).|
|||
  
> [!TIP]  
>  Pour plus d’informations sur ces limites et les niveaux de service, consultez les rubriques [niveaux de service](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) et [limites et fonctionnalités de niveau de service](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/).  
  
## <a name="permissions"></a>Autorisations  
 Cette vue nécessite l'autorisation VIEW DATABASE STATE.  
  
## <a name="remarks"></a>Notes  
 Les données retournées par **sys. dm_db_resource_stats** sont exprimées sous la forme d’un pourcentage des limites maximales autorisées pour le niveau de service/niveau de performances que vous exécutez.
 
 Si la base de données a basculé vers un autre serveur lors des 60 dernières minutes, l’affichage retourne uniquement les données pour le temps durant lequel elle est la base de données primaire, depuis ce basculement.  
  
 Pour obtenir une vue moins granulaire de ces données avec une période de rétention plus longue, utilisez l’affichage catalogue **sys. resource_stats** dans la base de données **Master** . Cette vue capture des données toutes les 5 minutes et conserve 14 jours d'historique des données.  Pour plus d’informations, consultez [sys. resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md).  
  
 Lorsqu’une base de données est membre d’un pool élastique, les statistiques de ressources présentées sous forme de pourcentages sont exprimées en pourcentage de la limite maximale pour les bases de données définies dans la configuration du pool élastique.  
  
## <a name="example"></a>Exemple  
  
L'exemple suivant retourne les données d'utilisation de ressources ordonnées selon l’heure la plus récente pour la base de données actuellement connectée.  
  
```  
SELECT * FROM sys.dm_db_resource_stats ORDER BY end_time DESC;  
  
```  
  
 L'exemple suivant identifie la consommation moyenne en UDBD, sous forme de pourcentage de la limite maximale autorisée d’UDBD du niveau de performance de la base de données utilisateur sur la dernière heure. Envisagez d'augmenter le niveau de performance si ces pourcentages sont souvent proches de 100 %.  
  
```  
SELECT end_time,   
  (SELECT Max(v)    
   FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS    
   value(v)) AS [avg_DTU_percent]   
FROM sys.dm_db_resource_stats;  
  
```  
  
 L'exemple suivant retourne les valeurs moyennes et maximales de pourcentage de CPU, d’E/S de données et de journaux et de consommation de mémoire sur la dernière heure.  
  
```  
SELECT    
    AVG(avg_cpu_percent) AS 'Average CPU Utilization In Percent',   
    MAX(avg_cpu_percent) AS 'Maximum CPU Utilization In Percent',   
    AVG(avg_data_io_percent) AS 'Average Data IO In Percent',   
    MAX(avg_data_io_percent) AS 'Maximum Data IO In Percent',   
    AVG(avg_log_write_percent) AS 'Average Log Write I/O Throughput Utilization In Percent',   
    MAX(avg_log_write_percent) AS 'Maximum Log Write I/O Throughput Utilization In Percent',   
    AVG(avg_memory_usage_percent) AS 'Average Memory Usage In Percent',   
    MAX(avg_memory_usage_percent) AS 'Maximum Memory Usage In Percent'   
FROM sys.dm_db_resource_stats;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys. resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Niveaux de service](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Capacités et limites des niveaux de service](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
