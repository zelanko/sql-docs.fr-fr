---
title: sp_droprolemember (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprolemember_TSQL
- sp_droprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprolemember
ms.assetid: c2f19ab1-e742-4d56-ba8e-8ffd40cf4925
ms.author: vanto
author: VanMSFT
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7123c1bd3fee61a3d0671a0d8fbe27c2943ba7ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124851"
---
# <a name="spdroprolemember-transact-sql"></a>sp_droprolemember (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime un compte de sécurité d'un rôle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la base de données active.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  

### <a name="syntax-for-both-sql-server-and-azure-sql-database"></a>Syntaxe pour SQL Server et base de données SQL Azure

```  
sp_droprolemember [ @rolename = ] 'role' ,   
     [ @membername = ] 'security_account'  
```  

### <a name="syntax-for-both-azure-sql-data-warehouse-and-parallel-data-warehouse"></a>Syntaxe pour Azure SQL Data Warehouse et Parallel Data Warehouse

```  
sp_droprolemember 'role' ,  
     'security_account'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @rolename = ] 'role'` Est le nom du rôle à partir de laquelle le membre est supprimé. *rôle* est **sysname**, sans valeur par défaut. *rôle* doit exister dans la base de données actuelle.  
  
`[ @membername = ] 'security_account'` Le nom du compte de sécurité est supprimé du rôle. *celui-ci* est **sysname**, sans valeur par défaut. *celui-ci* peut être un utilisateur de base de données, un autre rôle de base de données, un compte de connexion Windows ou un groupe Windows. *celui-ci* doit exister dans la base de données actuelle.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 sp_droprolemember supprime un membre d’un rôle de base de données en supprimant une ligne de la table sysmembers. Lorsqu'un membre est supprimé d'un rôle, il perd toutes les autorisations accordées par son appartenance à ce rôle.  
  
 Pour supprimer un utilisateur d’un rôle serveur fixe, utilisez sp_dropsrvrolemember. Les utilisateurs ne peuvent pas être supprimés du rôle public, et dbo ne peut pas être supprimé dans aucun rôle.  
  
 Utilisez sp_helpuser pour afficher les membres d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôle et utilisez ALTER de rôle pour ajouter un membre à un rôle.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER sur le rôle.  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant supprime l'utilisateur `JonB` dans le rôle `Sales`.  
  
```sql
EXEC sp_droprolemember 'Sales', 'Jonb';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Le code exemple suivant supprime l'utilisateur `JonB` dans le rôle `Sales`.  
  
```sql
EXEC sp_droprolemember 'Sales', 'JonB'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

