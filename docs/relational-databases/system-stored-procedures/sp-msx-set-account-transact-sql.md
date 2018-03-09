---
title: sp_msx_set_account (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d463863e71a0ba2899a987fdb425d08c8f5245a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="spmsxsetaccount-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit le nom du compte et le mot de passe du serveur maître de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sur le serveur cible.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@credential_name=** ] **'***credential_name***'**  
 Nom des informations d'identification à utiliser pour la connexion au serveur maître. Ce nom doit être celui d'informations d'identification existantes. Soit *credential_name* ou *credential_id* doit être spécifié.  
  
 [ **@credential_id=** ] *credential_id*  
 Identificateur des informations d'identification à utiliser pour la connexion au serveur maître. Il doit désigner des informations d'identification existantes. Soit *credential_name* ou *credential_id* doit être spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise les informations d’identification pour stocker les informations de nom et mot de passe utilisateur pour vous connecter à un serveur maître par un serveur cible. Cette procédure définit les informations d'identification utilisées par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de ce serveur cible pour se connecter au serveur maître.  
  
 Il doit s'agir d'informations d'identification existantes. Pour plus d’informations sur la création d’une information d’identification, consultez [CREATE CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-credential-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution **sp_msx_set_account** par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant configure ce serveur afin qu'il utilise les informations d'identification `MsxAccount` pour la connexion au serveur maître.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [L’Agent SQL Server stockées procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_get_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
