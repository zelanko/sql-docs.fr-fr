---
title: "Nouveaut&#233;s de SQL Server vNext (moteur de base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42f45b23-6509-45e8-8ee7-76a78f99a920
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Nouveaut&#233;s de SQL Server vNext (moteur de base de donn&#233;es)
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

**Remarque :** SQL Server vNext inclut également les fonctionnalités ajoutées dans les Service Packs SQL Server 2016. Pour plus d’informations sur ces éléments, consultez [Nouveautés de SQL Server 2016 (moteur de base de données)](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md).

## <a name="sql-server-database-engine-ctp-13"></a>Moteur de base de données SQL Server (CTP 1.3)
- Améliorations des performances des points de contrôle indirects.
- Ajout de la prise en charge des groupes de disponibilité sans cluster.
- Ajout du paramètre des groupes de disponibilité à validation de réplica minimale.
- Les groupes de disponibilité peuvent désormais fonctionner sur Windows-Linux pour activer les migrations entre systèmes d’exploitation et les tests.
- Ajout de la prise en charge de la stratégie de rétention des tables temporelles
- Nouvel élément DMV SYS.DM_DB_STATS_HISTOGRAM.
- Ajout de la prise en charge de la génération et de la régénération d’index columnstore non cluster en ligne.
- Ajout de&5; nouvelles vues de gestion dynamique pour retourner des informations sur le processus Linux. Pour plus d’informations, consultez l’article [Vues de gestion dynamique de processus Linux (Transact-SQL)](../../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- Le paramètre [Sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) est ajouté pour l’examen des statistiques.

## <a name="sql-server-database-engine-ctp-12"></a>Moteur de base de données SQL Server (CTP 1.2)

- L’Assistant Paramétrage de base de données (DTA) fourni avec SQL Server Management Studio version 16.4 lors de l’analyse de SQL Server 2016 et ultérieur, possède des options supplémentaires.    
   - Performances améliorées. Pour plus d’informations, consultez l’article [Performance Improvements using Database Engine Tuning Advisor (DTA) recommendations (Recommandations relatives à l’amélioration des performances à l’aide de l’Assistant Paramétrage de base de données [DTA])](Performance%20Improvements%20using%20Database%20Engine%20Tuning%20Advisor%20\(DTA\)%20recommendations.md).
   - Option `-fc` pour autoriser les recommandations d’index columnstore. Pour plus d’informations, consultez les articles [Utilitaire DTA](../../tools/dta/dta-utility.md) et [Columnstore index recommendations in Database Engine Tuning Advisor (DTA) (Recommandations relatives aux index columnstore dans l’Assistant Paramétrage de base de données [DTA])](Columnstore%20index%20recommendations%20in%20Database%20Engine%20Tuning%20Advisor%20\(DTA\).md).  
   - Option `-iq` pour autoriser l’Assistant Paramétrage de base de données (DTA) à vérifier une charge de travail du magasin de requêtes. Pour plus d’informations, consultez l’article [Tuning Database Using Workload from Query Store (Paramétrage de base de données à l’aide des charges de travail du magasin de requêtes)](../../relational-databases/performance/tuning-database-using-workload-from-query-store.md).
   

## <a name="sql-server-database-engine-ctp-11"></a>Moteur de base de données SQL Server (CTP 1.1)

<a name="InMemoryBulletsCtp11"/>
- Pour les fonctionnalités en mémoire, des améliorations supplémentaires apportées aux tables optimisées en mémoire et aux fonctions compilées en mode natif sont décrites ci-dessous, et des exemples de code sont disponibles dans le [texte qui vient à la suite ](#InMemory_CodeSamples):
    - Prise en charge des colonnes calculées dans les tables optimisées en mémoire, notamment des index sur les colonnes calculées.
    - Prise en charge complète des fonctions JSON dans des modules compilés en mode natif et dans des contraintes de validation.
    - Opérateur `CROSS APPLY` dans des modules compilés en mode natif.   
- De nouvelles fonctions de chaîne [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md), [TRANSLATE](../../t-sql/functions/translate-transact-sql.md) et [TRIM](../../t-sql/functions/trim-transact-sql.md) sont ajoutées.   
- La clause `WITHIN GROUP` est maintenant prise en charge pour la fonction [STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md).
- Deux nouvelles familles de classements japonais (Japanese_Bushu_Kakusu_140 et Japanese_XJIS_140) ont été ajoutées, et l’option de classement Variation-selector-sensitive (_VSS) a été ajoutée pour une utilisation dans les classements japonais. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)   
- De nouvelles options d’accès en bloc ([BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) et [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md)) permettent d’accéder aux données directement à partir d’un fichier spécifié au format CSV et à partir de fichiers stockés dans le stockage Blob Azure via la nouvelle option `BLOB_STORAGE` [d’EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).


## <a name="sql-server-database-engine-ctp-10"></a>Moteur de base de données SQL Server (CTP 1.0)

- Le niveau de compatibilité (**COMPATIBILITY_LEVEL**) de base de données 140 a été ajouté.   Les clients qui exécutent ce niveau obtiendront les fonctionnalités de langage et les comportements de l’optimiseur de requêtes les plus récents. Cela comprend les modifications apportées à chaque version préliminaire publiée par Microsoft.
- Améliorations apportées à la façon dont les seuils de mise à jour des statistiques incrémentielles sont calculés (mode de compatibilité&140; obligatoire).
- [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md) a été ajouté.
- Nous avons ajouté de nombreuses améliorations de performances et de langage aux tables en mémoire :
    - `sp_spaceused` est maintenant pris en charge pour les tables en mémoire.
    - `sp_rename` est maintenant pris en charge pour les modules natifs.
    - Les instructions `CASE` sont désormais prises en charge pour les modules natifs.
    - La limite de huit index sur les tables en mémoire a été supprimée.
    - `TOP (N) WITH TIES` est maintenant pris en charge dans les modules natifs.
    - `ALTER TABLE` exécuté sur les tables en mémoire est désormais beaucoup plus rapide dans certains cas.
    - La restauration par progression des transactions pour les tables en mémoire est désormais effectuée en parallèle. Cela réduit sensiblement la durée nécessaire pour effectuer les basculements ou, dans certains cas, les redémarrages.
    - Les fichiers de point de contrôle en mémoire peuvent désormais être stockés sur Azure Storage. Cela fournit des fonctionnalités équivalentes à MDF, comparé aux fichiers LDF qui offrent déjà cette fonctionnalité.
- Les index cluster Columnstore prennent désormais en charge les colonnes LOB (nvarchar(max), varchar(max), varbinary(max)).
- La fonction d’agrégation [STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md) a été ajoutée.  
- Nouvelles autorisations : `DATABASE SCOPED CREDENTIAL` est maintenant une classe d’éléments sécurisables, prenant en charge les autorisations `CONTROL`, `ALTER`, `REFERENCES`, `TAKE OWNERSHIP` et `VIEW DEFINITION`. `ADMINISTER DATABASE BULK OPERATIONS` qui est limitée à SQL Database est maintenant visible dans `sys.fn_builtin_permissions`.   
- La DMV [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md) a été ajoutée pour fournir des informations sur les systèmes d’exploitation Windows et Linux.   
- Les rôles de base de données sont créés avec R Services pour la gestion des autorisations associées aux packages. Pour plus d’informations, consultez [Gestion des packages R pour SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md).
 
<a name="InMemory_CodeSamples"/> 
## <a name="code-samples-for-new-in-memory-enhancements"></a>Exemples de code pour les nouvelles améliorations apportées en mémoire

Les sous-sections suivantes fournissent des exemples de code Transact-SQL qui illustrent les nouvelles fonctionnalités qui sont indiquées dans la liste à puces dans le texte précédent de cet article.

La liste à puces CTP 1.1 des nouvelles fonctionnalités en mémoire est indiquée [ici](#InMemoryBulletsCtp11).

#### <a name="computed-column-in-a-memory-optimized-table"></a>Colonne calculée dans une table optimisée en mémoire

Cette instruction CREATE TABLE illustre les fonctionnalités suivantes qui ont été mentionnées dans le texte précédent portant sur la version CTP 1.1 :

- Contrainte de validation JSON sur une colonne.
- Nouvelles colonnes calculées.
- Index sur une colonne calculée.

```tsql
CREATE TABLE Product(
    ProductID  int            PRIMARY KEY NONCLUSTERED,
    Name       nvarchar(400)  NOT NULL,
    Price      float,

    Data      nvarchar(4000)  CONSTRAINT [Data contains JSON]  CHECK (ISJSON(Data)=1),

    MadeIn  AS CAST(JSON_VALUE(Data, '$.MadeIn')            as NVARCHAR(50)) PERSISTED,
    Cost    AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float       ),

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)
)
        WITH (MEMORY_OPTIMIZED=ON);
```

#### <a name="cross-apply-and-json-functions"></a>CROSS APPLY et fonctions JSON

Cette instruction CREATE PROCEDURE destinée à une procédure stockée compilée en mode natif illustre les fonctionnalités suivantes qui ont été mentionnées dans le texte précédent portant sur la version CTP 1.1 :

- Opérateur CROSS APPLY.
- Fonctions JSON.

```tsql
CREATE OR ALTER PROCEDURE ProductList()
    WITH SCHEMABINDING, NATIVE_COMPILATION
as begin
    atomic with (transaction isolation level = snapshot,  language = N'English')

    SELECT
            ProductID, Name, Price, Tags,
            Data,
            JSON_VALUE(Data,'$.MadeIn') AS MadeIn,
            value
        FROM Product
        CROSS APPLY OPENJSON(Data, '$.SalesReasons')
        FOR JSON PATH
end;
```
