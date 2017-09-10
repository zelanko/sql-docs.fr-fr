---
title: ALTER SERVER CONFIGURATION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER SERVER CONFIGURATION
- ALTER_SERVER_CONFIGURATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER CONFIGURATION, ALTER
- process affinity, setting
- ALTER SERVER CONFIGURATION statement
- setting process affinity
ms.assetid: f3059e42-5f6f-4a64-903c-86dca212a4b4
caps.latest.revision: 72
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4c406824e51b79b74403623a100f2fc355d28bc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-configuration-transact-sql"></a>ALTER SERVER CONFIGURATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les options de configuration générales pour le serveur actif dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ALTER SERVER CONFIGURATION  
SET <optionspec>   
[;]  
  
<optionspec> ::=  
{  
     <process_affinity>  
   | <diagnostic_log>  
   | <failover_cluster_property>  
   | <hadr_cluster_context>  
   | <buffer_pool_extension>  
   | <soft_numa>  
}  
  
<process_affinity> ::=   
   PROCESS AFFINITY   
   {  
     CPU = { AUTO | <CPU_range_spec> }   
   | NUMANODE = <NUMA_node_range_spec>   
   }  
   <CPU_range_spec> ::=   
      { CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]   
  
   <NUMA_node_range_spec> ::=   
      { NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID } [ ,...n ]  
  
<diagnostic_log> ::=   
   DIAGNOSTICS LOG   
   {   
     ON    
   | OFF    
   | PATH = { 'os_file_path' | DEFAULT }    
   | MAX_SIZE = { 'log_max_size' MB | DEFAULT }    
   | MAX_FILES = { 'max_file_count' | DEFAULT }    
   }  
  
<failover_cluster_property> ::=   
   FAILOVER CLUSTER PROPERTY <resource_property>  
   <resource_property> ::=  
      {  
        VerboseLogging = { 'logging_detail' | DEFAULT }    
      | SqlDumperDumpFlags = { 'dump_file_type' | DEFAULT }  
      | SqlDumperDumpPath = { 'os_file_path'| DEFAULT }  
      | SqlDumperDumpTimeOut = { 'dump_time-out' | DEFAULT }  
      | FailureConditionLevel = { 'failure_condition_level' | DEFAULT }  
      | HealthCheckTimeout = { 'health_check_time-out' | DEFAULT }  
      }  
  
<hadr_cluster_context> ::=  
   HADR CLUSTER CONTEXT = { 'remote_windows_cluster' | LOCAL }  
  
<buffer_pool_extension>::=  
    BUFFER POOL EXTENSION   
    { ON ( FILENAME = 'os_file_path_and_name' , SIZE = <size_spec> )   
    | OFF }  
  
    <size_spec> ::=  
        { size [ KB | MB | GB ] }  
  
<soft_numa> ::=  
    SET SOFTNUMA  
    { ON | OFF }  
```  
  
## <a name="arguments"></a>Arguments  
 **\<process_affinity > :: =**  
  
 PROCESS AFFINITY  
 Active des threads de matériel à associer aux unités centrales.  
  
 PROCESSEUR = {AUTOMATIQUE | \<CPU_range_spec >}  
 Distribue des threads de travail [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à chaque UC dans la plage spécifiée. Les unités centrales situées à l'extérieur de la plage spécifiée ne se verront attribuer aucun thread.  
  
 AUTO  
 Spécifie qu'aucun thread n'est associé à une unité centrale. Le système d'exploitation peut déplacer librement des threads entre les unités centrales, selon la charge de travail du serveur. Ceci est la valeur par défaut et recommandée.  
  
 \<CPU_range_spec > :: =  
 Spécifie l'unité centrale ou la plage d'unités centrales à laquelle affecter des threads.  
  
 { CPU_ID | CPU_ID  TO  CPU_ID } [ ,...n ]  
 Liste d'une ou de plusieurs unités centrales. ID d’UC commencent à 0 et sont **entier** valeurs.  
  
 NUMANODE = \<NUMA_node_range_spec >  
 Attribue des threads à toutes les unités centrales qui appartiennent au nœud NUMA spécifié ou à la page de nœuds.  
  
 \<NUMA_node_range_spec > :: =  
 Spécifie le nœud NUMA ou la plage de nœuds NUMA.  
  
 { NUMA_node_ID | NUMA_node_ID  TO NUMA_node_ID } [ ,...n ]  
 Liste d'un ou de plusieurs nœuds NUMA. ID de nœud NUMA commencent à 0 et sont **entier** valeurs.  
  
 **\<diagnostic_log > :: =**  
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 DIAGNOSTICS LOG  
 Démarre ou cesse de journaliser des données de diagnostics capturées par la procédure sp_server_diagnostics et définit les paramètres de configuration de journalisation SQLDIAG, tels que le nombre de substitution du fichier journal, la taille du fichier journal et l'emplacement du fichier. Pour plus d’informations, consultez [Afficher et lire le journal de diagnostic de l’instance de cluster de basculement](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md).  
  
 ON  
 Démarre la journalisation [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] des données de diagnostics à l'emplacement spécifié dans l'option de fichier PATH. Il s'agit du paramètre par défaut.  
  
 OFF  
 Cesse la journalisation des données de diagnostics.  
  
 PATH = { 'os_file_path' | DEFAULT }  
 Chemin d'accès qui indique l'emplacement des journaux de diagnostics. L’emplacement par défaut est \<\MSSQL\Log > dans le dossier d’installation de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de cluster de basculement.  
  
 MAX_SIZE = { 'log_max_size' MB | DEFAULT }  
 Taille maximale, en mégaoctets, que peut atteindre chaque journal de diagnostics. La valeur par défaut est 100 MB.  
  
 MAX_FILES = { 'max_file_count' | DEFAULT }  
 Nombre maximal de fichiers journaux de diagnostics qui peuvent être stockés sur l'ordinateur avant qu'ils ne soient recyclés pour créer de nouveaux journaux de diagnostics.  
  
 **\<failover_cluster_property > :: =**  
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 FAILOVER CLUSTER PROPERTY  
 Modifie les propriétés de cluster de basculement privées de ressources SQL Server.  
  
 VERBOSE LOGGING = { 'logging_detail' | DEFAULT }  
 Définit le niveau de journalisation pour le clustering de basculement SQL Server. Il peut être activé pour fournir des détails supplémentaires dans les journaux des erreurs à des fins de dépannage.  
  
-   0 – La journalisation est désactivée (valeur par défaut)  
  
-   1 - Erreurs uniquement  
  
-   2 – Erreurs et avertissements  
  
SQLDUMPEREDUMPFLAGS  
 Détermine le type de fichiers dump généré par l'utilitaire SQL Server SQLDumper. Le paramètre par défaut est 0. Pour plus d’informations, consultez [SQL Server Dumper utilitaire l’article](http://go.microsoft.com/fwlink/?LinkId=206173).  
  
 SQLDUMPERDUMPPATH = { 'os_file_path' | DEFAULT }  
 Emplacement de stockage des fichiers dump par l'utilitaire SQLDumper. Pour plus d’informations, consultez [SQL Server Dumper utilitaire l’article](http://go.microsoft.com/fwlink/?LinkId=206173).  
  
 SQLDUMPERDUMPTIMEOUT = { 'dump_time-out' | DEFAULT }  
 Valeur du délai d'attente, en millisecondes, de l'utilitaire SQLDumper pour générer un vidage en cas d'échec de SQL Server. La valeur par défaut est 0, ce qui signifie qu'il n'existe aucune limite de temps pour procéder au vidage. Pour plus d’informations, consultez [SQL Server Dumper utilitaire l’article](http://go.microsoft.com/fwlink/?LinkId=206173).  
  
 FAILURECONDITIONLEVEL = { 'failure_condition_level' | DEFAULT }  
 Conditions dans lesquelles l'instance de cluster de basculement SQL Server doit basculer ou redémarrer. La valeur par défaut est 3, ce qui signifie que la ressource SQL Server procèdera au basculement ou au redémarrage lors d'erreurs de serveur critiques. Pour plus d’informations sur cette modification et autres niveaux de condition d’échec, consultez [configurer les paramètres de propriété FailureConditionLevel](../../sql-server/failover-clusters/windows/configure-failureconditionlevel-property-settings.md).  
  
 HEALTHCHECKTIMEOUT = { 'health_check_time-out' | DEFAULT }  
 Valeur du délai d'attente qui définit la durée pendant laquelle la DLL de ressource du moteur de base de données SQL Server doit attendre les informations d'intégrité du serveur avant de considérer que l'instance de SQL Server ne répond pas. Valeur de délai d'attente, exprimée en millisecondes. La valeur par défaut est 60 000 millisecondes (60 secondes).  
  
 **\<hadr_cluster_context > :: =**  
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 CONTEXTE de CLUSTER HADR  **=**  { **'***remote_windows_cluster***'** | LOCAL}  
 Remplace le contexte de cluster HADR de l'instance de serveur par le cluster de clustering de basculement Windows Server (WSFC) spécifié. Le *de cluster HADR* détermine quel cluster Clustering de basculement Windows Server (WSFC) qui gère les métadonnées pour les réplicas de disponibilité hébergé par l’instance de serveur. N'utilisez l'option SET HADR CLUSTER CONTEXT que pendant une migration entre clusters de [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] vers une instance de [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)], ou d'une version supérieure, sur un nouveau cluster WSFC.  
  
 Vous pouvez basculer le contexte de cluster HADR uniquement du cluster WSFC local vers un cluster distant, puis de nouveau du cluster distant vers le cluster local. Il est possible de basculer le contexte de cluster HADR vers un cluster distant uniquement lorsque l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'héberge pas un réplica de disponibilité.  
  
 Un environnement de cluster HADR distant peut être basculé vers le cluster local à tout moment. Toutefois, le contexte ne peut pas être rebasculé tant que l'instance de serveur héberge des réplicas de disponibilité.  
  
 Pour identifier le cluster de destination, spécifiez l'une des valeurs suivantes :  
  
 *windows_cluster*  
 Le nom d'objet cluster (CON) d'un cluster WSFC. Vous pouvez spécifier le nom court ou le nom de domaine complet. Pour rechercher l'adresse IP cible d'un nom court, ALTER SERVER CONFIGURATION utilise la résolution DNS. Dans certains cas, un nom court peut entraîner quelques confusions, et DNS peut retourner une adresse IP incorrecte. Par conséquent, nous vous recommandons de spécifier le nom de domaine complet.  
  
 LOCAL  
 Cluster WSFC local  
  
 Pour plus d’informations, consultez [modifier le contexte de Cluster HADR de serveur Instance &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md).  
  
 **\<buffer_pool_extension > :: =**  
  
**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ON  
 Active l'option d'extension du pool de mémoires tampons. Cette option étend la taille du pool de mémoires tampons en utilisant une mémoire non volatile comme un disque SSD pour conserver les pages de données nettoyées dans le pool. Pour plus d’informations sur cette fonctionnalité, consultez [Buffer Pool Extension](../../database-engine/configure-windows/buffer-pool-extension.md). L’extension du pool de mémoire tampon n’est pas disponible dans toutes les éditions SQL Server. Pour plus d’informations, consultez [éditions et les fonctionnalités prises en charge pour SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 FILENAME = 'os_file_path_and_name'  
 Définit le chemin d'accès au répertoire et le nom du fichier du cache d'extension du pool de mémoires tampons. L'extension de fichier doit être spécifiée comme .BPE. Vous devez désactiver BUFFER POOL EXTENSION avant de modifier FILENAME.  
  
 TAILLE = *taille* [ **Ko** | MO | GO]  
 Définit la taille du cache. La spécification de la taille par défaut est en Ko. La taille maximale est la taille de Max Server Memory. La limite est 32 fois la taille de Max Server Memory. Pour plus d’informations sur Max Server Memory, consultez [sp_configure &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 Vous devez désactiver BUFFER POOL EXTENSION avant de modifier la taille du fichier. Pour spécifier une taille inférieure à la taille actuelle, l'instance de SQL Server doit être redémarrer afin de récupérer de la mémoire. Sinon, la taille spécifiée doit être supérieure ou égale à la taille actuelle.  
  
 OFF  
 Désactive l'option d'extension du pool de mémoires tampons. Désactivez l'option d'extension du pool de mémoires tampons avant de modifier les paramètres associés tels que la taille ou le nom du fichier. Lorsque cette option est désactivée, toutes les informations de configuration associées sont supprimées du Registre.  
  
> [!WARNING]  
>  Désactiver l'extension du pool de mémoires tampons peut avoir un impact négatif sur les performances du serveur car le pool de mémoires tampons a une taille sensiblement réduite.  
  
 **\<Soft-NUMA >**  

**S'applique à**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ON  
 Active le partitionnement automatique fractionner des nœuds NUMA matériels volumineux dans des nœuds NUMA plus petits. La modification en cours d’exécution requiert un redémarrage du moteur de base de données.  
  
 OFF  
 Désactive le logiciel automatique le partitionnement des nœuds NUMA matériel de grande taille dans des nœuds NUMA plus petits. La modification en cours d’exécution requiert un redémarrage du moteur de base de données.  

> [!WARNING]  
> Il existe des problèmes avec le comportement de l’instruction ALTER SERVER CONFIGURATION avec l’option de configuration NUMA logicielle et l’Agent SQL Server connus.  Voici l’ordre recommandé des opérations :  
> 1) Arrêtez l’instance de SQL Server Agent.  
> 2) Exécuter votre option ALTER SERVER des logicielle NUMA.  
> 3) Redémarrez l’instance de SQL Server.  
> 4) Démarrez l’instance de SQL Server Agent.  
  
**Plus d’informations :** si un ALTER SERVER CONFIGURATION avec la commande SET SOFTNUMA est exécutée avant que le service SQL Server est redémarré, puis lorsque le service SQL Server Agent est arrêté, il exécute une commande T-SQL RECONFIGURE qui permettra de restaurer les paramètres SOFTNUMA à leur état antérieur ALTER SERVER CONFIGURATION. 
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Cette instruction ne nécessite pas un redémarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sauf spécification contraire. Dans le cas d'une instance du cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], elle ne requiert pas un redémarrage de la ressource de cluster [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Cette instruction ne prend pas en charge les déclencheurs DDL.  
  
## <a name="permissions"></a>Permissions  
 Requiert des autorisations ALTER SETTINGS pour l'option d'affinité de processus. Requiert des autorisations ALTER SETTINGS et VIEW SERVER STATE pour les options de propriété de cluster de basculement et de journal de diagnostics, et des autorisations CONTROL SERVER pour l'option de contexte de cluster HADR.  
  
 Nécessite l'autorisation ALTER SERVER STATE pour l'option d'entension du pool de mémoires tampons.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] ressource DLL s’exécute sous le compte système Local. Par conséquent, le compte Système local doit disposer d'un accès en lecture et en écriture au chemin d'accès spécifié dans l'option de journal de diagnostics.  
  
## <a name="examples"></a>Exemples  
  
|Catégorie|Éléments syntaxiques proposés|  
|--------------|------------------------------|  
|[Affinité du processus de configuration](#Affinity)|CPU • NUMANODE • AUTO|  
|[Définition des options du journal de Diagnostics](#Diagnostic)|ON • OFF • PATH • MAX_SIZE|  
|[Définition des propriétés de cluster de basculement](#Failover)|HealthCheckTimeout|  
|[Modification du contexte de cluster d’un réplica de disponibilité](#ChangeClusterContextExample)|**'** *windows_cluster* **'**|  
|[Définition de l’extension de pool de mémoires tampons](#BufferPoolExtension)|BUFFER POOL EXTENSION|  
  
###  <a name="Affinity"></a>Affinité du processus de configuration  
 Les exemples de cette section montrent comment définir l'affinité de processus sur les unités centrales et les nœuds NUMA. Dans les exemples suivants, on part de l'hypothèse que le serveur contient 256 unités centrales qui sont réparties dans quatre groupes de 16 nœuds NUMA chacun. Les threads ne sont attribués à aucun nœud NUMA ou UC.  
  
-   Groupe 0 : Nœuds NUMA 0 à 3, UC 0 à 63  
-   Groupe 1 : Les nœuds NUMA 4 à 7 pour processeurs 64 à 127  
-   Groupe 2 : Les nœuds NUMA 8 à 12, les unités centrales 128 à 191.  
-   Groupe 3 : nœuds NUMA 13 à 16, unités centrales 192 à 255  
  
#### <a name="a-setting-affinity-to-all-cpus-in-groups-0-and-2"></a>A. Définition de l'affinité sur toutes les unités centrales dans les groupes 0 et 2  
 L'exemple suivant définit l'affinité sur toutes les unités centrales dans les groupes 0 et 2.  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=0 TO 63, 128 TO 191;  
```  
  
#### <a name="b-setting-affinity-to-all-cpus-in-numa-nodes-0-and-7"></a>B. Définition de l'affinité sur toutes les unités centrales dans les nœuds NUMA 0 et 7  
 L'exemple suivant définit l'affinité UC sur les nœuds `0` et `7` uniquement.  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY NUMANODE=0, 7;  
```  
  
#### <a name="c-setting-affinity-to-cpus-60-through-200"></a>C. Définition de l'affinité sur les unités centrales entre 60 et 200  
 L'exemple suivant définit l'affinité sur les unités centrales entre 60 et 200.  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=60 TO 200;  
```  
  
#### <a name="d-setting-affinity-to-cpu-0-on-a-system-that-has-two-cpus"></a>D. Définition de l'affinité sur l'UC 0 sur un système qui compte deux unités centrales  
 L'exemple suivant définit l'affinité sur `CPU=0` sur un ordinateur qui compte deux unités centrales. Avant l'exécution de l'instruction suivante, le masque de bits d'affinité interne est de 00.  
  
```  
ALTER SERVER CONFIGURATION SET PROCESS AFFINITY CPU=0;  
```  
  
#### <a name="e-setting-affinity-to-auto"></a>E. Définition de l'affinité sur AUTO  
 L'exemple suivant définit l'affinité sur la valeur `AUTO`.  
  
```  
ALTER SERVER CONFIGURATION  
SET PROCESS AFFINITY CPU=AUTO;  
```  
  
###  <a name="Diagnostic"></a> Setting diagnostic log options  
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Les exemples de cette section montrent comment définir les valeurs de l'option de journal de diagnostics.  
  
#### <a name="a-starting-diagnostic-logging"></a>A. Début de la journalisation des diagnostics  
 L'exemple suivant démarre la journalisation de données de diagnostics.  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG ON;  
```  
  
#### <a name="b-stopping-diagnostic-logging"></a>B. Fin de la journalisation des diagnostics  
 L'exemple suivant met fin à la journalisation des données de diagnostics.  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG OFF;  
```  
  
#### <a name="c-specifying-the-location-of-the-diagnostic-logs"></a>C. Spécification de l'emplacement des journaux de diagnostics  
 L'exemple suivant définit l'emplacement des journaux de diagnostics sur le chemin d'accès au fichier spécifié.  
  
```  
ALTER SERVER CONFIGURATION  
SET DIAGNOSTICS LOG PATH = 'C:\logs';  
```  
  
#### <a name="d-specifying-the-maximum-size-of-each-diagnostic-log"></a>D. Spécification de la taille maximale de chaque journal de diagnostics  
 L'exemple suivant définit la taille maximale de chaque journal de diagnostics sur 10 mégaoctets.  
  
```  
ALTER SERVER CONFIGURATION   
SET DIAGNOSTICS LOG MAX_SIZE = 10 MB;  
```  
  
###  <a name="Failover"></a>Définition des propriétés de cluster de basculement  
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 L'exemple suivant illustre la définition des valeurs des propriétés de ressource de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### <a name="a-specifying-the-value-for-the-healthchecktimeout-property"></a>A. Spécification de la valeur de la propriété HealthCheckTimeout  
 L'exemple suivant définit l'option `HealthCheckTimeout` sur 15 000 millisecondes (15 secondes).  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
###  <a name="ChangeClusterContextExample"></a> B. Modification du contexte de cluster d'un réplica de disponibilité  
 L'exemple qui suit remplace le contexte de cluster HADR de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour spécifier le cluster WSFC de destination, `clus01`, l'exemple spécifie le nom d'objet cluster complet, `clus01.xyz.com`.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
### <a name="setting-buffer-pool-extension-options"></a>Définition des options d'extension du pool de mémoires tampons  
  
####  <a name="BufferPoolExtension"></a> A. Définition de l'option d'extension du pool de mémoires tampons  
  
**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 L'exemple suivant active l'option d'extension du pool de mémoires tampons et spécifie un nom de fichier et une taille.  
  
```  
ALTER SERVER CONFIGURATION   
SET BUFFER POOL EXTENSION ON  
    (FILENAME = 'F:\SSDCACHE\Example.BPE', SIZE = 50 GB);  
```  
  
#### <a name="b-modifying-buffer-pool-extension-parameters"></a>B. Modifier les paramètres de l'extension du pool de mémoires tampons  
 L'exemple suivant modifie la taille du fichier d'extension du pool de mémoires tampons. L'option d'extension du pool de mémoires tampons doit être désactivée avant de modifier les paramètres.  
  
```  
ALTER SERVER CONFIGURATION   
SET BUFFER POOL EXTENSION OFF;  
GO  
EXEC sp_configure 'max server memory (MB)', 12000;  
GO  
RECONFIGURE;  
GO  
ALTER SERVER CONFIGURATION  
SET BUFFER POOL EXTENSION ON  
    (FILENAME = 'F:\SSDCACHE\Example.BPE', SIZE = 60 GB);  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Soft-NUMA &#40; SQL Server &#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)   
 [Modifier le contexte de Cluster HADR de l’Instance de serveur &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)   
 [Sys.DM_OS_SCHEDULERS &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)   
 [Sys.dm_os_memory_nodes &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-nodes-transact-sql.md)   
 [Sys.dm_os_buffer_pool_extension_configuration &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-pool-extension-configuration-transact-sql.md)   
 [Extension du pool de mémoires tampons](../../database-engine/configure-windows/buffer-pool-extension.md)  
  
  

