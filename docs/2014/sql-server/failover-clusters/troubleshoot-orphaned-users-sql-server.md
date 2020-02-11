---
title: Résoudre les problèmes liés aux utilisateurs orphelins (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38a33b34b64cf285e94f66c547b2309b8daf1ae8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035661"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a>Dépanner des utilisateurs orphelins (SQL Server)
  Pour se connecter à une instance de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un principal doit posséder une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide. Cette connexion est utilisée dans le processus d'authentification chargé de vérifier que le principal est autorisé à se connecter à l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexions sur une instance de serveur sont visibles dans l’affichage catalogue **sys. server_principals** et l’affichage de compatibilité **sys. syslogins** .  
  
 Les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accèdent aux bases de données à l'aide d'un utilisateur de base de données mappé à la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il y a deux exceptions à cette règle :  
  
-   Le compte invité.  
  
     Lorsqu'il est activé dans la base de données, ce compte autorise les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non mappées à un utilisateur de base de données à accéder en tant qu'invité à la base de données.  
  
-   Appartenance aux groupes Microsoft Windows.  
  
     Une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée à partir d'un utilisateur Windows peut accéder à la base de données si cet utilisateur est membre d'un groupe Windows lui-même utilisateur de la base de données.  
  
 Les informations relatives au mappage d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à un utilisateur de base de données sont stockées dans la base de données. Elles incluent le nom de l'utilisateur de base de données et l'identificateur de sécurité de connexion (SID) de la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correspondante. Les autorisations de cet utilisateur de base de données sont utilisées comme autorisation de la base de données.  
  
 Un utilisateur de base de données pour lequel la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correspondante n'est pas définie sur une instance serveur, ou l'est de façon incorrecte, ne peut pas se connecter à cette instance. L'utilisateur devient donc un *utilisateur orphelin* de la base de données sur cette instance du serveur. Un utilisateur de base de données peut se retrouver orphelin si la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correspondante est supprimée. De même, un utilisateur peut devenir orphelin après qu'une base de données a été restaurée ou attachée à une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le fait de se retrouver orphelin peut se produire si l'utilisateur de base de données est mappé à un SID absent dans la nouvelle instance de serveur.  
  
> [!NOTE]  
>  Une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ne peut pas accéder à une base de données dans laquelle elle n’a pas d’utilisateur de base de données correspondant, sauf si l' **invité** est activé dans cette base de données. Pour plus d’informations sur la création d’un compte d’utilisateur de base de données, consultez [Create user &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
## <a name="to-detect-orphaned-users"></a>Pour détecter des utilisateurs orphelins  
 Pour détecter des utilisateurs orphelins, exécutez les instructions Transact-SQL suivantes :  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 Vous obtenez la liste des utilisateurs et de leurs identificateurs de sécurité (SID) qui, dans la base de données en cours, ne sont pas liés à une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).  
  
> [!NOTE]  
>  **sp_change_users_login** ne peut pas être [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé avec des connexions créées à partir de Windows.  
  
## <a name="to-resolve-an-orphaned-user"></a>Pour résoudre le cas d'un utilisateur orphelin  
 Pour résoudre le cas d'un orphelin, utilisez la procédure suivante :  
  
1.  La commande suivante relient le compte de connexion au serveur spécifié par *<login_name>* avec l’utilisateur de base de données spécifié par *<Database_user *>.  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     Pour plus d’informations, consultez [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).  
  
2.  Dès l'exécution du code de l'étape ci-dessus, l'utilisateur peut accéder à la base de données. L’utilisateur peut ensuite modifier le mot de passe de l' *<login_name>* compte de connexion à l’aide de la procédure stockée **sp_password** , comme suit :  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  Seuls les comptes de connexion avec l'autorisation ALTER ANY LOGIN peuvent modifier le mot de passe du compte de connexion d'un autre utilisateur. Toutefois, seuls les membres du rôle **sysadmin** peuvent modifier les mots de passe des membres du rôle **sysadmin** .  
  
    > [!NOTE]  
    >  **sp_password** ne peut pas être [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilisé pour les comptes Windows. Les utilisateurs se connectant à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par l'intermédiaire de leur compte réseau Windows sont authentifiés par Windows ; par conséquent, leurs mots de passe ne peuvent être modifiés que dans Windows.  
  
     Pour plus d’informations, consultez [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER un utilisateur &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)   
 [CRÉER une connexion &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)   
 [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)   
 [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)   
 [sp_grantlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql)   
 [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)   
 [sys. sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)   
 [sys. syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
