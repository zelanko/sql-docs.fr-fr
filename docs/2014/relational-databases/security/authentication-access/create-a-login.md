---
title: Créer un compte de connexion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.LOGIN.SERVERROLES.F1
- sql12.swb.login.databaseaccess.f1
- sql12.swb.login.general.f1
- sql12.swb.login.effectivepermissions.f1
- sql12.swb.login.status.f1
helpviewer_keywords:
- authentication [SQL Server], logins
- logins [SQL Server], creating
- creating logins with Management Studio
- Create login [SQL Server]
- SQL Server logins
ms.assetid: fb163e47-1546-4682-abaa-8c9494e9ddc7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b765248e43dc66b9e1c038df27ca9a8b6135706d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63012028"
---
# <a name="create-a-login"></a>Créer un compte de connexion
  Cette rubrique explique comment créer un compte de connexion dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Un compte de connexion est l'identité de la personne ou du processus qui se connecte à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Contexte](#Background)  
  
     [Sécurité](#Security)  
  
-   **Pour créer un compte de connexion, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Mesures à prendre après avoir créé une connexion](#FollowUp)  
  
##  <a name="background"></a>Informations générales sur la <a name="Background"></a>  
 Un compte de connexion est un principal de sécurité, ou une entité qui peut être authentifiée par un système sécurisé. Pour se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les utilisateurs doivent disposer d'un compte de connexion. Vous pouvez créer un compte de connexion basé sur un principal Windows (tel qu'un utilisateur de domaine ou un groupe de domaines Windows) ou créer un compte de connexion qui n'est pas basé sur un principal Windows (tel qu'un compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ).  
  
> [!NOTE]  
>  Pour utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] doit utiliser une authentification en mode mixte. Pour plus d’informations, consultez [choisir un mode d’authentification](../choose-an-authentication-mode.md).  
  
 En tant que principal de sécurité, il est possible d'accorder des autorisations à des comptes de connexion. L'étendue d'un compte de connexion est l'intégralité du [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Pour se connecter à une base de données spécifique sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un compte de connexion doit être mappé à un utilisateur de base de données. Les autorisations dans la base de données sont accordées et refusées à l'utilisateur de la base de données, pas au compte de connexion. Les autorisations dont l'étendue englobe la totalité de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (par exemple, l'autorisation `CREATE ENDPOINT`), peuvent être accordées à un compte de connexion.  
  
##  <a name="security"></a><a name="Security"></a> Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Requiert l'autorisation `ALTER ANY LOGIN` ou `ALTER LOGIN` sur le serveur.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
##### <a name="to-create-a-sql-server-login"></a>Pour créer un compte de connexion SQL Server  
  
1.  Dans l'Explorateur d'objets, développez le dossier de l'instance du serveur où vous souhaitez créer le compte de connexion.  
  
2.  Cliquez avec le bouton droit sur le dossier **sécurité** , pointez sur **nouveau**, puis sélectionnez **connexion...**.  
  
3.  Dans la boîte de dialogue **nouvelle connexion** , dans la page **général** , entrez le nom d’un utilisateur dans la zone **nom de connexion** . Vous pouvez également cliquer sur **Rechercher…** pour ouvrir la boîte de dialogue **Sélectionner un utilisateur ou un groupe**.  
  
     Si vous cliquez sur **Rechercher...**:  
  
    1.  Sous **Sélectionner ce type d’objet**, cliquez sur **Types d’objets…** pour ouvrir la boîte de dialogue **Types d’objets** et sélectionnez l’ensemble ou certains des éléments suivants : **Principaux de sécurité intégrés**, **Groupes** et **Utilisateurs**. Les options**Principaux de sécurité intégrés** et **Utilisateurs** sont sélectionnées par défaut. Lorsque vous avez terminé, cliquez sur **OK**.  
  
    2.  Sous **À partir de cet emplacement**, cliquez sur **Emplacements…** pour ouvrir la boîte de dialogue **Emplacements** et sélectionner un des emplacements de serveur disponibles. Lorsque vous avez terminé, cliquez sur **OK**.  
  
    3.  Sous **Entrez le nom de l’objet à sélectionner (exemples)**, entrez l’utilisateur ou le nom de groupe que vous souhaitez rechercher. Pour plus d'informations, consultez [Boîte de dialogue Choisir des utilisateurs, des ordinateurs ou des groupes](https://technet.microsoft.com/library/cc771712.aspx).  
  
    4.  Cliquez sur **Avancé…** pour obtenir davantage d’options de recherche avancée. Pour plus d’informations, consultez [Boîte de dialogue Choisir des utilisateurs, des ordinateurs ou des groupes - Page Avancé](https://technet.microsoft.com/library/cc733110.aspx).  
  
    5.  Cliquez sur **OK**.  
  
4.  Pour créer un compte de connexion selon un principal Windows, sélectionnez **Authentification Windows**. Il s'agit de la sélection par défaut.  
  
5.  Pour créer un compte de connexion qui est enregistré sur une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , sélectionnez **Authentification SQL Server**.  
  
    1.  Dans la zone **Mot de passe**, entrez un mot de passe pour le nouvel utilisateur. Entrez à nouveau ce mot de passe dans la zone **Confirmer le mot de passe**.  
  
    2.  Lorsque vous modifiez un mot de passe existant, sélectionnez **Spécifier l'ancien mot de passe**, puis tapez l'ancien mot de passe dans la zone **Ancien mot de passe** .  
  
    3.  Pour appliquer des options de stratégie de mot de passe pour la complexité et l'application, sélectionnez **Conserver la stratégie de mot de passe**. Pour plus d'informations, consultez [Password Policy](../password-policy.md). Il s’agit d’une option par défaut lorsque **l’authentification SQL Server** est sélectionnée.  
  
    4.  Pour appliquer des options de stratégie de mot de passe pour l'expiration, sélectionnez **Conserver l'expiration du mot de passe**. L’option **appliquer la stratégie de mot de passe** doit être sélectionnée pour activer cette case à cocher. Il s’agit d’une option par défaut lorsque **l’authentification SQL Server** est sélectionnée.  
  
    5.  Pour forcer l'utilisateur à créer un nouveau mot de passe après la première utilisation du compte de connexion, sélectionnez **L'utilisateur doit changer de mot de passe à la prochaine connexion**. L’option **appliquer l’expiration du mot de passe** doit être sélectionnée pour activer cette case à cocher. Il s’agit d’une option par défaut lorsque **l’authentification SQL Server** est sélectionnée.  
  
6.  Pour associer le compte de connexion à un certificat de sécurité autonome, sélectionnez **Mappé au certificat** , puis sélectionnez le nom d’un certificat existant dans la liste.  
  
7.  Pour associer le compte de connexion à une clé asymétrique autonome, sélectionnez **Mappé à la clé asymétrique** , puis sélectionnez le nom d’une clé existante dans la liste.  
  
8.  Pour associer le compte de connexion à des informations d'identification de sécurité, activez la case à cocher **Mappé aux informations d'identification** , puis sélectionnez des informations d'identification existantes dans la liste ou cliquez sur **Ajouter** pour créer de nouvelles informations d'identification. Pour supprimer du compte de connexion un mappage à des informations d'identification de sécurité, sélectionnez les informations d'identification dans **Informations d'identification mappées** et cliquez sur **Supprimer**. Pour plus d’informations sur les informations d’identification en général, consultez [Informations d’identification &#40;moteur de base de données&#41;](credentials-database-engine.md).  
  
9. Sélectionnez une base de données par défaut pour le compte de connexion dans la liste **Base de données par défaut** . **Master** est la valeur par défaut de cette option.  
  
10. Dans la liste **Langue par défaut** , sélectionnez une langue par défaut pour le compte de connexion.  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>Options supplémentaires  
 La boîte de dialogue **nouvelle connexion** offre également des options sur quatre pages supplémentaires **: rôles de serveur**, **mappage utilisateur**, éléments **sécurisables**et **État**.  
  
### <a name="server-roles"></a>Rôles de serveur  
 La page **Rôles de serveur** répertorie tous les rôles possibles qui peuvent être affectés au nouveau compte de connexion. Les options suivantes sont disponibles :  
  
 Case à cocher**bulkadmin**  
 Les membres du rôle serveur fixe **bulkadmin** peuvent exécuter l’instruction BULK INSERT.  
  
 Case à cocher**dbcreator**  
 Les membres du rôle serveur fixe **dbcreator** peuvent créer, modifier, supprimer et restaurer n’importe quelle base de données.  
  
 Case à cocher**diskadmin**  
 Les membres du rôle serveur fixe **diskadmin** peuvent gérer les fichiers de disque.  
  
 Case à cocher**processadmin**  
 Les membres du rôle serveur fixe **processadmin** peuvent arrêter les processus en cours d’exécution dans une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
 Case à cocher**public**  
 Tous les utilisateurs, groupes et rôles SQL Server appartiennent au rôle serveur fixe **public** par défaut.  
  
 Case à cocher**securityadmin**  
 Les membres du rôle serveur fixe **securityadmin** gèrent les connexions et leurs propriétés. Ils peuvent assigner des autorisations GRANT, DENY et REVOKE au niveau du serveur. Ils peuvent aussi assigner des autorisations GRANT, DENY et REVOKE au niveau de la base de données. En outre, ils peuvent réinitialiser les mots de passe pour les connexions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Case à cocher**serveradmin**  
 Les membres du rôle serveur fixe **serveradmin** peuvent modifier les options de configuration à l’échelle du serveur et arrêter le serveur.  
  
 Case à cocher**setupadmin**  
 Les membres du rôle serveur fixe **setupadmin** peuvent ajouter et supprimer des serveurs liés et exécuter certaines procédures stockées du système.  
  
 Case à cocher**sysadmin**  
 Les membres du rôle serveur fixe **sysadmin** peuvent exécuter n’importe quelle activité dans le [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
### <a name="user-mapping"></a>Mappage de l'utilisateur  
 La page **Mappage de l'utilisateur** répertorie toutes les bases de données possibles et les appartenances de rôle de base de données sur ces bases de données qui peuvent être appliquées à la connexion. Les bases de données sélectionnées déterminent les appartenances aux rôles disponibles pour la connexion. Les options suivantes sont disponibles sur cette page :  
  
 **Utilisateurs mappés à cette connexion**  
 Sélectionnez les bases de données auxquelles cette connexion peut accéder. Lorsque vous sélectionnez une base de données, ses rôles de base de données valides s’affichent dans le volet **Appartenance au rôle de base de données pour :** _nom_base_de_données_ .  
  
 **Map**  
 Autorise la connexion à accéder aux bases de données répertoriées au-dessous.  
  
 **Sauvegarde de la base de données**  
 Répertorie les bases de données disponibles sur le serveur.  
  
 **Utilisateur**  
 Spécifiez un utilisateur de la base de données à mapper sur cette connexion. Par défaut, l'utilisateur a le même nom que la connexion.  
  
 **Schéma par défaut**  
 Spécifie le schéma par défaut de l'utilisateur. Lors de la création d'un utilisateur, son schéma par défaut est **dbo**. Il est possible de spécifier un schéma par défaut qui n'existe pas encore. Vous ne pouvez pas spécifier de schéma par défaut pour un utilisateur mappé sur un groupe Windows, un certificat ou une clé asymétrique.  
  
 **Compte Invité activé pour :**  _nom_base_de_données_  
 Attribut en lecture seule indiquant si le compte Invité est activé sur la base de données sélectionnée. Utilisez la page **État** de la boîte de dialogue **Propriétés de la connexion** du compte Invité pour activer ou désactiver le compte Invité.  
  
 **Appartenance au rôle de base de données pour :**  _nom_base_de_données_  
 Sélectionnez les rôles pour l'utilisateur dans la base de données spécifiée. Tous les utilisateurs sont membres du rôle **public** de chaque base de données et ne peuvent pas être supprimés. Pour plus d’informations sur les rôles de base de données, consultez [Rôles au niveau de la base de données](database-level-roles.md).  
  
### <a name="securables"></a>Éléments sécurisables  
 La page **Éléments sécurisables** répertorie tous les éléments sécurisables possibles et les autorisations sur ces éléments sécurisables qui peuvent être accordées à la connexion. Les options suivantes sont disponibles sur cette page :  
  
 **Grille supérieure**  
 Contient un ou plusieurs éléments pour lesquels des autorisations peuvent être définies. Les colonnes affichées dans la grille supérieure varient selon le principal ou l'élément sécurisable.  
  
 Pour ajouter des éléments à la grille supérieure :  
  
1.  Cliquez sur **Rechercher**.  
  
2.  Dans la boîte de dialogue **Ajouter des objets** , sélectionnez l’une des options suivantes : **objets spécifiques...**, **tous les objets des types...** ou **le serveur**_SERVER_NAME_. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  La sélection de l’option **Le serveur**_nom_serveur_ remplit automatiquement la grille supérieure avec tous les objets sécurisables de ce serveur.  
  
3.  Si vous sélectionnez **des objets spécifiques...**:  
  
    1.  Dans la boîte de dialogue **Sélectionner des objets** , sous **sélectionnez ces types**d’objets, cliquez sur types d’objets **...**.  
  
    2.  Dans la boîte de dialogue **Sélectionner les types d'objets** , sélectionnez tout ou partie des types d'objets suivants : **Points de terminaison**, **Connexions**, **Serveurs**, **Groupes de disponibilité**et **Rôles de serveur**. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    3.  Sous **Entrez les noms des objets à sélectionner (exemples)**, cliquez sur **Parcourir...**.  
  
    4.  Dans la boîte de dialogue **Rechercher des objets** , sélectionnez les objets disponibles du type sélectionné dans la boîte de dialogue **Sélectionner les types d'objets** , puis cliquez sur **OK**.  
  
    5.  Dans la boîte de dialogue **Sélectionner des objets** , cliquez sur **OK**.  
  
4.  Si vous sélectionnez **tous les objets des types...**, dans la boîte de dialogue **Sélectionner les types** d’objets, sélectionnez tout ou partie des types d’objets suivants : **points de terminaison**, **connexions**, **serveurs**, **groupes de disponibilité**et **rôles de serveur**. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 **Nom**  
 Nom de chaque principal ou élément sécurisable ajouté à la grille.  
  
 **Type**  
 Décrit le type de chaque élément.  
  
 **Onglet Autorisations explicites**  
 Énumère les autorisations possibles pour les éléments sécurisables sélectionnés dans la grille supérieure. Toutes les options ne sont pas disponibles pour toutes les autorisations explicites.  
  
 **autorisations**  
 Nom de l'autorisation.  
  
 **Fournisseur**  
 Principal ayant accordé l'autorisation.  
  
 **Licence**  
 Sélectionnez cette option pour octroyer cette autorisation à la connexion. Désactivez-la pour révoquer cette autorisation.  
  
 **Avec autorisation**  
 Reflète l'état de l'option WITH GRANT pour l'autorisation indiquée dans la liste. Cette zone est en lecture seule. Pour appliquer cette autorisation, utilisez l'instruction [GRANT](/sql/t-sql/statements/grant-transact-sql) .  
  
 **Deny**  
 Sélectionnez cette option pour refuser cette autorisation à la connexion. Désactivez-la pour révoquer cette autorisation.  
  
### <a name="status"></a>État  
 La page **État** répertorie certaines des options d'authentification et d'autorisation qui peuvent être configurées sur la connexion sélectionnée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Les options suivantes sont disponibles sur cette page :  
  
 **Autorisation de se connecter au moteur de base de données**  
 Lorsque vous travaillez avec ce paramètre, vous devez considérer la connexion sélectionnée comme un principal auquel une autorisation sur un élément sécurisable peut être accordée ou refusée.  
  
 Sélectionnez **Octroyer** pour accorder l'autorisation CONNECT SQL à la connexion. Sélectionnez **Refuser** pour refuser l'autorisation CONNECT SQL à la connexion.  
  
 **Connexion**  
 Lorsque vous travaillez avec ce paramètre, vous devez considérer la connexion sélectionnée comme un enregistrement d'une table. Les modifications apportées aux valeurs répertoriées ici seront appliquées à l'enregistrement.  
  
 Une connexion qui a été désactivée continue d'exister en tant qu'enregistrement. Mais si elle tente de se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], elle ne sera pas authentifiée.  
  
 Sélectionnez cette option pour activer ou désactiver cette connexion. Cette option utilise l'instruction ALTER LOGIN avec l'option ENABLE ou DISABLE.  
  
 **Authentification SQL Server**  
 La case à cocher la **connexion est verrouillée** est disponible uniquement si la connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sélectionnée se connecte à l’aide de l’authentification et que la connexion a été verrouillée. Ce paramètre est en lecture seule. Pour déverrouiller une connexion verrouillée, exécutez ALTER LOGIN avec l'option UNLOCK.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-login-using-windows-authentication"></a>Pour créer une connexion à l'aide de l'authentification Windows  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Create a login for SQL Server by specifying a server name and a Windows domain account name.  
  
    CREATE LOGIN [<domainName>\<loginName>] FROM WINDOWS;  
    GO  
  
    ```  
  
#### <a name="to-create-a-login-using-sql-server-authentication"></a>Pour créer une connexion via l'authentification SQL Server  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Creates the user "shcooper" for SQL Server using the security credential "RestrictedFaculty"   
    -- The user login starts with the password "Baz1nga," but that password must be changed after the first login.  
  
    CREATE LOGIN shcooper   
       WITH PASSWORD = 'Baz1nga' MUST_CHANGE,  
       CREDENTIAL = RestrictedFaculty;  
    GO  
  
    ```  
  
 Pour plus d’informations, consultez [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-login"></a><a name="FollowUp"></a>Suivi : étapes à suivre après avoir créé une connexion  
 Une fois le compte de connexion créé, celui-ci peut se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], mais il ne dispose pas nécessairement des autorisations suffisantes pour effectuer des tâches utiles. La liste suivante fournit des liens vers des actions de compte de connexion courantes.  
  
-   Pour effectuer une jointure entre le compte de connexion et un rôle de base de données, consultez [Attacher un rôle](join-a-role.md).  
  
-   Pour autoriser un compte de connexion à utiliser une base de données, consultez [Créer un utilisateur de base de données](../authentication-access/create-a-database-user.md).  
  
-   Pour accorder une autorisation à un compte de connexion, consultez [Accorder une autorisation à un principal](grant-a-permission-to-a-principal.md).  
  
  
