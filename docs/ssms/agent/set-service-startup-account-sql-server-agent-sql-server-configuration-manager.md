---
title: Définir le compte de démarrage du service pour SQL Server Agent (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4540d5b52d1c4f92753588f6bd918107afe04c1d
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67685070"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Le compte de démarrage du service Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet de définir le compte Windows sous lequel s'exécute l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que ses autorisations réseau. Cette rubrique explique comment définir le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] avec [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   [Pour définir le compte de démarrage du service de SQL Server Agent à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'exige plus que le compte de démarrage du service soit membre du groupe Administrateurs [!INCLUDE[msCoName](../../includes/msconame_md.md)] . Toutefois, le compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être membre du rôle serveur fixe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin. En cas d’utilisation du traitement de travaux multiserveur, le compte doit être membre du rôle de base de données msdb TargetServersRole sur le serveur maître.  
  
-   Cependant, l'Explorateur d'objets affiche le nœud de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
Pour plus d’informations sur les autorisations Windows nécessaires pour le compte de service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) et [Setting Up Windows Service Accounts](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)(Configuration des comptes de service Windows).  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>Pour configurer le compte de démarrage du service pour l'Agent SQL Server  
  
1.  Dans **Serveurs inscrits**, cliquez sur le signe plus pour développer **Moteur de base de données**.  
  
2.  Cliquez sur le signe plus pour développer le dossier **Groupes de serveurs locaux** .  
  
3.  Cliquez avec le bouton droit sur l’instance de serveur où vous souhaitez configurer le compte de démarrage du service, puis sélectionnez **Gestionnaire de configuration SQL Server...** .  
  
4.  Dans la boîte de dialogue **Contrôle de compte d'utilisateur** , cliquez sur **Oui**.  
  
5.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez **Services SQL Server**dans le volet de la console.  
  
6.  Dans le volet d’informations, cliquez avec le bouton droit sur **Agent SQL Server** _(nom\_serveur)_ , où *nom_serveur* représente le nom de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour laquelle vous voulez changer le compte de démarrage du service, puis sélectionnez **Propriétés**.  
  
7.  Dans la boîte de dialogue **Propriétés** de **SQL Server Agent** _(nom\_serveur)_ , sous l’onglet **Ouvrir une session**, sélectionnez l’une des options suivantes sous **Ouvrir une session en tant que** :  
  
    -   **Compte intégré**: sélectionnez cette option si vos travaux nécessitent des ressources du serveur local uniquement. Pour plus d’informations sur la façon de choisir un type de compte intégré Windows, consultez [Sélection d’un compte pour le service SQL Server Agent](https://msdn.microsoft.com/library/ms191543.aspx).  
  
        > [!IMPORTANT]  
        > Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne prend pas en charge le compte **Service local** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
    -   **Ce compte**: sélectionnez cette option si vos travaux nécessitent des ressources sur le réseau, notamment des ressources d’application, si vous souhaitez transférer des événements vers d’autres journaux d’applications Windows, ou si vous souhaitez notifier des opérateurs par courrier électronique ou radiomessagerie.  
  
        Si vous sélectionnez cette option :  
  
        1.  Dans la zone **Nom du compte** , entrez le compte qui sera utilisé pour exécuter SQL Server Agent. Vous pouvez également cliquer sur **Parcourir** pour ouvrir la boîte de dialogue **Sélectionnez l'utilisateur ou le groupe** et sélectionner le compte à utiliser.  
  
        2.  Dans la zone **Mot de passe** , entrez le mot de passe du compte. Dans la zone **Confirmer le mot de passe** , retapez le mot de passe.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez sur le bouton **Fermer** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le Gestionnaire de configuration.  
  
