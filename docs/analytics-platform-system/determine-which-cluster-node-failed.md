---
title: Déterminer le nœud de cluster en échec
description: Cet article explique comment déterminer le nom du nœud APS (Analytics Platform System) qui a échoué après un basculement de cluster et qu’une alerte de basculement de cluster a été générée. Dans le cadre du dépannage d’un basculement de cluster, vous devez déterminer le nom du nœud qui a échoué avant de contacter Microsoft pour aider à résoudre le problème.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 68ebdb7f17ddee311644e11c48eaa4b586beac74
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401205"
---
# <a name="determine-which-cluster-node-failed-for-analytics-platform-system"></a>Déterminer le nœud de cluster ayant échoué pour Analytics Platform System
Cette rubrique explique comment déterminer le nom du nœud APS (Analytics Platform System) qui a échoué après un basculement de cluster et qu’une alerte de basculement de cluster a été générée. Dans le cadre du dépannage d’un basculement de cluster, vous devez déterminer le nom du nœud qui a échoué avant de contacter Microsoft pour aider à résoudre le problème.  
  
## <a name="Background"></a>Informations  
Pour la haute disponibilité dans SQL Server PDW, le nœud de contrôle et les nœuds de calcul sont configurés en tant que composants actifs ou passifs des clusters de basculement Windows. Lorsqu’un serveur actif ne parvient pas à répondre aux demandes du système critique, le serveur passif bascule et exécute les fonctions du serveur qui a échoué.  
  
Après un basculement de cluster, lorsque SQL Server PDW rapports sur l’état du nœud, le serveur passif a un État basculé. Toutefois, il n’est pas évident de savoir quel serveur ou nœud a échoué, surtout si le serveur qui a échoué est toujours en ligne. Pour résoudre le problème de défaillance du cluster, vous devez déterminer le nom du nœud qui a basculé.  
  
## <a name="AdminConsoleSolution"></a>Solution de la console d’administration  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>Pour rechercher le nom du nœud qui a échoué  
  
1.  Ouvrez la console d’administration. Pour plus d’informations sur la console d’administration, consultez [surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). Une fois le basculement effectué, l’événement de basculement est inclus dans le nombre d’alertes dans la page **intégrité** . Il existe une page d' **intégrité** pour la région PDW et la région de la structure de l’appareil. Chaque page d’intégrité comporte un onglet **alertes** . Pour en savoir plus sur une alerte, cliquez sur la page intégrité, sur l’onglet Alertes, puis cliquez sur une alerte.  
  
## <a name="SystemView"></a>Solution vue système  
L’instruction SQL suivante montre comment utiliser la vue système [sys. dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md) pour rechercher le nom du serveur qui a échoué.  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
