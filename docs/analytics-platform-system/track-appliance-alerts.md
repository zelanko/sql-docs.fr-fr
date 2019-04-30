---
title: Effectuer le suivi des alertes de l’appliance - Analytique Platform System | Microsoft Docs
description: Effectuer le suivi des alertes de l’appliance d’Analytique Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f38f76975290538a35203ddbbed84b9354285edc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156988"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Effectuer le suivi des alertes de l’appliance d’Analytique Platform System
Cette rubrique explique comment utiliser la Console d’administration et les vues système pour effectuer le suivi des alertes dans une appliance SQL Server PDW.  
  
## <a name="to-track-appliance-alerts"></a>Pour effectuer le suivi des alertes de l’Appliance  
SQL Server PDW crée des alertes pour les problèmes matériels et logiciels qui nécessitent votre attention. Chaque alerte contient un titre et une description du problème.  
  
SQL Server PDW consigne les alertes dans le [sys.dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) DMV. Le système conserve une limite de 10 000 alertes et supprime tout d’abord l’alerte plus ancien lorsque la limite est dépassée.  
  
### <a name="view-alerts-by-using-the-admin-console"></a>Afficher les alertes à l’aide de la Console d’administration  
Il existe un **alertes** onglet pour la région PDW et pour la région de l’infrastructure de l’appliance. Une fois le basculement se produit, l’événement de basculement est inclus dans le nombre d’alertes sur la page. Il existe une page pour la région PDW et pour la région de l’infrastructure de l’appliance. Chaque page de contrôle d’intégrité comporte un onglet. Pour en savoir plus sur une alerte, cliquez sur le **intégrité** page, le **alertes** onglet, puis cliquez sur une alerte.  
  
![Alertes de la Console d’administration PDW](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
Sur le **alertes** page :  
  
-   Pour afficher l’historique des alertes, cliquez sur le **l’historique de révision alerte** lien.  
  
-   Pour afficher le composant d’alerte et ses valeurs de propriété actuelles, cliquez sur la ligne d’alerte.  
  
-   Pour afficher des détails sur le nœud qui a déclenché l’alerte, cliquez sur le nom du nœud.  
  
### <a name="view-alerts-by-using-the-system-views"></a>Afficher les alertes en utilisant les vues système  
Pour afficher les alertes à l’aide de vues système, interrogez [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md). Cette DMV affiche les alertes qui n’ont pas été corrigées. Pour faciliter le triage des alertes et les erreurs, utilisez le [sys.dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) DMV.  
  
L’exemple suivant est une requête commune pour l’affichage des alertes en cours.  
  
```sql  
SELECT   
    aa.[pdw_node_id],  
    n.[name] AS [node_name],  
    g.[group_name] ,  
    c.[component_name] ,  
    aa.[component_instance_id] ,   
    a.[alert_name] ,  
    a.[state] ,  
    a.[severity] ,  
    aa.[current_value] ,  
    aa.[previous_value] ,  
    aa.[create_time] ,  
    a.[description]   
FROM [sys].[dm_pdw_component_health_active_alerts] AS aa  
    INNER JOIN sys.dm_pdw_nodes AS n   
        ON aa.[pdw_node_id] = n.[pdw_node_id]  
    INNER JOIN [sys].[pdw_health_components] AS c   
        ON aa.[component_id] = c.[component_id]  
    INNER JOIN [sys].[pdw_health_component_groups] AS g   
        ON c.[group_id] = g.[group_id]  
    INNER JOIN [sys].[pdw_health_alerts] AS a   
        ON aa.[alert_id] = a.[alert_id] and aa.[component_id] = c.[component_id]  
ORDER BY  
    a.alert_id ,  
    aa.[pdw_node_id];  
```  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[Surveillance de l’appliance &#40;Analytique Platform System&#41;](appliance-monitoring.md)  
  
