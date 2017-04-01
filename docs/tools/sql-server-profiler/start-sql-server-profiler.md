---
title: "D&#233;marrer SQL Server Profiler | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profileur [SQL Server Profiler], démarrage"
  - "SQL Server Profiler, démarrage"
  - "démarrage du Générateur de profils SQL Server"
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# D&#233;marrer SQL Server Profiler
  Il existe différentes méthodes pour démarrer le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] afin de prendre en charge la collecte des sorties de trace dans divers scénarios. Vous pouvez démarrer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] à partir du menu **Démarrer**, du menu **Outils** dans l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] ou à partir de plusieurs autres emplacements dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Quand vous démarrez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour la première fois et que vous sélectionnez **Nouvelle trace** dans le menu **Fichier**, l’application affiche la boîte de dialogue **Se connecter au serveur** dans laquelle vous pouvez spécifier l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous souhaitez vous connecter.  
  
### Pour démarrer le Générateur de profils SQL Server à partir du menu Démarrer  
  
1.  Dans le menu **Démarrer**, pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de performances**, puis cliquez sur **SQL Server Profiler**.  
  
### Pour démarrer le Générateur de profils SQL Server dans l'Assistant Paramétrage du moteur de base de données  
  
1.  Dans le menu **Outils** de l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)], cliquez sur **SQL Server Profiler**.  
  
## Démarrage du Générateur de profils SQL Server dans Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] démarre chaque session de SQL Server Profiler dans sa propre instance et poursuit son exécution si vous arrêtez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Vous pouvez démarrer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] à partir de plusieurs emplacements dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], comme illustré dans les procédures suivantes. Lorsque [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] démarre, il charge le contexte de connexion, le modèle de trace et le contexte du filtre de son point de lancement.  
  
#### Pour démarrer le Générateur de profils SQL Server à partir du menu Outils  
  
1.  Dans le menu **Outils** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur **SQL Server Profiler**.  
  
#### Pour démarrer le Générateur de profils SQL Server à partir de l’Éditeur de requête  
  
1.  Dans la barre de menus de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur **Nouvelle requête**.  
  
2.  Dans l’Éditeur de requête, cliquez avec le bouton droit, puis sélectionnez **Requête de trace dans SQL Server Profiler**.  
  
    > [!NOTE]  
    >  Le contexte de connexion est la connexion d'éditeur, le modèle de trace est TSQL_SPs, et le filtre appliqué est SPID = SPID de la fenêtre de requête.  
  
#### Pour démarrer le Générateur de profils SQL Server à partir du moniteur d'activité  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis cliquez sur **Moniteur d’activité**.  
  
2.  Cliquez sur le volet **Processus**, cliquez avec le bouton droit sur le processus à profiler, puis cliquez sur **Processus de trace dans SQL Server Profiler**.  
  
    > [!NOTE]  
    >  Lorsqu'un processus est sélectionné, le contexte de connexion correspond à la connexion de l'Explorateur d'objets à l'ouverture du moniteur d'activité. Le modèle de trace correspond à la valeur par défaut selon le type de serveur et le SPID est égal au SPID du processus sélectionné.  
  
## Sécurité du .NET Framework  
 Avec le mode d'authentification Windows, le compte d'utilisateur utilisé pour exécuter le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] doit avoir l'autorisation de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour effectuer une opération de traçage à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], les utilisateurs doivent également avoir l'autorisation ALTER TRACE.  
  
## Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Utiliser SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
  
  