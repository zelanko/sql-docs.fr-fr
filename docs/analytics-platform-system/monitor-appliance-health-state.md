---
title: Surveiller l’intégrité de l’appliance - Analytique Platform System
description: Comment surveiller l’état d’un appareil Analytique Platform System à l’aide de la Console d’administration, ou en interrogeant directement les vues de gestion dynamique de Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d8616d291dcaa8afadc01c9bd237903ca6c13573
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62640037"
---
# <a name="monitor-appliance-health-state"></a>État de l’intégrité de l’analyse
Cet article explique comment surveiller l’état d’un appareil Analytique Platform System à l’aide de la Console d’administration, ou en interrogeant directement les vues de gestion dynamique de Parallel Data Warehouse. 
  
## <a name="to-monitor-the-appliance-state"></a>Pour surveiller l’état de l’Appliance  
Un administrateur système peut utiliser la Console d’administration ou les vues de gestion dynamique (DMV) SQL Server PDW pour récupérer la hiérarchie complète des nœuds, les composants et les logiciels. Le diagramme suivant donne une présentation de haut niveau des composants qui surveille SQL Server PDW.  
  
![Présentation de la surveillance](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>État du composant Moniteur à l’aide de la Console d’administration  
Pour récupérer l’état du composant à l’aide de la Console d’administration :  
  
1.  Cliquez sur le **Appliance état** onglet.  
  
2.  Dans la page État de l’Appliance, cliquez sur un nœud spécifique pour afficher les détails du nœud.  
  
    ![État de la Console Administrateur PDW](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>État du composant Moniteur à l’aide de vues système  
Pour récupérer l’état du composant à l’aide de vues système, utilisez [sys.dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Par exemple, la requête suivante récupère l’état pour tous les composants.  
  
```sql  
SELECT   
   s.[pdw_node_id],  
   n.[name] as [node_name],  
   n.[address] ,  
   g.[group_id] ,  
   g.[group_name] ,  
   c.[component_id] ,  
   c.[component_name] ,  
   s.[component_instance_id] ,   
   p.[property_name] ,  
   s.[property_value] ,  
   s.[update_time]  
FROM [sys].[dm_pdw_component_health_status] AS s  
JOIN sys.dm_pdw_nodes AS n   
   ON s.[pdw_node_id] = n.[pdw_node_id]  
JOIN [sys].[pdw_health_components] AS c   
   ON s.[component_id] = c.[component_id]  
JOIN [sys].[pdw_health_component_groups] AS g   
   ON c.[group_id] = g.[group_id]  
JOIN [sys].[pdw_health_component_properties] AS p   
   ON s.[property_id] = p.[property_id] AND s.[component_id] = p.[component_id]  
WHERE p.property_name = 'Status'  
ORDER BY  
   s.[pdw_node_id],  
   g.[group_name] ,   
   s.[component_instance_id] ,  
   c.[component_name] ,   
   p.[property_name];  
```  
  
Valeurs possibles retournées pour la propriété d’état sont :  
  
-   Ok  
  
-   NonCritical  
  
-   Critique  
  
-   Unknown  
  
-   Non pris en charge  
  
-   Inaccessible  
  
-   Irrécupérable  
  
Pour voir toutes les propriétés pour tous les composants, supprimez le `WHERE  p.property_name = 'Status'` clause.  
  
Le **[update_time]** colonne affiche la dernière fois que le composant a été interrogé par les agents d’intégrité de SQL Server PDW.  
  
> [!CAUTION]  
> Veillez à examiner le problème lorsqu’un composant n’a pas été interrogé pendant 5 minutes ou plus ; Il existe peut-être une alerte qui indique un problème avec les pulsations de logiciels.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Surveillance de l’appliance &#40;Analytique Platform System&#41;](appliance-monitoring.md)  
  
