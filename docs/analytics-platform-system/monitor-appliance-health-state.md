---
title: "État d’intégrité analyse Appliance (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91132e3c-3137-4670-adaa-8a7b234fb8d2
caps.latest.revision: "12"
ms.openlocfilehash: d83c3d35c4cf65ebf714b44bc9db7db36b11f818
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="monitor-appliance-health-state"></a>État de contrôle d’intégrité de l’analyse
Cette rubrique explique comment surveiller l’état d’un appareil de SQL Server PDW à l’aide de la Console d’administration, ou en interrogeant directement les vues de gestion dynamique SQL Server PDW.  
  
## <a name="to-monitor-the-appliance-state"></a>Pour surveiller l’état de l’équipement  
Un administrateur système peut utiliser la Console d’administration ou les vues de gestion dynamique (DMV) SQL Server PDW pour récupérer la hiérarchie complète des nœuds, les composants et les logiciels. Le diagramme suivant donne une présentation générale des composants SQL Server PDW surveille.  
  
![Présentation des moniteurs](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>État du composant Moniteur à l’aide de la Console d’administration  
Pour récupérer l’état du composant à l’aide de la Console d’administration :  
  
1.  Cliquez sur le **état des appliances** onglet.  
  
2.  Dans la page État de l’application, cliquez sur un nœud spécifique pour afficher les détails du nœud.  
  
    ![État de la Console Administration PDW](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>État du composant Moniteur à l’aide de vues système  
Pour récupérer l’état du composant à l’aide de vues système, utilisez [sys.dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Par exemple, la requête suivante récupère l’état de tous les composants.  
  
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
  
Retourné pour la propriété Status de valeurs possibles sont :  
  
-   Bien  
  
-   Non critique  
  
-   Critique  
  
-   Unknown  
  
-   Non pris en charge  
  
-   Inaccessible  
  
-   Impossible de récupérer  
  
Pour afficher toutes les propriétés de tous les composants, supprimez le `WHERE  p.property_name = 'Status'` clause.  
  
Le **[update_time]** colonne indique la dernière fois que le composant a été interrogé par les agents d’intégrité de SQL Server PDW.  
  
> [!CAUTION]  
> Veillez à examiner le problème lorsqu’un composant n’a pas été interrogé pendant 5 minutes ou plus ; Il peut exister une alerte qui indique un problème avec les pulsations de logiciel.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Surveillance de l’appliance &#40; Système de plateforme Analytique &#41;](appliance-monitoring.md)  
  
