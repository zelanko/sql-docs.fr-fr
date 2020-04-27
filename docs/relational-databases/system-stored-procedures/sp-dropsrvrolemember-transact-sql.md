---
title: sp_dropsrvrolemember (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropsrvrolemember
- sp_dropsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropsrvrolemember
ms.assetid: 7be99181-d221-49d0-9cb2-c930d8c044a0
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 2624ed4800a247b0847adc5839346758aa50f140
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67463561"
---
# <a name="sp_dropsrvrolemember-transact-sql"></a>sp_dropsrvrolemember (Transact-SQL)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Supprime une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un utilisateur ou un groupe Windows d'un rôle serveur fixe.

> [!IMPORTANT]
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez à la place [ALTER Server Role](../../t-sql/statements/alter-server-role-transact-sql.md) .

![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntaxe

```
sp_dropsrvrolemember [ @loginame = ] 'login' , [ @rolename = ] 'role'  
```

## <a name="arguments"></a>Arguments

**[ @loginame = ]** «_connexion_»  
Nom d'une connexion à supprimer du rôle serveur fixe. *login* est de **type sysname**, sans valeur par défaut. la *connexion* doit exister.  

**[ @rolename = ]** «_role_»  
Nom d'un rôle serveur. *role* est de **type sysname**, avec NULL comme valeur par défaut. le *rôle* doit avoir l’une des valeurs suivantes :  

-   administrateur système  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin 
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Seul sp_dropsrvrolemember peut être utilisé pour supprimer une connexion d'un rôle serveur fixe. Utilisez sp_droprolemember pour supprimer un membre d'un rôle de base de données.  
  
 Impossible de supprimer la connexion sa d'un rôle serveur fixe.  
  
 La procédure sp_dropsrvrolemember ne peut pas être exécutée dans une transaction définie par l'utilisateur.  
  
## <a name="permissions"></a>Autorisations  
 Il faut appartenir au rôle serveur fixe sysadmin, ou bien disposer de l'autorisation ALTER ANY LOGIN et dans le même temps appartenir au rôle duquel le membre est supprimé.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la connexion `JackO` du rôle serveur fixe `sysadmin`.  
  
```sql
EXEC sp_dropsrvrolemember 'JackO', 'sysadmin';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER un rôle serveur &#40;&#41;Transact-SQL](../../t-sql/statements/create-server-role-transact-sql.md)   
 [SUPPRIMER un rôle serveur &#40;&#41;Transact-SQL](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [Procédures stockées de sécurité &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [Procédures stockées système &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
