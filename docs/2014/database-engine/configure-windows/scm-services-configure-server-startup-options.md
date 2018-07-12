---
title: Configurer les options de démarrage du serveur (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a0eb6d3cc33a737f6d9930da4fc9d4726e362b74
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155040"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a>Configurer les options de démarrage du serveur (Gestionnaire de configuration SQL Server)
  Cette rubrique explique comment configurer les options de démarrage à utiliser à chaque démarrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour obtenir la liste des options de démarrage, consultez [Options de démarrage du service moteur de base de données](database-engine-service-startup-options.md).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
### <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écrit les paramètres de démarrage dans le Registre. Ils prennent effet lors du redémarrage suivant du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Dans un cluster, les modifications doivent être effectuées sur le serveur actif lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en ligne, et elles s'appliqueront lorsque le [!INCLUDE[ssDE](../../includes/ssde-md.md)] redémarrera. La mise à jour dans le Registre des options de démarrage sur l'autre nœud interviendra lors du basculement suivant.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 La configuration des options de démarrage du serveur est limitée aux utilisateurs qui peuvent modifier les entrées associées dans le Registre. Notamment :  
  
-   les membres du groupe Administrateurs local ;  
  
-   Le compte de domaine utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est configuré pour l'exécution sous un compte de domaine.  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-configure-startup-options"></a>Pour configurer les options de démarrage  
  
1.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur **Services SQL Server**.  
  
    > [!NOTE]  
    >  Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console et non pas un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’apparaît pas en tant qu’application dans les versions plus récentes de Windows.  
    >   
    >  -   **Windows 10**:  
    >          Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans le **Page de démarrage**, entrez SQLServerManager12.msc (pour [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). Pour les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] remplacez 12 par un nombre plus petit. Cliquez sur SQLServerManager12.msc pour ouvrir le Gestionnaire de Configuration. Pour épingler le Gestionnaire de Configuration pour la Page de démarrage ou de la barre des tâches, cliquez sur SQLServerManager12.msc, puis cliquez sur **ouvrir l’emplacement du fichier**. Dans l’Explorateur de fichiers Windows, cliquez sur SQLServerManager12.msc, puis cliquez sur **épingler au menu Démarrer** ou **épingler à la barre des tâches**.  
    > -   **Windows 8**:  
    >          Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans le **recherche** icône sous **applications**, type **SQLServerManager\<version > .msc** tels que `SQLServerManager12.msc`, puis appuyez sur **entrée**.  
  
2.  Dans le volet droit, cliquez avec le bouton droit sur **SQL Server (***<nom_instance>***)**, puis cliquez sur **Propriétés**.  
  
3.  Sous l'onglet **Paramètres de démarrage** , dans la zone **Spécifiez un paramètre de démarrage** , tapez le paramètre, puis cliquez sur **Ajouter**.  
  
     Par exemple, pour démarrer en mode mono-utilisateur, tapez `-m` dans le **spécifier un paramètre de démarrage** , puis cliquez sur **ajouter**. (Lorsque vous redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur, arrêtez l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sinon, l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut se connecter en premier et vous empêcher de vous connecter en tant que second utilisateur.)  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Redémarrez le [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!WARNING]  
    >  Une fois que vous avez terminé d’utiliser le mode mono-utilisateur, dans la zone de paramètres de démarrage, sélectionnez le `-m` paramètre dans le **paramètres existants** , puis cliquez sur **supprimer**. Redémarrez le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour rétablir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode multi-utilisateur habituel.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer SQL Server en mode mono-utilisateur](start-sql-server-in-single-user-mode.md)   
 [Se connecter à SQL Server quand les administrateurs système n’y ont plus accès](connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
