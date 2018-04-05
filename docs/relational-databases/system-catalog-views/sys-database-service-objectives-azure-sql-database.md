---
title: Sys.database_service_objectives (de base de données SQL Azure) | Documents Microsoft
ms.custom: ''
ms.date: 08/30/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
keywords:
- Pool élastique
- pool élastique, gestion
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 40f4d0d98cd33a57d6ab1e6f9c46ebd2174c9a15
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2018
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>sys.database_service_objectives (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Retourne l’édition (niveau de service), l’objectif de service (niveau de tarification) et le nom du pool élastique, si elle existe, pour une base de données SQL Azure ou d’un entrepôt de données SQL Azure. Si vous ouvrez une session à la base de données master sur un serveur de base de données SQL Azure, retourne des informations sur toutes les bases de données. Pour l’entrepôt de données SQL Azure, vous devez être connecté à la base de données master.  
  
  
 Pour plus d’informations sur la tarification, consultez [les options de base de données SQL et les performances : tarification de base de données SQL](https://azure.microsoft.com/en-us/pricing/details/sql-database/) et [tarification de l’entrepôt de données SQL](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Pour modifier les paramètres de service, consultez [ALTER DATABASE (base de données de SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md) et [ALTER DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
  
 La vue sys.database_service_objectives contient les colonnes suivantes.  
  
|Nom de la colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|database_id|int|ID de la base de données unique dans une instance du serveur de base de données SQL Azure. Joignable avec [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|édition|sysname|Le niveau de service pour l’entrepôt de données ou de la base de données : **base**, **Standard**, **Premium**, **usage général**,  **Critiques**, ou **l’entrepôt de données**.|  
|service_objective|sysname|Le niveau de tarification de la base de données. Si la base de données est dans un pool élastique, retourne **ElasticPool**.<br /><br /> Sur le **base** au niveau, retourne **base**.<br /><br /> Base de données dans un niveau de service standard retourne les valeurs valides actuelles pour ce niveau.<br /><br /> La base de données unique dans un niveau premium renvoie les valeurs valides actuelles pour ce niveau de service.<br /><br />Base de données dans la couche de service usage général retourne les valeurs valides actuelles pour ce niveau de service.<br /><br />Base de données dans la couche de service critique d’entreprise retourne les valeurs valides actuelles pour ce niveau de service.<br /><br /> SQL Data Warehouse retourne les valeurs valides actuelles pour l’entrepôt de données SQL.|  
|elastic_pool_name|sysname|Le nom de la [pool élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) appartenant à la base de données. Retourne **NULL** si la base de données est une base de données ou un warehoue de données.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert **dbManager** autorisation sur la base de données master.  Au niveau de la base de données, l’utilisateur doit être le créateur ou le propriétaire.  
  
## <a name="examples"></a>Exemples  
 Cet exemple peut être exécuté sur la base de données master ou sur les bases de données utilisateur. La requête retourne le nom, service et informations de niveau de performances des bases de données.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
