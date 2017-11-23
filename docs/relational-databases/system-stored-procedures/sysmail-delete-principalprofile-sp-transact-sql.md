---
title: sysmail_delete_principalprofile_sp (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ae436f9fc0abe27d4395bd64ef914858f8cd9e3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysmaildeleteprincipalprofilesp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime l'autorisation d'utilisation d'un profil de messagerie de base de données public ou privé pour un utilisateur de base de données ou un rôle de base de données.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@principal_id**  =] *principal_id*  
 Est l’ID de l’utilisateur de base de données ou d’un rôle dans le **msdb** base de données pour l’association à supprimer. *principal_id* est **int**, avec NULL comme valeur par défaut. Pour rendre un profil public en profil privé, fournissez l’identificateur principal **0** ou le nom principal **'public'**. Soit *principal_id* ou *principal_name* doit être spécifié.  
  
 [  **@principal_name**  =] **'***principal_name***'**  
 Est le nom de l’utilisateur de base de données ou d’un rôle dans le **msdb** base de données pour l’association à supprimer. *principal_name* est **sysname**, avec NULL comme valeur par défaut. Pour rendre un profil public en profil privé, fournissez l’identificateur principal **0** ou le nom principal **'public'**. Soit *principal_id* ou *principal_name* doit être spécifié.  
  
 [  **@profile_id**  =] *profile_id*  
 Identificateur du profil pour l'association à supprimer. *profile_id* est **int**, avec NULL comme valeur par défaut. Soit *profile_id* ou *profile_name* doit être spécifié.  
  
 [  **@profile_name**  =] **'***profile_name***'**  
 Nom du profil pour l'association à supprimer. *profile_name* est **sysname**, avec NULL comme valeur par défaut. Soit *profile_id* ou *profile_name* doit être spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Pour rendre un profil public en profil privé, fournissez **'public'** pour le nom principal ou **0** pour l’id du principal.  
  
 Soyez prudent lorsque vous supprimez des autorisations pour le profil privé par défaut d'un utilisateur ou pour le profil public par défaut. Si aucun profil par défaut n’est disponible, **sp_send_dbmail** exige que le nom d’un profil en tant qu’argument. Par conséquent, la suppression d’un profil par défaut peut provoquer des appels à **sp_send_dbmail** échec. Pour plus d’informations, consultez [sp_send_dbmail &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 La procédure stockée **sysmail_delete_principalprofile_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant illustre la suppression de l’association entre le profil **AdventureWorks Administrator** et la connexion **ApplicationUser** dans les **msdb** base de données.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Objets de Configuration de messagerie de base de données](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Messagerie de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
