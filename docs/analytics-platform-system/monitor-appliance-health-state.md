---
title: Surveiller l’intégrité de l’appliance
description: Comment surveiller l’état d’une appliance système Analytics Platform à l’aide de la console d’administration, ou en interrogeant directement les vues de gestion dynamique Data Warehouse parallèle.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: b99123f81fcdddd74dc72d485d97e428ca59ed84
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400993"
---
# <a name="monitor-appliance-health-state"></a>Surveiller l’état d’intégrité de l’appliance
Cet article explique comment surveiller l’état d’une appliance système Analytics Platform à l’aide de la console d’administration, ou en interrogeant directement les vues de gestion dynamique Data Warehouse parallèle. 
  
## <a name="to-monitor-the-appliance-state"></a>Pour surveiller l’état de l’appliance  
Un administrateur système peut utiliser la console d’administration ou les SQL Server PDW vues de gestion dynamique (DMV) pour récupérer la hiérarchie complète des nœuds, des composants et des logiciels. Le diagramme suivant offre une compréhension générale des composants analysés par SQL Server PDW.  
  
![Vue d’ensemble de la surveillance](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>Surveiller l’état des composants à l’aide de la console d’administration  
Pour récupérer l’état d’un composant à l’aide de la console d’administration :  
  
1.  Cliquez sur l’onglet État de l' **Appliance** .  
  
2.  Sur la page État de l’appliance, cliquez sur un nœud spécifique pour afficher les détails du nœud.  
  
    ![État de la console d'administration PDW](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>Surveiller l’état des composants à l’aide des vues système  
Pour récupérer l’état d’un composant à l’aide des vues système, utilisez [sys. dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Par exemple, la requête suivante récupère l’état de tous les composants.  
  
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
  
Les valeurs possibles retournées pour la propriété Status sont les suivantes :  
  
-   OK  
  
-   Non critique  
  
-   Critique  
  
-   Unknown  
  
-   Non pris en charge  
  
-   Inaccessible  
  
-   irrécupérable  
  
Pour afficher toutes les propriétés de tous les composants, supprimez la `WHERE  p.property_name = 'Status'` clause.  
  
La colonne **[update_time]** indique l’heure de la dernière interrogation du composant par les agents d’intégrité SQL Server PDW.  
  
> [!CAUTION]  
> Veillez à examiner le problème lorsqu’un composant n’a pas été interrogé pendant 5 minutes ou plus ; Il peut y avoir une alerte indiquant un problème lié aux pulsations logicielles.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Système de plateforme d’analyse de &#40;Analytics de l’appliance&#41;](appliance-monitoring.md)  
  
