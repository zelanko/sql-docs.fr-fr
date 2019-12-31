---
title: Afficher l’utilisation de la capacité
description: Affichez l’utilisation de la capacité dans Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: c2dafa2df09bb8141fca8c30a80c6471ffe1e060
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399454"
---
# <a name="view-capacity-utilization-in-analytics-platform-system"></a>Afficher l’utilisation de la capacité dans Analytics Platform System
Cette rubrique explique comment afficher l’utilisation de la capacité dans l’appliance SQL Server PDW.  
  
## <a name="to-view-capacity-utilization-by-using-admin-console"></a>Pour afficher l’utilisation de la capacité à l’aide de la console d’administration  
Pour afficher l’espace utilisé, ouvrez la console d’administration, puis cliquez sur l’onglet **stockage** . Il existe un onglet **stockage** pour la région PDW.  
  
![Stockage de la console d'administration PDW](./media/view-capacity-utilization/SQL_Server_PDW_AdminConsol_StorageV2.png "SQL_Server_PDW_AdminConsol_StorageV2")  
  
## <a name="to-view-capacity-utilization-by-using-queries"></a>Pour afficher l’utilisation de la capacité à l’aide de requêtes  
Pour déterminer si un nœud ne dispose pas de suffisamment d’espace, le système de contrôle d’intégrité SQL Server PDW surveille déjà l’espace libre pour tous les volumes de chaque nœud.  
  
Si l’espace libre au sein d’un volume descend en dessous de 30%, SQL Server PDW génère une alerte d' **Avertissement** dans [sys. dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md).  L’alerte reste jusqu’à ce que de l’espace libre soit rendu disponible.  
  
Si l’espace libre au sein d’un volume tombe moins de 10%, SQL Server PDW génère une alerte **critique** . Ce problème est considéré comme critique, car les requêtes peuvent échouer si elles provoquent le développement de la base de données.  
  
Pour récupérer l’utilisation du volume, consultez l’exemple suivant.  
  
```sql  
SELECT   
    space.[pdw_node_id] ,  
    space.[node_name] ,  
    MAX(space.[volume_name]) AS 'volume_name' ,  
    MAX(space.[volume_size_mb]) AS 'volume_size_mb' ,  
    MAX(space.[free_space_mb]) AS 'free_space_mb' ,  
   (MAX(space.[volume_size_mb]) - MAX(space.[free_space_mb])) AS 'space_utilized'  
FROM (  
    SELECT   
        s.[pdw_node_id],  
        n.[name] AS [node_name],  
        (CASE WHEN p.property_name = 'volume_name'   
            THEN s.[property_value] ELSE NULL END) AS 'volume_name' ,  
        (CASE WHEN p.property_name = 'volume_size'   
            THEN (CAST(ISNULL(s.[property_value], '0') AS BIGINT)/1024/1024)   
            ELSE 0 END) AS 'volume_size_mb' ,  
        (CASE WHEN p.property_name = 'volume_free_space'   
            THEN (CAST(ISNULL(s.[property_value], '0') AS BIGINT)/1024/1024)   
            ELSE 0 END) AS 'free_space_mb' , s.[component_instance_id]  
    FROM [sys].[dm_pdw_component_health_status] AS s  
        JOIN sys.dm_pdw_nodes AS n   
            ON s.[pdw_node_id] = n.[pdw_node_id]  
        JOIN [sys].[pdw_health_components] AS c   
            ON s.[component_id] = c.[component_id]  
        JOIN [sys].[pdw_health_component_properties] AS p   
            ON s.[property_id] = p.[property_id] AND s.[component_id] = p.[component_id]  
    WHERE  
        c.[Component_name] = 'Volume'  
        AND p.[property_name] IN ('volume_name', 'volume_free_space', 'volume_size')  
    ) AS space  
GROUP BY space.[pdw_node_id] , space.[node_name] , space.[component_instance_id]  
ORDER BY space.[pdw_node_id], MAX(space.[volume_name]);  
```  
  
Pour récupérer l’espace utilisé par les bases de données sur les nœuds de l’appliance, consultez l’exemple suivant.  
  
```sql  
SELECT   
    [pdw_node_id],   
    [db_name],   
    SUM(CASE WHEN [file_type] = 'DATA' THEN [value_MB] ELSE 0 END) AS [DataSizeMB],  
    SUM(CASE WHEN [file_type] = 'LOG' THEN [value_MB] ELSE 0 END) AS [LogSizeMB],  
    SUM([value_MB]) AS [TotalMB]  
FROM (  
    SELECT   
        pc.[pdw_node_id],   
        RTRIM(pc.[counter_name]) AS [counter_name],   
        ISNULL(d.[name], pc.[instance_name]) AS [db_name],   
        pc.[cntr_value]/1024 AS [value_MB],  
        CASE   
            WHEN [counter_name] LIKE 'Data File(s) Size%'   
            THEN 'DATA'   
            ELSE 'LOG'   
        END AS [file_type]  
    FROM sys.dm_pdw_nodes_os_performance_counters AS pc  
        LEFT JOIN sys.pdw_database_mappings AS dm   
            ON pc.instance_name = dm.physical_name  
        INNER JOIN sys.databases AS d   
            ON d.database_id = dm.database_id  
    WHERE   
        ([counter_name] LIKE 'Log File(s) Size%'  
             OR [counter_name] LIKE 'Data File(s) Size%')  
        AND (d.[name] <> dm.[physical_name]   
             OR pc.[instance_name] = 'tempdb')  
) AS db  
GROUP BY [pdw_node_id], [db_name]  
ORDER BY [db_name], [pdw_node_id];  
```  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[Système de plateforme d’analyse de &#40;Analytics de l’appliance&#41;](appliance-monitoring.md)  
  
