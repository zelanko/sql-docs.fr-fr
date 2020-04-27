---
title: Configurer les options de démarrage du serveur (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 91a48d4acd771c19617bac26c1393f30334768e8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62810367"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a>Configurer les options de démarrage du serveur (Gestionnaire de configuration SQL Server)
  Cette rubrique explique comment configurer les options de démarrage à utiliser à chaque démarrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de Configuration Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des options de démarrage, consultez [Options de démarrage du service moteur de base de données](database-engine-service-startup-options.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
### <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écrit les paramètres de démarrage dans le Registre. Ils prennent effet lors du redémarrage suivant du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Dans un cluster, les modifications doivent être effectuées sur le serveur actif lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en ligne, et elles s'appliqueront lorsque le [!INCLUDE[ssDE](../../includes/ssde-md.md)] redémarrera. La mise à jour dans le Registre des options de démarrage sur l'autre nœud interviendra lors du basculement suivant.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 La configuration des options de démarrage du serveur est limitée aux utilisateurs qui peuvent modifier les entrées associées dans le Registre. Notamment :  
  
-   les membres du groupe Administrateurs local ;  
  
-   Le compte de domaine utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est configuré pour l'exécution sous un compte de domaine.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-configure-startup-options"></a>Pour configurer les options de démarrage  
  
1.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur **Services SQL Server**.  
  
    > [!NOTE]  
    >  Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console et non pas un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’apparaît pas en tant qu’application dans les versions plus récentes de Windows.  
    >   
    >  -   **Windows 10**:  
    >          Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans la **page de démarrage**, tapez SQLServerManager12. msc ( [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]pour). Pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , remplacez 12 par un nombre plus petit. Le fait de cliquer sur SQLServerManager12.msc ouvre le Gestionnaire de Configuration. Pour épingler le Configuration Manager à la page de démarrage ou à la barre des tâches, cliquez avec le bouton droit sur SQLServerManager12. msc, puis cliquez sur **ouvrir l’emplacement du fichier**. Dans l’Explorateur de fichiers Windows, cliquez avec le bouton droit sur SQLServerManager12. msc, puis cliquez sur **épingler pour démarrer** ou **Épingler à la barre des tâches**.  
    > -   **Windows 8**:  
    >          Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans l’icône **Rechercher** , sous **applications**, tapez **SQLServerManager\<version>. msc** , par `SQLServerManager12.msc`exemple, puis appuyez sur **entrée**.  
  
2.  Dans le volet droit, cliquez avec le bouton droit sur **SQL Server (***<nom_instance>***)**, puis cliquez sur **Propriétés**.  
  
3.  Sous l'onglet **Paramètres de démarrage** , dans la zone **Spécifiez un paramètre de démarrage** , tapez le paramètre, puis cliquez sur **Ajouter**.  
  
     Par exemple, pour démarrer en mode mono-utilisateur, tapez `-m` dans la zone **Spécifiez un paramètre de démarrage** , puis cliquez sur **Ajouter**. (Lorsque vous redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur, arrêtez l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sinon, l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut se connecter en premier et vous empêcher de vous connecter en tant que second utilisateur.)  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Redémarrez le [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!WARNING]  
    >  Une fois que vous avez terminé d’utiliser le mode mono-utilisateur, dans la zone paramètres `-m` de démarrage, sélectionnez le paramètre dans la zone **paramètres existants** , puis cliquez sur **supprimer**. Redémarrez le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour rétablir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode multi-utilisateur habituel.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer SQL Server en mode mono-utilisateur](start-sql-server-in-single-user-mode.md)   
 [Se connecter à SQL Server lorsque les administrateurs système sont verrouillés](connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
