---
title: Gestion des charges de travail
description: Gestion des charges de travail dans Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: d14714cb23a9f6b0d6cc63ddca5049cb6741017c
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "74399442"
---
# <a name="workload-management-in-analytics-platform-system"></a>Gestion des charges de travail dans Analytics Platform System

Les fonctionnalités de gestion des charges de travail de SQL Server PDW permettent aux utilisateurs et aux administrateurs d’assigner des demandes aux configurations prédéfinies de mémoire et à la concurrence. Utilisez la gestion des charges de travail pour améliorer les performances de votre charge de travail, qu’elles soient cohérentes ou mixtes, en autorisant les demandes à disposer des ressources appropriées sans priver les demandes indéfiniment.  
  
Par exemple, avec les techniques de gestion de la charge de travail dans SQL Server PDW, vous pouvez :  
  
-   Allouez un grand nombre de ressources à un travail de chargement.  
  
-   Spécifiez plus de ressources pour la génération d’un index ColumnStore.  
  
-   Dépannez une jointure de hachage à exécution lente pour voir si elle a besoin de plus de mémoire, puis donnez-lui plus de mémoire.  
  
## <a name="workload-management-basics"></a><a name="Basics"></a>Notions de base de la gestion de la charge  
  
### <a name="key-terms"></a>Termes clés  
Gestion des charges de travail  
La *gestion des charges de travail* est la capacité à comprendre et à ajuster l’utilisation des ressources système afin d’obtenir les meilleures performances pour les demandes simultanées.  
  
Classe de ressource  
Dans SQL Server PDW, une *classe de ressource* est un rôle serveur intégré qui a des limites préaffectées pour la mémoire et l’accès concurrentiel. SQL Server PDW alloue des ressources aux demandes en fonction de l’appartenance au rôle de serveur de la classe de ressources de la connexion qui soumet les demandes.  
  
Sur les nœuds de calcul, l’implémentation des classes de ressources utilise la fonctionnalité Resource Governor dans SQL Server. Pour plus d’informations sur Resource Governor, consultez [Resource Governor](../relational-databases/resource-governor/resource-governor.md) sur MSDN.  
  
### <a name="understand-current-resource-utilization"></a>Comprendre l’utilisation actuelle des ressources  
Pour comprendre l’utilisation des ressources système pour les demandes en cours d’exécution, utilisez la SQL Server PDW vues de gestion dynamique. Par exemple, vous pouvez utiliser les vues DMV pour comprendre si une jointure de hachage volumineuse à exécution lente peut tirer parti d’une plus grande quantité de mémoire.  
  
<!-- MISSING LINKS
For examples, see [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md).  
-->
  
### <a name="adjust-resource-allocations"></a>Ajuster les allocations de ressources  
Pour ajuster l’utilisation des ressources, modifiez l’appartenance à la classe de ressource de la connexion qui soumet la demande. Les rôles de serveur de classe de ressources sont nommés **mediumrc**, **largerc**et **xlargerc**. Ils représentent respectivement des allocations de ressources moyennes, volumineuses et très importantes.  
  
Par exemple, pour allouer une grande quantité de ressources système à une demande, ajoutez la connexion qui soumet la demande au rôle serveur **largerc** . L’instruction ALTER SERVER ROLE suivante ajoute la connexion Anna au rôle de serveur largerc.  
  
```sql  
ALTER SERVER ROLE largerc ADD MEMBER Anna;  
```  
  
## <a name="resource-class-descriptions"></a><a name="RC"></a>Descriptions des classes de ressources  
Le tableau suivant décrit les classes de ressources et leurs allocations de ressources système.  
  
|Classe de ressource|Importance de la demande|Utilisation maximale de la mémoire *|Emplacements de concurrence (maximum = 32)|Description|  
|------------------|----------------------|--------------------------|---------------------------------------|---------------|  
|default|Moyenne|400 Mo|1|Par défaut, chaque connexion est autorisée à disposer d’une petite quantité de mémoire et de ressources d’accès concurrentiel pour ses demandes.<br /><br />Lorsqu’une connexion est ajoutée à une classe de ressource, la nouvelle classe est prioritaire. Lorsqu’une connexion est supprimée de toutes les classes de ressources, la connexion revient à l’allocation de ressources par défaut.|  
|MediumRC|Moyenne|1200 MO|3|Exemples de requêtes qui peuvent nécessiter la classe de ressources de taille moyenne :<br /><br />Opérations CTAS qui ont des jointures de hachage volumineuses.<br /><br />Sélectionnez les opérations qui nécessitent davantage de mémoire pour éviter la mise en cache sur disque.<br /><br />Chargement de données dans des index ColumnStore en cluster.<br /><br />La création, la reconstruction et la réorganisation des index ColumnStore en cluster pour les tables plus petites qui ont 10-15 colonnes.|  
|Largerc|Élevé|2,8 GO|7|Exemples de requêtes qui peuvent nécessiter la classe de ressources volumineuse :<br /><br />Des opérations CTAS très volumineuses qui ont des jointures de hachage énormes, ou qui contiennent des agrégations volumineuses, telles que des clauses de commande ou GROUP BY volumineuses.<br /><br />Sélectionnez les opérations qui nécessitent de très grandes quantités de mémoire pour les opérations telles que les jointures de hachage ou les agrégations telles que les clauses ORDER BY ou GROUP BY.<br /><br />Chargement de données dans des index ColumnStore en cluster.<br /><br />La création, la reconstruction et la réorganisation des index ColumnStore en cluster pour les tables plus petites qui ont 10-15 colonnes.|  
|xlargerc|Élevé|8,4 GO|22|La classe de ressources extra large est destinée aux demandes qui peuvent nécessiter une grande consommation de ressources au moment de l’exécution.|  
  
<sup>*</sup>L’utilisation maximale de la mémoire est une approximation.  
  
### <a name="request-importance"></a>Importance de la demande  
L’importance de la demande correspond à la quantité de temps processeur que SQL Server, s’exécutant sur les nœuds de calcul, donnera aux demandes.  Les demandes avec une priorité plus élevée reçoivent plus de temps processeur.  
  
### <a name="maximum-memory-usage"></a>Utilisation maximale de la mémoire  
L’utilisation maximale de la mémoire est la quantité maximale de mémoire disponible qu’une demande peut utiliser dans chaque espace de traitement. Par exemple, une demande mediumrc peut utiliser jusqu’à 1200 Mo pour le traitement au sein de chaque distribution. Il est toujours important de s’assurer que les données ne sont pas inclinées afin d’éviter d’avoir quelques distributions effectuant la majeure partie du travail.  
  
### <a name="concurrency-slots"></a>Emplacements de concurrence  
L’objectif de l’allocation de 1, 3, 7 et 22 emplacements de concurrence est de permettre l’exécution simultanée des processus de grande taille et de petite taille, sans bloquer le petit processus lorsqu’un processus de grande taille est en cours d’exécution.  Par exemple, SQL Server PDW pouvez allouer au maximum 32 emplacements de concurrence pour exécuter 1 demande supplémentaire (22 emplacements), 1 demande volumineuse (7 emplacements) et 1 demande moyenne (3 emplacements) en même temps.  
  
Voici des exemples d’allouer jusqu’à 32 emplacements de concurrence aux demandes simultanées :  
  
-   28 emplacements = 4 grands  
  
-   30 emplacements = 10 moyens  
  
-   32 emplacements = 32 par défaut  
  
-   32 emplacements = 1 extra grand + 1 grand + 1 moyen  
  
-   32 emplacements = 2 grande + 4 moyen + 6 par défaut  
  
Supposons que 6 demandes volumineuses sont soumises à SQL Server PDW, puis que 10 demandes par défaut sont soumises. SQL Server PDW traitera les demandes par ordre de priorité comme suit :  
  
-   Allouez 28 emplacements d’accès concurrentiel pour démarrer le traitement de 4 demandes volumineuses, car la mémoire devient disponible et conservez 2 demandes volumineuses dans la file d’attente.  
  
-   Allouez 4 emplacements de concurrence pour commencer à traiter 4 demandes par défaut et conserver 6 demandes par défaut dans la file d’attente.  
  
À mesure que les demandes sont terminées et que les emplacements de concurrence deviennent disponibles, SQL Server PDW allouera les demandes restantes en fonction des ressources disponibles et de la priorité. Par exemple, lorsqu’il y a 7 emplacements de concurrence ouverts, les demandes en attente volumineuses auront une priorité plus élevée pour les 7 emplacements que les demandes de moyenne d’attente.  Si 6 emplacements sont ouverts, SQL Server PDW allouera 6 demandes supplémentaires de taille par défaut. Toutefois, les emplacements de mémoire et de concurrence doivent tous être disponibles avant que SQL Server PDW autorise l’exécution d’une demande.  
  
Dans chaque classe de ressources, les demandes s’exécutent dans l’ordre FIFO (First in First Out).  
  
## <a name="general-remarks"></a><a name="GeneralRemarks"></a>Remarques d'ordre général  
Si une connexion est membre de plusieurs classes de ressources, la classe présentant le plus de ressources est prioritaire.  
  
Lorsqu’une connexion est ajoutée ou supprimée d’une classe de ressource, la modification prend effet immédiatement pour toutes les demandes ultérieures. les demandes en cours d’exécution ou en attente ne sont pas affectées. La connexion n’a pas besoin de se déconnecter et de se reconnecter pour que la modification se produise.  
  
Pour chaque connexion, les paramètres de classe de ressources sont appliqués aux instructions et opérations individuelles, et non à la session.  
  
Avant que SQL Server PDW exécute une instruction, il tente d’acquérir les emplacements de concurrence nécessaires à la demande. S’il ne peut pas acquérir suffisamment d’emplacements de concurrence, SQL Server PDW déplace la requête dans un état d’attente d’exécution. Tous les systèmes de ressources qui ont déjà été alloués à la demande sont renvoyés au système.  
  
La plupart des instructions SQL ont toujours besoin des allocations de ressources par défaut, et ne sont donc pas contrôlées par les classes de ressources. Par exemple, la création d’une connexion n’a besoin que d’une petite quantité de ressources et est allouée aux ressources par défaut même si la connexion qui appelle CREATe LOGIN est membre d’une classe de ressource.  Par exemple, si Anna est membre de la classe de ressources largerc et qu’elle envoie une instruction CREATe LOGIN, l’instruction CREATe LOGIN s’exécute avec le nombre de ressources par défaut.  
  
Instructions et opérations SQL régies par des classes de ressources :  
  
-   ALTER INDEX REBUILD  
  
-   ALTER INDEX REORGANIZE  
  
-   ALTER TABLE REBUILD  
  
-   CRÉER UN INDEX CLUSTER  
  
-   CREATE CLUSTERED COLUMNSTORE INDEX  
  
-   CREATE TABLE AS SELECT  
  
-   CRÉER UNE TABLE DISTANTE COMME SELECT  
  
-   Chargement de données avec **dwloader**.  
  
-   INSERT-SELECT  
  
-   UPDATE  
  
-   Suppression  
  
-   RESTAURER la base de données lors de la restauration dans une appliance avec davantage de nœuds de calcul.  
  
-   SELECT, à l’exclusion de requêtes DMV uniquement  
  
## <a name="limitations-and-restrictions"></a><a name="Limits"></a>Limitations et restrictions  
Les classes de ressources gouvernent les allocations de mémoire et de concurrence.  Elles ne régissent pas les opérations d’entrée/sortie.  
  
## <a name="metadata"></a><a name="Metadata"></a>Métadonnées  
DMV qui contiennent des informations sur les classes de ressources et les membres de la classe de ressources.  
  
-   [sys.server_role_members](../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
-   [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
DMV qui contiennent des informations sur l’état des demandes et les ressources dont elles ont besoin :  
  
-   [sys.dm_pdw_lock_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
-   [sys.dm_pdw_resource_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
Vues système associées exposées à partir des DMV de SQL Server sur les nœuds de calcul. Consultez [SQL Server vues de gestion dynamique](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) pour obtenir des liens vers ces DMV sur MSDN.  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   sys.dm_pdw_nodes_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   sys. dm_pdw_nodws_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_exec_sessions  
  
-   sys.dm_pdw_nodes_exec_requests  
  
-   sys.dm_pdw_nodes_exec_query_memory_grants  
  
-   sys.dm_pdw_nodes_exec_query_resource_semaphores  
  
-   sys.dm_pdw_nodes_os_memory_brokers  
  
-   sys.dm_pdw_nodes_os_memory_cache_entries  
  
-   sys.dm_pdw_nodes_exec_cached_plans  
  
## <a name="related-tasks"></a><a name="RelatedTasks"></a>Tâches associées  
[Tâches de gestion des charges de travail](workload-management-tasks.md)  
  
<!-- MISSING LINKS
See the Workload Management section of [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md) for the following tasks:  
  
1.  Find the number of active requests for each resource group.  
  
2.  Determine if my requests need more memory  
  
3.  Determine if there are a high number of query optimizations or suboptimal plan generations.  
  
4.  Determine Average CPU time per request in each resource pool to date  
  
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
