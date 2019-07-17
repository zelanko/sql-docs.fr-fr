---
title: Sys.dm_continuous_copy_status (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_continuous_copy_status_TSQL
- dm_continuous_copy_status_TSQL
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
dev_langs:
- TSQL
helpviewer_keywords:
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
ms.assetid: 411b2e71-4421-4ef5-900d-5af068750899
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: cace39108f3f99d5c165f42b4337e837e1fb7c5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68121028"
---
# <a name="sysdmcontinuouscopystatus-azure-sql-database"></a>sys.dm_continuous_copy_status (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque base de données utilisateur (V11) qui est actuellement engagée dans une relation de copie continue de géo-réplication. Si plusieurs relations de copie continue sont initialisées pour une base de données primaire donnée, cette table contient une ligne pour chaque base de données secondaire active.  
  
Si vous utilisez SQL Database V12, vous devez utiliser [sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) (étant donné que *sys.dm_continuous_copy_status* s’applique uniquement aux V11).

  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**copy_guid**|**uniqueidentifier**|ID unique de la base de données réplica.|  
|**partner_server**|**sysname**|Nom du serveur SQL Database lié.|  
|**partner_database**|**sysname**|Nom de la base de données liée sur le serveur SQL Database lié.|  
|**last_replication**|**datetimeoffset**|Horodateur de la dernière transaction dupliquée appliquée.|  
|**replication_lag_sec**|**Int**|Décalage horaire en secondes entre l'heure actuelle et l'horodateur de la dernière transaction validée dans la base de données primaire qui n'a pas été acceptée par la base de données secondaire active.|  
|**replication_state**|**tinyint**|L’état de réplication de copie continue pour cette base de données. Voici les valeurs possibles et leurs descriptions.<br /><br /> 1 : L’amorçage. La cible de réplication est amorcée et est dans un état incohérent d'un point de vue transactionnel. Tant que l'amorçage n'est pas terminé, vous ne pouvez pas vous connecter à la base de données secondaire active. <br />2 : Rattrapage. La base de données secondaire active rattrape la base de données primaire et est dans un état cohérent d'un point de vue transactionnel.<br />3 : Réamorçage. La base de données secondaire active est automatiquement réamorcée, en raison d'une erreur irrécupérable de réplication.<br />4 : Suspendu. Il ne s'agit pas d'une relation de copie continue active. Cet état indique généralement que la bande passante disponible pour l'interlien est insuffisante pour le niveau d'activité de transaction dans la base de données primaire. Toutefois, la relation de copie continue est toujours intacte.|  
|**replication_state_desc**|**nvarchar (256)**|Description de replication_state :<br /><br /> SEEDING<br /><br /> CATCH_UP<br /><br /> RE_SEEDING<br /><br /> SUSPENDED|  
|**is_rpo_limit_reached**|**bit**|A toujours pour valeur 0.|  
|**is_target_role**|**bit**|0 = Source de la relation de copie<br /><br /> 1 = Cible de la relation de copie|  
|**is_interlink_connected**|**bit**|1 = L'interlien est connecté.<br /><br /> 0 = L'interlien est déconnecté.|  
  
## <a name="permissions"></a>Autorisations  
 Pour récupérer des données, nécessite l’appartenance dans le **db_owner** rôle de base de données. L’utilisateur dbo, les membres de la **dbmanager** rôle de base de données et la connexion sa peuvent interroger cette vue ainsi.  
  
## <a name="remarks"></a>Notes  
 Le **sys.dm_continuous_copy_status** vue est créée dans le **ressource** est visible dans toutes les bases de données, y compris la logique principale et la base de données. Cependant, l'interrogation de cette vue dans la base de données master logique retourne un ensemble vide.  
  
 Si la relation de copie continue est interrompue sur une base de données, la ligne pour cette base de données dans le **sys.dm_continuous_copy_status** disparaît de la vue.  
  
 Comme le **sys.dm_database_copies** vue, **sys.dm_continuous_copy_status** reflète l’état de la relation de copie continue dans lequel la base de données est soit principal ou active secondaire . Contrairement aux **sys.dm_database_copies**, **sys.dm_continuous_copy_status** contient plusieurs colonnes qui fournissent des informations sur les opérations et les performances. Ces colonnes comprennent **last_replication**, et **replication_lag_sec**...  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.dm_database_copies &#40;base de données SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)   
 [Procédures stockées de géo-réplication Active &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)  
  
  
