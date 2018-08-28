---
title: Traitement de requêtes intelligent dans les bases de données Microsoft SQL | Microsoft Docs
description: Fonctionnalités de traitement de requêtes intelligent pour améliorer les performances des requêtes dans SQL Server et Azure SQL Database.
ms.custom: ''
ms.date: 07/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f36910f24b976b1c27f51ab45db40265a71c3c02
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43072992"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Traitement de requêtes intelligent dans les bases de données SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

La famille des fonctionnalités de **traitement de requêtes intelligent** inclut des fonctionnalités qui améliorent les performances des charges de travail existantes avec un minimum d’effort d’implémentation.

![Fonctionnalités de traitement de requêtes intelligent](./media/1_IQPFeatureFamily.png)

## <a name="adaptive-query-processing"></a>Traitement de requêtes adaptatif
La fonctionnalité de traitement de requêtes adaptatif inclut des améliorations du traitement des requêtes, qui adaptent les stratégies d’optimisation aux conditions d’exécution de la charge de travail de votre application. Ces améliorations sont incluses : jointures adaptatives en mode batch, retour d’allocation de mémoire et exécution entrelacée pour les fonctions table à instructions multiples.

### <a name="batch-mode-adaptive-joins"></a>Jointures adaptatives en mode batch
Cette fonctionnalité permet à votre plan de basculer dynamiquement sur une meilleure stratégie de jointure pendant l’exécution à l’aide d’un seul plan mis en cache.

### <a name="row-and-batch-mode-memory-grant-feedback"></a>Retour d’allocation de mémoire en mode en ligne et en mode batch
Cette fonctionnalité recalcule la mémoire réelle nécessaire pour une requête, puis met à jour la valeur d’allocation pour le plan mis en cache, ce qui réduit les allocations de mémoire excessives qui impactent la concurrence et corrige les allocations de mémoire sous-estimées qui entraînent des dépassements coûteux sur le disque.

### <a name="interleaved-execution-for-multi-statement-table-valued-functions-mstvfs"></a>Exécution entrelacée pour les fonctions table à instructions multiples (MSTVF)
Avec l’exécution entrelacée, le nombre réel de lignes de la fonction est utilisé pour prendre des décisions de plan de requête en aval plus avisées. 

Pour plus d’informations, consultez [Traitement adaptatif des requêtes dans les bases de données SQL](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="table-variable-deferred-compilation"></a>Compilation différée de variable de table
La compilation différée de variable de table améliore la qualité du plan et les performances globales pour les requêtes faisant référence à des variables de table. Pendant l’optimisation et la compilation initiale, cette fonctionnalité va propager les estimations de cardinalité basées sur le nombre réel de lignes de la variable de table.  Ces informations précises sur le nombre de lignes seront utilisées afin d’optimiser les opérations de plan en aval.

Avec la compilation différée de la variable de table, la compilation d’une instruction qui fait référence à une variable de table est différée jusqu'à la première exécution réelle de l’instruction. Ce comportement de compilation différée est identique au comportement des tables temporaires, et ce changement entraîne l’utilisation de la cardinalité réelle au lieu de l’estimation d’origine d’une ligne. Pour activer la préversion publique de la compilation différée de variable de table dans Azure SQL Database, fixez le niveau de compatibilité à 150 pour la base de données à laquelle vous vous connectez lors de l’exécution de la requête.

Pour plus d'informations, consultez [Compilation différée de variable de table](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation ).

## <a name="approximate-query-processing"></a>Traitement des requêtes approximatif
Le traitement des requêtes approximatif est une nouvelle famille de fonctionnalités conçues pour fournir des agrégations dans de vastes jeux de données où la réactivité est plus importante que la précision absolue.  Un exemple peut être le calcul d’un COUNT(DISTINCT()) dans 10 milliards de lignes pour l’affichage sur un tableau de bord.  Dans ce cas, la précision absolue n’est pas importante, mais la réactivité est essentielle. La nouvelle fonction d’agrégation APPROX_COUNT_DISTINCT retourne le nombre approximatif de valeurs non null uniques dans un groupe.

Pour plus d’informations, consultez [APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md).

## <a name="see-also"></a>Voir aussi
[Centre de performances pour le moteur de base de données SQL Server et Azure SQL Database](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md)    
[Guide de référence des opérateurs Showplan logiques et physiques](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Jointures](../../relational-databases/performance/joins.md)    
[Illustration du traitement de requêtes adaptatif](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)        
