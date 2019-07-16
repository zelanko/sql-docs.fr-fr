---
title: sp_notify_operator (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 74558320df59414a756e1655bb073e9bf0d7d73c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107982"
---
# <a name="spnotifyoperator-transact-sql"></a>sp_notify_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Envoie un message électronique à un opérateur utilisant la messagerie de base de données.  
  
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_notify_operator  
    [ @profile_name = ] 'profilename' ,  
    [ @id = ] id ,  
    [ @name = ] 'name' ,  
    [ @subject = ] 'subject' ,  
    [ @body = ] 'message' ,  
    [ @file_attachments = ] 'attachment'  
    [ @mail_database = ] 'mail_host_database'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_name = ] 'profilename'` Le nom du profil de messagerie de base de données à utiliser pour envoyer le message. *ProfileName* est **nvarchar (128)** . Si *profilename* n’est pas spécifié, le profil de messagerie de base de données par défaut est utilisé.  
  
`[ @id = ] id` L’identificateur de l’opérateur à laquelle envoyer le message. *ID* est **int**, avec NULL comme valeur par défaut. Un des *id* ou *nom* doit être spécifié.  
  
`[ @name = ] 'name'` Le nom de l’opérateur auquel envoyer le message. *nom* est **nvarchar (128)** , avec NULL comme valeur par défaut. Un des *id* ou *nom* doit être spécifié.  
  
> **REMARQUE :** Une adresse de messagerie doit être définie pour l’opérateur qu’il puisse recevoir des messages.  
  
`[ @subject = ] 'subject'` Le sujet du message électronique. *objet* est **nvarchar (256)** sans valeur par défaut.  
  
`[ @body = ] 'message'` Le corps du message électronique. *message* est **nvarchar (max)** sans valeur par défaut.  
  
`[ @file_attachments = ] 'attachment'` Le nom d’un fichier à joindre au message électronique. *pièce jointe* est **nvarchar (512)** , sans valeur par défaut.  
  
`[ @mail_database = ] 'mail_host_database'` Spécifie le nom de la base de données hôte de messagerie. *mail_host_database* est **nvarchar (128)** . Si aucun *mail_host_database* est spécifié, le **msdb** base de données est utilisé par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Envoie le message spécifié à l'adresse de messagerie de l'opérateur choisi. Si l'opérateur ne dispose pas d'une adresse de messagerie, une erreur est renvoyée.  
  
 La messagerie de base de données et une base de données hôte de courrier doivent être configurées avant qu'une notification puisse être envoyée à un opérateur.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant envoie une notification par courrier électronique à l'opérateur `François Ajenstat` à l'aide du profil de messagerie de la base de données `AdventureWorks Administrator`. Le message électronique a pour objet `Test Notification`. Le message électronique contient la phrase « This is a test of notification via e-mail. ».  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_notify_operator  
   @profile_name = N'AdventureWorks Administrator',  
   @name = N'François Ajenstat',  
   @subject = N'Test Notification',  
   @body = N'This is a test of notification via e-mail.' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
