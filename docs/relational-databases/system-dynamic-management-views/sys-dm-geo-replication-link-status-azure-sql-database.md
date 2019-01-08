---
title: Sys.dm_geo_replication_link_status (base de données Azure SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 251dcb7121b568444387a1e864294095a556b827
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52396019"
---
# <a name="sysdmgeoreplicationlinkstatus-azure-sql-database"></a>sys.dm_geo_replication_link_status (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Contient une ligne pour chaque lien de réplication entre les bases de données primaires et secondaires dans un partenariat de géo-réplication. Cela inclut les bases de données primaires et secondaire. S’il existe plusieurs liens de réplication continue pour une base de données primaire donnée, cette table contient une ligne pour chacune des relations. La vue est créée dans toutes les bases de données, y compris la logique principale. Cependant, l'interrogation de cette vue dans la base de données master logique retourne un ensemble vide.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|ID unique du lien de réplication.|  
|partner_server|**sysname**|Nom du serveur logique qui contient la base de données lié.|  
|partner_database|**sysname**|Nom de la base de données lié sur le serveur logique lié.|  
|last_replication|**datetimeoffset**|Horodatage de l’accusé de réception de la dernière transaction par la base de données secondaire en fonction de l’horloge de la base de données primaire. Cette valeur est disponible sur la base de données primaire.|  
|replication_lag_sec|**Int**|Différence de temps en secondes entre la valeur last_replication et l’horodateur de validation de cette transaction sur le serveur principal basé sur l’horloge de la base de données primaire.  Cette valeur est disponible sur la base de données primaire.|  
|replication_state|**tinyint**|L’état de géo-réplication pour cette base de données :.<br /><br /> 1 = Seeding. La cible de géo-réplication est en cours d’amorçage, mais les deux bases de données ne sont pas encore synchronisés. Jusqu'à ce que l’amorçage terminé, vous ne peut pas se connecter à la base de données secondaire. Suppression de base de données secondaire du site principal annulera l’opération d’amorçage.<br /><br /> 2 = mise à jour. La base de données secondaire est dans un état transactionnellement cohérent et est constamment synchronisé avec la base de données primaire.<br /><br /> 4 = messages interrompus. Il ne s'agit pas d'une relation de copie continue active. Cet état indique généralement que la bande passante disponible pour l'interlien est insuffisante pour le niveau d'activité de transaction dans la base de données primaire. Toutefois, la relation de copie continue est toujours intacte.|  
|replication_state_desc|**nvarchar (256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|rôle|**tinyint**|Rôle de géo-réplication, une des :<br /><br /> 0 = primary. Le database_id fait référence à la base de données primaire dans le partenariat de géo-réplication.<br /><br /> 1 = la base de données secondaire.  Le database_id fait référence à la base de données primaire dans le partenariat de géo-réplication.|  
|role_desc|**nvarchar (256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Le type secondaire, un des suivants :<br /><br /> 0 ne = aucune direct connexions sont autorisées pour la base de données secondaire et la base de données n’est pas disponible pour un accès en lecture.<br /><br /> 2 = toutes les connexions sont autorisées pour la base de données dans la boucle repl secondaire ; application pour l’accès en lecture seule.|  
|secondary_allow_connections_desc|**nvarchar (256)**|Non<br /><br /> All|  
|last_commit|**datetimeoffset**|L’heure de la dernière transaction validée dans la base de données. Si récupéré sur la base de données primaire, il indique la dernière heure de validation sur la base de données primaire. Si récupéré sur la base de données secondaire, cette propriété indique l’heure de la dernière validation sur la base de données secondaire. Si récupéré sur la base de données secondaire lorsque le réplica principal du lien de réplication est arrêté, il indique jusqu'à quel point la base de données secondaire a rattrapé.|
  
> [!NOTE]  
>  Si la relation de réplication est arrêtée en supprimant la base de données secondaire (section 4.2), la ligne pour cette base de données dans le **sys.dm_geo_replication_link_status** disparaît de la vue.  
  
## <a name="permissions"></a>Autorisations  
 N’importe quel compte avec l’autorisation de view_database_state peut interroger **sys.dm_geo_replication_link_status**.  
  
## <a name="example"></a>Exemple  
 Afficher les retards de réplication et l’heure de la dernière réplication de mes bases de données secondaire.  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;base de données SQL Azure&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [Sys.geo_replication_links &#40;base de données SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [Sys.dm_operation_status &#40;base de données SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
