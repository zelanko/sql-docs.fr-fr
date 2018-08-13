---
title: Sys.dm_db_missing_index_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_missing_index_columns_TSQL
- sys.dm_db_missing_index_columns_TSQL
- sys.dm_db_missing_index_columns
- dm_db_missing_index_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_columns dynamic management function
- missing indexes feature [SQL Server], sys.dm_db_missing_index_columns dynamic management function
ms.assetid: 3b24e5ed-0c79-47e5-805c-a0902d0aeb86
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 65f48f853fca55961a69e4e6905e5fa148cf739f
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560189"
---
# <a name="sysdmdbmissingindexcolumns-transact-sql"></a>sys.dm_db_missing_index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les colonnes des tables de base de données dans lesquelles un index est manquant, à l'exception des index spatiaux. **Sys.dm_db_missing_index_columns** est une fonction de gestion dynamique.  

## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.dm_db_missing_index_columns(index_handle)  
```  
  
## <a name="arguments"></a>Arguments  
 *index_handle*  
 Il s'agit d'un entier qui identifie de manière unique un index manquant. Il peut être obtenu à partir des objets de gestion dynamique suivants :  
  
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)  
  
 [sys.dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**column_id**|**Int**|ID de la colonne.|  
|**column_name**|**sysname**|Nom de la colonne de la table.|  
|**column_usage**|**varchar(20)**|Indique la manière dont la colonne est utilisée par la requête. Les valeurs possibles et leurs descriptions sont :<br /><br /> L’égalité : La colonne contribue à un prédicat qui exprime l’égalité, le formulaire : <br />                        *table.column* = *constant_value*<br /><br /> INÉGALITÉ : La colonne contribue à un prédicat qui exprime l’inégalité, par exemple, un prédicat de la forme : *table.column* > *constant_value*. Tout opérateur de comparaison autre que "=" exprime l'inégalité.<br /><br /> INCLUDE : Colonne n’est pas utilisé pour évaluer un prédicat, mais il est utilisé pour une autre raison, par exemple, pour couvrir une requête.|  
  
## <a name="remarks"></a>Notes  
 Informations retournées par **sys.dm_db_missing_index_columns** est mis à jour lorsqu’une requête est optimisée par l’optimiseur de requête et n’est pas persistant. Les informations sur les index manquants sont simplement conservées jusqu'au redémarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les administrateurs de base de données doivent effectuer régulièrement des copies de sauvegarde des informations sur les index manquants s'ils souhaitent les conserver après le recyclage du serveur.  
  
## <a name="transaction-consistency"></a>Cohérence transactionnelle  
 Si une transaction crée ou supprime une table, les lignes qui contiennent les informations d'index manquants concernant les objets supprimés sont retirées de cet objet de gestion dynamique, ce qui permet de préserver la cohérence des transactions.  
  
## <a name="permissions"></a>Permissions  
 Les utilisateurs doivent bénéficier de l'autorisation VIEW SERVER STATE ou de toute autorisation qui implique l'autorisation VIEW SERVER STATE pour interroger cette fonction de gestion dynamique.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant exécute une requête sur la table `Address` puis exécute une requête à l'aide de la vue de gestion dynamique `sys.dm_db_missing_index_columns` pour renvoyer les colonnes de table auxquelles il manque un index.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode  
FROM Person.Address  
WHERE StateProvinceID = 9;  
GO  
SELECT mig.*, statement AS table_name,  
    column_id, column_name, column_usage  
FROM sys.dm_db_missing_index_details AS mid  
CROSS APPLY sys.dm_db_missing_index_columns (mid.index_handle)  
INNER JOIN sys.dm_db_missing_index_groups AS mig ON mig.index_handle = mid.index_handle  
ORDER BY mig.index_group_handle, mig.index_handle, column_id;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
