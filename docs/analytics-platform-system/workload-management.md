---
title: Gestion de la charge de travail d’Analytique Platform System | Microsoft Docs
description: Gestion de la charge de travail d’Analytique Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2281262c086f4d8dcab27debc8bb735ea5e8e1ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63157474"
---
# <a name="workload-management-in-analytics-platform-system"></a>Gestion de la charge de travail d’Analytique Platform System

Fonctionnalités de gestion de la charge de travail de PDW de SQL Server permettent aux utilisateurs et administrateurs d’attribuer des demandes au préalable définir des configurations de mémoire et d’accès concurrentiel. Utiliser la gestion de la charge de travail pour améliorer les performances de votre charge de travail cohérent ou mixte, en permettant aux demandes pour que les ressources appropriées sans priver de toutes les demandes indéfiniment.  
  
Par exemple, avec les techniques de gestion de la charge de travail dans SQL Server PDW, vous pouvez :  
  
-   Allouer un grand nombre de ressources pour un travail de chargement.  
  
-   Spécifier plus de ressources pour la création d’un index columnstore.  
  
-   Résoudre les problèmes d’une jointure de hachage lentes pour voir si elle a besoin de davantage de mémoire et lui donner plus de mémoire.  
  
## <a name="Basics"></a>Principes fondamentaux de gestion de la charge de travail  
  
### <a name="key-terms"></a>Termes clés  
Gestion de la charge de travail  
*Gestion de la charge de travail* est la capacité à comprendre et ajuster l’utilisation des ressources système pour obtenir de meilleures performances pour les demandes simultanées.  
  
Classe de ressources  
Dans SQL Server PDW, un *classe de ressource* est un rôle de serveur intégré qui a préalablement assigné des limites de mémoire et de concurrence. SQL Server PDW alloue des ressources aux requêtes en fonction de l’appartenance de rôle de ressource classe serveur de la connexion qui soumet les requêtes.  
  
Sur les nœuds de calcul, l’implémentation de classes de ressources utilise la fonctionnalité gouverneur de ressources dans SQL Server. Pour plus d’informations sur le gouverneur de ressources, consultez [du gouverneur de ressources](../relational-databases/resource-governor/resource-governor.md) sur MSDN.  
  
### <a name="understand-current-resource-utilization"></a>Comprendre l’utilisation actuelle des ressources  
Pour comprendre l’utilisation des ressources système pour les demandes en cours d’exécution, utilisez les vues de gestion dynamique SQL Server PDW. Par exemple, vous pouvez utiliser des vues de gestion dynamique pour comprendre si une jointure de hachage volumineux à exécution lente peut tirer parti en ayant plus de mémoire.  
  
<!-- MISSING LINKS
For examples, see [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md).  
-->
  
### <a name="adjust-resource-allocations"></a>Ajuster les Allocations de ressources  
Pour ajuster l’utilisation des ressources, modifier l’appartenance de classe de ressource de la connexion qui soumet la demande. Les rôles de serveur de classe de ressource sont nommées **mediumrc**, **largerc**, et **xlargerc**. Ils représentent respectivement des allocations de ressources moyenne, grande et très grande taille.  
  
Par exemple, pour allouer une grande quantité de ressources système à une requête, ajouter la connexion qui soumet la demande à la **largerc** rôle de serveur. L’instruction ALTER SERVER ROLE suivante ajoute la connexion Anna au rôle de serveur largerc.  
  
```sql  
ALTER SERVER ROLE largerc ADD MEMBER Anna;  
```  
  
## <a name="RC"></a>Descriptions des ressources de classe  
Le tableau suivant décrit les classes de ressources et leurs allocations de ressources système.  
  
|Classe de ressources|Importance de la demande|L’utilisation de mémoire maximale *|Emplacements de concurrence (maximale = 32)|Description|  
|------------------|----------------------|--------------------------|---------------------------------------|---------------|  
|par défaut|Moyenne|400 MO|1|Par défaut, chaque connexion est autorisée une petite quantité de mémoire et des ressources d’accès concurrentiel pour ses demandes.<br /><br />Lorsqu’une connexion est ajoutée à une classe de ressource, la nouvelle classe est prioritaire. Lorsqu’une connexion est supprimée à partir de toutes les classes de ressources, la connexion revient à l’allocation de ressources par défaut.|  
|MediumRC|Moyenne|1 200 MO|3|Exemples de requêtes nécessitant la classe de ressources de taille moyenne :<br /><br />Opérations de CTAS importante des jointures de hachage.<br /><br />Sélectionnez les opérations qui nécessitent davantage de mémoire pour éviter la mise en cache sur le disque.<br /><br />Chargement des données dans les index columnstore en cluster.<br /><br />Création, reconstruction et la réorganisation d’index cluster columnstore pour les tables plus petites qui possèdent des colonnes de 10 à 15.|  
|Largerc|Élevée|2,8 GO|7|Exemples de requêtes nécessitant la classe de ressources de grande taille :<br /><br />Opérations de CTAS très volumineuses qui ont des jointures de hachage énorme, ou contient les agrégations importantes, telles que les clauses ORDER BY ou GROUP BY volumineux.<br /><br />Sélectionnez les opérations nécessitant de très grandes quantités de mémoire pour des opérations telles que les jointures de hachage, ou des agrégations telles que les clauses ORDER BY ou GROUP BY<br /><br />Chargement des données dans les index columnstore en cluster.<br /><br />Création, reconstruction et la réorganisation d’index cluster columnstore pour les tables plus petites qui possèdent des colonnes de 10 à 15.|  
|xlargerc|Élevée|8.4 GO|22|La classe de ressources de très grande taille est pour les demandes qui peuvent nécessiter la consommation des ressources de très grande taille au moment de l’exécution.|  
  
<sup>*</sup>Utilisation de la mémoire maximale est une approximation.  
  
### <a name="request-importance"></a>Importance de la demande  
L’importance de la demande est mappé à la quantité de temps processeur par SQL Server, s’exécutant sur les nœuds de calcul, donnera aux requêtes.  Demandes avec une priorité plus élevée reçoivent plus de temps processeur.  
  
### <a name="maximum-memory-usage"></a>Utilisation de la mémoire maximale  
Utilisation de la mémoire maximale est la quantité maximale de mémoire disponible, qu'une demande peut utiliser au sein de chaque espace de traitement. Par exemple une demande mediumrc peut utiliser jusqu'à 1 200 Mo pour le traitement au sein de chaque distribution. Il est toujours important de s’assurer de données ne sont pas asymétriques afin d’éviter d’avoir quelques distributions effectuant l’essentiel du travail.  
  
### <a name="concurrency-slots"></a>Emplacements de concurrence  
L’objectif d’allouer 1, 3, 7 et les emplacements de concurrence 22 consiste à autoriser petits et grands processus à exécuter en même temps, sans bloquer le processus petit lors de l’exécution d’un processus de grande taille.  Par exemple, SQL Server PDW peut allouer au maximum 32 emplacements de concurrence pour exécuter 1 demande de très grande taille (emplacements de 22), 1 demande de grande taille (7 connecteurs) et 1 demande de taille moyenne (3 emplacements) en même temps.  
  
Exemples d’allouer jusqu'à 32 emplacements de concurrence pour les demandes simultanées :  
  
-   emplacements de 28 = 4 volumineux  
  
-   emplacements de 30 = moyenne 10  
  
-   32 slots = 32 default  
  
-   les 32 emplacements = 1 extra-large + 1 moyen volumineux + 1  
  
-   les 32 emplacements = 2 moyen volumineux + 4 + 6 par défaut  
  
Supposons que 6 demandes volumineuses sont soumises à SQL Server PDW, puis 10 requêtes par défaut sont envoyées. SQL Server PDW traitera les demandes par ordre de priorité comme suit :  
  
-   Allouer des emplacements de concurrence 28 pour commencer le traitement des demandes volumineuses 4 comme mémoire devient disponible et conserver les 2 demandes volumineuses dans la file d’attente.  
  
-   Allouer 4 emplacements de concurrence pour commencer le traitement des requêtes par défaut 4 et conservez les 6 demandes par défaut dans la file d’attente.  
  
Que terminer des demandes et emplacements de concurrence sont disponibles, SQL Server PDW alloue les requêtes restantes en fonction des ressources disponibles et priorité. Par exemple, lorsqu’il y a 7 concurrence ouvrir des emplacements, en attente de demandes volumineuses aura une priorité plus élevée pour les 7 emplacements que d’attendre que les demandes de support.  Si les emplacements de 6 s’ouvre, SQL Server PDW allouera 6 demandes plus dimensionné par défaut. Toutefois, les emplacements de mémoire et d’accès concurrentiel doivent toutes être disponibles avant que SQL Server PDW autorise une demande d’exécution.  
  
Dans chaque classe de ressources, les requêtes s’exécutent en premier dans l’ordre, premier sorti (FIFO).  
  
## <a name="GeneralRemarks"></a>Remarques d’ordre général  
Si une connexion est membre de plusieurs classes de ressources, la classe avec le plus de ressources est prioritaire.  
  
Lorsqu’une connexion est ajoutée à ou supprimée à partir d’une classe de ressource, la modification prend effet immédiatement pour toutes les demandes futures ; demandes en cours qui sont en cours d’exécution ou en attente ne sont pas affectés. La connexion n’a pas besoin pour vous déconnecter et vous reconnecter afin que la modification ne survienne.  
  
Pour chaque connexion, les paramètres de classe de ressource sont appliqués aux opérations et les instructions individuelles et non à la session.  
  
Avant que SQL Server PDW exécute une instruction, il tente d’acquérir les emplacements de concurrence nécessaires à la demande. Si elle ne peut pas acquérir suffisamment d’emplacements de concurrence, SQL Server PDW déplace la demande dans un état d’attente pour exécution. Tous les systèmes de ressources qui ont été allouées à la demande sont retournées au système.  
  
La plupart des instructions SQL doivent toujours les allocations de ressources par défaut et par conséquent n’est pas contrôlée par les classes de ressources. Par exemple, CREATE LOGIN uniquement a besoin d’une petite quantité de ressources et est alloué les ressources par défaut même si la connexion de l’appel de CREATE LOGIN est un membre d’une classe de ressource.  Par exemple, si Anna est un membre de la classe de ressources largerc et elle envoie une instruction CREATE LOGIN, l’instruction CREATE LOGIN s’exécuter avec le nombre de ressources par défaut.  
  
Instructions SQL et opérations régies par des classes de ressources :  
  
-   ALTER INDEX REBUILD  
  
-   ALTER INDEX REORGANIZE  
  
-   ALTER TABLE REBUILD  
  
-   CRÉER DES INDEX CLUSTER  
  
-   CREATE CLUSTERED COLUMNSTORE INDEX  
  
-   CREATE TABLE AS SELECT  
  
-   CREATE REMOTE TABLE AS SELECT  
  
-   Chargement des données avec **dwloader**.  
  
-   INSERT-SELECT  
  
-   UPDATE  
  
-   Suppression  
  
-   RESTORE DATABASE lors de la restauration à un dispositif avec davantage de nœuds de calcul.  
  
-   Sélectionnez, à l’exclusion des requêtes DMV uniquement  
  
## <a name="Limits"></a>Limitations et restrictions  
Les classes de ressources régissent les allocations de mémoire et de concurrence.  Elles ne déterminent pas les opérations d’entrée/sortie.  
  
## <a name="Metadata"></a>Metadata  
Vues de gestion dynamique qui contiennent des informations sur les classes de ressources et les membres de classe de ressource.  
  
-   [sys.server_role_members](../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
-   [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
Vues de gestion dynamique qui contiennent des informations sur l’état des demandes et les ressources que dont ils ont besoin :  
  
-   [sys.dm_pdw_lock_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
-   [sys.dm_pdw_resource_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
Vues système associé exposées par les vues de gestion dynamique SQL Server sur les nœuds de calcul. Consultez [vues de gestion dynamique SQL Server](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) pour des liens vers ces DMV sur MSDN.  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   sys.dm_pdw_nodes_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   sys.dm_pdw_nodws_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_exec_sessions  
  
-   sys.dm_pdw_nodes_exec_requests  
  
-   sys.dm_pdw_nodes_exec_query_memory_grants  
  
-   sys.dm_pdw_nodes_exec_query_resource_semaphores  
  
-   sys.dm_pdw_nodes_os_memory_brokers  
  
-   sys.dm_pdw_nodes_os_memory_cache_entries  
  
-   sys.dm_pdw_nodes_exec_cached_plans  
  
## <a name="RelatedTasks"></a>Tâches associées  
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
  
