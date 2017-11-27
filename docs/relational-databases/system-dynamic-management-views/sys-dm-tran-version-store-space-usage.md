---
title: Sys.dm_tran_version_store_space_usage (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 04/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_version_store_space_usage_TSQL
- sys.dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_tran_version_store_space_usage dynamic management view
ms.assetid: 7ab44517-0351-4f91-bdd9-7cf940f03c51
caps.latest.revision: "10"
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: 8488ee0a8bb823438071cb912bd56c08af640b42
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmtranversionstorespaceusage-transact-sql"></a>Sys.dm_tran_version_store_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Retourne une table qui affiche l’espace total dans tempdb utilisé par les enregistrements de magasin de version pour chaque base de données. **Sys.dm_tran_version_store_space_usage** est efficace et performant pour exécuter comme il ne naviguer dans la banque des versions individuelles enregistre et retourne un espace magasin version agrégée consommé dans tempdb par base de données.
  
Chaque enregistrement avec contrôle de version est stocké sous forme de données binaires, avec des informations de suivi ou d'état. À l'instar des enregistrements des tables de la base de données, ceux de la banque des versions sont stockés dans des pages de 8 192 octets. Si un enregistrement excède ces 8 192 octets, il est réparti sur deux enregistrements.  
  
Comme l'enregistrement avec contrôle de version est stocké sous forme binaire, cela ne pose pas de problème avec les différents classements des différentes bases de données. Utilisez **sys.dm_tran_version_store_space_usage** à surveiller et planifier la taille de tempdb basée sur l’utilisation de l’espace de magasin de version des bases de données dans une instance de SQL Server.
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID de base de données de la base de données.|  
|**reserved_page_count**|**bigint**|Nombre total des pages réservées dans tempdb pour la version de stockage des enregistrements de la base de données.|  
|**reserved_space_kb**|**bigint**|Espace total utilisé en kilo-octets dans tempdb pour la version de stockage des enregistrements de la base de données.|  
  
## <a name="permissions"></a>Permissions  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   

## <a name="examples"></a>Exemples  
 La requête suivante peut être utilisée pour déterminer l’espace utilisé dans tempdb par la banque des versions de chaque base de données dans une instance de SQL Server. 
  
```tsql  
SELECT 
  DB_NAME(database_id) as 'Database Name',
  reserved_page_count,
  reserved_space_kb 
FROM sys.dm_tran_version_store_space_usage;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Database Name            reserved_page_count reserved_space_kb  
------------------------ -------------------- -----------  
msdb                      0                    0             
AdventureWorks2016        10                   80             
AdventureWorks2016DW      0                    0             
WideWorldImporters        20                   160             
```
 
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique relatives aux transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
