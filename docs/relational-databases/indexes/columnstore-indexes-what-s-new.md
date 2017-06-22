---
title: "Index columnStore - Nouveautés | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fe5ea05-5b19-45a4-9b7a-8ae5ca367897
caps.latest.revision: 28
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8dc55e28462cd04a90274ada860fd418bcc54775
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="columnstore-indexes---what39s-new"></a>Index columnstore - Nouveautés
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Synthèse des fonctionnalités columnstore disponibles pour chaque version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et les dernières versions d’Azure SQL Database Édition Premium, Azure SQL Data Warehouse et Parallel Data Warehouse.  

 >[!NOTE]
 > Pour Azure SQL Database, les index columnstore sont uniquement disponibles dans l’Édition Premium.
 
## <a name="feature-summary-for-product-releases"></a>Synthèse des fonctionnalités pour les versions du produit  
 Ce tableau récapitule les principales fonctionnalités des index columnstore et des produits dans lesquels ils sont disponibles.  

  
|Fonctionnalité d’index columnstore|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Édition Premium|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]|  
|-------------------------------|---------------------------|---------------------------|---------------------------|--------------------------------------------|-------------------------|  
|Exécution par lot de requêtes multithread|oui|oui|oui|oui|oui|  
|Exécution par lot de requêtes monothread|||oui|oui|oui|  
|Option de compression de l’archivage||oui|oui|oui|oui|  
|Isolement de capture instantanée et isolement de capture instantanée Read Committed|||oui|oui|oui|  
|Spécifier l’index columnstore lors de la création d’une table|||oui|oui|oui|  
|AlwaysOn prend en charge les index columnstore|oui|oui|oui|oui|oui|  
|Le secondaire accessible en lecture AlwaysOn prend en charge les index columnstore non cluster en lecture seule|oui|oui|oui|oui|oui|  
|Le secondaire accessible en lecture AlwaysOn prend en charge les index columnstore actualisables|||oui|||  
|Index columnstore non cluster en lecture seule sur segment de mémoire ou btree|oui|oui|oui*|oui*|oui*|  
|Index columnstore non cluster actualisable sur segment de mémoire ou btree|||oui|oui|oui|  
|Index btree supplémentaires autorisés sur un segment de mémoire ou btree ayant un index columnstore non cluster|oui|oui|oui|oui|oui|  
|Index columnstore cluster actualisable||oui|oui|oui|oui|  
|Index Btree sur un index columnstore cluster|||oui|oui|oui|  
|Index columnstore sur une table optimisée en mémoire|||oui|oui|oui|  
|Définition d’index columnstore non cluster prenant en charge l’utilisation d’une condition filtrée|||oui|oui|oui|  
|Option de temporisation de la compression pour les index columnstore dans CREATE TABLE et ALTER TABLE|||oui|oui|oui|   
  
 *Pour créer un index columnstore non cluster lisible, stockez l’index sur un groupe de fichiers en lecture seule.  
  
## [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ajoute des améliorations clés pour optimiser les performances et la flexibilité des index columnstore. Cela améliore les scénarios d’entreposage de données et permet l’analytique opérationnelle en temps réel.  
  
### <a name="functional"></a>Fonctionnel  
  
-   Une table rowstore peut avoir un index columnstore non cluster actualisable. Auparavant, l’index columnstore non cluster était en lecture seule.  
  
-   La définition d’index columnstore non cluster prend en charge l’utilisation d’une condition filtrée. Cette fonctionnalité permet de créer un index columnstore non cluster uniquement sur les données brutes d’une charge de travail opérationnelle. Ainsi, l’impact sur les performances d’un index columnstore sur une table OLTP sera minime.  
  
-   Une table en mémoire peut avoir un index columnstore. Vous pouvez le créer lors de la création de la table ou l’ajouter ultérieurement avec [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md). Auparavant, une table sur disque pouvait avoir un index columnstore.  
  
-   Un index columnstore cluster peut avoir un ou plusieurs index rowstore non cluster. Auparavant, l’index columnstore ne prenait pas en charge les index non cluster. SQL Server gère automatiquement les index non cluster pour les opérations DML.  
  
-   Prise en charge des clés primaires et étrangères à l’aide d’un index btree pour appliquer ces contraintes sur un index columnstore cluster.  
  
-   Les index columnstore ont une option de délai de compression qui réduit l’impact que la charge de travail transactionnelle peut avoir sur l’analytique opérationnelle en temps réel.  Cette option permet de modifier fréquemment les lignes pour les stabiliser avant leur compression dans le columnstore. Pour plus d’informations, consultez [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md) et [Prise en main de columnstore pour l’analytique opérationnelle en temps réel](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md).  
  
### <a name="performance-for-database-compatibility-level-120-or-130"></a>Performances pour les niveaux de compatibilité de base de données 120 ou 130  
  
-   Les index columnstore prennent en charge l’isolement de capture instantanée Read Committed (RCSI) et l’isolement de capture instantanée (SI). Cela permet d’effectuer des requêtes analytiques cohérentes d’un point de vue transactionnel sans verrou.  
  
-   L’index columnstore prend en charge la défragmentation de l’index en éliminant les lignes supprimées sans nécessité de reconstruire explicitement l’index. L’instruction ALTER INDEX... REORGANIZE élimine de l’index columnstore les lignes supprimées, selon une stratégie définie en interne, en tant qu’opération en ligne.  
  
-   Les index columnstore sont accessibles sur un réplica secondaire lisible AlwaysOn. Vous pouvez améliorer les performances d’analytique opérationnelle en déchargeant les requêtes analytiques sur un réplica secondaire AlwaysOn.  
  
-   Pour améliorer les performances, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] calcule les fonctions d’agrégation MIN, MAX, SUM, COUNT, AVG pendant les analyses de table quand le type de données n’utilise pas plus de huit octets, et n’est pas de type chaîne. La pile d’agrégats est prise en charge avec ou sans la clause Group By pour les index columnstore cluster et non cluster.  
  
-   La pile de prédicats accélère les requêtes qui comparent des chaînes de type [v]char ou n[v]char. Cela s’applique aux opérateurs de comparaison courants, et inclut des opérateurs tels que LIKE, qui utilisent des filtres bitmap. Cela fonctionne avec tous les classements que SQL Server prend en charge.  
  
### <a name="performance-for-database-compatibility-level-130"></a>Performances pour le niveau de compatibilité de base de données 130  
  
-   Nouvelle prise en charge de l’exécution en mode batch pour les requêtes utilisant l’une des opérations suivantes :  
  
    -   SORT  
  
    -   Agrégats avec plusieurs fonctions distinctes. Exemples : COUNT/COUNT, AVG/SUM, CHECKSUM_AGG, STDEV/STDEVP.  
  
    -   Fonctions d’agrégation Window : COUNT, COUNT_BIG, SUM, AVG, MIN, MAX et CLR.  
  
    -   Agrégats définis par l’utilisateur Windows : CHECKSUM_AGG, STDEV, STDEVP, VAR, VARP et GROUPING.  
  
    -   Fonctions analytiques d’agrégation Windows :  LAG< LEAD, FIRST_VALUE, LAST_VALUE, PERCENTILE_CONT, PERCENTILE_DISC, CUME_DIST et PERCENT_RANK.  
  
-   Les requêtes monothread s’exécutant sous MAXDOP 1 ou avec un plan de requête série s’exécutent en mode batch. Auparavant, seules les requêtes multithread s’exécutaient en mode batch.  
  
-   Les requêtes de table optimisée en mémoire peuvent avoir des plans parallèles en mode SQL InterOp lors de l’accès aux données dans rowstore ou dans les index columnstore.  
  
### <a name="supportability"></a>Prise en charge  
 Ces vues système sont nouvelles pour columnstore :  
  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  
  
-   [sys.dm_column_store_object_pool &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)  
  
-   [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
-   [sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)  
  
 Ces DMV basées sur OLTP en mémoire contiennent des mises à jour pour columnstore :  
  
-   [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-memory-consumers-transact-sql.md)  
  
-   [sys.dm_db_xtp_nonclustered_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-nonclustered-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_object_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-object-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql.md)  
  
### <a name="limitations"></a>Limitations  
  
-   La fonction MERGE est désactivée quand un index btree est défini sur un index columnstore cluster.  
  
-   Pour les tables en mémoire, un index columnstore doit inclure toutes les colonnes. L’index columnstore ne peut pas avoir de condition filtrée.  
  
-   Pour les tables en mémoire, les requêtes sur les index columnstore s’exécutent uniquement en mode InterOP et non en mode natif en mémoire. L’exécution en parallèle est prise en charge.  
  
## <a name="sql-server-2014"></a>SQL Server 2014  
 SQL Server 2014 a introduit l’index columnstore cluster en tant que format de stockage principal. Cela autorise des charges régulières ainsi que des opérations de mise à jour, de suppression et d’insertion.  
  
-   La table peut utiliser un index columnstore cluster en tant que stockage de table primaire. Aucun autre index n’est autorisé sur la table mais, l’index columnstore cluster étant actualisable, vous pouvez effectuer des chargements réguliers et apporter des modifications à des lignes individuelles.  
  
-   L’index columnstore non cluster conserve les mêmes fonctionnalités que dans SQL Server 2012, à l’exception des opérateurs supplémentaires qui peuvent désormais être exécutés en mode batch. Il n’est toujours pas actualisable, sauf par reconstruction et par basculement de partition. L’index columnstore non cluster est pris en charge uniquement sur les tables sur disque, pas sur les tables en mémoire.  
  
-   Les index columnstore cluster et non cluster disposent d’une option de compression d’archivage qui compresse davantage les données. L’option d’archivage est utile pour réduire la taille des données en mémoire et sur disque, mais elle ralentit les performances des requêtes. Elle fonctionne bien pour les données rarement utilisées.  
  
-   Les index columnstore cluster et non cluster fonctionnent d’une manière très similaire. Ils utilisent le même format de stockage en colonnes, le même moteur de traitement des requêtes et le même jeu de vues de gestion dynamique. La différence a trait aux types d’index (primaire et secondaire), et au fait que l’index columnstore non cluster est en lecture seule.  
  
-   Les opérateurs suivants s’exécutent en mode batch pour les requêtes multithread : scan, filter, project, join, group by et union all.  
  
## <a name="sql-server-2012"></a>SQL Server 2012  
 SQL Server 2012 a introduit l’index columnstore non cluster en tant qu’autre type d’index sur les tables rowstore, et le traitement par lots pour les requêtes sur des données columnstore.  
  
-   Une table rowstore peut avoir un index columnstore non cluster.  
  
-   L’index columnstore est en lecture seule. Après avoir créé l’index columnstore, vous ne pouvez pas mettre à jour la table à l’aide d’opérations d’insertion, de suppression et de mise à jour. Pour effectuer ces opérations, vous devez supprimer l’index, mettre à jour la table, puis reconstruire l’index. Vous pouvez charger des données supplémentaires dans la table à l’aide d’un basculement de partition. L’avantage du basculement de partition est que vous pouvez charger des données sans devoir supprimer et reconstruire l’index columnstore.  
  
-   L’index columnstore requiert toujours un stockage supplémentaire, généralement supérieur de 10 % à celui du rowstore, car il stocke une copie des données.  
  
-   Le traitement par lots offre des performances de requête au moins deux fois supérieures, mais il n’est disponible que pour l’exécution de requêtes parallèles.  
  
## <a name="see-also"></a>Voir aussi  
 Guide des index columnstore   
 Chargement de données d’index columnstore   
 [Performances des requêtes d’index columnstore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [Prise en main de columnstore pour l’analytique opérationnelle en temps réel](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 Index columnstore pour l’entreposage des données   
 [Défragmentation des index columnstore](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  

