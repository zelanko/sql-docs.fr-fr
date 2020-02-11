---
title: Monitoring de l’appliance
description: Ce guide de surveillance de l’appliance décrit les outils et les tâches permettant de surveiller l’appliance Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: cec604ff1a93213fc6308455cadda90e6efa2d61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401423"
---
# <a name="appliance-monitoring-for-analytics-platform-system"></a>Surveillance de l’appliance pour Analytics Platform System
Ce guide de surveillance de l’appliance décrit les outils et les tâches permettant de surveiller l’appliance Analytics Platform System.  
  
## <a name="Basics"></a>Outils de base et outils de surveillance  
Les valeurs et les informations qui peuvent être surveillées sur l’appareil SQL Server PDW sont étendues. Par exemple, les tâches de surveillance classiques sont les suivantes :  
  
-   Recherchez les alertes émises par SQL Server PDW.  
  
-   Analyse du matériel défaillant.  
  
-   Analyse des problèmes de connectivité réseau.  
  
-   Recherchez les erreurs retournées aux utilisateurs pendant le traitement des requêtes.  
  
-   Affichez le nombre de sessions et de requêtes actuellement actives.  
  
-   Vérifiez l’état des charges, des sauvegardes et des restaurations.  
  
### <a name="appliance-monitoring-tools"></a>Outils de surveillance de l’appliance  
Plusieurs outils sont disponibles pour surveiller l’appliance.  
  
Console Administration  
SQL Server PDW dispose d’une console d’administration. Il s’agit d’un outil basé sur le Web qui affiche des informations sur les requêtes, les chargements, les sauvegardes et les restaurations, les verrous, les sessions, les alertes et l’état de l’appareil. La console d’administration s’exécute sur l’appliance. les utilisateurs se connectent à la console d’administration via Internet Explorer. Pour plus d'informations, consultez les pages suivantes :  
  
-   [Surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![Alertes de la console d'administration PDW](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Vues système  
SQL Server PDW comprend des vues système complètes qui vous permettent d’obtenir des informations détaillées sur l’intégrité, l’État et les performances de l’appliance. Pour obtenir la liste des vues système pour les tâches de surveillance, consultez :  
  
-   [Surveiller l’appliance à l’aide des vues système &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW intègre une intégration complète à Systems Center Operations Manager. Les packs d’administration de SQL Server PDW sont disponibles en téléchargement gratuit. Pour plus d’informations sur l’utilisation de System Center pour analyser SQL Server PDW, consultez les rubriques suivantes :  
  
-   [Surveiller l’appliance à l’aide de System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Solutions personnalisées  
Dans les cas où System Center n’est pas disponible avec vos outils de surveillance de centre de données, vous pouvez surveiller l’appliance à l’aide d’une solution de surveillance tierce. L’installation d’agents logiciels externes n’est actuellement pas prise en charge dans PDW, mais la\-plupart des solutions de surveillance prennent en charge l’intégration Transact\-SQL. l’administrateur système peut donc implémenter des requêtes Transact SQL directes sur votre appliance PDW.  
  
Si votre solution de surveillance ne prend pas en\-charge les requêtes Transact SQL directes ou si vous ne disposez pas d’un outil d’analyse, vous pouvez utiliser des scripts pour effectuer des tâches de surveillance, telles que l’envoi de courrier électronique lorsqu’une alerte se produit.  Le wiki TechNet contient un exemple de solution de surveillance par script.  
  
-   [Exemple d’analyse de Power Shell pour SQL Server PDW](https://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>Tâches d’analyse associées  
  
|Tâche d’analyse|Description|  
|-------------------|---------------|  
|Surveillez l’appliance à l’aide de la console d’administration.|[Surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Surveiller l’appliance à l’aide des vues système.|[Surveiller l’appliance à l’aide des vues système &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)|  
|Surveiller l’appliance à l’aide de System Center|[Surveiller l’appliance à l’aide de System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Surveiller l’état de l’appliance.|[Surveiller l’état d’intégrité de l’appliance &#40;Analytics Platform System&#41;](monitor-appliance-health-state.md)|  
|Surveillance des pulsations.|[Envoyer des commentaires de télémétrie à Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Suivre les alertes de l’appliance.|[Suivre les alertes de l’appliance &#40;Analytics Platform System&#41;](track-appliance-alerts.md)|  
|Déterminez la quantité de capacité utilisée.|[Afficher l’utilisation de la capacité &#40;Analytics Platform System&#41;](view-capacity-utilization.md)|  
|Déterminez la fréquence d’interrogation de l’appliance.|[Déterminez la fréquence d’interrogation &#40;système de plateforme d’analyse&#41;](determine-polling-frequency.md)|  
|En cas de défaillance d’un cluster, déterminez le nœud de cluster qui a échoué.|[Identifiez le nœud de cluster ayant échoué &#40;Analytics Platform System&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Tâches de gestion d’appliance &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
