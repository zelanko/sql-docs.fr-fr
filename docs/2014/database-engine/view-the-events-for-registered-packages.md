---
title: Afficher les événements pour les Packages enregistrés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing events
- extended events [SQL Server], viewing events
ms.assetid: 9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1156a7272edc8ad1ecfb8e173f81bc678800c855
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089632"
---
# <a name="view-the-events-for-registered-packages"></a>Consulter les événements pour les packages enregistrés
  Avant de créer une session des événements étendus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], il est utile de savoir quels sont les événements présents dans les packages enregistrés. Pour plus d'informations, consultez [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).  
  
 L’utilisation de l'éditeur de requêtes dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] est nécessaire pour effectuer la procédure suivante.  
  
 Une fois que les instructions de cette procédure sont exécutées, l’onglet **Results** de l’éditeur de requêtes affiche les colonnes suivantes :  
  
-   nom. Nom du package.  
  
-   événement. Nom de l'événement.  
  
-   mot clé. Mot clé dérivé d'une table de mappage numérique interne.  
  
-   canal. Audience pour un événement.  
  
-   description. Description de l'événement.  
  
## <a name="to-view-the-events-for-registered-packages-using-query-editor"></a>Pour afficher les événements pour les packages enregistrés à l'aide de l'Éditeur de requête  
  
-   Dans l'éditeur de requêtes, émettez les instructions suivantes.  
  
    ```  
    USE msdb  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
    (  
    SELECT event_package=o.package_guid, o.description,   
    event=c.object_name, channel=v.map_value  
    FROM sys.dm_xe_objects o  
    LEFT JOIN sys.dm_xe_object_columns c ON o.name=c.object_name  
    INNER JOIN sys.dm_xe_map_values v ON c.type_name=v.name   
    AND c.column_value=cast(v.map_key AS nvarchar)  
    WHERE object_type='event' AND (c.name='CHANNEL' or c.name IS NULL)  
  
    ) c LEFT JOIN   
    (  
    SELECT event_package=c.object_package_guid, event=c.object_name,   
    keyword=v.map_value  
    FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
    ON c.type_name=v.name AND c.column_value=v.map_key   
    AND c.type_package_guid=v.object_package_guid  
    INNER JOIN sys.dm_xe_objects o ON o.name=c.object_name   
    AND o.package_guid=c.object_package_guid  
    WHERE object_type='event' AND c.name='KEYWORD'   
    ) k  
    ON  
    k.event_package=c.event_package AND (k.event=c.event or k.event IS NULL)  
    INNER JOIN sys.dm_xe_packages p ON p.guid=c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Packages d’événements étendus SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
