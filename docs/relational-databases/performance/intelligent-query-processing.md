---
title: Traitement de requêtes intelligent dans les bases de données Microsoft SQL | Microsoft Docs
description: Fonctionnalités de traitement de requêtes intelligent pour améliorer les performances des requêtes dans SQL Server et Azure SQL Database.
ms.custom: ''
ms.date: 01/11/2019
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
ms.openlocfilehash: 768f9d00e1eea9b97c32d35c240befdaf555122f
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54254924"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Traitement de requêtes intelligent dans les bases de données SQL

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

La famille des fonctionnalités de **traitement de requêtes intelligent** inclut des fonctionnalités qui améliorent les performances des charges de travail existantes avec un minimum d’effort d’implémentation.

![Fonctionnalités de traitement de requêtes intelligent](./media/3_IQPFeatureFamily2.png)

## <a name="adaptive-query-processing"></a>Traitement de requêtes adaptatif

La fonctionnalité de traitement de requêtes adaptatif inclut des améliorations du traitement des requêtes, qui adaptent les stratégies d’optimisation aux conditions d’exécution de la charge de travail de votre application. Ces améliorations comprennent : 
- Jointures adaptatives en mode batch
- Rétroaction d’allocation de mémoire
- Exécution entrelacée pour les fonctions table à instructions multiples (MSTVF)

### <a name="batch-mode-adaptive-joins"></a>Jointures adaptatives en mode batch

Cette fonctionnalité permet à votre plan de basculer dynamiquement sur une meilleure stratégie de jointure pendant l’exécution à l’aide d’un seul plan mis en cache.

Pour plus d’informations sur les jointures adaptatives en mode batch, consultez [Traitement de requêtes adaptatif dans les bases de données SQL](../../relational-databases/performance/adaptive-query-processing.md).

### <a name="row-and-batch-mode-memory-grant-feedback"></a>Retour d’allocation de mémoire en mode en ligne et en mode batch

> [!NOTE]
> La rétroaction d’allocation de mémoire en mode ligne est une fonctionnalité en préversion publique.  

Cette fonctionnalité recalcule la mémoire réelle nécessaire pour une requête, puis met à jour la valeur d’allocation pour le plan mis en cache, ce qui réduit les allocations de mémoire excessives qui impactent la concurrence et corrige les allocations de mémoire sous-estimées qui entraînent des dépassements coûteux sur le disque.

Pour plus d’informations sur la rétroaction d’allocation de mémoire, consultez [Traitement adaptatif des requêtes dans les bases de données SQL](../../relational-databases/performance/adaptive-query-processing.md).

### <a name="interleaved-execution-for-multi-statement-table-valued-functions-mstvfs"></a>Exécution entrelacée pour les fonctions table à instructions multiples (MSTVF)

Avec l’exécution entrelacée, le nombre réel de lignes de la fonction est utilisé pour prendre des décisions de plan de requête en aval plus avisées. Pour plus d’informations sur les fonctions table à instructions multiples (MSTVF), consultez [Fonctions table](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#TVF).

Pour plus d’informations sur l’exécution entrelacée, consultez [Traitement adaptatif des requêtes dans les bases de données SQL](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="table-variable-deferred-compilation"></a>Compilation différée de variable de table

> [!NOTE]
> Compilation différée de variable de table est une fonctionnalité en préversion publique.  

La compilation différée de variable de table améliore la qualité du plan et les performances globales pour les requêtes faisant référence à des variables de table. Pendant l’optimisation et la compilation initiale, cette fonctionnalité va propager les estimations de cardinalité basées sur le nombre réel de lignes de la variable de table.  Ces informations précises sur le nombre de lignes seront utilisées afin d’optimiser les opérations de plan en aval.

Avec la compilation différée de la variable de table, la compilation d’une instruction qui fait référence à une variable de table est différée jusqu'à la première exécution réelle de l’instruction. Ce comportement de compilation différée est identique au comportement des tables temporaires, et ce changement entraîne l’utilisation de la cardinalité réelle au lieu de l’estimation d’origine d’une ligne. Pour activer la préversion publique de la compilation différée de variable de table dans Azure SQL Database, fixez le niveau de compatibilité à 150 pour la base de données à laquelle vous vous connectez lors de l’exécution de la requête.

Pour plus d'informations, consultez [Compilation différée de variable de table](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation ).

## <a name="scalar-udf-inlining"></a>Incorporation (inlining) des fonctions UDF scalaires

> [!NOTE]
> La fonctionnalité d’incorporation des fonctions UDF scalaires est en préversion publique.  

L’inlining de fonctions UDF scalaires transforme des [fonctions scalaires définies par l’utilisateur (UDF)](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#Scalar) en expressions relationnelles et les incorpore à la requête SQL d’appel, ce qui améliore les performances des charges de travail qui tirent parti des fonctions UDF scalaires. L’inlining de fonctions UDF scalaires facilite l’optimisation du coût des opérations au sein des fonctions UDF et aboutit à des plans d’exécution efficaces, orientés ensembles et parallèles, par opposition à des plans inefficaces, itératifs et en série. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150.

Pour plus d’informations, consultez [Incorporation des fonctions UDF scalaires](../user-defined-functions/scalar-udf-inlining.md).

## <a name="approximate-query-processing"></a>Traitement des requêtes approximatif

> [!NOTE]
> APPROX_COUNT_DISTINCT est une fonctionnalité en préversion publique.  

Le traitement des requêtes approximatif est une nouvelle famille de fonctionnalités conçues pour fournir des agrégations dans de vastes jeux de données où la réactivité est plus importante que la précision absolue.  Un exemple peut être le calcul d’un COUNT(DISTINCT()) dans 10 milliards de lignes pour l’affichage sur un tableau de bord.  Dans ce cas, la précision absolue n’est pas importante, mais la réactivité est essentielle. La nouvelle fonction d’agrégation APPROX_COUNT_DISTINCT retourne le nombre approximatif de valeurs non null uniques dans un groupe.

Pour plus d’informations, consultez [APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md).

## <a name="batch-mode-on-rowstore"></a>Mode Batch sur Rowstore 

> [!NOTE]
> Mode Batch sur Rowstore est une fonctionnalité en préversion publique.  

### <a name="background"></a>Arrière-plan

[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a introduit une nouvelle fonctionnalité pour accélérer les charges de travail analytiques : les index columnstore. Nous avons étendu les cas d’utilisation et amélioré les performances des index columnstore dans chaque version suivante. Jusqu’à présent, nous avons présenté et documenté toutes ces fonctionnalités sous la forme d’une fonctionnalité unique. Vous créez des index columnstore sur vos tables et votre charge de travail analytique « va simplement plus vite ». En coulisses, cependant, il existe deux jeux de technologies connexes mais distincts :
- Les index **ColumnStore** permettent aux requêtes analytiques d’accéder uniquement aux données dans les colonnes nécessaires. Le format columnstore permet également la compression beaucoup plus efficace que celle obtenue avec la compression de page dans des index « rowstore » traditionnels. 
- Le traitement en **mode Batch** permet aux opérateurs de requête de traiter plus efficacement les données en travaillant sur un lot de lignes à la fois, au lieu d’une ligne à la fois. Plusieurs autres améliorations d’évolutivité sont liées au traitement en mode Batch. Pour plus d’informations sur le mode batch, consultez [Modes d’exécution](../../relational-databases/query-processing-architecture-guide.md#execution-modes).

Les deux ensembles de fonctionnalités fonctionnent ensemble pour améliorer les E/S et l’utilisation du processeur :
- Les index ColumnStore permettent à davantage de vos données de tenir en mémoire, réduisant ainsi la nécessité des E/S.
- Le traitement en mode Batch utilise plus efficacement le processeur.

Dès que possible, les deux technologies tirent parti l’une de l’autre. Par exemple, les agrégats en mode Batch peuvent être évalués dans le cadre d’une analyse d’index columnstore. Nous traitons également les données columnstore compressées à l’aide du codage de la longueur d’exécution beaucoup plus efficacement avec les jonctions en mode Batch et des agrégats en mode Batch. 
 
Les deux fonctionnalités sont déjà utilisables indépendamment : vous pouvez obtenir des plans en mode Row qui utilisent des index columnstore et vous pouvez obtenir des plans en mode Batch qui utilisent uniquement les index rowstore. Mais étant donné que dans la plupart des cas vous obtenez les meilleurs résultats lorsque les deux fonctionnalités sont utilisées ensemble, l’optimiseur de requête SQL n’a jusqu’à présent pris en compte que le traitement en mode Batch pour les requêtes qui impliquent au moins une table avec un index columnstore.

Pour certaines applications, les index columnstore ne sont pas une option viable étant donné que l’application utilise une autre fonctionnalité qui n’est pas prise en charge avec des index columnstore (les déclencheurs ne sont pas pris en charge sur les tables avec des index columnstore en cluster, par exemple). Plus important encore, les index columnstore ajoutent une surcharge pour les instructions DELETE et UPDATE, car les modifications sur place ne sont pas compatibles avec la compression columnstore. Pour certaines charges de travail transactionnelles-analytiques hybrides, l’avantage offert par l’index columnstore pour les requêtes analytiques est largement compensé par la surcharge sur les aspects transactionnels d’une charge de travail. Ces scénarios peuvent bénéficier d’une utilisation du processeur améliorée avec le traitement en mode Batch seul, c’est pourquoi la fonctionnalité **mode Batch sur rowstore** envisage d’utiliser le mode Batch pour toutes les requêtes, quels que soient les index impliqués.

### <a name="what-workloads-may-benefit-from-batch-mode-on-rowstore"></a>Quelles charges de travail peuvent tirer parti du mode Batch sur rowstore

Les charges de travail suivantes peuvent tirer parti du mode Batch sur rowstore :
1. Une partie importante de la charge de travail se compose de requêtes analytiques (en règle générale, des requêtes avec des opérateurs comme des jonctions ou des agrégats traitant des centaines de milliers de lignes ou plus), **ET**
2. La charge de travail est liée à l’UC (si le goulot d’étranglement est lié aux E/S, il est toujours recommandé d’envisager l’utilisation d’un index columnstore, si possible), **ET**
3. La création d’un index columnstore ajoute une surcharge trop importante à la partie transactionnelle de votre charge de travail **OU** la création d’un index columnstore n’est pas possible, car votre application dépend d’une fonctionnalité qui n’est pas encore prise en charge par les index columnstore.

> [!NOTE]
> Le mode Batch sur rowstore ne peut aider qu’en réduisant la consommation de l’UC. Si votre goulot d’étranglement est lié aux E/S et si les données ne sont pas déjà mises en cache (cache « à froid »), le mode Batch sur rowstore n’améliore PAS le temps écoulé. De même, si la mémoire sur l’ordinateur est insuffisante pour mettre en cache toutes les données, une amélioration des performances est peu probable.

### <a name="what-changes-with-batch-mode-on-rowstore"></a>Ce qui change avec le mode Batch sur rowstore

Autre que de passer au niveau de compatibilité 150, vous n’êtes pas obligé de modifier quoi que ce soit de votre côté pour activer le mode Batch sur rowstore pour les charges de travail éligibles.

Même si une requête n’implique aucune table avec un index columnstore, le processeur de requêtes utilise désormais des données heuristiques pour décider s’il faut prendre en compte le mode Batch. Les données heuristiques sont constituées de ce qui suit :
1. Une vérification initiale des tailles de la table, des opérateurs utilisés et des cardinalités estimées dans la requête d’entrée.
2. Des points de contrôle supplémentaires, lorsque l’optimiseur détecte des plans nouveaux et à moindre coût pour la requête. Si ces autres plans n’utilisent pas le mode Batch de manière significative, l’optimiseur cesse d’explorer les alternatives du mode Batch.

Si le mode batch sur rowstore est utilisé, dans le plan d’exécution de la requête vous verrez le mode d’exécution réel en tant que « mode Batch » utilisé par l’opérateur d’analyse des segments de mémoire sur disque et des index B-tree.  Cette analyse en mode Batch peut évaluer les filtres de bitmap du mode Batch.  Vous pouvez également voir d’autres opérateurs en mode Batch dans le plan, comme les jonctions de hachage, les agrégats basés sur le hachage, les tris, les agrégats de fenêtre, les filtres, la concaténation et les opérateurs scalaires de calcul.

### <a name="remarks"></a>Notes 

1. Il n’existe aucune garantie que les plans de requête utiliseront le mode Batch. L’optimiseur de requête peut décider que le mode Batch ne semble pas utile pour la requête. 
2. Alors que l’espace de recherche de l’optimiseur de requête change, il n’existe aucune garantie que si vous obtenez un plan en mode row, il sera identique au plan que vous obtenez dans un niveau de compatibilité inférieur. Il n’est pas non plus garanti que si vous obtenez un plan en mode Batch, il sera identique au plan que vous obtiendriez avec un index columnstore. 
3. Les plans peuvent également changer de manière subtile pour les requêtes qui combinent des index columnstore et rowstore, en raison de la nouvelle analyse rowstore du mode Batch.
4. Limitations actuelles pour la nouvelle analyse du mode Batch sur rowstore : elle n’intervient pas pour les tables OLTP en mémoire, ou pour tout index autre que des segments de mémoire sur disque et des arborescences B-tree. Elle n’intervient pas non plus si une colonne LOB est récupérée ou filtrée. Cette limitation inclut les jeux de colonnes éparses et les colonnes XML.
5. Il existe des requêtes pour lesquelles le mode Batch n’est pas utilisé même avec des index columnstore (par exemple les requêtes impliquant des curseurs), et ces mêmes exclusions s’étendent aussi au mode Batch sur rowstore.

### <a name="configuring-batch-mode-on-rowstore"></a>Configuration du mode Batch sur rowstore

La configuration limitée à la base de données BATCH_MODE_ON_ROWSTORE est activée par défaut et peut être utilisée pour désactiver le mode Batch sur rowstore sans nécessiter de changer le niveau de compatibilité de la base de données :

```sql
-- Disabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = OFF;

-- Enabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = ON;
```

Vous pouvez désactiver le mode Batch sur rowstore via la configuration limitée à la base de données, mais remplacez toujours le paramètre au niveau de la requête à l’aide de l’indicateur de requête ALLOW_BATCH_MODE. L’exemple suivant active le mode Batch sur rowstore même avec la fonctionnalité désactivée via la configuration limitée à la base de données :

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('ALLOW_BATCH_MODE'));
```

Vous pouvez aussi désactiver le mode Batch sur rowstore pour une requête spécifique à l’aide de l’indicateur de requête DISALLOW_BATCH_MODE. Exemple :

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
