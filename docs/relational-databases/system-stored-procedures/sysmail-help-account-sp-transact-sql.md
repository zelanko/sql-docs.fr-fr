---
title: sysmail_help_account_sp (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 857e4139081833980ee6c90eca9d90d16d4c0ad2
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305144"
---
# <a name="sysmail_help_account_sp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les informations (à l'exception des mots de passe) relatifs aux comptes de messagerie de base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @account_id = ] account_id` ID du compte pour lequel répertorier les informations. *account_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @account_name = ] 'account_name'` nom du compte pour lequel répertorier les informations. *nom_de_compte* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne un jeu de résultats contenant les colonnes répertoriées ci-après.  
  
||||  
|-|-|-|  
|Nom de la colonne|Type de données|Description|  
|**account_id**|**Int**|Identificateur du compte.|  
|**name**|**sysname**|Nom du compte|  
|**description**|**nvarchar (256)**|Description du compte.|  
|**email_address**|**nvarchar(128)**|Adresse électronique à partir de laquelle les messages sont envoyés.|  
|**display_name**|**nvarchar(128)**|Nom d'affichage du compte|  
|**replyto_address**|**nvarchar(128)**|Adresse à laquelle les réponses aux messages de ce compte sont envoyées.|  
|**servertype**|**sysname**|Type de serveur de messagerie pour le compte.|  
|**servername**|**sysname**|Nom du serveur de messagerie pour le compte.|  
|**port**|**Int**|Numéro de port utilisé par le serveur de messagerie.|  
|**username**|**nvarchar(128)**|Nom d'utilisateur à utiliser pour se connecter au serveur de messagerie, si ce serveur utilise l'authentification. Lorsque **username** a la valeur NULL, Database mail n’utilise pas l’authentification pour ce compte.|  
|**use_default_credentials**|**bit**|Spécifie si le courrier électronique doit être envoyé au serveur SMTP en utilisant les informations d'identification du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** est de bits, sans valeur par défaut. Lorsque ce paramètre a la valeur 1, Database Mail utilise les informations d’identification du service [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Lorsque ce paramètre a la valeur 0, Database Mail utilise les **\@username** et **\@password** pour l’authentification sur le serveur SMTP. Si **\@username** et **\@password** sont NULL, Database mail utilise l’authentification anonyme. Consultez l’administrateur SMTP avant de spécifier ce paramètre.|  
|**enable_ssl**|**bit**|Spécifie si la messagerie de base de données chiffre les communications à l'aide de la technologie SSL (Secure Sockets Layer). Utilisez cette option si SSL est obligatoire sur votre serveur SMTP. **enable_ssl** est de bits, sans valeur par défaut. 1 indique que la messagerie de base de données chiffre les communications au moyen de SSL tandis que la valeur 0 indique qu'elle envoie le courrier sans le chiffrement SSL.|  
  
## <a name="remarks"></a>Notes  
 Quand aucun *account_id* ou *nom_de_compte* n’est fourni, **sysmail_help_account** répertorie des informations sur tous les comptes de Database mail dans l’instance Microsoft SQL Server.  
  
 La procédure stockée **sysmail_help_account_sp** se trouve dans la base de données **msdb** et appartient au schéma **dbo** . La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution pour cette procédure sont octroyées par défaut aux membres du rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 **A. Affichage des informations pour tous les comptes @ no__t-0  
  
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
  
 **B. Affichage des informations relatives à un compte spécifique @ no__t-0  
  
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
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Créer un compte Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Procédures &#40;stockées Database mail Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
