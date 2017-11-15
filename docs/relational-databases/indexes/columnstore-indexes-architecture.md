---
title: "Index columnstore - Architecture | Microsoft Docs"
ms.custom: 
ms.date: 01/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96b8e884-8244-425f-b856-72a8ff6895a6
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 86700a7247c7a712e03a5b34c6b68e9364d870b9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="columnstore-indexes---architecture"></a>Index columnstore - Architecture
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Découvrez l’architecture d’un index columnstore. La connaissances de ces informations de base permet de comprendre plus facilement d’autres articles relatifs aux columnstores qui expliquent comment les utiliser efficacement.

## <a name="data-storage-uses-columnstore-and-rowstore-compression"></a>Le stockage de données utilise la compression de columnstore et de rowstore
Dans les discussions au sujet des index columnstore, nous utilisons les termes *rowstore* et *columnstore* pour mettre en évidence le format du stockage de données.  Les index columnstore utilisent les deux types de stockage.

 ![Clustered Columnstore Index](../../relational-databases/indexes/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")

- Un **columnstore** représente des données qui sont organisées logiquement sous la forme d’une table avec des lignes et des colonnes, et stockées physiquement dans un format de données selon les colonnes.
  
Un index columnstore stocke physiquement la plupart des données au format columnstore. Au format columnstore, les données sont compressées et décompressées sous la forme de colonnes. Il n’est pas nécessaire de décompresser les autres valeurs de chaque ligne qui ne sont pas demandées par la requête. Cela permet d’analyser rapidement une colonne entière d’une table volumineuse. 

- Un **rowstore** représente des données qui sont organisées logiquement sous la forme d’une table avec des lignes et des colonnes, puis stockées physiquement dans un format de données selon les lignes. Il s’agit de la méthode traditionnelle de stockage des données de table relationnelles, comme un segment de mémoire ou un index « BTree » cluster.

Un index columnstore stocke également physiquement des lignes dans un format rowstore appelé « deltastore ». Le deltastore, également appelé « rowgroups delta », est un espace de stockage pour les lignes qui sont en trop petit nombre pour bénéficier de la compression dans le columnstore. Chaque rowgroup delta est implémenté comme un index BTree cluster. 

- Un **deltastore** est un espace de stockage pour les lignes qui sont en trop petit nombre pour être compressées dans le columnstore. Le deltastore est un rowstore. 
  
## <a name="operations-are-performed-on-rowgroups-and-column-segments"></a>Les opérations sont effectuées sur des rowgroups et des segments de colonne

L’index columnstore regroupe des lignes en unités gérables. Chacune de ces unités est appelée « rowgroup ». Pour des performances optimales, le nombre de lignes dans le rowgroup doit être suffisamment important pour améliorer le taux de compression et suffisamment petit pour tirer parti des opérations en mémoire.

* Un **rowgroup** est un groupe de lignes sur lequel l’index columnstore effectue des opérations de gestion et de compression. 

Par exemple, l’index columnstore effectue les opérations suivantes sur des rowgroups :

* Compresse les rowgroups dans le columnstore. La compression est effectuée sur chaque segment de colonne d’un rowgroup.
* Fusionne des rowgroups lors d’une opération ALTER INDEX REORGANIZE.
* Crée des rowgroups lors d’une opération ALTER INDEX REBUILD.
* Génère des rapports sur l’intégrité et la fragmentation des rowgroups dans des vues de gestion dynamique (DMV).

Le deltastore se compose d’un ou de plusieurs rowgroups appelés « rowgroups delta ». Chaque rowgroup delta est un index BTree cluster qui stocke des lignes quand elles sont en trop petit nombre pour être compressées dans le columnstore.  

* Un **rowgroup delta** est un index BTree cluster qui stocke de petits chargements en masse et insère des données jusqu’à ce que le rowgroup contienne 1 048 576 lignes ou jusqu’à ce que l’index soit reconstruit.  Quand un rowgroup delta contient 1 048 576 lignes, il est marqué comme étant fermé et attend qu’un processus appelle le moteur de tuple pour le compresser dans le columnstore. 


Chaque colonne a certaines de ses valeurs dans chaque rowgroup. Ces valeurs sont appelées « segments de colonne ». Quand l’index columnstore compresse un rowgroup, il compresse chaque segment de colonne séparément. Pour décompresser la totalité d’une colonne, l’index columnstore doit simplement décompresser un segment de colonne dans chaque rowgroup.

* Un **segment de colonne** est la partie des valeurs de colonne dans un rowgroup. Chaque rowgroup contient un segment de colonne pour chaque colonne dans la table. Chaque colonne a un segment de colonne dans chaque rowgroup. 
  
 ![Column segment](../../relational-databases/indexes/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
 
## <a name="small-loads-and-inserts-go-to-the-deltastore"></a>Les petits chargements et les petites insertions sont placés dans le deltastore
Un index columnstore améliore la compression columnstore et les performances en compressant au moins 102 400 lignes à la fois dans l’index columnstore. Pour compresser des lignes en masse, l’index columnstore accumule les petits chargements et les petites insertions dans le deltastore. Les opérations deltastore sont effectuées en coulisse. Pour retourner des résultats de requête corrects, l'index columnstore cluster associe les résultats de columnstore et de deltastore. 

Les lignes sont placées dans le deltastore quand elles sont :
* Insérées à l’aide de l’instruction INSERT INTO VALUES.
* À la fin d’un chargement en masse et que leur nombre est inférieur à 102 400.
* Mises à jour. Chaque mise à jour correspond à une suppression et une insertion.

Le deltastore stocke également une liste des ID des lignes supprimées qui ont été marquées comme supprimées mais qui n’ont pas encore été supprimées physiquement de l’index columnstore. 

## <a name="when-delta-rowgroups-are-full-they-get-compressed-into-the-columnstore"></a>Quand les rowgroups delta sont pleins, ils sont compressés dans le columnstore

Les index columnstore cluster collectent jusqu’à 1 048 576 lignes dans chaque rowgroup delta avant de compresser le rowgroup dans le columnstore. Cela améliore la compression de l’index columnstore. Quand un rowgroup delta contient 1 048 576 lignes, l’index columnstore marque le rowgroup comme étant fermé. Un processus en arrière-plan, appelé *moteur de tuple*, recherche chaque rowgroup fermé et le compresse dans le columnstore. 

Vous pouvez placer de force des rowgroups delta dans le columnstore à l’aide de l’instruction [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) pour reconstruire ou réorganiser l’index.  Notez que s’il existe une sollicitation de la mémoire lors de la compression, l’index columnstore peut réduire le nombre de lignes stockées dans le rowgroup compressé.

## <a name="each-table-partition-has-its-own-rowgroups-and-delta-rowgroups"></a>Chaque partition de table a ses propres rowgroups et rowgroups delta

Le concept de partitionnement est identique dans un index cluster, un segment de mémoire et un index columnstore. Le partitionnement d’une table divise la table en groupes de lignes plus petits en fonction d’une plage de valeurs de colonne. Il est souvent utilisé pour la gestion des données. Par exemple, vous créez une partition pour chaque année de données, puis vous utilisez le basculement de partition pour archiver des données dans un stockage moins coûteux. Le basculement de partition fonctionne sur les index columnstore et facilite le déplacement d’une partition de données vers un autre emplacement.

Les rowgroups sont toujours définis dans une partition de table. Quand un index columnstore est partitionné, chaque partition possède ses propres rowgroups et rowgroups delta compressés.

### <a name="each-partition-can-have-multiple-delta-rowgroups"></a>Chaque partition peut posséder plusieurs rowgroups delta
Chaque partition peut posséder plusieurs rowgroups delta. Quand l’index columnstore doit ajouter des données à un rowgroup delta et que ce dernier est verrouillé, l’index columnstore tente d’obtenir un verrou sur un autre rowgroup delta. Si aucun rowgroup delta n’est disponible, l’index columnstore en crée un.  Par exemple, une table comportant 10 partitions peut facilement avoir au moins 20 rowgroups delta. 

  
## <a name="you-can-combine-columnstore-and-rowstore-indexes-on-the-same-table"></a>Vous pouvez combiner des index columnstore et rowstore sur la même table
Un index non cluster contient une copie de tout ou partie des lignes et colonnes de la table sous-jacente. L’index est défini comme une ou plusieurs colonnes de la table et a une condition facultative qui filtre les lignes. 

Depuis [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], vous pouvez créer un index non cluster columnstore pouvant être mis à jour sur une table rowstore. L’index columnstore stocke une copie des données, afin que vous n’ayez pas besoin de stockage supplémentaire. Toutefois, les données de l’index columnstore sont compressées à une taille plus petite que ce que nécessite la table rowstore.  Ce faisant, vous pouvez exécuter l’analytique sur l’index columnstore et les transactions sur l’index rowstore en même temps. La banque des colonnes (columnstore) est mise à jour lors de la modification des données de la table rowstore. Les deux index utilisent donc les mêmes données.  
  
 Depuis [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], vous pouvez avoir un ou plusieurs index non cluster rowstore sur un index columnstore. Ce faisant, vous pouvez effectuer des recherches de tables efficaces sur le columnstore sous-jacent. D’autres options sont également disponibles. Par exemple, vous pouvez appliquer une contrainte de clé primaire à l’aide d’une contrainte UNIQUE sur la table rowstore. Dans la mesure où une valeur non unique ne peut pas être insérée dans la table rowstore, SQL Server ne peut pas insérer la valeur dans le columnstore.  
 

## <a name="metadata"></a>Métadonnées  
Utilisez ces vues de métadonnées pour voir les attributs des index columnstore. Des informations supplémentaires sur l’architecture sont incorporées dans certaines de ces vues.

Notez que toutes les colonnes d’un index columnstore sont stockées dans les métadonnées comme colonnes incluses. L'index columnstore n'a pas de colonnes clés.  
  
-   [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
-   [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
-   [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)  
  
-   [sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)  
  
-   [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)  
  
-   [sys.dm_column_store_object_pool &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
|  


## <a name="next-steps"></a>Étapes suivantes
 Pour obtenir des conseils sur la conception de vos index columnstore, consultez [Index columnstore - Conseils en matière de conception](../../relational-databases/indexes/columnstore-indexes-design-guidance.md).
