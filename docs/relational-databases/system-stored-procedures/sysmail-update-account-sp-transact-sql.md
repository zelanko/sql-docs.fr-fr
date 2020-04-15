---
title: sysmail_update_account_sp (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_account_sp
- sysmail_update_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_account_sp
ms.assetid: ba2fdccc-5ed4-40ef-a479-79497b4d61aa
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3dd772a1519ea856cac0302d31be9eb7d0f9d782
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283137"
---
# <a name="sysmail_update_account_sp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les informations dans un compte de messagerie de base de données existant.  
 
 
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_update_account_sp [ [ @account_id = ] account_id ] [ , ] [ [ @account_name = ] 'account_name' ] ,  
    [ @email_address = ] 'email_address' ,   
    [ @display_name = ] 'display_name' ,   
    [ @replyto_address = ] 'replyto_address' ,  
    [ @description = ] 'description' ,   
    [ @mailserver_name = ] 'server_name' ,   
    [ @mailserver_type = ] 'server_type' ,   
    [ @port = ] port_number ,   
    [ @timeout = ] 'timeout' ,  
    [ @username = ] 'username' ,  
    [ @password = ] 'password' ,  
    [ @use_default_credentials = ] use_default_credentials ,  
    [ @enable_ssl = ] enable_ssl   
```  
  
## <a name="arguments"></a>Arguments  
`[ @account_id = ] account_id`L’ID du compte à mettre à jour. *account_id* est **int**, avec un défaut de NULL. Au moins un des *account_id* ou *account_name* doit être spécifié. Si les deux arguments sont précisés, la procédure modifie le nom du compte.  
  
`[ @account_name = ] 'account_name'`Le nom du compte à mettre à jour. *account_name* est **sysname**, avec un défaut de NULL. Au moins un des *account_id* ou *account_name* doit être spécifié. Si les deux arguments sont précisés, la procédure modifie le nom du compte.  
  
`[ @email_address = ] 'email_address'`La nouvelle adresse e-mail pour envoyer le message de. Cette adresse doit être une adresse de messagerie Internet. Le nom de serveur figurant dans l'adresse identifie le serveur qu'utilise la messagerie de base de données pour envoyer le courrier à partir de ce compte. *email_address* est **nvarchar(128)**, avec un défaut de NULL.  
  
`[ @display_name = ] 'display_name'`Le nouveau nom d’affichage à utiliser sur les messages électroniques de ce compte. *display_name* est **nvarchar(128)**, sans défaut.  
  
`[ @replyto_address = ] 'replyto_address'`La nouvelle adresse à utiliser dans l’en-tête De Réponse à des messages électroniques à partir de ce compte. *replyto_address* est **nvarchar(128)**, sans défaut.  
  
`[ @description = ] 'description'`La nouvelle description du compte. *description* est **nvarchar(256)**, avec un défaut de NULL.  
  
`[ @mailserver_name = ] 'server_name'`Le nouveau nom du serveur de messagerie SMTP à utiliser pour ce compte. L’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s’exécute doit être en mesure de résoudre le *server_name* à une adresse IP. *server_name* est **sysname**, sans défaut.  
  
`[ @mailserver_type = ] 'server_type'`Le nouveau type de serveur de messagerie. *server_type* est **sysname**, sans défaut. Seule une valeur de **'SMTP'** est prise en charge.  
  
`[ @port = ] port_number`Le nouveau numéro de port du serveur de messagerie. *port_number* est **int**, sans défaut.  
  
`[ @timeout = ] 'timeout'`Paramètre de délai d’attente pour SmtpClient.Send d’un seul message électronique. *Le délai d’attente* est **int** en quelques secondes, sans défaut.  
  
`[ @username = ] 'username'`Le nouveau nom d’utilisateur à utiliser pour se connecter au serveur de messagerie. *Nom d’utilisateur* est **sysname**, sans défaut.  
  
`[ @password = ] 'password'`Le nouveau mot de passe à utiliser pour se connecter au serveur de messagerie. *mot de passe* est **sysname**, sans défaut.  
  
`[ @use_default_credentials = ] use_default_credentials`Précise s’il faut envoyer le courrier au serveur SMTP en utilisant les informations d’identification du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service. **use_default_credentials** est un peu, sans défaut. Lorsque la valeur de ce paramètre est définie sur 1, la messagerie de base de données utilise les informations d'identification du moteur de base de données [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Lorsque ce paramètre est 0, Database Mail utilise le ** \@nom d’utilisateur** et ** \@** le mot de passe pour l’authentification sur le serveur SMTP. Si ** \@le nom d’utilisateur** et ** \@le mot de passe** sont NULL alors il utilisera l’authentification anonyme. Contactez votre administrateur SMTP avant de définir ce paramètre.  
  
`[ @enable_ssl = ] enable_ssl`Précise si Database Mail crypte la communication à l’aide de transport Layer Security (TLS), précédemment connu sous le nom de Couche de prises sécurisées (SSL). Utilisez cette option si TLS est nécessaire sur votre serveur SMTP. **enable_ssl** est un peu, sans défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Lorsque le nom et l'ID du compte sont tous deux spécifiés, la procédure stockée change le nom du compte en plus de mettre à jour les autres informations du compte. Il peut s'avérer nécessaire de modifier le nom du compte pour corriger des erreurs qui s'y seraient glissées.  
  
 La procédure stockée **sysmail_update_account_sp** se trouve dans la base de données **msdb** et appartient au **schéma dbo.** La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle **n’est**pas msdb .  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’adhésion au rôle de serveur fixe **sysadmin.**  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-the-information-for-an-account"></a>R. Modification des informations d'un compte  
 L’exemple suivant `AdventureWorks Administrator` met à jour le compte Dans la base de données **msdb.** Les informations du compte prennent les valeurs fournies.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_name = 'AdventureWorks Administrator'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
### <a name="b-changing-the-name-of-an-account-and-the-information-for-an-account"></a>B. Modification du nom d'un compte et des informations qui s'y rapportent  
 L'exemple suivant modifie le nom du compte et le met à jour avec l'ID de compte `125`. Le nouveau nom du compte est `Backup Mail Server`.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_id = 125  
    ,@account_name = 'Backup Mail Server'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp-backup.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Courrier de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Procédures stockées par courrier de base de données &#40;&#41;de Transact-SQL](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
