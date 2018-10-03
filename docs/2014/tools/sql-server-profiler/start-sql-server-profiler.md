---
title: Démarrer SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d8d306be84e1c039122a462fdfa8b298bb451c1f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084719"
---
# <a name="start-sql-server-profiler"></a>Démarrer SQL Server Profiler
  Il existe différentes méthodes pour démarrer le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] afin de prendre en charge la collecte des sorties de trace dans divers scénarios. Vous pouvez démarrer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] à partir du menu **Démarrer** , du menu **Outils** dans l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] ou à partir de plusieurs autres emplacements dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Quand vous démarrez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour la première fois et que vous sélectionnez **Nouvelle trace** dans le menu **Fichier** , l’application affiche la boîte de dialogue **Se connecter au serveur** dans laquelle vous pouvez spécifier l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous souhaitez vous connecter.  
  
### <a name="to-start-sql-server-profiler-from-the-start-menu"></a>Pour démarrer le Générateur de profils SQL Server à partir du menu Démarrer  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de performances**, puis cliquez sur **SQL Server Profiler**.  
  
### <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>Pour démarrer le Générateur de profils SQL Server dans l'Assistant Paramétrage du moteur de base de données  
  
1.  Dans le menu [!INCLUDE[ssDE](../../includes/ssde-md.md)] Outils **de l’Assistant Paramétrage du** , cliquez sur **SQL Server Profiler**.  
  
## <a name="starting-sql-server-profiler-in-management-studio"></a>Démarrage du Générateur de profils SQL Server dans Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] démarre chaque session de SQL Server Profiler dans sa propre instance et poursuit son exécution si vous arrêtez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Vous pouvez démarrer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] à partir de plusieurs emplacements dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], comme illustré dans les procédures suivantes. Lorsque [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] démarre, il charge le contexte de connexion, le modèle de trace et le contexte du filtre de son point de lancement.  
  
#### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>Pour démarrer le Générateur de profils SQL Server à partir du menu Outils  
  
1.  Dans le menu [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **SQL Server Profiler**.  
  
#### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>Pour démarrer le Générateur de profils SQL Server à partir de l’Éditeur de requête  
  
1.  Dans la barre de menus de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , cliquez sur **Nouvelle requête**.  
  
2.  Dans l’Éditeur de requête, cliquez avec le bouton droit, puis sélectionnez **Requête de trace dans SQL Server Profiler**.  
  
    > [!NOTE]  
    >  Le contexte de connexion est la connexion d'éditeur, le modèle de trace est TSQL_SPs, et le filtre appliqué est SPID = SPID de la fenêtre de requête.  
  
#### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>Pour démarrer le Générateur de profils SQL Server à partir du moniteur d'activité  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis cliquez sur **Moniteur d’activité**.  
  
2.  Cliquez sur le volet **Processus** , cliquez avec le bouton droit sur le processus à profiler, puis cliquez sur **Processus de trace dans SQL Server Profiler**.  
  
    > [!NOTE]  
    >  Lorsqu'un processus est sélectionné, le contexte de connexion correspond à la connexion de l'Explorateur d'objets à l'ouverture du moniteur d'activité. Le modèle de trace correspond à la valeur par défaut selon le type de serveur et le SPID est égal au SPID du processus sélectionné.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Avec le mode d'authentification Windows, le compte d'utilisateur utilisé pour exécuter le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] doit avoir l'autorisation de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour effectuer une opération de traçage à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], les utilisateurs doivent également avoir l'autorisation ALTER TRACE.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)   
 [Utiliser SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)  
  
  
