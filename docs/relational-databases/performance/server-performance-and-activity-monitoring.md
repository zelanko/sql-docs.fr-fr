---
title: Analyse des performances et surveillance de l’activité du serveur | Microsoft Docs
description: Utilisez ces ressources pour apprendre à utiliser SQL Server et les outils de supervision des performances et de l’activité Windows afin d’évaluer le fonctionnement d’un serveur.
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- activity monitoring [SQL Server]
- traces [SQL Server], how-to topics
- monitoring server performance [SQL Server], activity monitoring
- stored procedures [SQL Server], traces
- performance [SQL Server], servers
- servers [SQL Server], performance
- SQL Server Profiler, how-to topics
- SQL Server Management Studio [SQL Server], monitoring system
- Profiler [SQL Server Profiler], how-to topics
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: f53b951e9b97b079c67132e836b2444d2871ddf0
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505000"
---
# <a name="server-performance-and-activity-monitoring"></a>Analyse des performances et surveillance de l'activité du serveur
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Le but de la surveillance des bases de données est d'évaluer le fonctionnement d'un serveur. Une surveillance efficace implique la prise d'instantanés périodiques des performances actuelles afin d'isoler les processus à l’origine des problèmes, ainsi que la collecte de données en continu pour suivre de près les tendances des performances. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le système d’exploitation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows fournissent des utilitaires qui permettent de contrôler les conditions actuelles de la base de données et de suivre le niveau de performance à mesure que les conditions évoluent.  
  
 La section suivante contient des rubriques qui décrivent comment utiliser les outils d'analyse des performances et de l'activité de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de Windows. Elle contient les rubriques suivantes :  
  
## <a name="to-perform-monitoring-tasks-with-windows-tools"></a>Pour effectuer une analyse des tâches à l'aide des outils Windows 
  
-   [Démarrer le Moniteur système &#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md)  
  
-   [Afficher le journal des applications Windows &#40;Windows&#41;](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
## <a name="to-create-sql-server-database-alerts-with-windows-tools"></a>Pour créer des alertes de base de données SQL Server à l'aide des outils Windows  
  
-   [Configurer une alerte de base de données SQL Server &#40;Windows&#41;](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md)  

## <a name="to-perform-monitoring-tasks-with-extended-events"></a>Pour exécuter les tâches de surveillance avec les Événements étendus  
 
 -   [Événements étendus](../../relational-databases/extended-events/extended-events.md)
 
 -   [Démarrage rapide : Événements étendus dans SQL Server](../../relational-databases/extended-events/quick-start-extended-events-in-sql-server.md)
 
 -   [Gérer les sessions d’événements dans l’Explorateur d’objets](../../relational-databases/extended-events/manage-event-sessions-in-the-object-explorer.md)
 
 -   [Modifier une session d’événements étendus](../../relational-databases/extended-events/alter-an-extended-events-session.md)
 
 -   [Convertir un script Trace SQL existant en session d’événements étendus](../../relational-databases/extended-events/convert-an-existing-sql-trace-script-to-an-extended-events-session.md)
 
 -   [Consulter les événements étendus équivalents aux classes d’événements Trace SQL](../../relational-databases/extended-events/view-the-extended-events-equivalents-to-sql-trace-event-classes.md)
   
## <a name="to-perform-monitoring-tasks-with-sql-server-management-studio"></a>Pour effectuer une analyse des tâches à l'aide de SQL Server Management Studio  
  
-   [Afficher le journal des erreurs SQL Server &#40;SQL Server Management Studio&#41;](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)  
  
-   [Ouvrir le Moniteur d’activité &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)  

-   [Surveillance des performances à l’aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)

## <a name="to-perform-monitoring-tasks-with-sql-trace-and-sql-server-profiler"></a>Pour effectuer des tâches de supervision avec Trace SQL et SQL Server Profiler

> [!IMPORTANT]
> Les sections suivantes décrivent les méthodes d’utilisation de Trace SQL et [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
> Trace SQL et [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] sont dépréciés. L’espace de noms *Microsoft.SqlServer.Management.Trace* qui contient les objets Trace et Replay Microsoft SQL Server est également déconseillé.   
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
> Utilisez plutôt des événements étendus. Pour plus d’informations sur les [événements étendus](../../relational-databases/extended-events/extended-events.md), consultez [Démarrage rapide : Événements étendus dans SQL Server](../../relational-databases/extended-events/quick-start-extended-events-in-sql-server.md) et [SSMS XEvent Profiler](../../relational-databases/extended-events/use-the-ssms-xe-profiler.md).

> [!NOTE] 
> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour les charges de travail Analysis Services n’est PAS déprécié et continuera à être pris en charge.

### <a name="to-perform-monitoring-tasks-with-sql-trace-by-using-transact-sql-stored-procedures"></a>Pour effectuer une analyse des tâches à l'aide de Trace SQL en utilisant des procédures stockées écrites en Transact-SQL  
  
-   [Créer une trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)  
  
-   [Définir un filtre de trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/set-a-trace-filter-transact-sql.md)  
  
-   [Modifier une trace existante &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
-   [Afficher une trace enregistrée &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md)  
  
-   [Afficher des informations de filtrage &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md)  
  
-   [Supprimer une trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/delete-a-trace-transact-sql.md)  
  
### <a name="to-create-and-modify-traces-by-using-sql-server-profiler"></a>Pour créer et modifier des traces à l'aide du Générateur de profils SQL Server  
  
-   [Créer une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
-   [Définir les options globales de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)  
  
-   [Spécifier les événements et les colonnes de données d’un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
-   [Créer un script Transact-SQL pour exécuter une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)  
  
-   [Enregistrer des résultats d’une trace dans un fichier &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
-   [Définir la taille maximale d’un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
-   [Enregistrer des résultats d’une trace dans une table &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
-   [Définir la taille maximale d’une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
-   [Filtrer des événements dans une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
-   [Afficher des informations de filtre &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)  
  
-   [Modifier un filtre &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
-   [Filtrer des événements en fonction de leur heure de début &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)  
  
-   [Filtrer des événements en fonction de leur heure de fin &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
-   [Filtrer des ID du processus serveur &#40;SPID&#41; dans une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)  
  
-   [Organiser les colonnes affichées dans une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)  
  
### <a name="to-start-pause-and-stop-traces-by-using-sql-server-profiler"></a>Pour démarrer, suspendre et arrêter des traces à l'aide du Générateur de profils SQL Server  
  
-   [Démarrer automatiquement une trace après s’être connecté à un serveur &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)  
  
-   [Suspendre une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)  
  
-   [Arrêter une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)  
  
-   [Exécuter une trace après qu’elle a été suspendue ou arrêtée &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
### <a name="to-open-traces-and-configure-how-traces-are-displayed-by-using-sql-server-profiler"></a>Pour ouvrir des traces et configurer la façon dont elles sont affichées à l'aide du Générateur de profils SQL Server  
  
-   [Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)  
  
-   [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
-   [Effacer une fenêtre de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)  
  
-   [Fermer une fenêtre de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)  
  
-   [Définir les valeurs par défaut des définitions de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
-   [Définir les valeurs par défaut de l’affichage des traces &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
### <a name="to-replay-traces-by-using-sql-server-profiler"></a>Pour rejouer des traces à l'aide du Générateur de profils SQL Server  
  
-   [Relire un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)  
  
-   [Relire une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)  
  
-   [Relire un seul événement à la fois &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)  
  
-   [Relire jusqu’à un point d’arrêt &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)  
  
-   [Relire jusqu’à un curseur &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)  
  
-   [Relire un script Transact-SQL &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)  
  
### <a name="to-create-modify-and-use-trace-templates-by-using-sql-server-profiler"></a>Pour créer, modifier et utiliser des modèles de traces à l'aide du Générateur de profils SQL Server  
  
-   [Créer un modèle de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
-   [Modifier un modèle de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/modify-trace-templates.md)  
  
-   [Dériver un modèle à partir d’une trace en cours d’exécution &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)  
  
-   [Dériver un modèle à partir d’un fichier de trace ou d’une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)  
  
-   [Exporter un modèle de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)  
  
-   [Importer un modèle de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)  
  
### <a name="to-use-sql-server-profiler-traces-to-collect-and-monitor-server-performance"></a>Pour utiliser les traces du Générateur de profils SQL Server afin de collecter et de surveiller les performances du serveur  
  
-   [Retrouver une valeur ou une colonne de données au cours de l’exécution d’une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)  
  
-   [Enregistrer les événements Deadlock Graph &#40;SQL Server Profiler&#41;](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
-   [Enregistrer séparément des événements Showplan XML &#40;SQL Server Profiler&#41;](../../relational-databases/performance/save-showplan-xml-events-separately-sql-server-profiler.md)  
  
-   [Enregistrer les événements Showplan XML Statistics Profile séparément &#40;SQL Server Profiler&#41;](../../relational-databases/performance/save-showplan-xml-statistics-profile-events-separately-sql-server-profiler.md)  
  
-   [Extraire un script d’une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)  
  
-   [Corréler une trace aux données du journal de performances Windows &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
