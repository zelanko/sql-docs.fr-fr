---
title: Créer une session d’événements étendus à l’aide de l’éditeur de requête | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- create extended events session
- extended events [SQL Server], create session
ms.assetid: cba0e02b-b201-4863-bf1b-9164e68e5fa8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 648370ecdd2938b6fb425955dc02da8960f884c2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934530"
---
# <a name="create-an-extended-events-session-using-query-editor"></a>Créer une session d'événements étendus à l'aide de l'éditeur de requête
  Vous pouvez créer une session d'événements étendus à l'aide de l'éditeur de requête, ou vous pouvez créer une session dans l'Explorateur d'objets. Dans l’Explorateur d’objets, les événements étendus fournissent deux interfaces utilisateur que vous pouvez utiliser pour créer, modifier et afficher des données de session d’événements : un assistant qui vous guide tout au long du processus de création de la session d’événements et une interface utilisateur de nouvelle session qui fournit des options de configuration plus avancées. Vous pouvez créer des sessions d'événements étendus pour diagnostiquer le suivi SQL Server, qui vous permet de résoudre des problèmes tels que :  
  
-   Rechercher les requêtes les plus onéreuses  
  
-   Rechercher les causes premières d'une contention de verrouillage  
  
-   Rechercher une requête qui bloque d'autres requêtes  
  
-   Remédier à l'utilisation excessive du processeur due à la recompilation de requêtes  
  
-   Résoudre les problèmes de blocages  
  
 Pour plus d’informations sur la création d’une session Événements étendus à l’aide de l’Assistant Nouvelle session, consultez [Créer une session d’événements étendus à l’aide de l’Assistant &#40;Explorateur d’objets&#41;](../ssms/object/object-explorer.md). Pour plus d’informations sur la création d’une session d’événements étendus en utilisant l’interface utilisateur de nouvelle session, consultez [Créer une session Événements étendus à l’aide de la boîte de dialogue Nouvelle session](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md).  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> Autorisations  
 Pour créer une session d'événements étendus, vous devez disposer de l'autorisation ALTER ANY EVENT SESSION.  
  
## <a name="creating-an-extended-events-session-using-query-editor"></a>Création d'une session d'événements étendus à l'aide de l'éditeur de requête  
  
#### <a name="to-create-an-extended-events-session"></a>Pour créer une session d'événements étendus  
  
1.  La procédure suivante indique comment créer une session d'événements étendus en utilisant l'Éditeur de requête dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
     Déterminez quels événements vous souhaitez utiliser dans la session. Pour consulter tous les événements qui sont disponibles, avec le mot clé et le canal, utilisez la requête suivante :  
  
    > [!NOTE]  
    >  Pour plus d’informations sur les mots clés et les canaux, consultez [Packages d’événements étendus SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md).  
  
    ```  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
       (  
       SELECT event_package = o.package_guid, o.description,   
       event=c.object_name, channel = v.map_value  
       FROM sys.dm_xe_objects o  
       LEFT JOIN sys.dm_xe_object_columns c ON o.name = c.object_name  
       INNER JOIN sys.dm_xe_map_values v ON c.type_name = v.name   
       AND c.column_value = cast(v.map_key AS nvarchar)  
       WHERE object_type = 'event' AND (c.name = 'CHANNEL' or c.name IS NULL)  
       ) c LEFT JOIN   
       (  
       SELECT event_package = c.object_package_guid, event = c.object_name,   
       keyword = v.map_value  
       FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
       ON c.type_name = v.name AND c.column_value = v.map_key   
       AND c.type_package_guid = v.object_package_guid  
       INNER JOIN sys.dm_xe_objects o ON o.name = c.object_name   
       AND o.package_guid = c.object_package_guid  
       WHERE object_type = 'event' AND c.name = 'KEYWORD'   
       ) k  
       ON  
       k.event_package = c.event_package AND (k.event=c.event or k.event IS NULL)  
       INNER JOIN sys.dm_xe_packages p ON p.guid = c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
2.  Dans une nouvelle fenêtre de requête, ajoutez les instructions suivantes pour créer une session d’événements, en remplaçant *session_name* par le nom de session à utiliser :  
  
    > [!IMPORTANT]  
    >  Les étapes 2 à 6 de cette procédure décrivent chaque section de la définition de session d'événements. Vous devez ajouter toutes les instructions dans une seule fenêtre de requête avant l'exécution. Pour obtenir un exemple complet, consultez la section Exemple de cette rubrique.  
  
    ```  
    CREATE EVENT SESSION session_name   
    ON SERVER  
    ```  
  
3.  Ajoutez les événements à surveiller, au format *package_name*.*event_name*. Pour chaque événement, ajoutez une ligne semblable à la suivante :  
  
    ```  
    ADD EVENT package_name.event_name  
    ```  
  
     Par exemple :  
  
    ```  
    ADD EVENT sqlserver.file_read_completed,  
    ADD EVENT sqlserver.file_write_completed  
    ```  
  
4.  (Facultatif) Après avoir ajouté un événement, vous pouvez ajouter des actions à entreprendre. Vous pouvez également ajouter des prédicats. Les prédicats sont utilisés pour établir des critères pour la consommation des informations d'événements par la cible. Les actions sont ajoutées à l'aide d'une clause ACTION, et les prédicats sont ajoutés à l'aide d'une clause WHERE. Par exemple, pour ajouter une action et un prédicat là où le texte [!INCLUDE[tsql](../includes/tsql-md.md)] est capturé pour l’événement sqlserver.file_read_completed, où l’ID de fichier correspond à 1, vous devez inclure l’instruction suivante :  
  
    ```  
    ADD EVENT sqlserver.file_read_completed  
       (ACTION (sqlserver.sql_text)  
       WHERE file_id = 1),  
    ```  
  
    -   Pour afficher les actions disponibles, utilisez la requête suivante :  
  
        ```  
        SELECT p.name AS 'package_name', xo.name AS 'action_name', xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'action'  
        AND (xo.capabilities & 1 = 0   
        OR xo.capabilities IS NULL)  
        ORDER BY p.name, xo.name  
        ```  
  
    -   Pour afficher les prédicats disponibles pour un événement, utilisez la requête suivante, en remplaçant *event_name* par le nom de l’événement pour lequel vous souhaitez ajouter un prédicat :  
  
        ```  
        SELECT *  
        FROM sys.dm_xe_object_columns  
        WHERE object_name = 'event_name'  
        AND column_type = 'data'  
        ```  
  
         Par exemple :  
  
        ```  
        SELECT *   
        FROM sys.dm_xe_object_columns   
        WHERE object_name = 'file_read_completed'  
        AND column_type = 'data'  
        ```  
  
         Sachez que vous pouvez également ajouter des sources de prédicat globales. Une source de prédicat globale peut être utilisée dans toute expression de prédicat. Pour afficher les sources de prédicat globales disponibles, utilisez la requête suivante :  
  
        ```  
        SELECT p.name AS package_name, xo.name AS predicate_name  
           , xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'pred_source'  
        ORDER BY p.name, xo.name  
        ```  
  
         Par exemple, vous pouvez utiliser l'expression de prédicat suivante pour spécifier que les données doivent uniquement être collectées pour un événement les cinq premières fois qu'un événement se produit.  
  
        ```  
        WHERE package0.counter <= 5  
        ```  
  
5.  Ajoutez la cible souhaitée, où les données d'événement seront traitées et consommées. Utilisez le format suivant :  
  
    ```  
    ADD TARGET package_name.target_name  
    ```  
  
     L'exemple suivant ajoute la cible de fichier asynchrone :  
  
    ```  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
    ```  
  
     Pour consulter la liste de cibles disponibles, utilisez la requête suivante :  
  
    ```  
    SELECT p.name AS 'package_name', xo.name AS 'target_name'  
       , xo.description, xo.object_type   
    FROM sys.dm_xe_objects AS xo  
    JOIN sys.dm_xe_packages AS p  
       ON xo.package_guid = p.guid  
    WHERE xo.object_type = 'target'  
    AND (xo.capabilities & 1 = 0  
    OR xo.capabilities IS NULL)  
    ORDER BY p.name, xo.name  
    ```  
  
    > [!NOTE]  
    >  Pour plus d’informations sur les différents types de cible, consultez [Cibles des événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
6.  Examinez et ajoutez toutes options de configuration supplémentaires. Par exemple, vous pouvez configurer des options telles que le mode de rétention d'événement, le mode de mise en mémoire tampon des longs événements, ou si la session d'événements doit démarrer automatiquement au démarrage de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les options sont décrites dans la rubrique [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql). N’oubliez pas que les valeurs par défaut sont affectées si ces options ne sont pas spécifiées.  
  
7.  Démarrez la session.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la consultation des résultats de session, reportez-vous à la rubrique correspondant au type de cible que vous avez utilisé dans le nœud [Cibles des événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md) de la documentation en ligne.  
  
 L'exemple suivant crée une session d'événements étendus nommée IOActivity qui capture les informations suivantes :  
  
-   des données d'événement pour les lectures de fichier achevées, notamment le texte [!INCLUDE[tsql](../includes/tsql-md.md)] associé pour les lectures de fichier où l'ID de fichier correspond à 1 ;  
  
-   des données d'événement pour les écritures de fichier achevées ;  
  
-   des données d'événement relatives à l'écriture des données du cache du journal dans le fichier journal physique ;  
  
 La session envoie la sortie à une cible de fichier.  
  
```  
CREATE EVENT SESSION IOActivity  
ON SERVER  
  
ADD EVENT sqlserver.file_read_completed  
   (  
   ACTION (sqlserver.sql_text)  
   WHERE file_id = 1),  
ADD EVENT sqlserver.file_write_completed,  
ADD EVENT sqlserver.databases_log_flush  
  
ADD TARGET package0.asynchronous_file_target   
   (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une SESSION d’événements &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [SQL Server les cibles d’événements étendus](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [Packages d’événements étendus SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)  
  
  
