---
title: "Sys.resource_stats (base de données de SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 05/23/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
caps.latest.revision: "28"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dad039b91c30e4c8d89168dd90d549ec6507c750
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne les données de stockage et d'utilisation de l'UC pour Azure SQL Database. Les données sont collectées et agrégées dans des intervalles de cinq minutes. Pour chaque base de données utilisateur, il existe une ligne pour chaque fenêtre de rapports toutes les cinq minutes dans laquelle a lieu une modification de la consommation des ressources. Cela inclut l'utilisation de l'UC, la modification de la taille de stockage ou la modification de la référence de base de données. Il est possible que les bases de données inactives sans modification ne contienne pas de lignes pour chaque intervalle de cinq minutes. Les données historiques sont conservées pendant environ 14 jours.  
  
 Le **sys.resource_stats** vue a des définitions différentes selon la version du serveur de base de données SQL Azure qui est associé à la base de données. Tenez compte de ces différences et des modifications requises par votre application lors de la mise à niveau vers une nouvelle version de serveur.  
  
 Le tableau suivant décrit les colonnes disponibles dans un serveur v12 :  
  
|Colonnes (serveur v12)|Type de données| Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Heure UTC indiquant le début de l'intervalle de rapports de cinq minutes.|  
|end_time|**datetime**|Heure UTC indiquant la fin de l’intervalle de rapports de cinq minutes.|  
|database_name|**varchar**|Nom de la base de données utilisateur.|  
|sku|**varchar**|Niveau de service de la base de données. Les valeurs possibles sont les suivantes :<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium|  
|storage_in_megabytes|**float**|Taille de stockage maximale, en mégaoctets, pour la période, y compris les données de la base de données, index, procédures stockées et métadonnées.|  
|avg_cpu_percent|**numeric**|Utilisation moyenne du calcul en pourcentage de la limite de la couche de service.|  
|avg_data_io_percent|**numeric**|Utilisation moyenne des E-S en pourcentage en fonction de la limite du niveau de service.|  
|avg_log_write_percent|**numeric**|Utilisation moyenne de la ressource d'écriture en pourcentage de la limite de la couche de service.|  
|max_worker_percent|**Decimal(5,2)**|Traitements simultanés maximum (demandes) en pourcentage de la limite de niveau de service de la base de données.<br /><br /> Nombre maximal est actuellement calculée pour l’intervalle de 5 minutes basée sur les échantillons de deuxième 15 des nombres de travail simultanés.|  
|max_session_percent|**Decimal(5,2)**|Nombre maximal de sessions simultané en pourcentage de la limite de niveau de service de la base de données.<br /><br /> Nombre maximal est actuellement calculée pour l’intervalle de 5 minutes basée sur les échantillons de deuxième 15 de nombre de sessions simultanées.|  
|dtu_limit|**int**|Base de données max DTU paramètre actuel de cette base de données pendant cet intervalle.|  
  
> [!TIP]  
>  Pour plus d’informations sur ces limites et les niveaux de service, consultez les rubriques [niveaux de Service](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) et [les limites et les fonctionnalités de niveau de Service](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/).  
  
 Le tableau suivant décrit les colonnes disponibles dans un serveur v11 :  
  
|Colonnes (serveur v11)|Type de données| Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Heure UTC indiquant le début de l'intervalle de rapports de cinq minutes.|  
|end_time|**datetime**|Heure UTC indiquant la fin de l’intervalle de rapports de cinq minutes.|  
|database_name|**nvarchar**|Nom de la base de données.|  
|sku|**nvarchar**|Niveau de service de la base de données. Les valeurs possibles sont les suivantes :<br /><br /> Web<br /><br /> Business<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium|  
|usage_in_seconds|**int**|*Remarque : Cette colonne est déconseillée pour v11 et sa valeur est toujours définie sur 0.*<br /><br /> Heure de l'UC utilisée lors de la dernière mesure.<br /><br /> Pour la mesure du processeur, nous vous recommandons d’utiliser le **avg_cpu_cores_used** colonne au lieu de cette colonne.|  
|storage_in_megabytes|**decimal**|Taille de stockage maximale, en mégaoctets, pour la période, y compris les données de la base de données, index, procédures stockées et métadonnées.|  
|avg_cpu_cores_used|**decimal**|*Remarque : Cette colonne est déconseillée pour v11 et sa valeur est toujours définie sur 0.*<br /><br /> Moyenne des cœurs d'UC utilisés dans cet intervalle.|  
|avg_physical_read_iops|**decimal**|*Remarque : Cette colonne est déconseillée pour v11 et sa valeur est toujours définie sur 0.*<br /><br /> Moyenne des E/S par seconde lues dans cet intervalle.|  
|avg_physical_write_iops|**decimal**|*Remarque : Cette colonne est déconseillée pour v11 et sa valeur est toujours définie sur 0.*<br /><br /> Moyenne des E/S par seconde écrites dans cet intervalle.|  
|active_memory_used_kb|**bigint**|*Remarque : Cette colonne est déconseillée pour v11 et sa valeur est toujours définie sur 0.*<br /><br /> Capacité de mémoire active utilisée à la fin de cet intervalle.|  
|active_session_count|**int**|Nombre de sessions actives à la fin de cet intervalle.|  
|active_worker_count|**int**|Nombre de threads de travail actifs à la fin de cet intervalle.|  
|avg_cpu_percent|**decimal**|Utilisation moyenne du calcul en pourcentage de la limite de la couche de service.|  
|avg_physical_data_read_percent|**decimal**|Utilisation moyenne des E-S en pourcentage en fonction de la limite du niveau de service.|  
|avg_log_write_percent|**decimal**|Utilisation moyenne de la ressource d'écriture en pourcentage de la limite de la couche de service.|  
  
## <a name="permissions"></a>Permissions  
 Cette vue est disponible pour tous les rôles d’utilisateur disposant des autorisations pour se connecter à virtuel **master** base de données.  
  
## <a name="remarks"></a>Notes  
 Les données retournées par **sys.resource_stats** est exprimée en pourcentage de la valeur maximale autorisée des limites DTU du niveau de service et niveau de performances qui vous sont en cours d’exécution pour les bases de données basique, Standard et Premium.  Pour les niveaux « Web» et « Business », ces nombres indiquent les pourcentages selon les termes du niveau de performance Standard S2.  Par exemple, lors d'une exécution avec une base de données web, si avg_cpu_percent retourne 70 %, cela indique 70 % de la limite du niveau S2. Pour les niveaux « Web» et « Business », les pourcentages peuvent aussi atteindre un nombre qui dépasse 100 %, également basé sur la limite de niveau S2.  
  
 Lorsqu’une base de données est un membre d’un pool élastique, présentées sous forme de valeurs de pourcentage, statistiques des ressources sont exprimées en pourcentage de la limite maximale de DTU pour les bases de données défini dans la configuration du pool élastique.  
  
 Pour obtenir une vue plus granulaire de ces données, utilisez **sys.dm_db_resource_stats** vue de gestion dynamique dans une base de données utilisateur. Cette vue capture des données toutes les 15 secondes et conserve 1 heure d'historique des données.  Pour plus d’informations, consultez [sys.dm_db_resource_stats &#40; Base de données SQL Azure &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>Exemples  
 L'exemple suivant retourne toutes les bases de données dont la moyenne s'établit à au moins 80 % de l'utilisation du calcul au cours de la dernière semaine.  
  
```  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT database_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY database_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
  
 L'exemple suivant calcule le pourcentage de consommation moyenne en UDBD pour une base de données. (Cette requête fonctionne uniquement quand elle est exécutée sur un serveur v11.)  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
   FROM (VALUES (avg_cpu_percent), (avg_physical_data_read_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.resource_stats   
WHERE database_name = '<your db name>'   
ORDER BY end_time DESC;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Niveaux de service](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Limites et des fonctions de niveau de Service](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
