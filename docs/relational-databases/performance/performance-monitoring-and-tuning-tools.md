---
title: Outils d’analyse et de paramétrage des performances | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tools [SQL Server], monitoring performance
- monitoring server performance [SQL Server], tools
- monitoring performance [SQL Server], tools
- database performance [SQL Server], tools
- tuning databases [SQL Server], tools
- database monitoring [SQL Server], tools
- performance [SQL Server], monitoring tools
- server performance [SQL Server], tools
ms.assetid: 31529dfe-68e7-49f7-b3c2-39fcecf33a95
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 91a1c007add2810588f7b41499c046336d5bc322
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371481"
---
# <a name="performance-monitoring-and-tuning-tools"></a>Outils d'analyse et de paramétrage des performances
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un ensemble complet d'outils permettant de surveiller les événements de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de paramétrer la structure physique de la base de données. Le choix de l'outil dépend du type de surveillance ou de paramétrage à effectuer et des événements spécifiques à contrôler.  
  
 Les outils de surveillance et de paramétrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivants :  
  
|Outil|Description|  
|----------|-----------------|  
|[Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)|Les fonctions intégrées affichent des statistiques d'instantané sur l'activité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depuis le démarrage du serveur ; ces statistiques sont stockées dans des compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prédéfinis. Par exemple, **@@CPU_BUSY** indique pendant combien de temps l’UC a exécuté du code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; **@@CONNECTIONS** indique le nombre de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de tentatives de connexion ; enfin, **@@PACKET_ERRORS** indique le nombre de paquets réseau sur des connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)|Les instructions DBCC (Database Console Command) vous permettent de contrôler les statistiques de performances et la cohérence logique et physique d'une base de données.|  
|[Assistant Paramétrage du moteur de base de données (DTA)](../../relational-databases/performance/database-engine-tuning-advisor.md)|L'Assistant de Paramétrage du moteur de base de données analyse les effets des performances des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutées sur des bases de données à paramétrer. Il fournit des recommandations pour ajouter, supprimer ou modifier des index, des vues indexées et un partitionnement.|  
|[Assistant Expérimentation de base de données (DEA)](https://www.microsoft.com/download/details.aspx?id=54090)|L’Assistant Expérimentation de base de données (DEA) est une nouvelle solution de test A/B pour SQL Server. Elle vous aidera à évaluer une version ciblée du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] pour une charge de travail donnée. Lors de la mise à niveau à partir d’une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]) vers une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], DEA sera en mesure de fournir des métriques d’analyse comparative.|
|Journaux des erreurs|Le journal des événements des applications Windows fournit une image complète des événements survenant sur les systèmes d'exploitation Windows Server et Windows dans leur ensemble, ainsi que des événements survenant dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dans l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et dans la recherche en texte intégral. Il contient des informations exclusives sur les événements qui se produisent dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez utiliser les informations du journal des erreurs pour résoudre des problèmes liés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Événements étendus](../../relational-databases/extended-events/extended-events.md)|Les événements étendus sont un système léger d'analyse des performances qui utilise très peu de ressources de performances. Les événements étendus fournissent trois interfaces utilisateur graphiques (Assistant Nouvelle session, Nouvelle session et XE Profiler) permettant de créer, de modifier, d’afficher et d’analyser vos données de session.|  
|[Fonctions et vues de gestion dynamique relatives aux exécutions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)|Les vues de gestion dynamique relatives à l’exécution vous permettent de vérifier les informations liées à l’exécution.|
|[Statistiques des requêtes actives](../../relational-databases/performance/live-query-statistics.md)|Affiche les statistiques en temps réel sur les étapes d’exécution des requêtes. Puisque ces données sont accessibles pendant l’exécution des requêtes, ces statistiques d’exécution sont extrêmement utiles pour résoudre les problèmes de performances de requêtes.|  
|[Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)|Le Moniteur système surveille principalement l'utilisation des ressources, notamment le nombre de demandes de pages en cours au gestionnaire de tampons, ce qui vous permet de contrôler les performances et l'activité du serveur à l'aide d'objets et de compteurs prédéfinis, ou de compteurs définis par l'utilisateur pour surveiller les événements. Le Moniteur système (l’Analyseur de performances dans Microsoft Windows NT 4.0) recueille le nombre et le taux et non pas les données concernant les événements (par exemple, l'utilisation de la mémoire, le nombre de transactions actives, le nombre de verrous bloqués, ou l'activité de l'UC). Vous pouvez définir des seuils pour des compteurs spécifiques de manière à générer des alertes pour avertir les opérateurs.<br /><br /> Le Moniteur système fonctionne sur les systèmes d'exploitation Microsoft Windows Server et Windows. Il peut surveiller (à distance ou localement) une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows NT 4.0 ou version ultérieure.<br /><br /> La différence essentielle entre le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et le Moniteur système, est que le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] surveille les événements du moteur de base de données, tandis que le Moniteur système surveille l'utilisation des ressources associées aux processus du serveur.|  
|[Ouvrir le Moniteur d’activité &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|Le Moniteur d’activité dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est utile pour les vues ad hoc de l’activité en cours et affiche graphiquement des informations sur :<br /><br /> les processus s'exécutant dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];<br /><br /> les processus bloqués ;<br /><br /> les verrous ;<br /><br /> l'activité utilisateur.|  
|[Assistant Paramétrage de requêtes](../../relational-databases/performance/upgrade-dbcompat-using-qta.md)|La fonctionnalité Assistant Paramétrage de requêtes guide les utilisateurs tout le long du flux de travail recommandé pour maintenir la stabilité des performances pendant les mises à niveau vers des versions plus récentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme décrit dans la section *Maintenir la stabilité des performances lors de la mise à niveau vers une version plus récente de SQL Server* de [Scénarios d’utilisation du Magasin des requêtes](../../relational-databases/performance/query-store-usage-scenarios.md#CEUpgrade). |  
|[Magasin de requêtes](../..//relational-databases/performance/monitoring-performance-by-using-the-query-store.md)|La fonctionnalité Magasin des requêtes fournit des informations sur le choix de plan de requête et sur les performances. Elle simplifie la résolution des problèmes de performances en vous permettant de trouver rapidement les différences de performances provoquées par des changements de plan de requête. Le magasin de requête capture automatiquement l'historique des requêtes, des plans et des statistiques d'exécution et les conserve à des fins de révision. Elle sépare les données en périodes, ce qui vous permet de voir les modèles d'utilisation de base de données et de comprendre à quel moment les changements de plan de requête ont eu lieu sur le serveur.|
|[Trace SQL](../../relational-databases/sql-trace/sql-trace.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] qui créent, filtrent et définissent la trace :<br /><br /> [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)<br /><br /> [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)<br /><br /> [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)<br /><br /> [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)<br /><br /> [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)|  
|[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay peut utiliser plusieurs ordinateurs pour relire les données de trace, en simulant mieux les charges de travail sensibles.|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] assure le suivi des événements de processus du moteur, notamment le début d’un lot ou d’une transaction, ce qui vous permet de surveiller l’activité du serveur et de la base de données (par exemple les blocages, les erreurs irrécupérables ou les connexions). Vous pouvez capturer les données du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] dans une table ou un fichier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en vue d'une analyse ultérieure, et relire les événements capturés sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , pas à pas, pour savoir ce qui s'est passé exactement.|  
|[Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)|Les procédures stockées système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ci-après fournissent une puissante alternative à de nombreuses tâches de surveillance :<br /><br /> [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md):<br />                    Renvoie des informations d'instantané sur les utilisateurs et les processus actifs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], y compris l'exécution de l'instruction active et si l'instruction est bloquée.<br /><br /> [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md):<br />                    Renvoie des informations d'instantané sur les verrous, y compris l'ID de l'objet, l'ID d'index, le type de verrou et le type de ressource auquel s'applique le verrou.<br /><br /> [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md): <br />                    Affiche une estimation de l'espace disque actuellement utilisé par une table (ou une base de données entière).<br /><br /> [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md):<br />                    Affiche des statistiques, notamment l’utilisation de l’UC, l’utilisation des E/S et la durée d’inactivité depuis la dernière exécution de **sp_monitor** .|  
|[Indicateurs de trace &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)|Les indicateurs de trace affichent des informations sur une activité spécifique sur le serveur ; ils permettent de diagnostiquer les problèmes ou les causes agissant sur les performances (par exemple, chaînes de blocage).|  
  
## <a name="choosing-a-monitoring-tool"></a>Choix d'un outil de surveillance  
 Le choix d'un outil de surveillance dépend de l'événement ou de l'activité à surveiller.  
  
|Événement ou activité|Événements étendus|SQL Server Profiler|Distributed Replay|Moniteur système|Moniteur d'activité|Transact-SQL|Journaux des erreurs|  
|-----------------------|-----------------------|-------------------------|------------------------|--------------------|----------------------|-------------------|----------------|  
|Analyse de tendance|Oui|Oui||Oui||||  
|Relecture des événements capturés||Oui (depuis un ordinateur unique)|Oui (depuis plusieurs ordinateurs)|||||  
|Surveillance ad hoc|Oui<sup>1</sup>|Oui|||Oui|Oui|Oui|  
|Génération d'alertes||||Oui||||  
|Interface graphique|Oui|Oui||Oui|Oui||Oui|  
|Utilisation dans une application personnalisée|Oui|Oui<sup>2</sup>||||Oui||  
  
 <sup>1</sup> Utilisation de [SQL Server Management Studio XEvent Profiler](../../relational-databases/extended-events/use-the-ssms-xe-profiler.md)    
 <sup>2</sup> Utilisation des procédures stockées système [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
## <a name="windows-monitoring-tools"></a>Outils de surveillance Windows  
 Les systèmes d'exploitation Windows et Windows Server 2003 proposent également les outils de surveillance suivants.  
  
|Outil|Description|  
|----------|-----------------|  
|Gestionnaire des tâches|Affiche un résumé des processus et des applications en cours d'exécution sur le système.|  
|Agent de surveillance du réseau|Surveille le trafic réseau.|  
  
 Pour plus d'informations sur les outils des systèmes d'exploitation Windows ou Windows Server, consultez la documentation Windows.  
  
  
