---
title: "Modifier le mot de passe des comptes utilis&#233;s par SQL Server (Gestionnaire de configuration SQL Server) | Microsoft Docs"
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
  - "mot de passe expiré [SQL Server], SQL Server Agent"
  - "mots de passe [SQL Server], service SQL Server Agent"
  - "mots de passe [SQL Server], modification"
  - "mot de passe expiré [SQL Server], moteur de base de données"
  - "mots de passe [SQL Server], service SQL Server"
  - "Moteur de base de données [SQL Server], mots de passe"
  - "modifier les mots de passe utilisés par SQL Server"
  - "modification des mots de passe"
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Modifier le mot de passe des comptes utilis&#233;s par SQL Server (Gestionnaire de configuration SQL Server)
  Cette rubrique explique comment modifier le mot de passe des comptes utilisés par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration SQL Server. Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutent sur un ordinateur en tant que service, à l'aide des informations d'identification qui sont fournies au départ durant l'installation. Si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est exécutée sous un compte de domaine et que le mot de passe de ce compte est modifié, le mot de passe utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être mis à jour pour refléter le nouveau mot de passe. Si le mot de passe n'est pas mis à jour, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut perdre l'accès à certaines ressources du domaine, et si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'arrête, le service ne redémarrera pas tant que le mot de passe n'aura pas été mis à jour.  
  
 Pour modifier les mots de passe d’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Mot de passe expiré](../../ssms/f1-help/password-expired.md).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est l'outil conçu pour et autorisé à modifier les paramètres des services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le fait de modifier un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du Gestionnaire de contrôle des services Windows (**services.msc**) ne modifie pas toujours les paramètres nécessaires et peut empêcher le service de fonctionner correctement. Toutefois, dans un environnement cluster, après avoir modifié le mot de passe sur le nœud actif à l'aide du Gestionnaire de configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez modifier le mot de passe sur le nœud passif à l'aide du Gestionnaire de contrôle des services.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez être administrateur de l'ordinateur pour modifier le mot de passe utilisé par un service.  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### Pour modifier le mot de passe utilisé par le service SQL Server (moteur de base de données)  
  
1.  Cliquez sur le bouton **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
    > [!NOTE]  
    >  Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console et non pas un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’apparaît pas en tant qu’application dans les versions plus récentes de Windows.  
    >   
    >  -   **Windows 10** :  
    >          pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dans la **page d’accueil**, tapez SQLServerManager13.msc (pour [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , remplacez 13 par un nombre plus petit. Le fait de cliquer sur SQLServerManager13.msc ouvre le Gestionnaire de configuration. Pour épingler le Gestionnaire de configuration à la page d’accueil ou à la barre des tâches, cliquez avec le bouton droit sur SQLServerManager13.msc, puis cliquez sur **Ouvrir l’emplacement du fichier**. Dans l’Explorateur de fichiers Windows, cliquez avec le bouton droit sur SQLServerManager13.msc, puis cliquez sur **Épingler à l’écran d’accueil** ou **Épingler à la barre des tâches**.  
    > -   **Windows 8** :  
    >          pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sur l’icône **Rechercher**, sous **Applications**, tapez **SQLServerManager\<version>.msc**, par exemple **SQLServerManager13.msc**, puis appuyez sur **Entrée**.  
  
2.  Dans le Gestionnaire de configuration SQL Server, cliquez sur **Services SQL Server**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur **SQL Server (**\<nom_instance>**)**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de SQL Server (**\<nom_instance>**)**, sous l’onglet Ouvrir une session, pour le compte figurant dans la zone **Nom du compte**, tapez le nouveau mot de passe dans les zones **Mot de passe** et **Confirmer le mot de passe**, puis cliquez sur **OK**.  
  
     Le mot de passe prend effet immédiatement, sans qu'il soit nécessaire de redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### Pour modifier le mot de passe utilisé par le service SQL Server Agent  
  
1.  Cliquez sur le bouton **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
2.  Dans le Gestionnaire de configuration SQL Server, cliquez sur **Services SQL Server**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur **SQL Server Agent (**\<nom_instance>**)**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de SQL Server Agent (**\<nom_instance>**)**, sous l’onglet Ouvrir une session, pour le compte figurant dans la zone **Nom du compte**, tapez le nouveau mot de passe dans les zones **Mot de passe** et **Confirmer le mot de passe**, puis cliquez sur **OK**.  
  
     Sur une instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le mot de passe prend effet immédiatement, sans redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sur une instance cluster, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut mettre la ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hors connexion, et nécessite un redémarrage.  
  
## Voir aussi  
 [Rubriques de procédures concernant la gestion des services &#40;Gestionnaire de configuration SQL Server&#41;](../Topic/Managing%20Services%20How-to%20Topics%20\(SQL%20Server%20Configuration%20Manager\).md)  
  
  