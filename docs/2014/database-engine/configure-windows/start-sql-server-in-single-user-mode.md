---
title: Démarrer SQL Server en mode mono-utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server, single-user mode
- single-user mode [SQL Server]
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
caps.latest.revision: 35
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5ba40d074b8782d4a0a34bd3e8e91cc27609a02b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185266"
---
# <a name="start-sql-server-in-single-user-mode"></a>Démarrer SQL Server en mode mono-utilisateur
  Dans certaines circonstances, vous devrez peut-être démarrer une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur à l’aide de **startup option -m.** Vous pouvez par exemple vouloir modifier les options de configuration du serveur ou rétablir une base de données master ou une autre base de données système endommagées. Les deux actions requièrent le démarrage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur.  
  
 Le démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur permet à tout membre du groupe Administrateurs local de l'ordinateur de se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que membre du rôle serveur fixe sysadmin. Pour plus d’informations, consultez [Se connecter à SQL Server lorsque les administrateurs système n’y ont plus accès](connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 Lorsque vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur, notez les éléments suivants :  
  
-   Un seul utilisateur peut se connecter au serveur.  
  
-   Le processus CHECKPOINT n'est pas exécuté. Par défaut, il est exécuté automatiquement au démarrage.  
  
> [!NOTE]  
>  Arrêtez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent avant de vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur ; sinon, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent utilise cette connexion et, par conséquent, la bloque.  
  
 Lorsque vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] peut se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'exécution de l'Explorateur d'objets dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] peut échouer, car il requiert plusieurs connexions pour certaines opérations. Pour gérer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur, exécutez des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] en vous connectant uniquement via l’éditeur de requête dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ou utilisez l’ [utilitaire sqlcmd](../../tools/sqlcmd-utility.md).  
  
 Lorsque vous utilisez l’option **-m** avec **sqlcmd** ou [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], vous pouvez limiter les connexions à une application cliente spécifiée. Par exemple, **-m"sqlcmd"** limite les connexions à une connexion unique, laquelle doit s’identifier en tant que programme client **sqlcmd** . Utilisez cette option lorsque vous démarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur et qu'une application cliente inconnue utilise la seule connexion disponible. Pour vous connecter par le biais de l’éditeur de requête dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], utilisez **-m"Microsoft SQL Server Management Studio - Query"**.  
  
> [!IMPORTANT]  
>  N'utilisez pas cette option comme fonctionnalité de sécurité. L'application cliente fournit le nom d'application cliente et peut fournir un nom erroné dans la chaîne de connexion.  
  
## <a name="note-for-clustered-installations"></a>Remarque relative aux installations en cluster  
 Pour l'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un environnement en cluster, lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est démarré en mode mono-utilisateur, la DLL de ressource de cluster utilise la connexion disponible, ce qui bloque par conséquent les autres connexions au serveur. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est dans cet état, si vous essayez de mettre la ressource Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en ligne, la ressource SQL peut basculer à un nœud différent si la ressource est configurée pour affecter le groupe.  
  
 Pour contourner le problème, utilisez la procédure suivante :  
  
1.  Supprimez le paramètre de démarrage –m des Propriétés avancées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Mettez la ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hors connexion.  
  
3.  À partir du nœud de propriétaire actuel de ce groupe, émettez le commande suivante de l'invite de commandes :  
    net start MSSQLSERVER /m.  
  
4.  Vérifiez dans la console de l'administrateur de cluster ou de gestion de cluster de basculement que la ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est encore hors connexion.  
  
5.  Connectez-vous maintenant à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant la commande suivante et exécutez l’opération nécessaire : SQLCMD -E -S\<nom_serveur>.  
  
6.  Une fois que l'opération est terminée, fermez l'invite de commandes et remettez les ressources SQL et d'autres ressources en ligne via la console de l'administrateur de cluster.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Connexion de diagnostic pour les administrateurs de base de données](diagnostic-connection-for-database-administrators.md)   
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Options de démarrage du service moteur de base de données](database-engine-service-startup-options.md)  
  
  
