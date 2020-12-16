---
title: Rechercher les objets ayant le plus de verrous à l’aide des événements étendus
description: Cet article explique comment rechercher des objets qui ont le plus de verrous. Les administrateurs de base de données peuvent avoir besoin de trouver les objets les plus verrouillés pour améliorer les performances de la base de données.
ms.date: 10/18/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
helpviewer_keywords:
- objects [SQL Server], extended events
- xe
- extended events [SQL Server], locks
- objects [SQL Server], locks
ms.assetid: fcbadbda-c91c-43f0-a1b5-601e40110e07
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 522017d6ced6039cd7e5b9a30cf60404eee9249a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97465500"
---
# <a name="find-the-objects-that-have-the-most-locks-taken-on-them"></a>Trouver les objets comportant le plus de verrous

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Les administrateurs de base de données ont souvent besoin d’identifier la source des verrous qui entravent les performances d’une base de données.  
  
Par exemple, vous surveillez votre serveur de production pour identifier les goulots d'étranglement possibles. Vous soupçonnez que certaines ressources sont l’objet d’une concurrence très élevée, et aimeriez connaître le nombre de verrous posés sur ces objets. Une fois que les objets les plus fréquemment verrouillés ont été identifiés, des mesures peuvent être prises pour optimiser l'accès aux objets convoités.  
  
Pour cela, utilisez l'éditeur de requêtes de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### <a name="to-find-the-objects-that-have-the-most-locks"></a>Pour trouver les objets comportant le plus de verrous  
  
1. Dans l'éditeur de requêtes, émettez les instructions suivantes.

    ```sql
    -- Find objects in a particular database that have the most
    -- lock acquired. This sample uses AdventureWorksDW2012.
    -- Create the session and add an event and target.
    
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='LockCounts')
        DROP EVENT session LockCounts ON SERVER;
    GO
    DECLARE @dbid int;
  
    SELECT @dbid = db_id('AdventureWorksDW2012');
  
    DECLARE @sql nvarchar(1024);
    SET @sql = '
        CREATE event session LockCounts ON SERVER
            ADD EVENT sqlserver.lock_acquired (WHERE database_id ='
                + CAST(@dbid AS nvarchar) +')
            ADD TARGET package0.histogram(
                SET filtering_event_name=''sqlserver.lock_acquired'',
                    source_type=0, source=''resource_0'')';
  
    EXEC (@sql);
    GO
    ALTER EVENT session LockCounts ON SERVER
        STATE=start;
    GO
    -- Create a simple workload that takes locks.
    
    USE AdventureWorksDW2012;
    GO
    SELECT TOP 1 * FROM dbo.vAssocSeqLineItems;
    GO
    -- The histogram target output is available from the
    -- sys.dm_xe_session_targets dynamic management view in
    -- XML format.
    -- The following query joins the bucketizing target output with
    -- sys.objects to obtain the object names.
    
    SELECT name, object_id, lock_count
        FROM
        (
        SELECT objstats.value('.','bigint') AS lobject_id,
            objstats.value('@count', 'bigint') AS lock_count
            FROM (
                SELECT CAST(xest.target_data AS XML)
                    LockData
                FROM     sys.dm_xe_session_targets xest
                    JOIN sys.dm_xe_sessions        xes  ON xes.address = xest.event_session_address
                    JOIN sys.server_event_sessions ses  ON xes.name    = ses.name
                WHERE xest.target_name = 'histogram' AND xes.name = 'LockCounts'
                 ) Locks
            CROSS APPLY LockData.nodes('//HistogramTarget/Slot') AS T(objstats)
        ) LockedObjects
        INNER JOIN sys.objects o  ON LockedObjects.lobject_id = o.object_id
        WHERE o.type != 'S' AND o.type = 'U'
        ORDER BY lock_count desc;
    GO
    
    -- Stop the event session.
    
    ALTER EVENT SESSION LockCounts ON SERVER
        state=stop;
    GO
    ```

> [!NOTE]
> L’exemple de code Transact-SQL précédent s’exécute sur SQL Server localement, mais peut _ne pas s’exécuter sur Azure SQL Database._ Les parties principales de l’exemple qui impliquent directement des événements, telles que `ADD EVENT sqlserver.lock_acquired`, fonctionnent également sur Azure SQL Database. Toutefois, les éléments préliminaires, tels que `sys.server_event_sessions`, doivent être modifiés en leurs équivalents Azure SQL Database comme `sys.database_event_sessions` pour que l’exemple s’exécute.
> Pour plus d’informations sur ces différences mineures entre SQL Server localement et Azure SQL Database, consultez les articles suivants :
> - [Événements étendus dans Azure SQL Database](/azure/sql-database/sql-database-xevent-db-diff-from-svr#transact-sql-differences)
> - [Objets système qui prennent en charge les événements étendus](xevents-references-system-objects.md)

Une fois que les instructions du script Transact-SQL précédent sont exécutées, l’onglet **Résultats** de l’éditeur de requêtes affiche les colonnes suivantes :
  
- name
- object_id
- lock_count
  
## <a name="see-also"></a>Voir aussi

[CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)  
[ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)  
[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql.md)  
[sys.dm_xe_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql.md)  
[sys.server_event_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)  
