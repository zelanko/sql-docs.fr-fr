---
title: SHUTDOWN (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHUTDOWN_TSQL
- SHUTDOWN
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server, stopping
- shutting down SQL Server
- SHUTDOWN statement
- stopping SQL Server
- immediately stopping SQL Server
ms.assetid: c8b03ff9-688c-4fe8-86e8-bd6bd401c9a4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: df8ef0a3cfe0ac4adb6f45bddb0bef650fea6ff3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="shutdown-transact-sql"></a>SHUTDOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL Server s’arrête immédiatement.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SHUTDOWN [ WITH NOWAIT ]   
```  
  
## <a name="arguments"></a>Arguments  
 WITH NOWAIT  
 Ce paramètre est facultatif. Arrête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans générer de points de contrôle dans chaque base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'arrête après avoir essayé de mettre un terme à tous les processus utilisateurs. Lorsque le serveur redémarre, il annule et restaure à l'état initial toutes les transactions incomplètes.  
  
## <a name="remarks"></a>Notes  
 Sauf si l’option WITHNOWAIT est utilisée, SHUTDOWN arrête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par :  
  
1.  Désactive les connexions (sauf pour les membres de la **sysadmin** et **serveradmin** rôles serveur fixes).  
  
    > [!NOTE]  
    >  Pour afficher une liste de tous les utilisateurs actuels, exécutez **sp_who**.  
  
2.  Attend que les instructions Transact-SQL ou les procédures stockées en cours d'exécution s'achèvent. Pour afficher une liste de tous les processus et verrous actifs, exécutez **sp_who** et **sp_lock**, respectivement.  
  
3.  Insert un point de contrôle dans chaque base de données.  
  
 À l’aide de l’instruction SHUTDOWN minimise le de la récupération automatique travail exigé lorsque les membres de la **sysadmin** fixe de redémarrage du rôle serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les outils et méthodes suivants peuvent également être utilisés pour arrêter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chacun d'entre eux génère un point de contrôle dans toutes les bases de données. Vous pouvez vider les données validées du cache de données et arrêter le serveur :  
  
-   à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   En exécutant **net stop mssqlserver** à partir d’une invite de commandes pour une instance par défaut, ou en exécutant **net stop mssql$ *** instancename* à partir d’une invite de commandes pour une instance nommée.  
  
-   à l'aide des Services du Panneau de configuration ;  
  
 Si **sqlservr.exe** a été démarré à partir de l’invite de commandes, appuyez sur CTRL + C pour arrêter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sachez toutefois que Ctrl+C ne génère pas de point de contrôle.  
  
> [!NOTE]  
>  Quelle que soit la méthode utilisée pour arrêter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le message `SERVICE_CONTROL_STOP` est envoyé à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Autorisations  
 Autorisations SHUTDOWN sont attribuées aux membres de la **sysadmin** et **serveradmin** rôles serveur fixes et ils ne sont pas transférables.  
  
## <a name="see-also"></a>Voir aussi  
 [Point de contrôle &#40; Transact-SQL &#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Application sqlservr](../../tools/sqlservr-application.md)   
 [Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
