---
title: sp_dropremotelogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropremotelogin
- sp_dropremotelogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropremotelogin
ms.assetid: 9f097652-a286-40b2-be73-568d77ada698
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: c316f48f3e590fcba419e125f8e327b25ee1ede6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933821"
---
# <a name="spdropremotelogin-transact-sql"></a>sp_dropremotelogin (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une connexion distante mappée sur une connexion locale utilisée pour exécuter des procédures stockées distantes sur le serveur local exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilisez plutôt des serveurs liés et des procédures stockées de serveurs liés.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_dropremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @remoteserver = ] 'remoteserver'` Est le nom du serveur distant mappé à la connexion à distance doit être supprimée. *RemoteServer* est **sysname**, sans valeur par défaut. *RemoteServer* doit déjà exister.  
  
`[ @loginame = ] 'login'` Est le nom de connexion facultatif sur le serveur local qui est associé avec le serveur distant. *login* est de type **sysname**, avec NULL comme valeur par défaut. *connexion* doit déjà exister si spécifié.  
  
`[ @remotename = ] 'remote_name'` Nom facultatif de la connexion distante qui est mappée à *connexion* lors de la connexion à partir du serveur distant. *nom_distant* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Si seuls *remoteserver* est spécifié, toutes les connexions à distance pour ce serveur distant sont supprimées du serveur local. Si *connexion* est également spécifiées, qui est distantes toutes les connexions à partir de *remoteserver* mappées sur cette connexion locale sont supprimées du serveur local. Si *nom_distant* est également spécifiée, seule la connexion à distance pour cet utilisateur à distance à partir de *remoteserver* est supprimé du serveur local.  
  
 Pour ajouter des utilisateurs du serveur local, utilisez **sp_addlogin**. Pour supprimer des utilisateurs du serveur local, utilisez **sp_droplogin**.  
  
 Les connexions distantes sont obligatoires uniquement lorsque vous utilisez des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 et les versions ultérieures utilisent à la place des connexions de serveurs liés. Utilisez **sp_addlinkedsrvlogin** et **sp_droplinkedsrvlogin** pour ajouter et supprimer des connexions de serveurs liés.  
  
 **sp_dropremotelogin** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **sysadmin** ou **securityadmin** rôles serveur fixes.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-dropping-all-remote-logins-for-a-remote-server"></a>R. Suppression de toutes les connexions distantes d'un serveur distant  
 Le code exemple suivant supprime l'entrée du serveur distant `ACCOUNTS`, supprimant ainsi tous les mappages entre les connexions sur le serveur local et les connexions distantes sur le serveur distant.  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-dropping-a-login-mapping"></a>B. Suppression d'un mappage de connexion  
 Le code exemple suivant supprime l'entrée qui mappe des connexions distantes du serveur distant `ACCOUNTS` sur la connexion locale `Albert`.  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-dropping-a-remote-user"></a>C. Suppression d'un utilisateur distant  
 Le code exemple suivant supprime la connexion de l'utilisateur distant `Chris` sur le serveur distant `ACCOUNTS` qui a été mappée sur l'utilisateur local `salesmgr`.  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
