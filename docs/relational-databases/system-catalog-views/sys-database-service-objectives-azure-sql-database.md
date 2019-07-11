---
title: Sys.database_service_objectives (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2018
ms.service: sql-database
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.topic: conceptual
keywords:
- pool élastique
- pool élastique, gestion
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 1bd16b4ac7fb0b27296fb2cc7e47ec683d761ed4
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716646"
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>Sys.database_service_objectives (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Retourne l’édition (niveau de service), un objectif de service (niveau tarifaire) et un nom du pool élastique, le cas échéant, pour une base de données SQL Azure ou Azure SQL Data Warehouse. Si vous êtes connecté à la base de données MASTER d’un serveur Azure SQL Database, retourne les informations sur toutes les bases de données. Pour Azure SQL Data Warehouse, vous devez être connecté à la base de données MASTER.  
  
  
 Pour plus d’informations sur la tarification, consultez [les options de base de données SQL et les performances : Tarification de base de données SQL](https://azure.microsoft.com/pricing/details/sql-database/) et [SQL Data Warehouse tarification](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Pour modifier les paramètres du service, consultez [ALTER DATABASE (Azure SQL Database)](../../t-sql/statements/alter-database-azure-sql-database.md) et [ALTER DATABASE (Azure SQL Data Warehouse)](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest).  
  
 La vue sys.database_service_objectives contient les colonnes suivantes.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|database_id|int|ID de la base de données unique au sein d’une instance de serveur de base de données SQL Azure. Joignable avec [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|édition|sysname|Le niveau de service pour l’entrepôt de données ou de la base de données : **Base**, **Standard**, **Premium** ou **Data Warehouse**.|  
|service_objective|sysname|Le niveau tarifaire de la base de données. Si la base de données est dans un pool élastique, retourne **ElasticPool**.<br /><br /> Sur le **base** tier, retourne **base**.<br /><br /> **Base de données unique dans un niveau de service standard** retourne une des opérations suivantes : S0, S1, S2, S3, S4, S6, S7, S9 ou S12.<br /><br /> **Base de données unique dans un niveau premium** retourne des éléments suivants : P1, P2, P4, P6, P11 ou P15.<br /><br /> **SQL Data Warehouse** retourne DW100 via DW30000c.|  
|elastic_pool_name|sysname|Le nom de la [pool élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) appartenant à la base de données. Retourne **NULL** si la base de données est une base de données unique ou un warehoue de données.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert **dbManager** autorisation sur la base de données master.  Au niveau base de données, l’utilisateur doit être le créateur ou le propriétaire.  
  
## <a name="examples"></a>Exemples  
 Cet exemple peut être exécuté sur la base de données master ou sur les bases de données utilisateur de base de données SQL Azure. La requête retourne le nom, service et informations de niveau de performances des bases de données.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
