---
title: "Suspension et reprise de la migration de données (Stretch Database) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, pausing and resuming
- pausing Stretch Database
- resuming Stretch Database
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: Human Translation
ms.sourcegitcommit: 0fef9c7f912cb824b3f1fcf8653a82fa99a35561
ms.openlocfilehash: a291fd543d572fc621e7b59e968e7ca69d79552e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="pause-and-resume-data-migration-stretch-database"></a>Suspension et reprise de la migration de données (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Pour suspendre ou reprendre la migration de données vers Azure, sélectionnez **Stretch** pour une table dans SQL Server Management Studio, puis sélectionnez **Suspendre** pour suspendre la migration des données ou **Reprendre** pour reprendre la migration des données. Vous pouvez également utiliser Transact-SQL pour suspendre ou reprendre la migration des données.  
  
 Vous pouvez suspendre la migration des données sur des tables spécifiques pour résoudre des problèmes sur le serveur local ou optimiser la bande passante réseau disponible.  

## <a name="pause-data-migration"></a>Suspendre la migration des données  
  
### <a name="use-sql-server-management-studio-to-pause-data-migration"></a>Utilisation de SQL Server Management Studio pour suspendre la migration des données  
  
1.  Dans SQL Server Management Studio, dans l’Explorateur d’objets, sélectionnez la table pour laquelle vous souhaitez suspendre la migration des données.  
  
2.  Cliquez avec le bouton droit et sélectionnez **Stretch**, puis choisissez **Suspendre**.  
  
### <a name="use-transact-sql-to-pause-data-migration"></a>Utilisation de Transact-SQL pour suspendre la migration des données  
 Exécutez la commande suivante :  
  
```tsql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = PAUSED ) ) ;  
GO 
```  
  
## <a name="resume-data-migration"></a>Reprendre la migration des données  
  
### <a name="use-sql-server-management-studio-to-resume-data-migration"></a>Utilisation de SQL Server Management Studio pour reprendre la migration des données  
  
1.  Dans SQL Server Management Studio, dans l’Explorateur d’objets, sélectionnez la table pour laquelle vous souhaitez reprendre la migration des données.  
  
2.  Cliquez avec le bouton droit et sélectionnez **Stretch**, puis choisissez **Reprendre**.  
  
### <a name="use-transact-sql-to-resume-data-migration"></a>Utilisation de Transact-SQL pour reprendre la migration des données  
 Exécutez la commande suivante :  
  
```tsql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>   
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;  
 GO
```  

## <a name="check-whether-migration-is-active-or-paused"></a>Vérifier si la migration est active ou suspendue

### <a name="use-sql-server-management-studio-to-check-whether-migration-is-active-or-paused"></a>Utiliser SQL Server Management Studio pour vérifier si la migration est active ou suspendue
Dans SQL Server Management Studio, ouvrez **Surveillance de Stretch Database** et vérifiez la valeur de la colonne **État de la migration** . Pour plus d’informations, consultez [Surveiller et résoudre les problèmes liés à la migration des données](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).

### <a name="use-transact-sql-to-check-whether-migration-is-active-or-paused"></a>Utiliser Transact-SQL pour vérifier si la migration est active ou suspendue
Interrogez l’affichage catalogue **sys.remote_data_archive_tables** et vérifiez la valeur de la colonne **is_migration_paused** . Pour plus d’informations, consultez [sys.remote_data_archive_tables](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md).

## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[Surveiller et résoudre les problèmes liés à la migration des données](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) 
  

