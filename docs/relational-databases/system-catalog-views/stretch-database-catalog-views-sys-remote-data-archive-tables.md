---
title: sys.remote_data_archive_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_tables
- sys.remote_data_archive_tables_TSQL
- remote_data_archive_tables
- remote_data_archive_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_tables catalog view
ms.assetid: 765069b7-60fd-414c-875f-3455460b75cd
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 93dfc97acab31b5078bcba569b52c64f773c775b
ms.sourcegitcommit: 04c031f7411aa33e2174be11dfced7feca8fbcda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945667"
---
# <a name="stretch-database-catalog-views---sysremotedataarchivetables"></a>Stretch Database des vues de catalogue - sys.remote_data_archive_tables
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque table distante qui stocke les données d’une table locale prenant en charge Stretch.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|L’ID d’objet de la table locale prenant en charge Stretch.|  
|**remote_database_id**|**Int**|L’identificateur local généré automatiquement de la base de données distante.|  
|**remote_table_name**|**sysname**|Le nom de la table dans la base de données distante qui correspond à la table locale prenant en charge Stretch.|  
|**filter_predicate**|**nvarchar(max)**|Prédicat de filtre, le cas échéant, qui identifie les lignes de la table à migrer. Si la valeur est null, la table entière peut être migrée.<br /><br /> Pour plus d’informations, consultez [activer de Stretch Database pour une table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) et [sélectionner les lignes à migrer à l’aide d’un prédicat de filtre](~/sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).|  
|**migration_direction**|**tinyint**|La direction dans laquelle données sont en cours de migration. Les valeurs disponibles sont les suivantes.<br/>1 (sortant)<br/>2 (entrant)|  
|**migration_direction_desc**|**nvarchar(60)**|La description de la direction dans laquelle données sont en cours de migration. Les valeurs disponibles sont les suivantes.<br/>sortant (1)<br/>trafic entrant (2)|  
|**is_migration_paused**|**bit**|Indique si migration est actuellement suspendue.|  
|**is_reconciled**|**bit**| Indique si la table distante et la table SQL Server sont synchronisées.<br/><br/>Lorsque la valeur de **is_reconciled** est 1 (true), la table distante et la table SQL Server sont synchronisés, et vous pouvez exécuter des requêtes qui incluent les données distantes.<br/><br/>Lorsque la valeur de **is_reconciled** est 0 (false), la table distante et la table SQL Server ne sont pas synchronisés. Récemment lignes migrées doivent être migrés à nouveau. Cela se produit lorsque vous restaurez la base de données Azure distante, ou lorsque vous supprimez des lignes manuellement à partir de la table distante. Jusqu'à ce que vous rapprochez les tables, vous ne pouvez pas exécuter des requêtes qui incluent les données distantes. Pour rapprocher les tables, exécuter [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md). |  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

