---
title: Surveillance de l’appliance - Analytique Platform System | Microsoft Docs
description: Ce guide de surveillance appliance décrit les outils et les tâches de surveillance de l’appliance Analytique Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cb25a5eccd1e77f08cedc74ad8042e0dc573605c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961509"
---
# <a name="appliance-monitoring-for-analytics-platform-system"></a>Surveillance de l’appliance pour l’Analytique Platform System
Ce guide de surveillance appliance décrit les outils et les tâches de surveillance de l’appliance Analytique Platform System.  
  
## <a name="Basics"></a>Concepts de base et les outils de surveillance  
Les valeurs et les informations qui peuvent être surveillées sur l’appliance SQL Server PDW sont nombreuses. Par exemple, les éléments suivants sont typiques de tâches de surveillance.  
  
-   Recherchez toute alerte émise par SQL Server PDW.  
  
-   Analyse pour le matériel défaillant.  
  
-   Analyse des problèmes de connectivité réseau.  
  
-   Recherchez les erreurs retournées aux utilisateurs pendant le traitement des requêtes.  
  
-   Afficher le nombre de sessions actuellement actives et des requêtes.  
  
-   Vérifier l’état de chargements, sauvegardes et restaurations.  
  
### <a name="appliance-monitoring-tools"></a>Outils de surveillance de matériel  
Il existe plusieurs outils disponibles pour surveiller l’appliance.  
  
Console Administration  
SQL Server PDW a une Console d’administration. Il s’agit d’un outil basé sur le web qui affiche des informations sur les requêtes, les charges, sauvegarde et restauration, verrous, sessions, alertes et état de l’appliance. La Console d’administration s’exécute sur l’application ; les utilisateurs se connecter à la Console d’administration d’Internet Explorer. Pour plus d'informations, consultez :  
  
-   [Surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![Alertes de la Console d’administration PDW](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Vues système  
SQL Server PDW inclut les vues système complète qui vous permettent d’obtenir des informations détaillées sur l’appliance, état et les performances. Pour obtenir la liste de vues système pour la surveillance des tâches, consultez :  
  
-   [Surveiller l’Appliance à l’aide de vues système &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW offre une intégration complète avec Systems Center Operations Manager. Les packs d’administration pour SQL Server PDW sont disponibles en téléchargement gratuit. Pour plus d’informations sur l’utilisation de System Center pour surveiller SQL Server PDW, consultez les rubriques suivantes :  
  
-   [Surveiller l’Appliance à l’aide de System Center Operations Manager &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Solutions personnalisées  
Pour les situations lorsque System Center n’est pas disponible avec votre centre de données outils d’analyse, vous pouvez surveiller l’appliance à l’aide d’une solution de surveillance par des tiers. Installation d’agents logiciels externes n’est actuellement pas prise en charge dans PDW, mais la plupart des solutions de surveillance prend en charge Transact\-SQL integration, donc l’administrateur système peut implémenter Transact direct\-requêtes SQL sur votre PDW appliance.  
  
Si votre solution de surveillance ne prend pas en charge directe Transact\-requêtes SQL, ou vous ne possédez pas d’un outil de surveillance, puis vous pouvez utiliser des scripts pour exécuter des tâches de surveillance, telles que l’envoi de courrier électronique lorsqu’une alerte se produit.  Le wiki TechNet contient un exemple de solution de surveillance par script.  
  
-   [Exemple d’analyse pour SQL Server PDW de Power Shell](https://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>Liées de tâches de surveillance  
  
|Tâche d’analyse|Description|  
|-------------------|---------------|  
|Surveiller l’appliance à l’aide de la Console d’administration.|[Surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Surveiller l’appliance à l’aide de vues système.|[Surveiller l’Appliance à l’aide de vues système &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-views.md)|  
|Surveiller l’appliance à l’aide de System Center|[Surveiller l’Appliance à l’aide de System Center Operations Manager &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Surveiller l’état de l’appliance.|[État de l’intégrité de l’analyse &#40;Analytique Platform System&#41;](monitor-appliance-health-state.md)|  
|Analyse des pulsations.|[Envoyer des commentaires de télémétrie à Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Effectuer le suivi des alertes de l’appliance.|[Effectuer le suivi des alertes de l’Appliance &#40;Analytique Platform System&#41;](track-appliance-alerts.md)|  
|Déterminez la quantité de capacité est utilisé.|[Afficher l’utilisation de la capacité &#40;Analytique Platform System&#41;](view-capacity-utilization.md)|  
|Déterminer la fréquence d’interrogation de l’appliance.|[Déterminer la fréquence d’interrogation &#40;Analytique Platform System&#41;](determine-polling-frequency.md)|  
|En cas de défaillance d’un cluster, de déterminer quel cluster échoué du nœud.|[Déterminer le nœud de Cluster défectueux &#40;Analytique Platform System&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Tâches de gestion appliance &#40;Analytique Platform System&#41;](appliance-management-tasks.md)  
  
