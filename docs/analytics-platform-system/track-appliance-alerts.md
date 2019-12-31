---
title: Suivre les alertes de l’appliance
description: Suivre les alertes d’appliance dans Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 03568666367bf6273f197994f572bbbbd62bb42e
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399942"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Suivre les alertes d’appliance dans Analytics Platform System
Cette rubrique explique comment utiliser la console d’administration et les vues système pour suivre les alertes dans un appareil SQL Server PDW.  
  
## <a name="to-track-appliance-alerts"></a>Pour suivre les alertes de l’appliance  
SQL Server PDW crée des alertes pour les problèmes matériels et logiciels qui requièrent votre attention. Chaque alerte contient un titre et une description du problème.  
  
SQL Server PDW consigne les alertes dans la DMV [sys. dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) . Le système conserve une limite de 10 000 alertes et supprime d’abord l’alerte la plus ancienne lorsque la limite est dépassée.  
  
### <a name="view-alerts-by-using-the-admin-console"></a>Afficher les alertes à l’aide de la console d’administration  
Il existe un onglet **alertes** pour la région PDW et la région de la structure de l’appliance. Une fois le basculement effectué, l’événement de basculement est inclus dans le nombre d’alertes sur la page. Il existe une page pour la région PDW et pour la région de la structure de l’appareil. Chaque page d’intégrité a un onglet. Pour en savoir plus sur une alerte, cliquez sur la page **intégrité** , sur l’onglet **alertes** , puis cliquez sur une alerte.  
  
![Alertes de la console d'administration PDW](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
Sur la page **alertes** :  
  
-   Pour afficher l’historique des alertes, cliquez sur le lien **consulter l’historique des alertes** .  
  
-   Pour afficher le composant d’alerte et ses valeurs de propriété actuelles, cliquez sur la ligne d’alerte.  
  
-   Pour afficher des détails sur le nœud qui a déclenché l’alerte, cliquez sur le nom du nœud.  
  
### <a name="view-alerts-by-using-the-system-views"></a>Afficher les alertes à l’aide des vues système  
Pour afficher les alertes à l’aide des vues système, interrogez [sys. dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md). Cette vue de gestion dynamique affiche les alertes qui n’ont pas été corrigées. Pour obtenir de l’aide sur les erreurs et les alertes de triage, utilisez la DMV [sys. dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) .  
  
L’exemple suivant est une requête courante permettant d’afficher les alertes actuelles.  
  
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
[Système de plateforme d’analyse de &#40;Analytics de l’appliance&#41;](appliance-monitoring.md)  
  
