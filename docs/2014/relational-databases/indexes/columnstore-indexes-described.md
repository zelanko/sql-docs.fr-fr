---
title: Description des index ColumnStore | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
author: mikeraymsft
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 58bf23c84914d7df4b9f2637cc7682de2021bf08
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63155504"
---
# <a name="columnstore-indexes-described"></a>Columnstore Indexes Described
  Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *les index columnstore en mémoire* stocke et gère les données à l’aide de stockage de données en colonnes et de traitement de requête fondée sur une colonne. Les index columnstore fonctionnent bien pour les charges de travail de stockage de données qui effectuent principalement des chargements en masse et des requêtes en lecture seule. Utilisez l'index columnstore pour atteindre des gains de **performances des requêtes** pouvant être multipliés par 10 par rapport au stockage orienté lignes traditionnel, et une **compression de données** multipliée par 7 par rapport à la taille des données non compressées.  
  
> [!NOTE]  
>  Nous considérons l'index columnstore cluster comme étant la norme pour le stockage de grandes tables de faits de stockage des données, et nous pensons qu'il va être utilisé dans la plupart des scénarios de stockage des données. Étant donné que l'index columnstore cluster est modifiable, votre charge de travail peut exécuter un grand nombre d'insertions, mises à jour, et suppressions.  
  
## <a name="contents"></a>Sommaire  
  
-   [Principes de base](#basics)  
  
-   [Chargement de données](#dataload)  
  
-   [Conseils sur les performances](#performance)  
  
-   [Tâches et rubriques connexes](#related)  
  
##  <a name="basics"></a> Principes de base  
 Un *columnstore index* est une technologie permettant de stocker, extraire et gérer les données à l'aide d'un format de données en colonnes, appelé columnstore. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge les index columnstore cluster et non cluster. Les deux utilisent la même technologie columnstore en mémoire, mais sont différents en ce qui concerne leur but et les fonctionnalités qu'ils prennent en charge.  
  
###  <a name="benefits"></a> Avantages  
 Les index columnstore fonctionnent bien pour la plupart des requêtes en lecture seule qui effectuent des analyses sur des ensembles de données volumineux. Bien souvent, il s'agit de requêtes destinées à des charges de travail de stockage de données. Les index columnstore offrent des gains de performances importants pour les requêtes qui utilisent des analyses de table complètes, et ne conviennent pas pour les requêtes qui effectuent des opérations de recherche de données, notamment qui recherchent une valeur particulière.  
  
 Avantages de l'index columnstore :  
  
-   Les colonnes contenant souvent des données similaires, les taux de compression sont élevés.  
  
-   Les taux de compression élevés améliorent les performances des requêtes en utilisant un plus faible encombrement en mémoire. En conséquence, les performances des requêtes sont améliorées, car [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut exécuter davantage d'opérations de requêtes et sur les données en mémoire.  
  
-   Un nouveau mécanisme d'exécution de requête, appelé « exécution en mode batch » a été ajouté à SQL Server pour réduire considérablement l'utilisation de l'UC. L'exécution en mode batch est étroitement intégrée avec (et optimisée pour) le format de stockage columnstore. L'exécution en mode batch est parfois appelée « exécution vectorielle ou vectorisée ».  
  
-   Les requêtes sélectionnent souvent seulement quelques colonnes d'une table, ce qui réduit les E/S totales à partir du support physique.  
  
### <a name="columnstore-versions"></a>Versions de columnstore  
 SQL Server 2012, SQL Server 2012 Parallel Data Warehouse, et SQL Server 2014 utilisent tous des index columnstore pour accélérer les requêtes d'entrepôts de données communs. SQL Server 2012 introduit deux nouvelles fonctionnalités : un index columnstore non cluster et une fonction d'exécution de requête vectorielle qui traite les données dans des unités appelées « lots ». SQL Server 2014 contient les fonctionnalités de SQL Server 2012 plus des index columnstore cluster pouvant être mis à jour.  
  
### <a name="key-characteristics"></a>Caractéristiques clés  
  
||  
|-|  
|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].|  
  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un index columnstore :  
  
-   Est disponible dans les éditions Enterprise, Developer et Evaluation.  
  
-   Peut être mis à jour.  
  
-   Est la méthode de stockage principale de la table entière.  
  
-   N'a pas de colonnes clés. Toutes les colonnes sont des colonnes incluses.  
  
-   Est le seul index sur la table. Ne peut pas être associé à d'autres index.  
  
-   Peut être configuré pour utiliser columnstore ou la compression d'archivage columnstore.  
  
-   Ne stocke pas physiquement les colonnes dans un ordre de tri. Au lieu de cela, il stocke les données pour améliorer la compression et les performances.  
  
||  
|-|  
|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].|  
  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un index non cluster :  
  
-   Peut indexer un sous-ensemble de colonnes dans l'index cluster ou le segment de mémoire. Par exemple, il peut indexer les colonnes utilisées fréquemment.  
  
-   Nécessite un stockage supplémentaire pour stocker une copie des colonnes dans l'index.  
  
-   Est mis à jour par la reconstruction de l'index ou le basculement de partitions. Il ne peut pas être mis à jour en utilisant des opérations DML telles que l'insertion, la mise à jour et la suppression.  
  
-   Peut être associé à d'autres index sur la table.  
  
-   Peut être configuré pour utiliser columnstore ou la compression d'archivage columnstore.  
  
-   Ne stocke pas physiquement les colonnes dans un ordre de tri. Au lieu de cela, il stocke les données pour améliorer la compression et les performances. Le prétri des données avant de créer l'index columnstore n'est pas requis, mais cela peut améliorer la compression columnstore.  
  
###  <a name="Concepts"></a> Termes et Concepts clés  
 Les termes et concepts clés suivants sont associés aux index columnstore.  
  
 columnstore index  
 Un *columnstore index* est une technologie permettant de stocker, extraire et gérer les données à l'aide d'un format de données en colonnes, appelé columnstore. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge les index columnstore cluster et non cluster. Les deux utilisent la même technologie columnstore en mémoire, mais sont différents en ce qui concerne leur but et les fonctionnalités qu'ils prennent en charge.  
  
 columnstore  
 Un *columnstore* représente des données qui sont organisées logiquement sous la forme d’une table avec des lignes et des colonnes, et stockées physiquement dans un format de données selon les colonnes.  
  
 rowstore  
 Un *rowstore* représente des données qui sont organisées logiquement sous la forme d’une table avec des lignes et des colonnes, puis stockées physiquement dans un format de données selon les lignes. Il s'agit de la méthode traditionnelle de stockage des données de table relationnelles.  
  
 rowgroups et segments de colonne  
 Pour une haute performance et des taux de compression élevés, l'index columnstore découpe la table en groupes de lignes, appelés rowgroups, puis comprime chaque groupe de lignes selon les colonnes. Le nombre de lignes dans le groupe de lignes doit être assez grand pour améliorer le taux de compression, et assez petit tirer parti des opérations en mémoire.  
  
 groupe de lignes  
 Un *rowgroup* est un groupe de lignes qui sont compressées au format columnstore en même temps.  
  
 segment de colonne  
 Un *segment de colonne* est une colonne de données au sein d'un rowgroup.  
  
-   Un rowgroup contient généralement le nombre maximal de lignes par rowgroup qui est de 1 048 576 lignes.  
  
-   Chaque rowgroup contient un segment de colonne pour chaque colonne dans la table.  
  
-   Chaque segment de colonne est compressé et stocké sur un support physique.  
  
 ![Column segment](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
  
 index columnstore non cluster  
 Un *nonclustered columnstore index* est un index en lecture seule créé sur un index cluster existant ou une table de segments de mémoire. Il contient une copie d'un sous-ensemble de colonnes, et peut contenir toutes les colonnes de la table. La table est en lecture seule alors qu'elle contient un index columnstore non cluster.  
  
 Un index columnstore non cluster permet d'avoir un index columnstore pour exécuter les requêtes d'analyse tout en exécutant des opérations en lecture seule sur la table d'origine.  
  
 ![Index non cluster columnstore](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "index non cluster columnstore")  
  
 index columnstore cluster  
 Un *clustered columnstore index* est le stockage physique de la totalité de la table, et est le seul index de la table. L'index cluster peut être mis à jour. Effectuez des opérations d'insertion, suppression, et mise à jour sur l'index et chargez en masse des données dans l'index.  
  
 ![Clustered Columnstore Index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")  
  
 Pour réduire la fragmentation des segments de colonne et améliorer les performances, l'index columnstore peut stocker des données temporaires dans une table rowstore, appelée un deltastore, plus un arbre B d'ID pour les lignes supprimées. Les opérations deltastore sont effectuées en coulisse. Pour retourner des résultats de requête corrects, l'index columnstore cluster associe les résultats de columnstore et de deltastore.  
  
 deltastore  
 Utilisé seulement avec des index columnstore cluster, un *deltastore* est une table rowstore contenant des lignes jusqu'à ce que le nombre de lignes soit suffisamment important pour être inséré dans le columnstore. Un deltastore est utilisé avec des index columnstore cluster pour améliorer les performances du chargement et d'autres opérations DML.  
  
 Lors d'un chargement en masse important, la plupart des lignes sont directement placées dans le columnstore sans passer par le deltastore. Certaines lignes à la fin du chargement en masse peuvent être en trop petit nombre pour atteindre la taille minimale d'un rowgroup, qui est de 102 400 lignes. Dans ce cas, les lignes finales sont placées dans le deltastore plutôt que dans le columnstore. Pour les petits chargements en masse de taille inférieure à 102 400 lignes, toutes les lignes vont directement au deltastore.  
  
 Lorsque le deltastore atteint le nombre maximal de lignes, il est fermé. Un processus de déplacement de tuple vérifie les groupes de lignes fermés. Lorsqu'il trouve un rowgroup fermé, il le compresse et le stocke dans le columnstore.  
  
##  <a name="dataload"></a> Chargement des données  
  
###  <a name="dataload_nci"></a> Chargement des données dans un Index Columnstore non cluster  
 Pour charger des données dans un index non cluster, première charger des données dans une table rowstore traditionnelle stockée comme un segment de mémoire ou en cluster d’index et puis créer l’index columnstore non cluster avec [CREATE COLUMNSTORE INDEX &#40;&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).  
  
 ![Chargement des données dans un index columnstore](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "le chargement des données dans un index columnstore")  
  
 Une table avec un index columnstore non cluster est en lecture seule jusqu'à ce que l'index soit désactivé ou supprimé. Pour mettre à jour la table et l'index columnstore non cluster, basculez des partitions. Vous pouvez également désactiver l'index, mettre à jour la table, puis reconstruire l'index.  
  
 Pour plus d'informations, consultez [Using Nonclustered Columnstore Indexes](indexes.md)  
  
###  <a name="dataload_cci"></a> Chargement des données dans un Index cluster Columnstore  
 ![Chargement dans un index columnstore cluster](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "Chargement dans un index columnstore cluster")  
  
 Comme le suggère le diagramme, pour charger des données dans un index columnstore cluster, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
1.  Insère les rowgroups de taille maximale directement dans le columnstore. Lorsque les données sont chargées, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] affecte les lignes de données dans l'ordre premier arrivé premier servi dans un rowgroup ouvert.  
  
2.  Pour chaque rowgroup, après qu'il a atteint la taille maximale, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
    1.  Marque le rowgroup comme étant CLOSED.  
  
    2.  Ignore le deltastore.  
  
    3.  Compresse chaque segment de colonne avec le rowgroup à l'aide de la compression columnstore.  
  
    4.  Stocke physiquement chaque segment de colonne compressé dans le columnstore.  
  
3.  Insère les lignes restantes dans le columnstore ou le deltastore comme suit :  
  
    1.  Si le nombre de lignes répond à l'exigence de nombre de lignes minimal par rowgroup, les lignes sont ajoutées au columnstore.  
  
    2.  Si le nombre de lignes est inférieur au nombre de lignes minimal par rowgroup, les lignes sont ajoutées au deltastore.  
  
 Pour plus d'informations sur les tâches et les processus deltastore, consultez [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)  
  
##  <a name="performance"></a> Conseils sur les performances  
  
### <a name="plan-for-enough-memory-to-create-columnstore-indexes-in-parallel"></a>Planifiez suffisamment de mémoire pour créer des index columnstore en parallèle  
 La création d'un index columnstore par défaut est une opération parallèle tant que la mémoire est contrainte. La création de l'index en parallèle requiert plus de mémoire que la création de l'index en série. Lorsqu'il y a suffisamment de mémoire, la création d'un index columnstore prend 1,5 fois plus de temps que créer un arbre B sur les mêmes colonnes.  
  
 La mémoire requise pour créer un index columnstore dépend du nombre de colonnes, du nombre de colonnes de chaîne, du degré de parallélisme (DOP), et des caractéristiques des données. Par exemple, si la table a moins d'un million de lignes, SQL Server utilisera un seul thread pour créer l'index columnstore.  
  
 Si votre table a plus d'un million de lignes, mais SQL Server ne peut pas obtenir suffisamment d'allocation de mémoire pour créer l'index à l'aide de MAXDOP, il réduira automatiquement MAXDOP de sorte qu'il tienne dans l'allocation de mémoire disponible.  Dans certains cas, le DOP doit être réduit à un pour pouvoir créer l'index sous une mémoire contrainte.  
  
##  <a name="related"></a> Tâches et rubriques connexes  
  
### <a name="nonclustered-columnstore-indexes"></a>Index columnstore non cluster  
 Pour les tâches courantes, consultez [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md).  
  
-   [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)  
  
-   [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD.  
  
-   [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
### <a name="clustered-columnstore-indexes"></a>Index columnstore cluster  
 Pour les tâches courantes, consultez [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md).  
  
-   [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)  
  
-   [ALTER INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-index-transact-sql) avec REBUILD ou REORGANIZE.  
  
-   [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
-   [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)  
  
-   [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)  
  
-   [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql)  
  
### <a name="metadata"></a>Métadonnées  
 Toutes les colonnes dans un index columnstore sont stockées dans les métadonnées en tant que colonnes incluses. L'index columnstore n'a pas de colonnes clés.  
  
-   [sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
-   [sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)  
  
-   [sys.partitions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql)  
  
-   [sys.column_store_segments &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-segments-transact-sql)  
  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql)  
  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)  
  
  
