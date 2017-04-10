---
title: "Configurer les options de d&#233;marrage du serveur (Gestionnaire de configuration SQL&#160;Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paramètres [SQL Server], options de démarrage"
  - "SQL Server, options de démarrage"
  - "mode mono-utilisateur [SQL Server], démarrage en"
  - "options de démarrage [SQL Server]"
  - "services SQL Server, définition des options de démarrage"
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Configurer les options de d&#233;marrage du serveur (Gestionnaire de configuration SQL&#160;Server)
  Cette rubrique explique comment configurer les options de démarrage à utiliser à chaque démarrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des options de démarrage, consultez [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
### Limitations et restrictions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écrit les paramètres de démarrage dans le Registre. Ils prennent effet lors du redémarrage suivant du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Dans un cluster, les modifications doivent être effectuées sur le serveur actif lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en ligne, et elles s'appliqueront lorsque le [!INCLUDE[ssDE](../../includes/ssde-md.md)] redémarrera. La mise à jour dans le Registre des options de démarrage sur l'autre nœud interviendra lors du basculement suivant.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 La configuration des options de démarrage du serveur est limitée aux utilisateurs qui peuvent modifier les entrées associées dans le Registre. Notamment :  
  
-   les membres du groupe Administrateurs local ;  
  
-   Le compte de domaine utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est configuré pour l'exécution sous un compte de domaine.  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### Pour configurer les options de démarrage  
  
1.  Cliquez sur le bouton **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
    > [!NOTE]  
    >  Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console et non pas un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’apparaît pas en tant qu’application dans les versions plus récentes de Windows.  
    >   
    >  -   **Windows 10** :  
    >          pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dans la **page d’accueil**, tapez SQLServerManager13.msc (pour [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , remplacez 13 par un nombre plus petit. Le fait de cliquer sur SQLServerManager13.msc ouvre le Gestionnaire de configuration. Pour épingler le Gestionnaire de configuration à la page d’accueil ou à la barre des tâches, cliquez avec le bouton droit sur SQLServerManager13.msc, puis cliquez sur **Ouvrir l’emplacement du fichier**. Dans l’Explorateur de fichiers Windows, cliquez avec le bouton droit sur SQLServerManager13.msc, puis cliquez sur **Épingler à l’écran d’accueil** ou **Épingler à la barre des tâches**.  
    > -   **Windows 8** :  
    >          pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sur l’icône **Rechercher**, sous **Applications**, tapez **SQLServerManager\<version>.msc**, par exemple **SQLServerManager13.msc**, puis appuyez sur **Entrée**.  
  
2.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur **Services SQL Server**.  
  
3.  Dans le volet droit, cliquez avec le bouton droit sur **SQL Server (***<nom_instance>***)**, puis cliquez sur **Propriétés**.  
  
4.  Sous l'onglet **Paramètres de démarrage** , dans la zone **Spécifiez un paramètre de démarrage** , tapez le paramètre, puis cliquez sur **Ajouter**.  
  
     Par exemple, pour démarrer en mode mono-utilisateur, tapez **-m** dans la zone **Spécifiez un paramètre de démarrage**, puis cliquez sur **Ajouter**. (Lorsque vous redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur, arrêtez l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sinon, l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut se connecter en premier et vous empêcher de vous connecter en tant que second utilisateur.)  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Redémarrez le [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!WARNING]  
    >  Au terme de l’utilisation du mode mono-utilisateur, dans la zone Paramètres de démarrage, sélectionnez le paramètre **-m** dans la zone **Paramètres existants**, puis cliquez sur **Supprimer**. Redémarrez le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour rétablir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode multi-utilisateur habituel.  
  
## Voir aussi  
 [Démarrer SQL Server en mode mono-utilisateur](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)   
 [Se connecter à SQL Server lorsque les administrateurs système n'y ont plus accès](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  