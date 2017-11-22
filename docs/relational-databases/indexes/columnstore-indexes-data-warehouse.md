---
title: "Index columnstore - Entrepôt de données | Microsoft Docs"
ms.custom: 
ms.date: 01/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: indexes
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21fd153b-116d-47fc-a926-f1528299a391
caps.latest.revision: "15"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5fd07fe225529bd8a3be25a988059a72e99dc5c8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="columnstore-indexes---data-warehouse"></a>Index columnstore - Entrepôt de données
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les index columnstore, conjointement avec le partitionnement, sont essentiels pour générer un entrepôt de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="whats-new"></a>Nouveautés  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] présente ces fonctionnalités pour les améliorations des performances de columnstore :  
  
-   Always On prend en charge l’interrogation d’un index columnstore sur un réplica secondaire lisible.  
  
-   MARS (Multiple Active Result Sets) prend en charge les index columnstore.  
  
-   Une nouvelle vue de gestion dynamique [sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md) fournit des informations sur la résolution des problèmes de performances au niveau du groupe de lignes.  
  
-   Les requêtes monothread sur les index columnstore peuvent s’exécuter en mode batch. Auparavant, seules les requêtes multi-threads pouvaient s’exécuter en mode batch.  
  
-   L’opérateur SORT s’exécute en mode batch.  
  
-   Les opérations DISTINCT multiples s’exécutent en mode batch.  
  
-   Les agrégats de fenêtres s’exécutent maintenant en mode de traitement par lots pour le niveau de compatibilité de base de données 130  
  
-   Agrégation en mode Push pour un traitement efficace des agrégats. Ceci est pris en charge sur tous les niveaux de compatibilité de base de données.  
  
-   Prédicats de chaîne en mode Push pour un traitement efficace des prédicats de chaîne. Ceci est pris en charge sur tous les niveaux de compatibilité de base de données.  
  
-   Isolement d’instantané pour le niveau de compatibilité de base de données 130  
  
## <a name="improve-performance-by-combining-nonclustered-and-columnstore-indexes"></a>Amélioration des performances grâce à l’association d’index non cluster et columnstore  
 À partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], vous pouvez définir des index non cluster sur un index columnstore en cluster.  
  
### <a name="example-improve-efficiency-of-table-seeks-with-a-nonclustered-index"></a>Exemple : Améliorer l’efficacité des recherches dans la table avec un index non cluster  
 Pour améliorer l’efficacité des recherches dans la table dans un entrepôt de données, vous pouvez créer un non cluster conçu pour exécuter des requêtes plus efficaces avec les recherches dans la table. Par exemple, les requêtes de recherche de valeurs correspondantes ou pour retourner une petite plage de valeurs seront plus performantes avec un index btree plutôt qu’avec un index columnstore. Elles ne nécessitent pas une analyse complète de la table via l’index columnstore et elles retourneront le résultat correct plus rapidement en effectuant une recherche binaire à l’aide d’un index btree.  
  
```  
--BASIC EXAMPLE: Create a nonclustered index on a columnstore table.  
  
--Create the table  
CREATE TABLE t_account (  
    AccountKey int NOT NULL,  
    AccountDescription nvarchar (50),  
    AccountType nvarchar(50),  
    UnitSold int  
);  
GO  
  
--Store the table as a columnstore.  
CREATE CLUSTERED COLUMNSTORE INDEX taccount_cci ON t_account;  
GO  
  
--Add a nonclustered index.  
CREATE UNIQUE INDEX taccount_nc1 ON t_account (AccountKey);  
```  
  
### <a name="example-use-a-nonclustered-index-to-enforce-a-primary-key-constraint-on-a-columnstore-table"></a>Exemple : Utiliser un index non cluster pour appliquer une contrainte de clé primaire sur une table columnstore  
 Par défaut, une table columnstore n’autorise pas une contrainte de clé primaire. Maintenant, vous pouvez utiliser un index non cluster sur une table columnstore pour appliquer une contrainte de clé primaire. Une clé primaire est équivalente à une contrainte UNIQUE sur une colonne non NULL et SQL Server implémente une contrainte UNIQUE comme index non cluster. En combinant ces faits, l’exemple suivant définit une contrainte UNIQUE sur la valeur accountkey de colonne non NULL. Il en résulte un index non cluster qui applique une contrainte de clé primaire comme une contrainte UNIQUE sur une colonne non NULL.  
  
 Ensuite, la table est convertie en un index columnstore en cluster. Lors de la conversion, l’index non cluster est conservé. Il en résulte un index columnstore en cluster avec un index non cluster qui applique une contrainte de clé primaire. Étant donné que toute mise à jour ou insertion dans la table columnstore affectera également l’index non cluster, toutes les opérations qui violent la contrainte unique et la valeur non NULL entraîneront l’échec de toute l’opération.  
  
 Il en résulte un index columnstore avec un index non cluster qui applique une contrainte de clé primaire sur les deux index.  
  
```  
--EXAMPLE: Enforce a primary key constraint on a columnstore table.   
  
--Create a rowstore table with a unique constraint.  
--The unique constraint is implemented as a nonclustered index.  
CREATE TABLE t_account (  
    AccountKey int NOT NULL,  
    AccountDescription nvarchar (50),  
    AccountType nvarchar(50),  
    UnitSold int,  
  
    CONSTRAINT uniq_account UNIQUE (AccountKey)  
);  
  
--Store the table as a columnstore.   
--The unique constraint is preserved as a nonclustered index on the columnstore table.  
CREATE CLUSTERED COLUMNSTORE INDEX t_account_cci ON t_account  
  
--By using the previous two steps, every row in the table meets the UNIQUE constraint  
--on a non-NULL column.  
--This has the same end-result as having a primary key constraint  
--All updates and inserts must meet the unique constraint on the nonclustered index or they will fail.  
  
--If desired, add a foreign key constraint on AccountKey.  
  
ALTER TABLE [dbo].[t_account]  
WITH CHECK ADD FOREIGN KEY([AccountKey]) REFERENCES my_dimension(Accountkey)  
;  
  
```  
  
### <a name="improve-performance-by-enabling-row-level-and-row-group-level-locking"></a>Amélioration des performances avec l’activation du verrouillage au niveau de la ligne et au niveau du groupe de lignes  
 Pour compléter l’index non cluster sur une fonctionnalité d’index columnstore, [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] offre une fonctionnalité de verrouillage granulaire pour les opérations de sélection, de mise à jour et de suppression. Les requêtes peuvent être exécutées avec le verrouillage au niveau de la ligne sur les recherches d’index avec un index non cluster et avec le verrouillage au niveau du groupe de lignes sur les analyses de tables complètes avec l’index columnstore. Cela permet d’obtenir une concurrence en lecture/écriture plus élevée avec le verrouillage au niveau de la ligne et au niveau du groupe de ligne utilisé de façon appropriée.  
  
```  
--Granular locking example  
--Store table t_account as a columnstore table.  
CREATE CLUSTERED COLUMNSTORE INDEX taccount_cci ON t_account  
GO  
  
--Add a nonclustered index for use with this example  
CREATE UNIQUE INDEX taccount_nc1 ON t_account (AccountKey);  
GO  
  
--Look at locking with access through the nonclustered index  
SET TRANSACTION ISOLATION LEVEL repeatable read;  
GO  
  
BEGIN TRAN  
    -- The query plan chooses a seek operation on the nonclustered index  
    -- and takes the row lock  
    SELECT * FROM t_account WHERE AccountKey = 100;  
END TRAN  
  
```  
  
### <a name="snapshot-isolation-and-read-committed-snapshot-isolations"></a>Isolement d'instantané et isolements d’instantanés de lecture validée  
 Utilisez l’isolement d’instantané (SI) pour garantir la cohérence transactionnelle et les isolements d’instantanés de lecture validée (RCSI) pour garantir la cohérence au niveau de l’instruction des requêtes sur les index columnstore. Ainsi, les requêtes s’exécutent sans bloquer les enregistreurs de données. Ce comportement non bloquant réduit également sensiblement la probabilité de blocages pour les transactions complexes. Pour plus d’informations, consultez [Isolement d’instantané dans SQL Server](http://msdn.microsoft.com/library/tcbchxcb\(v=vs.110\).aspx) sur MSDN.  
  
## <a name="see-also"></a>Voir aussi  
 Guide des index columnstore   
 Chargement de données d’index columnstore   
 Synthèse des fonctionnalités des index columnstore en fonction des versions   
 [Performances des requêtes d’index columnstore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [Prise en main de columnstore pour l’analytique opérationnelle en temps réel](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [Défragmentation des index columnstore](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  
