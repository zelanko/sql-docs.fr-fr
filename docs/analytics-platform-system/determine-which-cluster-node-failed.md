---
title: Déterminer le nœud de cluster a échoué - Analytique Platform System | Microsoft Docs
description: Cet article décrit comment déterminer le nom du nœud Analytique Platform System (APS) qui ont échoué après un basculement de cluster s’est produite et une alerte de basculement de cluster a été déclenchée. Dans le cadre de la résolution des problèmes d’un cluster de basculement, vous devez déterminer le nom du nœud ayant échoué avant de contacter Microsoft pour vous aider à résoudre le problème.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4fd739e55725a3138a22539ef837088f86c8d8b9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63283147"
---
# <a name="determine-which-cluster-node-failed-for-analytics-platform-system"></a>Déterminer quel cluster nœud a échoué pour l’Analytique Platform System
Cette rubrique décrit comment déterminer le nom du nœud Analytique Platform System (APS) qui ont échoué après un basculement de cluster s’est produite et une alerte de basculement de cluster a été déclenchée. Dans le cadre de la résolution des problèmes d’un cluster de basculement, vous devez déterminer le nom du nœud ayant échoué avant de contacter Microsoft pour vous aider à résoudre le problème.  
  
## <a name="Background"></a>En arrière-plan  
Pour la haute disponibilité dans SQL Server PDW, le nœud de contrôle et les nœuds de calcul sont configurés en tant que composants actifs ou passifs des clusters de basculement Windows. Lorsqu’un serveur actif ne parvient pas à répondre aux demandes du système critiques, le serveur passif bascule et exécute les fonctions du serveur qui a échoué.  
  
Après un basculement de cluster, lorsque SQL Server PDW de rapports sur l’état du nœud, le serveur passif a un échec sur l’état. Toutefois, il n’est pas évident serveur ou du nœud a échoué, en particulier si le serveur qui a échoué est encore en ligne. Pour résoudre le problème de cluster, vous devez déterminer le nom du nœud ayant basculé.  
  
## <a name="AdminConsoleSolution"></a>Solution de la Console d’administration  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>Pour rechercher le nom du nœud qui a échoué  
  
1.  Ouvrez la Console d’administration. Pour plus d’informations sur la Console d’administration, consultez [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). Une fois le basculement se produit, l’événement de basculement est inclus dans le nombre d’alertes sur le **intégrité** page. Il existe un **intégrité** page pour la région PDW et pour la région de l’infrastructure de l’appliance. Chaque page d’intégrité a un **alertes** onglet. Pour en savoir plus sur une alerte, cliquez sur la page de contrôle d’intégrité, l’onglet alertes et puis cliquez sur une alerte.  
  
## <a name="SystemView"></a>Solution de vue système  
L’instruction SQL suivante montre comment utiliser le [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md) vue système pour rechercher le nom du serveur qui a échoué.  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
