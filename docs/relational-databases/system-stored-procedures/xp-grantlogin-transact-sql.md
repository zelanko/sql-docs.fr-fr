---
title: xp_grantlogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_grantlogin
- xp_grantlogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_grantlogin
ms.assetid: c851c1ab-3b29-4b99-9902-78c2665a844b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c6a6e31b4dc36e0f280dfb03d8eadf09a7d4ff7c
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534861"
---
# <a name="xpgrantlogin-transact-sql"></a>xp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Autorise un groupe ou un utilisateur Windows à accéder à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xp_grantlogin {[@loginame = ] 'login'} [,[@logintype = ] 'logintype']  
```  
  
## <a name="arguments"></a>Arguments  
`[ @loginame = ] 'login'` Est le nom de l’utilisateur de Windows ou le groupe à ajouter. L’utilisateur de Windows ou le groupe doit être qualifié avec un nom de domaine Windows sous la forme *domaine*\\*utilisateur*. *connexion* est **sysname**, sans valeur par défaut.  
  
`[ @logintype = ] 'logintype'` Le niveau de sécurité de la connexion en cours a accès. *le LoginType* est **varchar (5)**, avec NULL comme valeur par défaut. Uniquement **administrateur** peut être spécifié. Si **administrateur** est spécifié, *connexion* a accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et ajouté en tant que membre de la **sysadmin** rôle serveur fixe.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **xp_grantlogin** est maintenant un système de procédure stockée au lieu une procédure stockée étendue. **xp_grantlogin** appels **sp_grantlogin** et **sp_addsrvrolemember**.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **securityadmin** rôle serveur fixe. Lorsque vous modifiez le *logintype*, nécessite l’appartenance dans le **sysadmin** rôle serveur fixe.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées étendues générales &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_enumgroups &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-enumgroups-transact-sql.md)   
 [xp_loginconfig &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)  
  
  
