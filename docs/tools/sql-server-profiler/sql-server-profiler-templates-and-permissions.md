---
title: "Modèles du Générateur de profils SQL Server et autorisations | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d55a2aaf43865897995dea95fd900bf9f6eee422
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-profiler-templates-and-permissions"></a>Modèles et autorisations du générateur de SQL Server Profiler
  Le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indique comment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] résout les requêtes de manière interne. Les administrateurs peuvent ainsi voir exactement quelles sont les expressions multidimensionnelles ou les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui sont soumises au serveur et comment celui-ci accède à la base de données ou au cube pour renvoyer des jeux de résultats.  
  
 Le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]vous permet d'effectuer les opérations suivantes :  
  
-   Créer une trace basée sur un modèle réutilisable  
  
-   Observer les résultats de la trace au fil de son exécution  
  
-   Stocker les résultats de la trace dans une table  
  
-   Démarrer, arrêter, suspendre et modifier les résultats de la trace en fonction des besoins  
  
-   Relire les résultats de la trace  
  
 Utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour surveiller uniquement les événements qui vous intéressent. Si les traces deviennent trop volumineuses, vous pouvez les filtrer en fonction des informations de votre choix, de manière à ce que seul un sous-ensemble des données d’événement soit recueilli. La surveillance d'un trop grand nombre d'événements s'ajoute à la charge du serveur et du processus de surveillance, et peut considérablement accroître la taille du fichier ou de la table de trace, en particulier si le processus de surveillance se prolonge sur une période importante.  
  
> [!NOTE]  
>  Les valeurs des colonnes de traces supérieures à 1 Go renvoient une erreur et sont tronquées dans la sortie de trace.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Modèles du Générateur de profils SQL Server](../../tools/sql-server-profiler/sql-server-profiler-templates.md)|Contient des informations relatives aux modèles de trace prédéfinis fournis avec le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Autorisations requises pour exécuter SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)|Contient des informations relatives aux autorisations requises pour exécuter le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Enregistrer des Traces et des modèles de Trace](../../tools/sql-server-profiler/save-traces-and-trace-templates.md)|Contient des informations relatives à l'enregistrement de la sortie de la trace et des définitions de la trace dans un modèle.|  
|[Modifier des modèles de Trace](../../tools/sql-server-profiler/modify-trace-templates.md)|Contient des informations relatives à la modification des modèles de trace à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|[Démarrer une Trace](../../tools/sql-server-profiler/start-a-trace.md)|Contient des informations relatives à ce qui se passe quand vous démarrez, quand vous suspendez ou quand vous arrêtez une trace.|  
|[Mettre en corrélation une Trace avec les données de journal de performances Windows](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)|Contient des informations relatives à la corrélation des données du journal de performances Windows avec une trace à l'aide du Générateur de profils [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Afficher et analyser des traces avec SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)|Contient des informations relatives à l'utilisation de traces pour la résolution de problèmes de données, à l'affichage des noms d'objet dans une trace et à la recherche d'événements dans une trace.|  
|[Analyser des blocages à l'aide de SQL Server Profiler](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)|Contient des informations relatives à l'utilisation du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour identifier la cause d'un blocage.|  
|[Analyser des requêtes avec des résultats SHOWPLAN dans SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)|Contient des informations relatives à l'utilisation du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour collecter et afficher les résultats des classes d'événements Showplan et Showplan Statistics.|  
|[Filtrer des Traces avec SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md)|Contient des informations relatives à l'utilisation du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]pour définir des filtres sur les colonnes de données afin de filtrer la sortie de la trace.|  
|[Relire des Traces](../../tools/sql-server-profiler/replay-traces.md)|Contient des informations qui expliquent ce qu'est la relecture d'une trace et qui indiquent les conditions nécessaires à sa réalisation.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Démarrer le Générateur de profils SQL Server](../../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  
