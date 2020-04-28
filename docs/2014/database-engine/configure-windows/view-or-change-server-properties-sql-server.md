---
title: Afficher ou modifier des propriétés de serveur (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- viewing server properties
- server properties [SQL Server]
- displaying server properties
- servers [SQL Server], viewing
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5c5ff985b62e39287b696e96f10142daf90ae0a3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72783125"
---
# <a name="view-or-change-server-properties-sql-server"></a>Afficher ou modifier des propriétés de serveur (SQL Server)
  Cette rubrique explique comment afficher ou modifier les propriétés d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]ou SQL Server Configuration Manager.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour afficher ou modifier des propriétés de serveur à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Gestionnaire de configuration SQL Server](#PowerShellProcedure)  
  
-   **Suivi :**  [Après avoir modifié les propriétés du serveur](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Lorsque vous utilisez sp_configure, vous devez exécuter RECONFIGURE ou RECONFIGURE WITH OVERRIDE après la définition d'une option de configuration. L'instruction RECONFIGURE WITH OVERRIDE est généralement réservée aux options de configuration qui doivent être utilisées avec une extrême prudence. Cependant, RECONFIGURE WITH OVERRIDE fonctionne avec toutes les options de configuration, et vous pouvez l'utiliser pour remplacer RECONFIGURE.  
  
    > [!NOTE]  
    >  RECONFIGURE s'exécute au sein d'une transaction. Si l'une des opérations de reconfiguration échoue, aucune de ces opérations ne prend effet.  
  
-   Certaines pages de propriétés présentent des informations fournies par l'intermédiaire de WMI (Windows Management Instrumentation). Pour afficher ces pages, WMI doit être installé sur l'ordinateur qui exécute [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Pour plus d’informations, consultez [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md).  
  
 Les autorisations d' `sp_configure` exécution sur sans paramètre ou avec uniquement le premier paramètre sont accordées par défaut à tous les utilisateurs. Pour exécuter `sp_configure` avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation ALTER Settings au niveau du serveur. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-or-change-server-properties"></a>Pour afficher ou modifier des propriétés de serveur  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés du serveur** , cliquez sur une page pour afficher ou modifier les informations du serveur relatives à cette page. Certaines propriétés sont en lecture seule.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-server-properties-by-using-the-serverproperty-built-in-function"></a>Pour afficher les propriétés du serveur à l'aide de la fonction intégrée SERVERPROPERTY  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise la fonction intégrée [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) dans une instruction `SELECT` pour retourner des informations sur le serveur actif. Ce scénario est utile lorsque plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont installées sur un serveur basé sur Windows et que le client doit ouvrir une autre connexion vers l'instance utilisée par la connexion actuelle.  
  
    ```sql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysservers-catalog-view"></a>Pour afficher les propriétés du serveur à l'aide de la vue de catalogue sys.servers  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L’exemple suivant interroge l’affichage catalogue [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) pour retourner le nom (`name`) et l’ID (`server_id`) du serveur actuel, ainsi que le nom du fournisseur OLE DB (`provider`) pour vous connecter à un serveur lié.  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysconfigurations-catalog-view"></a>Pour afficher les propriétés du serveur à l'aide de la vue de catalogue sys.configurations  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple suivant interroge la vue de catalogue [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) pour retourner des informations sur chaque option de configuration du serveur sur le serveur actuel. L'exemple retourne le nom (`name`) et la description (`description`) de l'option et indique si l'option est une option avancée (`is_advanced`).  
  
    ```sql
    USE AdventureWorks2012;
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;
    GO
    ```  
  
#### <a name="to-change-a-server-property-by-using-sp_configure"></a>Pour modifier une propriété de serveur à l'aide de sp_configure  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour modifier une propriété de serveur. L'exemple modifie la valeur de l'option `fill factor` sur `100`. Le serveur doit être redémarré pour appliquer le changement.  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="PowerShellProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
 Certaines propriétés du serveur peuvent être affichées ou modifiées à l'aide du gestionnaire de configuration SQL Server. Par exemple, vous pouvez afficher la version et l'édition de l'instance de SQL Server, ou modifier l'emplacement où les fichiers des journaux d'erreurs sont stockés. Vous pouvez aussi afficher ces propriétés en interrogeant les [fonctions et vues de gestion dynamique relatives au serveur](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql).  
  
#### <a name="to-view-or-change-server-properties"></a>Pour afficher ou modifier des propriétés de serveur  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
2.  Dans le **Gestionnaire de configuration SQL Server**, cliquez sur **Services SQL Server**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur **SQL Server (\<***InstanceName***>)**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de SQL Server (\<***nom_instance***>)** , modifiez les propriétés du serveur sous l’onglet **service** ou **avancé** , puis cliquez sur **OK**.  
  
##  <a name="follow-up-after-you-change-server-properties"></a><a name="FollowUp"></a> Suivi : Après avoir modifié les propriétés du serveur  
 Pour certaines propriétés, le serveur doit être redémarré afin d'appliquer les modification.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Instructions SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [Configurer WMI pour afficher l’état du serveur dans les outils SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)   
 [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
 [Fonctions de configuration &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql)   
 [Fonctions et vues de gestion dynamique relatives au serveur &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)  
