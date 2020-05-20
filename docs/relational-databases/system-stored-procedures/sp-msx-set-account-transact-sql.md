---
title: sp_msx_set_account (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a1ba416b8e23bb56879e492e2970414f56e92776
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834385"
---
# <a name="sp_msx_set_account-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit le nom du compte et le mot de passe du serveur maître de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sur le serveur cible.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>Arguments  
`[ @credential_name = ] 'credential_name'`Nom des informations d’identification à utiliser pour se connecter au serveur maître. Ce nom doit être celui d'informations d'identification existantes. *Credential_name* ou *credential_id* doivent être spécifiés.  
  
`[ @credential_id = ] credential_id`Identificateur des informations d’identification à utiliser pour se connecter au serveur maître. Il doit désigner des informations d'identification existantes. *Credential_name* ou *credential_id* doivent être spécifiés.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des informations d'identification pour stocker le nom d'utilisateur et le mot de passe qu'un serveur cible utilise pour se connecter à un serveur maître. Cette procédure définit les informations d'identification utilisées par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de ce serveur cible pour se connecter au serveur maître.  
  
 Il doit s'agir d'informations d'identification existantes. Pour plus d’informations sur la création d’informations d’identification, consultez [Create credential &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution pour **sp_msx_set_account** par défaut aux membres du rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant configure ce serveur afin qu'il utilise les informations d'identification `MsxAccount` pour la connexion au serveur maître.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Agent des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CRÉER des informations d’identification &#40;&#41;Transact-SQL](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_get_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
