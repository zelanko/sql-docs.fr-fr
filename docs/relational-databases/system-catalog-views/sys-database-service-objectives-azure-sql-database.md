---
title: Sys.database_service_objectives (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- pool élastique
- pool élastique, gestion
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 0dd29dbfe5e71f3dbae8d0330c1413dda2d3cc26
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989271"
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>Sys.database_service_objectives (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Retourne l’édition (niveau de service), un objectif de service (niveau tarifaire) et un nom du pool élastique, le cas échéant, pour une base de données SQL Azure ou Azure SQL Data Warehouse. Si connecté à la base de données master sur un serveur de base de données SQL Azure, retourne des informations sur toutes les bases de données. Pour Azure SQL Data Warehouse, vous devez être connecté à la base de données master.  
  
  
 Pour plus d’informations sur la tarification, consultez [les options de base de données SQL et les performances : tarification de base de données SQL](https://azure.microsoft.com/pricing/details/sql-database/) et [SQL Data Warehouse tarification](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Pour modifier les paramètres du service, consultez [ALTER DATABASE (Azure SQL Database)](../../t-sql/statements/alter-database-azure-sql-database.md) et [ALTER DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
  
 La vue sys.database_service_objectives contient les colonnes suivantes.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|database_id|INT|ID de la base de données unique au sein d’une instance de serveur de base de données SQL Azure. Joignable avec [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|édition|sysname|Le niveau de service pour l’entrepôt de données ou de la base de données : **base**, **Standard**, **Premium** ou **Data Warehouse**.|  
|service_objective|sysname|Le niveau tarifaire de la base de données. Si la base de données est dans un pool élastique, retourne **ElasticPool**.<br /><br /> Sur le **base** tier, retourne **base**.<br /><br /> **Base de données unique dans un niveau de service standard** retourne une des opérations suivantes : S0, S1, S2 ou S3.<br /><br /> **Base de données unique dans un niveau premium** retourne des éléments suivants : P1, P2, P4, P6/P3 ou P11.<br /><br /> **SQL Data Warehouse** retourne DW100 via DW10000c.|  
|elastic_pool_name|sysname|Le nom de la [pool élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) appartenant à la base de données. Retourne **NULL** si la base de données est une base de données unique ou un warehoue de données.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert **dbManager** autorisation sur la base de données master.  Au niveau base de données, l’utilisateur doit être le créateur ou le propriétaire.  
  
## <a name="examples"></a>Exemples  
 Cet exemple peut être exécuté sur la base de données master ou sur les bases de données utilisateur. La requête retourne le nom, service et informations de niveau de performances des bases de données.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
