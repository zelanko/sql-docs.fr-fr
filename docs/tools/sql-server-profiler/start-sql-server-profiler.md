---
title: "Exécuter SQL Server Profiler | Documents Microsoft"
ms.custom: 
ms.date: 7/7/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
- Profiler [SQL Server Profiler], running
- SQL Server Profiler, running
- running SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7b875fa70017ce162ca50aa7d6d0235627d2f5f8
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="run-sql-server-profiler"></a>Exécuter SQL Server Profiler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Vous pouvez exécuter [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] de plusieurs façons différentes, pour prendre en charge de la trace de la collecte de sortie dans une variété de scénarios. Vous pouvez démarrer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] de Windows 10 **Démarrer** menu, à partir de la **outils** menu [!INCLUDE[ssDE](../../includes/ssde-md.md)] paramétrage et à partir de plusieurs emplacements dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Lorsque vous démarrez pour la première fois [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et sélectionnez **nouvelle Trace** à partir de la **fichier** menu, l’application affiche un **se connecter au serveur** boîte de dialogue dans laquelle vous pouvez spécifier un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance pour se connecter à.  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>Pour démarrer le Générateur de profils SQL Server à partir du menu Démarrer de Windows 10  
-  Cliquez sur les fenêtres **Démarrer** ou appuyez sur les fenêtres de clé et commencent à taper « SQL Server Profiler 17 ». Lorsque le **SQL Server Profiler 17** vignette s’affiche, cliquez dessus.   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>Pour démarrer le Générateur de profils SQL Server dans l'Assistant Paramétrage du moteur de base de données  
-  Dans le menu [!INCLUDE[ssDE](../../includes/ssde-md.md)] Outils **de l’Assistant Paramétrage du** , cliquez sur **SQL Server Profiler**.  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>Pour démarrer le Générateur de profils SQL Server dans SQL Server Management Studio  
 Vous pouvez démarrer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] depuis plusieurs emplacements dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Lorsque [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] démarre, il charge le contexte de connexion, le modèle de trace et le contexte de filtre de son point de lancement. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]démarre chaque session de SQL Server Profiler dans sa propre instance et Profiler continue de s’exécuter si vous arrêtez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>Pour démarrer le Générateur de profils SQL Server à partir du menu Outils  
-  Dans le menu [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **SQL Server Profiler**.  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>Pour démarrer le Générateur de profils SQL Server à partir de l’Éditeur de requête  
- Dans l’Éditeur de requête, cliquez avec le bouton droit, puis sélectionnez **Requête de trace dans SQL Server Profiler**.  

  > [!NOTE]  
  >  Le contexte de connexion est la connexion d'éditeur, le modèle de trace est TSQL_SPs, et le filtre appliqué est SPID = SPID de la fenêtre de requête.  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>Pour démarrer le Générateur de profils SQL Server à partir du moniteur d'activité  
- Dans le moniteur d’activité, cliquez sur le **processus** volet, cliquez sur le processus que vous souhaitez profiler, puis cliquez sur **processus de Trace dans le Générateur de profils SQL Server**.  

    > [!NOTE]  
    >  Lorsqu'un processus est sélectionné, le contexte de connexion correspond à la connexion de l'Explorateur d'objets à l'ouverture du moniteur d'activité. Le modèle de trace correspond à la valeur par défaut selon le type de serveur et le SPID est égal au SPID du processus sélectionné.  
    
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
- En mode d’authentification Windows, le compte d’utilisateur qui exécute [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] doit avoir l’autorisation de se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
- Pour effectuer une opération de traçage à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], les utilisateurs doivent également avoir l'autorisation ALTER TRACE.  

## <a name="next-steps"></a>Étapes suivantes  
 [Vue d’ensemble de SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Utiliser SQL Server Management Studio](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  
