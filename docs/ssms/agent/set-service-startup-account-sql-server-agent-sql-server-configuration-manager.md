---
title: "Définir le compte de démarrage du service pour SQL Server Agent (Gestionnaire de configuration SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 94f718475a3b37b71864d883479848ec4058f252
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Le compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent permet de définir le compte Windows sous lequel s’exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, ainsi que ses autorisations réseau. Cette rubrique explique comment définir le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] avec [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   [Pour définir le compte de démarrage du service de SQL Server Agent à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] n'exige plus que le compte de démarrage du service soit membre du groupe Administrateurs [!INCLUDE[msCoName](../../includes/msconame_md.md)] . Toutefois, le compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit être membre du rôle serveur fixe [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]sysadmin. En cas d’utilisation du traitement de travaux multiserveur, le compte doit être membre du rôle de base de données msdb TargetServersRole sur le serveur maître.  
  
-   Cependant, l'Explorateur d'objets affiche le nœud de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
Pour plus d’informations sur les autorisations Windows nécessaires pour le compte de service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) et [Setting Up Windows Service Accounts](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)(Configuration des comptes de service Windows).  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>Pour configurer le compte de démarrage du service pour l'Agent SQL Server  
  
1.  Dans **Serveurs inscrits**, cliquez sur le signe plus pour développer **Moteur de base de données**.  
  
2.  Cliquez sur le signe plus pour développer le dossier **Groupes de serveurs locaux** .  
  
3.  Cliquez avec le bouton droit sur l’instance de serveur où vous souhaitez configurer le compte de démarrage du service, puis sélectionnez **Gestionnaire de configuration SQL Server**.  
  
4.  Dans la boîte de dialogue **Contrôle de compte d'utilisateur** , cliquez sur **Oui**.  
  
5.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , sélectionnez **Services SQL Server**dans le volet de la console.  
  
6.  Dans le volet d’informations, cliquez avec le bouton droit sur **Agent SQL Server***(nom_serveur)*, où *nom_serveur* représente le nom de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent pour laquelle vous voulez modifier le compte de démarrage du service, puis sélectionnez **Propriétés**.  
  
7.  Dans la boîte de dialogue **Propriétés** **de l’Agent SQL Server***(nom_serveur)*, sous l’onglet **Ouvrir une session**, sélectionnez l’une des options suivantes sous **Ouvrir une session en tant que** :  
  
    -   **Compte intégré** : sélectionnez cette option si vos travaux nécessitent des ressources du serveur local uniquement. Pour plus d’informations sur la façon de choisir un type de compte intégré Windows, consultez [Sélection d’un compte pour le service SQL Server Agent](http://msdn.microsoft.com/library/ms191543.aspx).  
  
        > [!IMPORTANT]  
        > Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent ne prend pas en charge le compte **Service local** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
    -   **Ce compte**: sélectionnez cette option si vos travaux nécessitent des ressources sur le réseau, notamment des ressources d’application, si vous souhaitez transférer des événements vers d’autres journaux d’applications Windows, ou si vous souhaitez notifier des opérateurs par courrier électronique ou radiomessagerie.  
  
        Si vous sélectionnez cette option :  
  
        1.  Dans la zone **Nom du compte** , entrez le compte qui sera utilisé pour exécuter SQL Server Agent. Vous pouvez également cliquer sur **Parcourir** pour ouvrir la boîte de dialogue **Sélectionnez l'utilisateur ou le groupe** et sélectionner le compte à utiliser.  
  
        2.  Dans la zone **Mot de passe** , entrez le mot de passe du compte. Dans la zone **Confirmer le mot de passe** , retapez le mot de passe.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez sur le bouton **Fermer** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dans le Gestionnaire de configuration.  
  
