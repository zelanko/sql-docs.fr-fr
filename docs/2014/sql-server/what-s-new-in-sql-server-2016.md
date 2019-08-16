---
title: Nouveautés&#39;de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: f368da503c90595624f476344724719206cdb77c
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893701"
---
# <a name="what39s-new-in-sql-server-2014"></a>Nouveautés&#39;de SQL Server 2014
  Cette rubrique résume les liens détaillés vers les nouvelles [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] fonctionnalités de et résume les services packs pour[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Essayez :** ![La petite](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) machine virtuelle Azure dispose d’un compte Azure?  Cliquez **[ici](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** pour lancer une machine virtuelle avec SQL Server 2014 Service Pack 1 (SP1) déjà installé. 
  
-   [Nouveautés &#40;moteur de base de données&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Nouveautés de Analysis Services et Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)  
  
-   [Nouveautés liées à l’installation de SQL Server](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]n’a pas introduit de nouvelles fonctionnalités significatives pour les éléments suivants:**  
  
-   [Nouveautés &#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Nouveautés &#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)](SP1) n’a pas introduit de nouvelles fonctionnalités significatives.
-  [SQL Server les informations de publication du Service Pack 1 2014](https://support.microsoft.com/en-us/kb/3058865).
-  [![Télécharger le Service Pack 1 pour Microsoft? SQL Server?? ](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) 2014[Télécharger le Service Pack 1 pour Microsoft? SQL Server?? 2014](https://www.microsoft.com/en-us/download/details.aspx?id=46694).


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Service Pack 2 (SP2)
- [Informations de publication de SQL Server 2014 Service Pack 2](https://support.microsoft.com/en-us/kb/3171021).
-  [![Télécharger le Service Pack 2 pour Microsoft? SQL Server?? ](./media/what-s-new-in-sql-server-2016/download.png)](https://go.microsoft.com/fwlink/?LinkID=821558) 2014[Télécharger le Service Pack 2 pour Microsoft? SQL Server?? 2014](https://go.microsoft.com/fwlink/?LinkID=821558).
-  [![Télécharger SQL Server 2014 SP2 Feature Pack](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [Téléchargez le Feature Pack SQL Server 2014 SP2](https://www.microsoft.com/en-us/download/details.aspx?id=53164).

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]INSTALLÉ Comprend les améliorations suivantes:

### <a name="performance-and-scalability-improvements"></a>Améliorations des performances et de l’évolutivité 
-   **Partitionnement NUMA automatique:** Avec [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2, le NUMA logiciel automatique est activé lorsque l’indicateur de trace 8079 est activé au démarrage de l’instance. Lorsque l’indicateur de trace 8079 est activé au [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] démarrage, SP2 interroge la disposition matérielle et configure automatiquement le NUMA logiciel sur les systèmes Reporting 8 UC ou plus par nœud NUMA. Le comportement NUMA automatique et logiciel est compatible avec les hyperthreads (HT/Logical Processor). Le partitionnement et la création de nœuds supplémentaires permettent de dimensionner le traitement en arrière-plan en augmentant le nombre d’écouteurs, le nombre d’instances, ainsi que les capacités réseau et de chiffrement. Il est recommandé de commencer par tester la charge de travail des performances avec la technologie NUMA auto-Soft avant de la mettre en production. [Pour plus d’informations, consultez le blog](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Mise à l’échelle des objets Mémoire dynamique:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 partitionne dynamiquement les objets mémoire en fonction du nombre de nœuds et de cœurs à mettre à l’échelle sur le matériel moderne. L’objectif de la promotion dynamique est de partitionner automatiquement un objet mémoire sécurisée (CMEMTHREAD) de thread s’il devient un goulot d’étranglement. Les objets mémoire non partitionnés peuvent être promus de manière dynamique pour être partitionnés par nœud (nombre de partitions égal au nombre de nœuds NUMA) et les objets mémoire partitionnés par nœud peuvent être promus davantage pour être partitionnés par UC (nombre de partitions égal au nombre de Unités centrales). [Pour plus d’informations, consultez le blog](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **Indicateur MAXDOP pour les commandes\* DBCC CHECK:** Cette amélioration concerne la [connexion aux commentaires (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). Vous pouvez maintenant exécuter DBCC CHECKDB avec un paramètre MAXDOP autre que la valeur sp_configure. Si MAXDOP dépasse la valeur configurée avec Resource Governor, le moteur de base de données utilise la valeur MAXDOP de Resource Governor, décrite dans ALTER WORKLOAD GROUP (Transact-SQL). Toutes les règles sémantiques utilisées avec l'option de configuration max degree of parallelism sont applicables lorsque vous utilisez l'indicateur de requête MAXDOP. Pour plus d’informations, consultez [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **Activer > 8 to pour le pool de mémoires tampons:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 active la 128TB de l’espace d’adressage virtuel pour l’utilisation du pool de mémoires tampons. Cette amélioration permet à SQL Server pool de mémoires tampons de s’adapter au-delà de 8 to sur le matériel moderne.
-   **Amélioration du verrouillage SpinLock SOS_RWLock:** Le SOS_RWLock est une primitive de synchronisation utilisée à différents emplacements dans la base de code SQL Server.  Comme son nom l’indique, le code peut avoir plusieurs propriétés Shared (Readers) ou Single (Writer). Cette amélioration élimine le besoin de verrouillage SpinLock pour SOS_RWLock et utilise plutôt des techniques sans verrou similaires à l’OLTP en mémoire. Avec cette modification, de nombreux threads peuvent lire une structure de données protégée par SOS_RWLock en parallèle sans se bloquer les unes les autres et ainsi offrir une évolutivité accrue. Avant cette modification, l’implémentation de SpinLock permettait à un seul thread d’acquérir le SOS_RWLock à la fois, même pour lire une structure de données.  [Pour plus d’informations, consultez le blog](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Implémentation native spatiale:** Une amélioration significative des performances des requêtes spatiales [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] est introduite dans SP2 par le biais de l’implémentation native. Pour plus d’informations, consultez l’article de la [base de connaissances KB3107399](https://support.microsoft.com/en-us/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Améliorations de la prise en charge et des diagnostics
-   **Clonage de base de données:** Clone Database est une nouvelle commande DBCC qui améliore la résolution des problèmes de bases de données de production existantes en clonant le schéma et les métadonnées sans les données. Le clone est créé avec la `DBCC clonedatabase('source_database_name', 'clone_database_name')`commande.  **Remarque :** Les bases de données clonées ne doivent pas être utilisées dans les environnements de production. Utilisez la commande suivante pour déterminer si une base de données a été générée à partir d' `select DATABASEPROPERTYEX('clonedb', 'isClone')`une base de données clonée:. La valeur de retour **1** indique que la base de données est créée à partir de clonedatabase, tandis que **0** indique qu’il ne s’agit pas d’un clone.
-   **Prise en charge de tempdb:**  Nouveau message ErrorLog qui indique le nombre de fichiers tempdb et la taille/croissance automatique des fichiers de données tempdb présents au démarrage du serveur.
-   **Journalisation de l’initialisation instantanée des fichiers de base de données:** Nouveau message ErrorLog qui indique, sur le serveur statup, l’état de l’initialisation instantanée des fichiers de base de données (activé/désactivé).
-   **Noms de modules dans la pile des appels:** La pile d’appels XEvent comprend maintenant des noms de modules et des décalages à la place des adresses absolues.
-   **Nouveau DMF pour les statistiques incrémentielles:** Cette amélioration résout les [Commentaires de connexion (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) pour permettre le suivi des statistiques incrémentielles au niveau de la partition. Un nouveau DMF sys. DM _db_incremental_stats_properties est introduit pour exposer les informations par partition pour les statistiques incrémentielles.
-   **Comportement DMV de l’index mis à jour:** Cette amélioration résout les [Commentaires de connexion (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) des clients où la reconstruction d’un index n’efface *pas* les entrées de ligne existantes de sys. DM _db_index_usage_stats pour cet index. Le comportement est maintenant le même que dans SQL 2008 et SQL Server 2016. [Pour plus d’informations, consultez le blog](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Corrélation améliorée entre XE et DMV de diagnostic:** Cette amélioration concerne la [connexion aux commentaires (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). Query_hash et query_plan_hash sont utilisés pour identifier une requête de façon unique. DMV les définit comme des champs varbinary(8), tandis que XEvent les définit comme des champs UINT64. Étant donné que SQL Server n’a pas de «UNISIGNED BIGINT», le cast ne fonctionne pas toujours. Cette amélioration introduit de nouvelles colonnes d’action et de filtre XEvent équivalentes aux champs query_hash et query_plan_hash. La différence est qu’elles sont définies comme des colonnes INT64, ce qui permet une meilleure corrélation des requêtes entre XE et DMV.
-   **Prise en charge d’UTF-8 dans BULK INSERT et BCP:** Cette amélioration permet de [se connecter à Feedback (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) où la prise en charge de l’exportation et de l’importation de données encodées au format UTF-8 est désormais activée dans BULK INSERT et bcp.
-   **Profilage d’exécution de requête par opérateur léger:** Lors de la résolution des problèmes de performances des requêtes, bien que Showplan fournisse beaucoup d’informations sur le plan d’exécution de requête et le coût de l’opérateur dans le plan, mais il dispose d’informations limitées sur les statistiques d’exécution réelles comme (processeur, lectures d’e/s, temps écoulé par thread). SQL 2014 SP2 introduit ces statistiques d’exécution supplémentaires par opérateur dans le plan d’exécution de requêtes, ainsi qu’un XEvent (query_thread_profile) pour aider à résoudre les problèmes de performances des requêtes. [Pour plus d’informations, consultez le blog](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Nettoyage de la Change Tracking:** Une nouvelle procédure `sp_flush_CT_internal_table_on_demand` stockée est introduite pour nettoyer les tables internes de suivi des modifications à la demande.
-   **Journalisation du délai d’expiration de bail** AlwaysOn Ajout d’une nouvelle fonctionnalité de journalisation pour les messages de délai d’expiration de bail afin que l’heure actuelle et les durées de renouvellement attendues soient journalisées. En outre, un nouveau message a été introduit dans le journal des erreurs SQL en ce qui concerne les délais d’attente. [Pour plus d’informations, consultez le blog](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **Nouveau DMF pour la récupération de la mémoire tampon d’entrée dans SQL Server:** Une nouvelle DMF pour la récupération de la mémoire tampon d’entrée pour une session/requête (sys.dm_exec_input_buffer) est maintenant disponible. Il s’agit d’une fonctionnalité équivalente à DBCC INPUTBUFFER. [Pour plus d’informations, consultez le blog](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Atténuation des allocations de mémoire sous-estimée et surestimée:** Ajout de nouveaux indicateurs de requête pour Resource Governor via MIN_GRANT_PERCENT et MAX_GRANT_PERCENT. Cela vous permet de tirer parti de ces indicateurs lors de l’exécution de requêtes en limitant leurs allocations de mémoire pour éviter la contention de mémoire. Pour plus d’informations, consultez [l’article de la base de connaissances KB310740](https://support.microsoft.com/en-us/kb/3107401)
-   **Amélioration des diagnostics d’allocation/utilisation de la mémoire:** Un nouvel événement étendu a été ajouté à la liste des fonctionnalités de suivi dans SQL Server (query_memory_grant_usage) pour suivre les allocations de mémoire demandées et accordées. Cela offre de meilleures fonctionnalités de suivi et d’analyse pour résoudre les problèmes d’exécution de requête liés aux allocations de mémoire. Pour plus d’informations, consultez [l’article de la base de connaissances KB3107173](https://support.microsoft.com/en-us/kb/3107173).
-   **Diagnostics de l’exécution des requêtes pour**le débordement de tempdb:-les avertissements de tri et d’avertissement de hachage possèdent désormais des colonnes supplémentaires pour suivre les statistiques d’e/s physiques, la mémoire utilisée et les lignes affectées. Nous avons également introduit un nouvel événement étendu hash_spill_details. Vous pouvez désormais suivre des informations plus granulaires pour vos avertissements de hachage et de tri ([KB3107172](https://support.microsoft.com/en-us/kb/3107172)). Cette amélioration est également exposée à travers les plans de requête XML sous la forme d’un nouvel attribut au type complexe SpillToTempDbType ([KB3107400](https://support.microsoft.com/en-us/kb/3107400)). Set Statistics on affiche désormais les statistiques de tables de travail de tri. .
-   **Amélioration des diagnostics pour les plans d’exécution de requête qui impliquent la poussée des prédicats résiduels:** La lecture des lignes réelles sera désormais signalée dans les plans d’exécution de la requête afin d’améliorer la résolution des problèmes de performances des requêtes. Cela doit annuler la capture des e/s des statistiques SET séparément. Cela vous permet désormais de voir les informations relatives à un détourage de prédicat résiduel dans un plan de requête. Pour plus d’informations, consultez [l’article de la base de connaissances KB3107397](https://support.microsoft.com/en-us/kb/3107397).


## <a name="additional-information"></a>Informations supplémentaires  
 [Ressources SQL Server 2014](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [Centre de ressources SQL Server 2014](https://msdn.microsoft.com/sqlserver/dn135309)  
  
 [Site Web SQLCat](https://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  
