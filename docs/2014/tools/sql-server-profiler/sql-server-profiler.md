---
title: Le Générateur de profils SQL Server | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- traces [SQL Server], SQL Server Profiler
- database monitoring [SQL Server], SQL Server Profiler
- tuning databases [SQL Server], SQL Server Profiler
- SQL Server Profiler
- server performance [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler]
- tracing [SQL Server]
- monitoring performance [SQL Server], SQL Server Profiler
- events [SQL Server], SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
- tools [SQL Server], SQL Server Profiler
- database performance [SQL Server], SQL Server Profiler
- trace [SQL Server]
ms.assetid: 3ad5f33d-559e-41a4-bde6-bb98792f7f1a
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3ea44d8b04cb576662eb2145cb4dc9551a122978
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153169"
---
# <a name="sql-server-profiler"></a>SQL Server Profiler
  Le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] est une interface puissante qui permet de créer et gérer des traces ainsi que d'analyser et relire les résultats de trace. Ces événements sont enregistrés dans un fichier de trace qui peut être analysé ou utilisé ultérieurement pour relire une série d'étapes spécifique lors d'une tentative de diagnostic d'un problème.  
  
> [!IMPORTANT]  
>  Nous annonçons l'abandon du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour la capture de trace et la relecture de trace du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Ces fonctions seront prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais seront supprimées dans une version ultérieure. La version spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas été déterminée. L'espace de noms *Microsoft.SqlServer.Management.Trace* qui contient les objets Trace et Replay Microsoft SQL Server sera également déconseillé. Notez que le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour les charges de travail Analysis Services n'est pas déconseillé, et continuera à être pris en charge.  
>   
>  Le tableau suivant indique les fonctionnalités que nous vous recommandons d'utiliser dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour capturer et relire les données de trace :  
  
||||  
|-|-|-|  
|**Fonctionnalité/Charge de travail cible**|**Moteur relationnel**|**Analysis Services**|  
|**Capture de trace**|Interface utilisateur graphique des événements étendus dans SQL Server Management Studio|SQL Server Profiler|  
|**Relecture de trace**|Distributed Replay|SQL Server Profiler|  
  
## <a name="benefits-of-sql-server-profiler"></a>Avantages du Générateur de profils SQL Server  
 Le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] est une interface utilisateur graphique de Trace SQL qui permet de surveiller une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] ou Analysis Services. Vous pouvez capturer et enregistrer des données sur chaque événement dans un fichier ou dans une table en vue d'une analyse ultérieure. Par exemple, vous pouvez surveiller un environnement de production pour savoir quelles sont les procédures stockées qui affectent les performances en s'exécutant trop lentement. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] est utilisé pour des activités telles que :  
  
-   Exécuter pas à pas des requêtes posant problème afin d'en déterminer la cause.  
  
-   Détecter les requêtes s'exécutant lentement et diagnostiquer la cause du problème.  
  
-   Capturer la série d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] conduisant à un problème. La trace enregistrée peut ensuite être utilisée pour répliquer le problème sur un serveur test à partir duquel il est possible de diagnostiquer sa cause.  
  
-   Surveiller les performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en vue de paramétrer les charges de travail. Pour plus d'informations sur le paramétrage de la conception d'une base de données physique pour les charges de travail de base de données, consultez [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).  
  
-   Mise en corrélation des compteurs de performances pour diagnostiquer des problèmes.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] prend également en charge l'audit des actions exécutées sur des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les audits enregistrent les actions relatives à la sécurité en vue de leur examen ultérieur par l'administrateur de la sécurité.  
  
## <a name="sql-server-profiler-concepts"></a>Concepts du Générateur de profils SQL Server  
 Pour utiliser le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], vous devez comprendre les termes qui décrivent le fonctionnement de l'outil.  
  
> [!NOTE]  
>  Pour utiliser [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], il est préférable de bien comprendre Trace SQL. Pour en savoir plus, voir [SQL Trace](../../relational-databases/sql-trace/sql-trace.md).  
  
 **Événement**  
 Un événement est une action générée dans une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. En voici quelques exemples :  
  
-   connexions d'accès, échecs et déconnexions ;  
  
-   instructions Transact-SQL SELECT, INSERT, UPDATE et DELETE ;  
  
-   état du traitement d'appel de procédure distante (RPC) ;  
  
-   le lancement ou la fin d'une procédure stockée ;  
  
-   le lancement ou la fin d'instructions à l'intérieur de procédures stockées ;  
  
-   le lancement ou la fin d'un traitement SQL ;  
  
-   une erreur consignée dans le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   un verrou placé ou libéré sur un objet de la base de données ;  
  
-   un curseur ouvert ;  
  
-   vérifications des autorisations de sécurité.  
  
 Toutes les données générées par un événement sont affichées dans une même ligne de la trace. Cette ligne est composée de champs de colonnes de données qui décrivent l'événement en détail.  
  
 **EventClass**  
 Une classe d'événements est un type d'événement qui peut être tracé. La classe d'événements contient toutes les données qui peuvent être signalées par un événement. Voici quelques exemples de classes d'événements :  
  
-   **SQL:BatchCompleted**  
  
-   **Audit Login**  
  
-   **Audit Logout**  
  
-   **Lock:Acquired**  
  
-   **Lock:Released**  
  
 **EventCategory**  
 Une catégorie d'événements définit la façon dont les événements sont regroupés dans le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Par exemple, toutes les classes d'événements de verrou sont regroupées à l'intérieur de la catégorie d'événements **Verrous** . Toutefois, les catégories d'événements n'existent que dans le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Ce terme ne recouvre pas la façon dont les événements du moteur sont regroupés.  
  
 **DataColumn**  
 Une colonne de données est un attribut d'une classe d'événements capturée dans la trace. Chaque classe d'événements détermine le type des données qui peuvent être recueillies. C'est pourquoi les colonnes de données ne s'appliquent pas toutes à toutes les classes d'événements. Par exemple, dans une trace qui capture la classe d'événements **Lock:Acquired** , la colonne de données **BinaryData** contient la valeur de l'ID de la page verrouillée ou de la ligne, mais la colonne de données **Integer Data** ne contient aucune valeur car elle n'est pas applicable à la classe d'événements qui fait l'objet d'une capture.  
  
 **Modèle**  
 Un modèle définit la configuration par défaut d'une trace. Il comprend notamment les classes d'événements à surveiller avec le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Par exemple, vous pouvez créer un modèle spécifiant les événements, les colonnes de données et les filtres à utiliser. Un modèle n'est pas exécuté ; il est enregistré sous la forme d'un fichier portant l'extension .tdf. Une fois enregistré, le modèle contrôle les données de trace capturées à l'exécution d'une trace basée sur celui-ci.  
  
 **Trace**  
 Une trace capture des données en fonction de classes d'événements, de colonnes de données et de filtres spécifiques. Par exemple, vous pouvez créer un modèle pour tracer les erreurs d’exception. Pour ce faire, vous sélectionnez la classe d'événements **Exception** et les colonnes de données **Error**, **State**et **Severity** . Les données de ces trois colonnes doivent être récupérées afin que les résultats de trace fournissent des données significatives. Vous pouvez ensuite exécuter une trace configurée de la sorte, et collecter les données de tout événement **Exception** se produisant dans le serveur. Les données de trace peuvent être enregistrées ou utilisées immédiatement pour une analyse. Les traces peuvent être relues ultérieurement, bien que certains événements, tels que **Exception** , ne soient jamais relus. Vous pouvez également enregistrer la trace en tant que modèle en vue de créer plus tard des traces similaires.  
  
 SQL Server vous permet de tracer une instance SQL Server de deux façons : à l'aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], ou de procédures stockées système.  
  
 **Filter**  
 Lorsque vous créez une trace ou un modèle, vous pouvez définir des critères pour filtrer les données récupérées par l'événement. Pour éviter que les traces ne deviennent trop volumineuses, vous pouvez les filtrer de manière à ce que seul un sous-ensemble des données d'événement soit recueilli. Par exemple, vous pouvez limiter les noms d'utilisateurs Microsoft Windows contenus dans la trace à des utilisateurs spécifiques pour réduire les données de sortie.  
  
 Si aucun filtre n'est défini, tous les événements des classes d'événements sélectionnées sont retournés dans le résultat de trace.  
  
## <a name="sql-server-profiler-tasks"></a>Tâches du Générateur de profils SQL Server  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Répertorie les modèles prédéfinis que SQL Server fournit pour surveiller certains types d'événements, et les autorisations requises à utiliser pour relire les traces.|[Modèles et autorisations SQL Server Profiler](sql-server-profiler-templates-and-permissions.md)|  
|Décrit comment exécuter le Générateur de profils SQL Server.|[Autorisations nécessaires pour exécuter SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md)|  
|Décrit comment créer une trace.|[Créer une trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)|  
|Décrit comment spécifier les événements et les colonnes de données d'un fichier de trace.|[Spécifier les événements et les colonnes de données d’un fichier de trace &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)|  
|Explique comment enregistrer les résultats de trace dans un fichier.|[Enregistrer des résultats d’une trace dans un fichier &#40;SQL Server Profiler&#41;](save-trace-results-to-a-file-sql-server-profiler.md)|  
|Explique comment enregistrer les résultats de trace dans une table.|[Enregistrer des résultats d’une trace dans une table &#40;SQL Server Profiler&#41;](save-trace-results-to-a-table-sql-server-profiler.md)|  
|Explique comment filtrer des événements dans une trace.|[Filtrer des événements dans une trace &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)|  
|Explique comment afficher les informations de filtre.|[Afficher des informations de filtre &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md)|  
|Explique comment modifier un filtre.|[Modifier un filtre &#40;SQL Server Profiler&#41;](modify-a-filter-sql-server-profiler.md)|  
|Explique comment définir la taille maximale d'un fichier de trace (Générateur de profils SQL Server).|[Définir la taille maximale d’un fichier de trace &#40;SQL Server Profiler&#41;](set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)|  
|Explique comment définir une taille maximale de table de trace.|[Définir la taille maximale d’une table de trace &#40;SQL Server Profiler&#41;](set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)|  
|Décrit comment démarrer une trace.|[Démarrer une trace](start-a-trace.md)|  
|Explique comment démarrer automatiquement une trace après s'être connecté à un serveur.|[Démarrer automatiquement une trace après s’être connecté à un serveur &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)|  
|Explique comment filtrer des événements en fonction de l'heure de début de l'événement.|[Filtrer des événements en fonction de leur heure de début &#40;SQL Server Profiler&#41;](filter-events-based-on-the-event-start-time-sql-server-profiler.md)|  
|Explique comment filtrer des événements en fonction de l'heure de fin de l'événement.|[Filtrer des événements en fonction de leur heure de fin &#40;SQL Server Profiler&#41;](filter-events-based-on-the-event-end-time-sql-server-profiler.md)|  
|Explique comment filtrer les identificateurs de processus serveur (SPID, Server Process ID) dans une trace.|[Filtrer des ID du processus serveur &#40;SPID&#41; dans une trace &#40;SQL Server Profiler&#41;](filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)|  
|Décrit comment suspendre une trace.|[Suspendre une trace &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md)|  
|Décrit comment arrêter une trace.|[Arrêter une trace &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md)|  
|Décrit comment exécuter une trace après son interruption ou son arrêt.|[Exécuter une trace après qu’elle a été suspendue ou arrêtée &#40;SQL Server Profiler&#41;](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)|  
|Décrit comment effacer une fenêtre de trace.|[Effacer une fenêtre de trace &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md)|  
|Décrit comment fermer une fenêtre de trace.|[Fermer une fenêtre de trace &#40;SQL Server Profiler&#41;](close-a-trace-window-sql-server-profiler.md)|  
|Décrit comment définir des paramètres par défaut de définition de trace.|[Définir les valeurs par défaut des définitions de trace &#40;SQL Server Profiler&#41;](set-trace-definition-defaults-sql-server-profiler.md)|  
|Décrit comment définir des valeurs par défaut d'affichage de trace.|[Définir les valeurs par défaut de l’affichage des traces &#40;SQL Server Profiler&#41;](set-trace-display-defaults-sql-server-profiler.md)|  
|Décrit comment ouvrir un fichier de trace.|[Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)|  
|Décrit comment ouvrir une table de trace.|[Ouvrir une table de trace &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)|  
|Décrit comment relire une table de trace.|[Relire une table de trace &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md)|  
|Décrit comment relire un fichier de trace.|[Relire un fichier de trace &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)|  
|Décrit comment relire un seul événement à la fois.|[Relire un seul événement à la fois &#40;SQL Server Profiler&#41;](replay-a-single-event-at-a-time-sql-server-profiler.md)|  
|Décrit comment relire jusqu'à un point d'arrêt.|[Relire jusqu’à un point d’arrêt &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md)|  
|Décrit comment relire jusqu'à un curseur.|[Relire jusqu’à un curseur &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md)|  
|Décrit comment relire un script Transact-SQL.|[Relire un script Transact-SQL &#40;SQL Server Profiler&#41;](replay-a-transact-sql-script-sql-server-profiler.md)|  
|Décrit comment créer un modèle de trace.|[Créer un modèle de trace &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md)|  
|Explique comment modifier un modèle de trace.|[Modifier un modèle de trace &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md)|  
|Explique comment définir les options globales de trace.|[Définir les options globales de trace &#40;SQL Server Profiler&#41;](set-global-trace-options-sql-server-profiler.md)|  
|Explique comment rechercher une valeur ou une colonne de données au cours de l'exécution d'une trace.|[Retrouver une valeur ou une colonne de données au cours de l’exécution d’une trace &#40;SQL Server Profiler&#41;](find-a-value-or-data-column-while-tracing-sql-server-profiler.md)|  
|Explique comment dériver un modèle d'une trace en cours d'exécution.|[Dériver un modèle à partir d’une trace en cours d’exécution &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md)|  
|Explique comment dériver un modèle d'un fichier de trace ou d'une table de trace.|[Dériver un modèle à partir d’un fichier de trace ou d’une table de trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)|  
|Explique comment créer un script Transact-SQL pour exécuter une trace.|[Créer un script Transact-SQL pour exécuter une trace &#40;SQL Server Profiler&#41;](create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)|  
|Décrit comment exporter un modèle de trace.|[Exporter un modèle de trace &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md)|  
|Décrit comment importer un modèle de trace.|[Importer un modèle de trace &#40;SQL Server Profiler&#41;](import-a-trace-template-sql-server-profiler.md)|  
|Décrit comment extraire un script d'une trace.|[Extraire un script d’une trace &#40;SQL Server Profiler&#41;](extract-a-script-from-a-trace-sql-server-profiler.md)|  
|Explique comment corréler une trace avec les données du journal de performances Windows.|[Corréler une trace aux données du journal de performances Windows &#40;SQL Server Profiler&#41;](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)|  
|Décrit comment organiser les colonnes affichées dans une trace.|[Organiser les colonnes affichées dans une trace &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md)|  
|Décrit comment démarrer le Générateur de profils SQL Server.|[Démarrer SQL Server Profiler](start-sql-server-profiler.md)|  
|Explique comment enregistrer les traces et les modèles de trace.|[Enregistrer des traces et de modèles de trace](save-traces-and-trace-templates.md)|  
|Explique comment modifier les modèles de trace.|[Modifier des modèles de trace](modify-trace-templates.md)|  
|Explique comment corréler une trace avec les données du journal de performances Windows.|[Mettre en corrélation une trace avec les données du journal de performances Windows](correlate-a-trace-with-windows-performance-log-data.md)|  
|Décrit comment afficher et analyser des traces avec le Générateur de profils SQL Server.|[Afficher et analyser des traces avec SQL Server Profiler](view-and-analyze-traces-with-sql-server-profiler.md)|  
|Décrit comment analyser des blocages avec le Générateur de profils SQL Server.|[Analyser des blocages à l'aide de SQL Server Profiler](analyze-deadlocks-with-sql-server-profiler.md)|  
|Décrit comment analyser des requêtes avec des résultats SHOWPLAN dans le Générateur de profils SQL Server.|[Analyser des requêtes avec des résultats SHOWPLAN dans SQL Server Profiler](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|  
|Décrit comment filtrer des traces avec le Générateur de profils SQL Server.|[Filtrer des traces avec SQL Server Profiler](filter-traces-with-sql-server-profiler.md)|  
|Décrit comment utiliser les fonctionnalités de relecture du Générateur de profils SQL Server.|[Relire des traces](replay-traces.md)|  
|Répertorie les rubriques d'aide contextuelle du Générateur de profils SQL Server.|[Aide (F1) du Générateur de profils SQL](sql-server-profiler-f1-help.md)|  
|Répertorie les procédures stockées système utilisées par le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour contrôler l'activité et les performances.|[Procédures stockées de SQL Server Profiler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)|  
  
## <a name="see-also"></a>Voir aussi  
 [Verrous, catégorie d’événement](../../relational-databases/event-classes/locks-event-category.md)   
 [Sessions, catégorie d’événement](../../relational-databases/event-classes/sessions-event-category.md)   
 [Procédures stockées, catégorie d’événement](../../relational-databases/event-classes/stored-procedures-event-category.md)   
 [TSQL, catégorie d’événement](../../relational-databases/event-classes/tsql-event-category.md)   
 [Analyse des performances et surveillance de l’activité du serveur](../../relational-databases/performance/server-performance-and-activity-monitoring.md)  
  
  
