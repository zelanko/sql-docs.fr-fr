---
title: Utiliser des objets SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server performance [SQL Server], objects for monitoring
- database monitoring [SQL Server], objects for monitoring
- charts [SQL Server]
- System Monitor [SQL Server], counters
- counters [SQL Server], listed
- objects [SQL Server], performance monitoring
- objects [SQL Server], Windows System Monitor
- performance counters [SQL Server], about performance counters
- System Monitor [SQL Server], objects
- performance counters [SQL Server]
- counters [SQL Server], about performance counters
- tuning databases [SQL Server], objects for monitoring
- database performance [SQL Server], objects for monitoring
- SQL Server, objects
- monitoring performance [SQL Server], objects for monitoring
- Windows System Monitor [SQL Server], objects
- Windows System Monitor [SQL Server], counters
- counters [SQL Server]
- performance counters [SQL Server], listed
ms.assetid: bcd731b1-3c4e-4086-b58a-af7a3af904ad
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0678c741387e6b9e3a252d03fcebad8dcb5e5a52
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133029"
---
# <a name="use-sql-server-objects"></a>Utiliser des objets SQL Server
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des objets et des compteurs qui peuvent être utilisés par le Moniteur système pour surveiller l'activité des ordinateurs exécutant une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un objet peut être n'importe quelle ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , telle qu'un verrou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un processus Windows. Chaque objet contient un ou plusieurs compteurs qui déterminent divers aspects de l'objet à surveiller. Par exemple, l’objet **SQL Server Locks** contient des compteurs appelés **Nombre d’interblocages/s** et **Dépassement du délai d’attente des verrous/s**.  
  
 Certains objets disposent de plusieurs instances si plusieurs ressources d'un type donné sont présentes sur l'ordinateur. Par exemple, le type d'objet **Processor** possède plusieurs instances si le système est multiprocesseur. Le type d'objet **Databases** dispose d'une instance pour chaque base de données sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Certains types d’objets (l’objet **Memory Manager** , par exemple) ne disposent que d’une seule instance. Si un type d'objet dispose de plusieurs instances, vous pouvez ajouter des compteurs pour suivre les statistiques de chaque instance ou, le plus souvent, de toutes les instances à la fois. Les compteurs de l’instance par défaut apparaissent au format **SQLServer:***\<nom_objet>*. Les compteurs des instances nommées apparaissent au format **MSSQL$***\<nom_instance>***:***\<nom_compteur>* ou **SQLAgent$***\<nom_instance>***:***\<nom_compteur>*.  
  
 En ajoutant ou en supprimant des compteurs du graphique et en enregistrant les valeurs du graphique, vous pouvez spécifier les objets et compteurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] surveillés lors du démarrage du Moniteur système.  
  
 Vous pouvez configurer le Moniteur système pour qu'il affiche des statistiques provenant de n'importe quel compteur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . De plus, vous pouvez fixer une valeur seuil pour n'importe quel compteur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et générer ensuite une alerte quand le compteur dépasse ce seuil. Pour plus d’informations sur la définition d’une alerte, consultez [Créer une alerte de base de données SQL Server](create-a-sql-server-database-alert.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont affichées que lorsqu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installée. Si vous arrêtez puis relancez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'affichage des statistiques est interrompu, puis reprend automatiquement. Remarquez également que vous pouvez voir des compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le composant logiciel enfichable Moniteur système même si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas exécuté. Sur une instance cluster, les compteurs de performances ne fonctionnent sur le nœud que lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est exécuté.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Objets de performance de l'Agent SQL Server](#SQLServerAgentPOs)  
  
-   [Objets de performance de Service Broker](#ServiceBrokerPOs)  
  
-   [Objets de performance de SQL Server](#SQLServerPOs)  
  
-   [Objets de performance de la réplication de SQL Server](#SQLServerReplicationPOs)  
  
-   [Compteurs de pipeline SSIS](#SsisPipelineCounters)  
  
-   [Autorisations requises](#RequiredPermissions)  
  
##  <a name="SQLServerAgentPOs"></a> Objets de performance de l'Agent SQL Server  
 Le tableau suivant répertorie les objets de performance fournis pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
|Objet de performance|Description|  
|------------------------|-----------------|  
|[SQLAgent:Alerts](sql-server-agent-alerts-object.md)|Fournit des informations sur les alertes de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLAgent:Jobs](sql-server-agent-jobs-object.md)|Fournit des informations sur les travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLAgent:JobSteps](sql-server-agent-jobsteps-object.md)|Fournit des informations sur les étapes de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLAgent:Statistics](sql-server-agent-statistics-object.md)|Fournit des informations générales sur l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
##  <a name="ServiceBrokerPOs"></a> Objets de performance de Service Broker  
 Le tableau suivant répertorie les objets de performance fournis pour [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
|Objet de performance|Description|  
|------------------------|-----------------|  
|[SQLServer:Broker Activation](sql-server-broker-activation-object.md)|Fournit des informations sur les tâches activées par [!INCLUDE[ssSB](../../includes/sssb-md.md)].|  
|[SQLServer:Broker Statistics](sql-server-broker-statistics-object.md)|Fournit des informations générales sur [!INCLUDE[ssSB](../../includes/sssb-md.md)] .|  
|[SQLServer:Broker Transport](sql-server-broker-dbm-transport-object.md)|Fournit des informations sur le réseau [!INCLUDE[ssSB](../../includes/sssb-md.md)] .|  
  
##  <a name="SQLServerPOs"></a> Objets de performance de SQL Server  
 Le tableau ci-dessous décrit les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Objet de performance|Description|  
|------------------------|-----------------|  
|[SQLServer:Access Methods](sql-server-access-methods-object.md)|Recherche et mesure l'allocation des objets de bases de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (par exemple, le nombre de recherches d'index ou de pages allouées aux index et aux données).|  
|[SQLServer:Backup Device](sql-server-backup-device-object.md)|Fournit des informations sur les unités de sauvegarde utilisées pour les opérations de sauvegarde et de restauration, comme le débit de l'unité de sauvegarde.|  
|[SQLServer:Buffer Manager](sql-server-buffer-manager-object.md)|Fournit des informations sur les mémoires tampon utilisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme les **pages libres** et le **taux d'accès au cache des tampons**.|  
|[SQL Server:Buffer Node](sql-server-buffer-node.md)|Fournit des informations sur la fréquence à laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue des demandes et accède aux pages libres.|  
|[SQLServer:CLR](sql-server-clr-object.md)|Fournit des informations à propos du common language runtime (CLR).|  
|[SQLServer:Cursor Manager by Type](sql-server-cursor-manager-by-type-object.md)|Fournit des informations sur les curseurs.|  
|[SQLServer:Cursor Manager Total](sql-server-cursor-manager-total-object.md)|Fournit des informations sur les curseurs.|  
|[SQLServer:Database Mirroring](sql-server-database-mirroring-object.md)|Fournit des informations sur la mise en miroir de bases de données.|  
|[SQLServer:Databases](sql-server-databases-object.md)|Fournit des informations sur une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , comme la quantité d'espace journal disponible ou le nombre de transactions actives dans la base de données. Cet objet peut avoir plusieurs instances.|  
|[SQL Server : Fonctionnalités déconseillées](sql-server-deprecated-features-object.md)|Compte le nombre d'utilisations de fonctions déconseillées.|  
|[SQLServer:Exec Statistics](sql-server-execstatistics-object.md)|Fournit des informations sur les statistiques d'exécution.|  
|[SQLServer:General Statistics](sql-server-general-statistics-object.md)|Fournit des informations sur l'activité générale à l'échelle du serveur, comme le nombre d'utilisateurs connectés à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQL Server:HADR Availability Replica](sql-server-availability-replica.md)|Fournit des informations sur les alertes de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .|  
|[SQL Server:HADR Database Replica](sql-server-database-replica.md)|Fournit des informations sur les réplicas de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .|  
|[SQLServer:Latches](sql-server-latches-object.md)|Fournit des informations sur les verrous de ressources internes, comme les pages de bases de données, utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQLServer:Locks](sql-server-locks-object.md)|Fournit des informations sur les demandes de verrous individuelles émises par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme les dépassements du délai d'attente des verrous et les interblocages. Cet objet peut avoir plusieurs instances.|  
|[SQLServer:Memory Manager](sql-server-memory-manager-object.md)|Fournit des informations sur l'utilisation de la mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , comme le nombre total de structures de verrous actuellement allouées.|  
|[SQLServer:Plan Cache](sql-server-plan-cache-object.md)|Fournit des informations sur le cache de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour stocker des objets tels que les procédures stockées, les déclencheurs et les plans de requête.|  
|[SQLServer : Statistiques des pools de ressources](sql-server-resource-pool-stats-object.md)|Fournit des informations à propos des statistiques du pool de ressources de Resource Governor.|  
|[SQLServer:SQL Errors](sql-server-sql-errors-object.md)|Fournit des informations sur les erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLServer:SQL Statistics](sql-server-sql-statistics-object.md)|Fournit des informations sur les aspects des requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] , comme le nombre de lots d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] reçus par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQLServer:Transactions](sql-server-transactions-object.md)|Fournit des informations sur les transactions actives dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], telles que le nombre total de transactions et le nombre de transactions d'instantané.|  
|[SQLServer:User Settable](sql-server-user-settable-object.md)|Réalise une surveillance personnalisée. Chaque compteur peut être une procédure stockée personnalisée ou toute instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui renvoie une valeur à surveiller.|  
|[SQLServer:Wait Statistics](sql-server-wait-statistics-object.md)|Fournit des informations sur les attentes.|  
|[SQLServer : Statistiques des groupes de charges de travail](sql-server-workload-group-stats-object.md)|Fournit des informations à propos des statistiques du groupe de charges de travail de Resource Governor.|  
  
##  <a name="SQLServerReplicationPOs"></a> Objets de performance de la réplication de SQL Server  
 Le tableau suivant répertorie les objets de performance fournis pour la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
|Objet de performance|Description|  
|------------------------|-----------------|  
|**SQLServer:Replication Agents**<br /><br /> **SQLServer:Replication Snapshot**<br /><br /> **SQLServer:Replication Logreader**<br /><br /> **SQLServer:Replication Dist.**<br /><br /> **SQLServer:Replication Merge**<br /><br /> Pour plus d’informations, voir [Monitoring Replication with System Monitor](../replication/monitor/monitoring-replication-with-system-monitor.md).|Fournit des informations sur l'activité de l'agent de réplication.|  
  
##  <a name="SsisPipelineCounters"></a> Compteurs de pipeline SSIS  
 Pour le compteur **Pipeline SSIS** , consultez [Compteur de performances](../../integration-services/performance/performance-counters.md).  
  
##  <a name="RequiredPermissions"></a> Autorisations requises  
 L'utilisation des objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dépend des autorisations Windows, sauf **SQLAgent:Alerts**. Pour utiliser **SQLAgent:Alerts** , les utilisateurs doivent être membres du rôle de serveur fixe **sysadmin**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des objets de performance](../../ssms/agent/use-performance-objects.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
