---
title: sysmail_help_account_sp (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccb5cfd245148c97288a34b1857955f48f3efc73
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528408"
---
# <a name="sysmail_help_account_sp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les informations (à l'exception des mots de passe) relatifs aux comptes de messagerie de base de données.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @account_id = ] account_id`L’ID de compte du compte pour la liste des informations pour. *account_id* est **int**, avec un défaut de NULL.  
  
`[ @account_name = ] 'account_name'`Le nom du compte pour la liste des informations pour. *account_name* est **sysname**, avec un défaut de NULL.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne un jeu de résultats contenant les colonnes répertoriées ci-après.  
  
||||  
|-|-|-|  
|Nom de la colonne|Type de données|Description|  
|**account_id**|**int**|Identificateur du compte.|  
|**name**|**sysname**|Nom du compte|  
|**Description**|**nvarchar(256)**|Description du compte.|  
|**email_address**|**nvarchar(128)**|Adresse électronique à partir de laquelle les messages sont envoyés.|  
|**display_name**|**nvarchar(128)**|Nom d'affichage du compte|  
|**replyto_address**|**nvarchar(128)**|L’adresse où les réponses aux messages de ce compte sont envoyées.|  
|**servertype**|**sysname**|Type de serveur de messagerie pour le compte.|  
|**Servername**|**sysname**|Nom du serveur de messagerie pour le compte.|  
|**Port**|**int**|Numéro de port utilisé par le serveur de messagerie.|  
|**username**|**nvarchar(128)**|Nom d'utilisateur à utiliser pour se connecter au serveur de messagerie, si ce serveur utilise l'authentification. Lorsque **le nom d’utilisateur** est NULL, Database Mail n’utilise pas d’authentification pour ce compte.|  
|**use_default_credentials**|**bit**|Spécifie si le courrier électronique doit être envoyé au serveur SMTP en utilisant les informations d'identification du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** est un peu, sans défaut. Lorsque ce paramètre est 1, Database [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Mail utilise les informations d’identification du service. Lorsque ce paramètre est 0, Database Mail utilise le ** \@nom d’utilisateur** et ** \@** le mot de passe pour l’authentification sur le serveur SMTP. Si ** \@le nom d’utilisateur** et ** \@le mot de passe** sont NULL, le courrier de base de données utilise l’authentification anonyme. Consultez votre administrateur SMTP avant de spécifier ce paramètre.|  
|**enable_ssl**|**bit**|Précise si Database Mail crypte la communication à l’aide de transport Layer Security (TLS), précédemment connu sous le nom de Couche de prises sécurisées (SSL). Utilisez cette option si TLS est nécessaire sur votre serveur SMTP. **enable_ssl** est un peu, sans défaut. 1 indique que Database Mail crypte la communication à l’aide de TLS. 0 indique que Database Mail envoie le courrier sans cryptage TLS.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’aucune *account_id* ou *account_name* n’est fournie, **sysmail_help_account** répertorie les informations sur tous les comptes Database Mail dans l’instance Microsoft SQL Server.  
  
 La procédure stockée **sysmail_help_account_sp** se trouve dans la base de données **msdb** et appartient au **schéma dbo.** La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle **n’est**pas msdb .  
  
## <a name="permissions"></a>Autorisations  
 Exécutez les autorisations pour cette procédure par défaut aux membres du rôle de serveur fixe **sysadmin.**  
  
## <a name="examples"></a>Exemples  
 **A. Affichage d'informations relatives à tous les comptes**  
  
 L'exemple suivant illustre comment répertorier les informations relatives à tous les comptes de l'instance.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp ;  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- --------------------------------------- ------------------------- -------------------------------- --------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
149         Audit Account                Account for audit e-mail.               audit@Adventure-Works.com Automated Mailer (Audit)         NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
```  
  
 **B. Affichage d’informations sur un compte spécifique**  
  
 L'exemple suivant illustre comment répertorier les informations relatives au compte nommé `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- ------------------------------------------------------ ------------------------- ---------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL     0                       0       
```  
  
## <a name="see-also"></a>Voir aussi  
 [Courrier de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Procédures stockées par courrier de base de données &#40;&#41;de Transact-SQL](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
