---
title: Traitement de requêtes intelligent dans les bases de données Microsoft SQL | Microsoft Docs
description: Fonctionnalités de traitement de requêtes intelligent pour améliorer les performances des requêtes dans SQL Server et Azure SQL Database.
ms.custom: ''
ms.date: 02/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 00bea67666845ea43226b4bfe48b6dd5ab3f3741
ms.sourcegitcommit: 71913f80be0cb6f8d3af00c644ee53e3aafdcc44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56590454"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Traitement de requêtes intelligent dans les bases de données SQL

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

La famille de fonctionnalités de traitement de requêtes (QP) intelligent inclut des fonctionnalités ayant un impact important. Elles améliorent les performances des charges de travail existantes avec un effort d’implémentation minimal. Pour tirer automatiquement parti de cette famille de fonctionnalités, adoptez le niveau de compatibilité de base de données applicable.

| **Fonctionnalité IQP** | **Pris en charge dans Azure SQL Database** | **Pris en charge dans SQL Server** |
| --- | --- | --- |
| [Jointures adaptatives (mode batch)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#batch-mode-adaptive-joins) | Oui, avec le niveau de compatibilité 140| Oui, à partir de SQL Server 2017 sous le niveau de compatibilité 140|
| [Exécution entrelacée](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#interleaved-execution-for-multi-statement-table-valued-functions) | Oui, avec le niveau de compatibilité 140| Oui, à partir de SQL Server 2017 sous le niveau de compatibilité 140|
| [Retour d’allocation de mémoire (mode batch)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#batch-mode-memory-grant-feedback) | Oui, avec le niveau de compatibilité 140| Oui, à partir de SQL Server 2017 sous le niveau de compatibilité 140|
| [Retour d’allocation de mémoire (mode ligne)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#row-mode-memory-grant-feedback) | Oui, sous le niveau de compatibilité 150, préversion publique| Oui, à partir de SQL Server 2019 CTP 2.0 sous le niveau de compatibilité 150, préversion publique|
| [Nombre approximatif distinct](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#approximate-query-processing) | Oui, préversion publique| Oui, à partir de SQL Server 2019 CTP 2.0, préversion publique|
| [Compilation différée de variable de table](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#table-variable-deferred-compilation) | Oui, sous le niveau de compatibilité 150, préversion publique| Oui, à partir de SQL Server 2019 CTP 2.0 sous le niveau de compatibilité 150, préversion publique|
| [Mode Batch sur Rowstore](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#batch-mode-on-rowstore) | Oui, sous le niveau de compatibilité 150, préversion publique| Oui, à partir de SQL Server 2019 CTP 2.0 sous le niveau de compatibilité 150, préversion publique|
| [Incorporation (inlining) des fonctions UDF scalaires](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#scalar-udf-inlining) | Non, mais planifié pour une prochaine mise à jour | Oui, à partir de SQL Server 2019 CTP 2.1 sous le niveau de compatibilité 150, préversion publique|


## <a name="adaptive-query-processing"></a>Traitement de requêtes adaptatif

La famille de fonctionnalités de traitement de requêtes adaptatif inclut les améliorations du traitement de requêtes suivantes. Ces améliorations adaptent les stratégies d’optimisation aux conditions d’exécution de la charge de travail de votre application : 
- Jointures adaptatives en mode batch
- Rétroaction d’allocation de mémoire
- Exécution entrelacée pour les fonctions table à instructions multiples (MSTVF)

### <a name="batch-mode-adaptive-joins"></a>Jointures adaptatives en mode batch

Cette fonctionnalité permet à votre plan de basculer dynamiquement sur une meilleure stratégie de jointure pendant l’exécution à l’aide d’un seul plan mis en cache.

Pour plus d’informations sur les jointures adaptatives en mode batch, consultez [Traitement de requêtes adaptatif dans les bases de données SQL](../../relational-databases/performance/adaptive-query-processing.md).

### <a name="row-and-batch-mode-memory-grant-feedback"></a>Retour d’allocation de mémoire en mode en ligne et en mode batch

> [!NOTE]
> La rétroaction d’allocation de mémoire en mode ligne est une fonctionnalité en préversion publique.  

Cette fonctionnalité recalcule la mémoire réelle nécessaire pour une requête. Puis elle met à jour la valeur d’allocation pour le plan mis en cache. Elle permet de réduire les allocations de mémoire excessives qui affectent l’accès concurrentiel. Cette fonctionnalité résout également les allocations de mémoire sous-estimées qui provoquent des dépassements de capacité coûteux sur le disque.

Pour plus d’informations sur la rétroaction d’allocation de mémoire, consultez [Traitement adaptatif des requêtes dans les bases de données SQL](../../relational-databases/performance/adaptive-query-processing.md).

### <a name="interleaved-execution-for-mstvfs"></a>Exécution entrelacée pour les fonctions table à instructions multiples (MSTVF)

Avec l’exécution entrelacée, le nombre réel de lignes de la fonction est utilisé pour prendre des décisions de plan de requête en aval plus avisées. Pour plus d’informations sur les fonctions table à instructions multiples (MSTVF), consultez [Fonctions table](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#TVF).

Pour plus d’informations sur l’exécution entrelacée, consultez [Traitement adaptatif des requêtes dans les bases de données SQL](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="table-variable-deferred-compilation"></a>Compilation différée de variable de table

> [!NOTE]
> Compilation différée de variable de table est une fonctionnalité en préversion publique.  

La compilation différée de variable de table améliore la qualité du plan et les performances globales pour les requêtes faisant référence à des variables de table. Pendant l’optimisation et la compilation initiale, cette fonctionnalité propage les estimations de cardinalité basées sur le nombre réel de lignes de la variable de table. Ces informations précises sur le nombre de lignes optimisent les opérations de plan en aval.

Avec la compilation différée de la variable de table, la compilation d’une instruction qui fait référence à une variable de table est différée jusqu'à la première exécution réelle de l’instruction. Ce comportement de compilation différée est identique à celui des tables temporaires. Cette modification entraîne l’utilisation de la cardinalité réelle au lieu de l’estimation d’une ligne d’origine. 

Vous pouvez activer la préversion publique de la compilation différée de variable de table dans Azure SQL Database. Pour ce faire, activez le niveau de compatibilité 150 pour la base de données à laquelle vous êtes connecté lorsque vous exécutez la requête.

Pour plus d'informations, consultez [Compilation différée de variable de table](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation).

## <a name="scalar-udf-inlining"></a>Incorporation (inlining) des fonctions UDF scalaires

> [!NOTE]
> La fonctionnalité d’incorporation des fonctions définies par l’utilisateur (UDF) scalaires est en préversion publique.  

La fonctionnalité d’incorporation des fonctions UDF scalaires transforme automatiquement les [fonctions UDF scalaires](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#Scalar) en expressions relationnelles. Elle les incorpore dans la requête SQL appelante. Cette transformation améliore les performances des charges de travail qui tirent parti des fonctions UDF scalaires. La fonctionnalité d’incorporation des fonctions UDF scalaires facilite l’optimisation basée sur le coût des opérations à l’intérieur des fonctions UDF. Les résultats sont des plans efficaces, axés sur les ensembles et parallèles au lieu de plans d’exécution inefficaces, itératifs, en série. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150.

Pour plus d’informations, consultez [Incorporation des fonctions UDF scalaires](../user-defined-functions/scalar-udf-inlining.md).

## <a name="approximate-query-processing"></a>Traitement des requêtes approximatif

> [!NOTE]
> **APPROX_COUNT_DISTINCT** est une fonctionnalité en préversion publique.  

Le traitement des requêtes approximatif est une nouvelle famille de fonctionnalités. Il fournit des agrégations dans de vastes jeux de données où la réactivité est plus importante que la précision absolue. Un exemple est le calcul d’un **COUNT(DISTINCT())** dans 10 milliards de lignes pour l’affichage sur un tableau de bord. Dans ce cas, la précision absolue n’est pas importante, mais la réactivité est essentielle. La nouvelle fonction d’agrégation **APPROX_COUNT_DISTINCT** retourne le nombre approximatif de valeurs non null uniques dans un groupe.

Pour plus d’informations, consultez [APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md).

## <a name="batch-mode-on-rowstore"></a>Mode Batch sur rowstore 

> [!NOTE]
> Mode Batch sur rowstore est une fonctionnalité en préversion publique.  

Le mode batch sur rowstore permet l’exécution en mode batch des charges de travail analytiques sans avoir besoin d’index columnstore.  Cette fonctionnalité prend en charge les filtres bitmap et l’exécution du mode batch des segments de mémoire sur disque et des index B-tree. Le mode batch sur rowstore permet de prendre en charge tous les opérateurs existants compatibles avec le mode batch.

### <a name="background"></a>Arrière-plan

[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a introduit une nouvelle fonctionnalité pour accélérer les charges de travail analytiques : les index columnstore. Nous avons étendu les cas d’utilisation et amélioré les performances des index columnstore dans chaque version suivante. Jusqu’à présent, nous avons présenté et documenté toutes ces fonctionnalités sous la forme d’une fonctionnalité unique. Vous créez des index columnstore sur vos tables. Et votre charge de travail analytique s’exécute plus rapidement. Toutefois, il existe deux jeux de technologies connexes mais distincts :
- Les index **ColumnStore** permettent aux requêtes analytiques d’accéder uniquement aux données dans les colonnes nécessaires. La compression de page au format columnstore est aussi plus efficace que la compression dans des index **rowstore** traditionnels. 
- Avec le traitement **en mode batch**, les opérateurs de requête traitent les données plus efficacement. Ils travaillent sur un lot de lignes au lieu d’une ligne à la fois. Plusieurs autres améliorations d’évolutivité sont liées au traitement en mode Batch. Pour plus d’informations sur le mode batch, consultez [Modes d’exécution](../../relational-databases/query-processing-architecture-guide.md#execution-modes).

Les deux ensembles de fonctionnalités fonctionnent ensemble pour améliorer les entrées/sorties (E/S) et l’utilisation du processeur :
- En utilisant des index columnstore, une plus grande quantité de vos données s’intègre dans la mémoire. Cela réduit la nécessité des E/S.
- Le traitement en mode Batch utilise plus efficacement le processeur.

Dès que possible, les deux technologies tirent parti l’une de l’autre. Par exemple, les agrégats en mode Batch peuvent être évalués dans le cadre d’une analyse d’index columnstore. Nous traitons également les données columnstore compressées à l’aide du codage de la longueur d’exécution beaucoup plus efficacement avec les jonctions en mode Batch et des agrégats en mode Batch. 
 
Les deux fonctionnalités sont utilisables indépendamment :
* Vous bénéficiez de plans en mode ligne qui utilisent des index columnstore.
* Vous bénéficiez de plans en mode batch qui utilisent uniquement des index rowstore. 

Vous obtenez généralement les meilleurs résultats lorsque vous utilisez les deux fonctionnalités ensemble. Donc, jusqu’à présent, l’optimiseur de requête SQL Server ne prenait en compte le traitement en mode batch que pour les requêtes impliquant au moins une table avec un index columnstore.

Les index columnstore ne constituent pas une bonne option pour certaines applications. Une application peut utiliser une autre fonctionnalité qui n’est pas pris en charge avec des index columnstore. Par exemple, les modifications sur place ne sont pas compatibles avec la compression columnstore. Donc, les déclencheurs ne sont pas pris en charge sur les tables avec des index columnstore en cluster. Plus important encore, les index columnstore ajoutent une surcharge aux instructions **DELETE** et **UPDATE**. 

Pour certaines charges de travail transactionnelles-analytiques hybrides, les aspects transactionnels d’une charge de travail compense les avantages des index columnstore. Ces scénarios peuvent améliorer l’utilisation de l’UC par rapport au traitement en mode batch seul. C’est pourquoi le mode batch sur la fonctionnalité rowstore prend en compte le mode batch pour toutes les requêtes. Peu importe quels index sont impliqués.

### <a name="workloads-that-might-benefit-from-batch-mode-on-rowstore"></a>Charges de travail pouvant tirer parti du mode Batch sur rowstore

Les charges de travail suivantes peuvent tirer parti du mode Batch sur rowstore :
* Une partie importante de la charge de travail se compose de requêtes analytiques. En règle générale, ces requêtes possèdent des opérateurs tels que des jointures ou des agrégats qui traitent des centaines de milliers de lignes ou plus.
* La charge de travail est liée à l’UC. Si le goulot d’étranglement est au niveau des E/S, nous vous recommandons d’envisager d’utiliser un index columnstore, si possible.
* La création d’un index columnstore ajoute trop de surcharge à la partie transactionnelle de votre charge de travail. Ou bien, la création d’un index columnstore n’est pas faisable, car votre application dépend d’une fonctionnalité qui n’est pas encore prise en charge avec les index columnstore.

> [!NOTE]
> Le mode Batch sur rowstore ne peut aider qu’en réduisant la consommation de l’UC. Si votre goulot d’étranglement est lié aux E/S et si les données ne sont pas déjà mises en cache (cache « à froid »), le mode Batch sur rowstore n’améliore pas le temps écoulé. De même, si la mémoire sur l’ordinateur est insuffisante pour mettre en cache toutes les données, une amélioration des performances est peu probable.

### <a name="what-changes-with-batch-mode-on-rowstore"></a>Ce qui change avec le mode Batch sur rowstore

Autre que de passer au niveau de compatibilité 150, vous n’êtes pas obligé de modifier quoi que ce soit de votre côté pour activer le mode Batch sur rowstore pour les charges de travail éligibles.

Même si une requête n’implique aucune table avec un index columnstore, le processeur de requêtes utilise désormais des données heuristiques pour décider s’il faut prendre en compte le mode Batch. Les données heuristiques sont constituées de ces vérifications :
1. Une vérification initiale des tailles de la table, des opérateurs utilisés et des cardinalités estimées dans la requête d’entrée.
2. Des points de contrôle supplémentaires, lorsque l’optimiseur détecte des plans nouveaux et à moindre coût pour la requête. Si ces autres plans n’utilisent pas le mode Batch de manière significative, l’optimiseur cesse d’explorer les alternatives du mode Batch.

Si le mode Batch sur rowstore est utilisé, vous voyez le mode d’exécution réel en tant que **mode Batch** dans le plan de requête. L’opérateur d’analyse utilise le mode Batch pour les segments de mémoire sur disque et les index B-tree. Cette analyse en mode Batch peut évaluer les filtres de bitmap du mode Batch. Vous pouvez également voir d’autres opérateurs en mode Batch dans le plan. Par exemple, les jonctions de hachage, les agrégats basés sur le hachage, les tris, les agrégats de fenêtre, les filtres, la concaténation et les opérateurs scalaires de calcul.

### <a name="remarks"></a>Notes 

* Les plans de requête n’utilisent pas toujours le mode Batch. L’optimiseur de requête peut décider que le mode Batch n’est pas utile pour la requête. 
* L’espace de recherche de l’optimiseur de requête change. Par conséquent, si vous obtenez un plan en mode ligne, il peut être différent du plan que vous obtenez dans un niveau de compatibilité inférieur. Et si vous obtenez un plan en mode Batch, il peut être différent du plan que vous obtenez avec un index columstore. 
* Les plans peuvent également changer pour les requêtes qui combinent des index columnstore et rowstore, en raison de la nouvelle analyse rowstore du mode Batch.
* Voici les limitations actuelles pour la nouvelle analyse du mode Batch sur rowstore : 
    * Elle n’intervient pas pour les tables OLTP en mémoire, ou pour tout index autre que des segments de mémoire sur disque et des arborescences B-tree. 
    * Elle n’intervient pas non plus si une colonne LOB est récupérée ou filtrée. Cette limitation inclut les jeux de colonnes éparses et les colonnes XML.
* Il existe des requêtes pour lesquelles le mode Batch n’est pas utilisé même avec des index columnstore. Les requêtes qui impliquent des curseurs en sont des exemples. Ces mêmes exclusions s’étendent également au mode Batch sur rowstore.

### <a name="configure-batch-mode-on-rowstore"></a>Configurer le mode Batch sur rowstore

La configuration au niveau de la base de données **BATCH_MODE_ON_ROWSTORE** est activée par défaut. Elle désactive le mode Batch sur rowstore sans nécessiter de changement du niveau de compatibilité de la base de données :

```sql
-- Disabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = OFF;

-- Enabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = ON;
```

Vous pouvez désactiver le mode Batch sur rowstore via la configuration au niveau de la base de données. Mais vous pouvez toujours remplacer le paramètre au niveau de la requête à l’aide de l’indicateur de requête **ALLOW_BATCH_MODE**. L’exemple suivant active le mode Batch sur rowstore même avec la fonctionnalité désactivée via la configuration limitée à la base de données :

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('ALLOW_BATCH_MODE'));
```

Vous pouvez aussi désactiver le mode Batch sur rowstore pour une requête spécifique à l’aide de l’indicateur de requête **DISALLOW_BATCH_MODE**. Observez l'exemple suivant :

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('DISALLOW_BATCH_MODE'));
```

## <a name="see-also"></a>Voir aussi

[Centre de performances pour le moteur de base de données SQL Server et Azure SQL Database](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md)    
[Guide de référence des opérateurs Showplan logiques et physiques](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Jointures](../../relational-databases/performance/joins.md)    
[Illustration du traitement de requêtes adaptatif](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)       
[Illustration du traitement de requêtes (QP) intelligent](https://github.com/joesackmsft/Conferences/blob/master/IQPDemos/IQP_Demo_ReadMe.md)   
