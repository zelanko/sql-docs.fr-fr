---
title: Ce que&#39;nouveauté dans SQL Server 2014 | Documents Microsoft
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- database-engine
- integration-services
- master-data-services
- replication
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
caps.latest.revision: 70
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9144eeb653649e36cfed3551e4ec465d403ffdcb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042602"
---
# <a name="what39s-new-in-sql-server-2014"></a>Ce que&#39;nouveauté dans SQL Server 2014
  Cette rubrique résume détaillées des liens vers les nouvelles fonctionnalités de [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] et résume les packs de services pour [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Essayez-le :** ![Machine virtuelle Azure petit](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) ont un compte Azure ?  Passez **[ici](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** Spin une machine virtuelle avec SQL Server 2014 Service Pack 1 (SP1) déjà installé. 
  
-   [Quelles sont les nouveautés &#40;du moteur de base de données&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Quelles sont les nouveautés dans Analysis Services et Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md)  
  
-   [Nouveautés liées à l’installation de SQL Server](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] a introduit pas de nouvelles fonctionnalités importantes pour les éléments suivants :**  
  
-   [Quelles sont les nouveautés &#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Quelles sont les nouveautés &#40;réplication&#41;](../relational-databases/replication/what-s-new-replication.md)  
  
-   [Quelles sont les nouveautés &#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP1) n’avez pas introduit de nouvelles fonctionnalités importantes.
-  [Informations de version de SQL Server 2014 Service Pack 1 ](https://support.microsoft.com/en-us/kb/3058865).
-  [![Télécharger le Service Pack 1 pour Microsoft® SQL Server® 2014](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) [télécharger le Service Pack 1 pour Microsoft® SQL Server® 2014](https://www.microsoft.com/en-us/download/details.aspx?id=46694).


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 2 (SP2)
- [Informations de version de SQL Server 2014 Service Pack 2](https://support.microsoft.com/en-us/kb/3171021).
-  [![Télécharger le Service Pack 2 pour Microsoft® SQL Server® 2014](./media/what-s-new-in-sql-server-2016/download.png)](http://go.microsoft.com/fwlink/?LinkID=821558) [télécharger le Service Pack 2 pour Microsoft® SQL Server® 2014](http://go.microsoft.com/fwlink/?LinkID=821558).
-  [![Télécharger SQL Server 2014 SP2 Feature Pack](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [télécharger le Feature Pack SQL Server 2014 SP2](https://www.microsoft.com/en-us/download/details.aspx?id=53164).

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP2) Inclut les améliorations suivantes :

### <a name="performance-and-scalability-improvements"></a>Performances et évolutivité 
-   **Le partitionnement automatique configuration NUMA logicielle :** avec [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2, configuration NUMA logicielle automatique est activée lorsque 8079 d’indicateur de Trace est activé au cours du démarrage de l’instance. Lorsque 8079 d’indicateur de Trace est activé lors du démarrage, [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 sera interroger la disposition du matériel et configurer automatiquement la configuration NUMA logicielle sur les systèmes de création de rapports 8 ou plusieurs processeurs par nœud NUMA. Le comportement NUMA automatique, souple est Hyperthread (processeur logique/HT) prenant en charge. Le partitionnement et la création de nœuds supplémentaires permettent de dimensionner le traitement en arrière-plan en augmentant le nombre d’écouteurs, le nombre d’instances, ainsi que les capacités réseau et de chiffrement. Il est recommandé pour le premier test la charge de travail de performances avec Auto-Soft NUMA avant de l’activer en production. [Consultez le Blog pour plus d’informations](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Mise à l’échelle objet de mémoire dynamique :** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 partitions dynamiquement des objets de mémoire en fonction du nombre de nœuds et de cœurs à l’échelle sur du matériel moderne. L’objectif de la promotion dynamique est partitionner automatiquement un objet mémoire sécurisée de thread (CMEMTHREAD) s’il devient un goulot d’étranglement. Objets de mémoire non partitionné peuvent être promues dynamiquement pour être partitionnée par nœud (nombre de partitions est égal à des nœuds NUMA), et objets partitionnées par nœud peuvent en plus de la mémoire est promue pour être partitionné par processeur (nombre de partitions est égal à Unités centrales). [Consultez le blog pour plus d’informations](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **Indicateur MAXDOP pour DBCC CHECK\* commandes :** cette amélioration adresses [(468694) de commentaires connect](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). Vous pouvez maintenant exécuter DBCC CHECKDB avec l’un paramètre MAXDOP autre que la valeur de sp_configure. Si MAXDOP dépasse la valeur configurée avec Resource Governor, le moteur de base de données utilise la valeur MAXDOP de Resource Governor, décrite dans ALTER WORKLOAD GROUP (Transact-SQL). Toutes les règles sémantiques utilisées avec l'option de configuration max degree of parallelism sont applicables lorsque vous utilisez l'indicateur de requête MAXDOP. Pour plus d’informations, consultez [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **Activer > 8 To pour le Pool de mémoires tampons :** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 permet à 128 To d’espace d’adressage virtuel pour l’utilisation du pool de mémoires tampons. Cette amélioration permet de Pool de mémoires tampons de SQL Server à l’échelle au-delà de 8 To sur du matériel moderne.
-   **SOS_RWLock spinlock d’amélioration du produit :** SOS_RWLock l’est une primitive de synchronisation utilisée dans divers emplacements de la base de code SQL Server.  Comme son nom l’indique, le code peut avoir plusieurs partagés (lecteurs) ou la propriété d’unique (écriture). Cette amélioration supprime la nécessité de verrouillage spinlock pour SOS_RWLock et utilise à la place des techniques de verrouillage similaires à OLTP en mémoire. Cette modification, nombre de threads de lire une structure de données protégée par SOS_RWLock en parallèle sans blocage d’eux et en fournissant une extensibilité accrue. Avant cette modification, l’implémentation d’un verrouillage spinlock n'autorisé qu’un seul thread acquérir le SOS_RWLock à la fois, même pour lire une structure de données.  [Consultez le blog pour plus d’informations](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Spatiale implémentation Native :** une amélioration significative des performances de requête spatiale est introduite dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 via l’implémentation native. Pour plus d’informations, consultez la [l’article de la base de connaissances KB3107399](https://support.microsoft.com/en-us/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Prise en charge et les améliorations des Diagnostics
-   **Clonage de base de données :** base de données du Clone est une commande DBCC qui améliore la résolution des problèmes de bases de données de production existant par le schéma et les métadonnées sans les données de clonage. Le clone est créé avec la commande `DBCC clonedatabase(‘source_database_name’, ‘clone_database_name’)`.  **Remarque :** clonage de bases de données ne doivent pas être utilisés dans les environnements de production. Utilisez la commande suivante déterminer si une base de données a été généré à partir d’une base de données cloné : `select DATABASEPROPERTYEX('clonedb', 'isClone')`. La valeur de retour de **1** indique la base de données est créée à partir de la commande clonedatabase lors de la **0** indique qu’il n’est pas un clone.
-   **Prise en charge de tempdb :** un nouveau message du journal des erreurs qui indique le nombre de fichiers tempdb et de la taille/croissance automatique de données tempdb fichiers présent au démarrage du serveur.
-   **Journalisation de l’initialisation instantanée fichier de base de données :** un nouveau message du journal des erreurs qui indique sur Startup du serveur, l’état de la base de données initialisation instantanée des fichiers (activé/désactivé).
-   **Noms de module dans la pile des appels :** Xevent de la pile des appels inclut désormais les noms de modules + décalage au lieu d’adresses absolues.
-   **Nouvelle DMF pour les statistiques incrémentielles :** cette amélioration adresses [connecter des commentaires (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) pour activer le suivi des statistiques incrémentielles au niveau de la partition. Un nouveau sys.dm_db_incremental_stats_properties DMF est introduit pour exposer des informations par partition pour les statistiques incrémentielles.
-   **Comportement de gestion dynamique de l’utilisation des index mis à jour :** cette amélioration adresses [connecter des commentaires (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) à partir de clients où la reconstruction d’un index sera *pas* effacer l’entrée de la ligne existante à partir de sys.dm_db _index_usage_stats pour cet index. Le comportement est maintenant le même que dans SQL 2008 et SQL Server 2016. [Consultez le blog pour plus d’informations](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Amélioration de corrélation entre les diagnostics XE et les vues de gestion dynamique :** cette amélioration adresses [(1934583) de commentaires connect](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). Query_hash et query_plan_hash sont utilisés pour identifier de façon unique une requête. DMV les définit comme des champs varbinary(8), tandis que XEvent les définit comme des champs UINT64. Étant donné que SQL server n’a pas de « unisigned bigint », cast ne fonctionne pas toujours. Cette amélioration introduit de nouvelles colonnes d’action et de filtre XEvent équivalentes aux champs query_hash et query_plan_hash. La différence est qu’elles sont définies comme des colonnes INT64, ce qui permet une meilleure corrélation des requêtes entre XE et DMV.
-   **Prise en charge de UTF-8 dans l’instruction BULK INSERT et BCP :** cette amélioration adresses [(370419) de commentaires connect](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) où la prise en charge pour l’exportation et importation des données encodées dans le jeu de caractères UTF-8 est maintenant activée dans l’instruction BULK INSERT et BCP.
-   **Profilage de l’exécution de requête opérateur léger :** lors de la résolution des problèmes de performances des requêtes, bien que showplan fournit beaucoup d’informations sur le plan d’exécution de requête et le coût de l’opérateur dans le plan, mais il a limité les informations sur réel statistiques d’exécution comme (UC, lectures d’e/s, temps écoulé par thread). SQL 2014 SP2 introduit ces statistiques d’exécution supplémentaires par un opérateur dans le plan d’exécution, ainsi qu’un XEvent (query_thread_profile) pour faciliter la résolution des problèmes de performances des requêtes. [Consultez le blog pour plus d’informations](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Nettoyage du suivi de modification :** une nouvelle procédure stockée `sp_flush_CT_internal_table_on_demand` est introduit pour le nettoyage du suivi des modifications des tables internes à la demande.
-   **Journalisation de délai d’expiration de bail AlwaysON** ajouté la nouvelle fonctionnalité de journalisation pour les messages de délai de bail afin que l’heure actuelle et les heures de renouvellement attendus sont enregistrés. Également un nouveau message a été introduit dans le journal des erreurs SQL concernant les délais d’attente. [Consultez le blog pour plus d’informations](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **DMF nouveau pour la récupération d’entrée de mémoire tampon dans SQL Server :** un nouveau DMF pour la récupération de la mémoire tampon d’entrée pour une session/demande (sys.dm_exec_input_buffer) est disponible. Il s’agit d’une fonctionnalité équivalente à DBCC INPUTBUFFER. [Consultez le blog pour plus d’informations](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Atténuation d’allocation de mémoire sous-estimée et surestimés :** ajouté de nouveaux indicateurs de requête pour le gouverneur de ressources via MIN_GRANT_PERCENT et MAX_GRANT_PERCENT. Cela vous permet de tirer parti de ces indicateurs lors de l’exécution des requêtes par la limitation des allocations de mémoire pour éviter la contention de mémoire. Pour plus d’informations, consultez [l’article de la base de connaissances KB310740](https://support.microsoft.com/en-us/kb/3107401)
-   **Une meilleure diagnostics grant de l’utilisation de la mémoire :** un nouvel événement étendu a été ajouté à la liste des fonctionnalités de suivi dans SQL Server (query_memory_grant_usage) pour effectuer le suivi d’allocation de mémoire demandée et accordée. Cela fournit les meilleures possibilités de suivi et l’analyse pour résoudre les problèmes d’exécution de requête liés à des allocations de mémoire. Pour plus d’informations, consultez [l’article de la base de connaissances KB3107173](https://support.microsoft.com/en-us/kb/3107173).
-   **Interroger des diagnostics d’exécution pour le vidage de tempdb :**-Hash Warning et Sort Warnings désormais ont des colonnes supplémentaires pour effectuer le suivi des statistiques e/s physiques, mémoire utilisée et des lignes affectées. Nous avons également introduit un nouvel événement étendu hash_spill_details. Maintenant vous pouvez suivre des informations plus précises de votre avertissements de hachage et de tri ([KB3107172](https://support.microsoft.com/en-us/kb/3107172)). Cette amélioration est désormais également exposée via les Plans de requête XML sous la forme d’un nouvel attribut au type complexe SpillToTempDbType ([KB3107400](https://support.microsoft.com/en-us/kb/3107400)). Définir des statistiques sur maintenant affiche des statistiques de table de travail de tri. .
-   **Amélioration des diagnostics pour les plans d’exécution qui impliquent l’insertion d’un prédicat résiduelle :** réels lignes lues va maintenant être transmis dans les plans d’exécution de requête pour aider à améliorer les performances de requête résolution des problèmes. Cela doit inverser la nécessité de capture de SET STATISTICS IO séparément. Cela maintenant vous permet de vous permet de voir les informations relatives à une insertion d’un prédicat résiduelle dans un plan de requête. Pour plus d’informations, consultez [l’article de la base de connaissances KB3107397](https://support.microsoft.com/en-us/kb/3107397).


## <a name="additional-information"></a>Informations supplémentaires  
 [Ressources SQL Server 2014](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 Release Notes](http://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [Centre de ressources SQL Server 2014](http://msdn.microsoft.com/sqlserver/dn135309)  
  
 [Site Web SQLCat](http://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  