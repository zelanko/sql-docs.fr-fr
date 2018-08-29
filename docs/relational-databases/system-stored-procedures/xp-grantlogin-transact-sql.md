---
title: xp_grantlogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: fdf810b4039dd022d444cfc119e3b2d018395469
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023171"
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
 [  **@loginame =** ] **'***connexion***'**  
 Nom de l'utilisateur ou du groupe Windows à ajouter. L’utilisateur de Windows ou le groupe doit être qualifié avec un nom de domaine Windows sous la forme *domaine*\\*utilisateur*. *connexion* est **sysname**, sans valeur par défaut.  
  
 [  **@logintype =** ] **'***logintype***'**  
 Niveau de sécurité du nom de connexion auquel l'accès est accordé. *le LoginType* est **varchar (5)**, avec NULL comme valeur par défaut. Uniquement **administrateur** peut être spécifié. Si **administrateur** est spécifié, *connexion* a accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et ajouté en tant que membre de la **sysadmin** rôle serveur fixe.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **xp_grantlogin** est maintenant un système de procédure stockée au lieu une procédure stockée étendue. **xp_grantlogin** appels **sp_grantlogin** et **sp_addsrvrolemember**.  
  
## <a name="permissions"></a>Permissions  
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
  
  
