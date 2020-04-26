---
title: Surveiller l’activité système à l’aide d’événements étendus | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- extended events [SQL Server], monitoring system activity
ms.assetid: d83ad88f-818c-49fe-a9a9-299f704fca53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44bb482d1385ad9b22900bb74015a779ea6750d7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62638730"
---
# <a name="monitor-system-activity-using-extended-events"></a>Surveiller l'activité système à l’aide d’événements étendus
  Cette procédure illustre l’utilisation des événements étendus avec le suivi d'événements pour Windows (ETW) pour surveiller l’activité système. Elle indique également comment utiliser les instructions CREATE EVENT SESSION, ALTER EVENT SESSION et DROP EVENT SESSION.  
  
 L’utilisation de l'éditeur de requête de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est nécessaire pour effectuer la procédure suivante. Cette dernière nécessite également l'utilisation de l'invite de commandes pour exécuter des commandes ETW.  
  
### <a name="to-monitor-system-activity-using-extended-events"></a>Pour surveiller l'activité système à l’aide d’événements étendus  
  
1.  Dans l’éditeur de requêtes, émettez les instructions suivantes afin de créer une session d'événement et d’y ajouter deux événements. Ces événements, checkpoint_begin et checkpoint_end, se déclenchent au début et à la fin d'un point de contrôle de base de données.  
  
    ```  
    CREATE EVENT SESSION test0  
    ON SERVER  
    ADD EVENT sqlserver.checkpoint_begin,  
    ADD EVENT sqlserver.checkpoint_end  
    WITH (MAX_DISPATCH_LATENCY = 1 SECONDS)  
    go  
    ```  
  
2.  Ajoutez la cible de création de compartiments avec 32 compartiments pour compter le nombre de points de contrôle en fonction de l'ID de base de données.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.histogram  
    (  
          SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id'  
    )  
    go  
    ```  
  
3.  Émettez les instructions suivantes pour ajouter la cible ETW. Cela vous permettra de voir les événements de début et de fin et de déterminer ainsi le temps requis par le point de contrôle.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.etw_classic_sync_target  
    go  
    ```  
  
4.  Émettez les instructions suivantes pour démarrer la session et lancer la collecte d'événements.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = start  
    go  
    ```  
  
5.  Émettez les instructions suivantes pour provoquer le déclenchement de trois événements.  
  
    ```  
    USE tempdb  
          checkpoint  
    go  
    USE master  
          checkpoint  
          checkpoint  
    go  
    ```  
  
6.  Émettez les instructions suivantes pour afficher le nombre d’événements.  
  
    ```  
    SELECT CAST(xest.target_data AS xml) Bucketizer_Target_Data_in_XML  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'test0'  
    go  
    ```  
  
7.  À l'invite de commandes, émettez les commandes suivantes pour afficher les données ETW.  
  
    > [!NOTE]  
    >  Pour obtenir de l’aide sur la commande **tracerpt** , entrez `tracerpt /?`à l’invite de commandes.  
  
    ```  
    logman query -ets --- List the ETW sessions. This is optional.  
    logman update XE_DEFAULT_ETW_SESSION -fd -ets --- Flush the ETW log.  
    tracerpt %temp%\xeetw.etl -o xeetw.txt --- Dump the events so they can be seen.  
    ```  
  
8.  Émettez les instructions suivantes pour arrêter la session d'événement et la supprimer du serveur.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = STOP  
    go  
  
    DROP EVENT SESSION test0  
    ON SERVER  
    go  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une SESSION d’événements &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql)   
 [Affichages catalogue des événements étendus &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql)  
 [Vues de gestion dynamique des événements étendus](../views/views.md)   
 [Cibles des Événements étendus SQL Server](../../database-engine/sql-server-extended-events-targets.md)  
  
  
