---
title: sp_defaultdb (Transact-SQL) | Documents Microsoft
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
- sp_defaultdb_TSQL
- sp_defaultdb
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultdb
ms.assetid: 663b859f-c6da-4942-95a6-60b93d05654e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c44a3f1f26861e3e78e936aeb642e33ead4a4786
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="spdefaultdb-transact-sql"></a>sp_defaultdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie la base de données par défaut pour un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_defaultdb [ @loginame = ] 'login', [ @defdb = ] 'database'   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@loginame=**] **'***connexion***'**  
 Est le nom de connexion. *connexion* est **sysname**, sans valeur par défaut. *connexion* peut être un existant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ou un utilisateur ou groupe Windows. Si la connexion de l'utilisateur ou du groupe Windows n'existe pas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], elle est automatiquement ajoutée.  
  
 [  **@defdb=**] **'***base de données***'**  
 Nom de la nouvelle base de données par défaut. *base de données* est **sysname**, sans valeur par défaut. *base de données* doit déjà exister.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_defaultdb** appelle ALTER LOGIN. Cette instruction prend en charge d'autres options. Pour plus d’informations sur la modification de la base de données par défaut, consultez [ALTER LOGIN &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-login-transact-sql.md).  
  
 **sp_defaultdb** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER ANY LOGIN.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant définit [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] en tant que base de données par défaut pour le nom de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Victoria`.  
  
```  
EXEC sp_defaultdb 'Victoria', 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
