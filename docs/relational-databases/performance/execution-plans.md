---
title: Plans d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server]
- execution plans [SQL Server]
- query execution plans
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753f
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 9bf75c2d176c4ea2c596f29f1ddda910e794ae12
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68232019"
---
# <a name="execution-plans"></a>Plans d’exécution
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Pour pouvoir exécuter des requêtes, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] doit analyser l’instruction afin de déterminer la manière la plus efficace d’accéder aux données requises. Cette analyse est gérée par un composant appelé Optimiseur de requête. L’entrée de l’optimiseur de requête est composée de la requête, du schéma de base de données (définitions des tables et des index) et de ses statistiques de base de données. La sortie de l’optimiseur de requête est un plan d’exécution de requête, parfois appelé plan de requête ou simplement plan d’exécution.   

Un plan d'exécution de requête permet de définir : 

* l'ordre d'accès aux tables source.  
  Pour créer le jeu de résultats, le serveur de bases de données peut accéder aux tables de base selon de nombreux ordres différents. Par exemple, si une instruction `SELECT` référence trois tables, le serveur de base de données accédera d’abord à `TableA`, utilisera les données de `TableA` pour extraire les lignes correspondantes de `TableB`, puis utilisera les données de `TableB` pour extraire les données de `TableC`. Les autres séquences dans lesquelles le serveur de bases de données peut accéder aux tables sont les suivantes :  
  `TableC`, `TableB`, `TableA`ou  
  `TableB`, `TableA`, `TableC`ou  
  `TableB`, `TableC`, `TableA`ou  
  `TableC`, `TableA`, `TableB`  

* les méthodes utilisées pour extraire les données de chaque table.  
  Il existe également différentes méthodes d'accès aux données dans chaque table. Si seules quelques lignes ayant des valeurs de clés spécifiques sont nécessaires, le serveur de base de données peut utiliser un index. Si toutes les lignes de la table sont nécessaires, le serveur de base de données peut ignorer les index et procéder à une analyse de la table. Si toutes les lignes de la table sont nécessaires mais qu’il existe un index dont les colonnes clés se trouvent dans une clause `ORDER BY`, l’analyse d’index plutôt que l’analyse de table peut éviter un tri séparé du jeu de résultats. Dans le cas d'une table très petite, les analyses de table peuvent s'avérer plus efficaces pour quasiment tous les accès à la table.

> [!TIP]
> Pour plus d’informations sur le traitement des requêtes et les plans d’exécution de requête, consultez le [Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md).

## <a name="in-this-section"></a>Dans cette section  
  
-   [Infrastructure du profilage de requête](../../relational-databases/performance/query-profiling-infrastructure.md)  
  
-   [Afficher et enregistrer des plans d’exécution](../../relational-databases/performance/display-and-save-execution-plans.md)  
  
-   [Comparer et analyser des plans d’exécution](../../relational-databases/performance/compare-and-analyze-execution-plans.md)  

-   [Repères de plan](../../relational-databases/performance/plan-guides.md)  

## <a name="see-also"></a>Voir aussi  
 [Surveiller et optimiser les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Outils de surveillance et d’optimisation des performances](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md)    
 [Statistiques des requêtes dynamiques](../../relational-databases/performance/live-query-statistics.md)     
 [Moniteur d’activité](../../relational-databases/performance-monitor/activity-monitor.md)     
 [Surveillance des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
 [Indicateurs de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
 [Guide de référence des opérateurs Showplan logiques et physiques](../../relational-databases/showplan-logical-and-physical-operators-reference.md)
