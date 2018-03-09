---
title: sp_dropuser (Transact-SQL) | Documents Microsoft
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
- sp_dropuser
- sp_dropuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropuser
ms.assetid: e28f18f9-7ecf-4568-89f4-fe5c520df386
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 242950773bb0eabbd8b4170a05fd228311604bdf
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="spdropuser-transact-sql"></a>sp_dropuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un utilisateur de base de données à partir de la base de données actuelle. **sp_dropuser** assure la compatibilité avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropuser [ @name_in_db = ] 'user'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@name_in_db =**] **'***utilisateur***'**  
 Nom de l'utilisateur à supprimer. *utilisateur* est un **sysname**, sans valeur par défaut. *utilisateur* doit exister dans la base de données actuelle. Lorsque vous spécifiez une connexion Windows, utilisez le nom sous lequel la base de données connaît cette connexion.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropuser** exécute **sp_revokedbaccess** pour supprimer l’utilisateur à partir de la base de données actuelle.  
  
 Utilisez **sp_helpuser** pour afficher la liste des noms d’utilisateurs qui peuvent être supprimés de la base de données actuelle.  
  
 Lorsqu'un utilisateur de base de données est supprimé, les alias affectés à cet utilisateur sont également supprimés. Si l'utilisateur possède un schéma vide dont le nom est identique à celui de l'utilisateur, le schéma est supprimé. Si l'utilisateur possède d'autres éléments sécurisables dans la base de données, il n'est pas supprimé. La propriété des objets doit être auparavant transmise à un autre principal. Pour plus d’informations, consultez [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md). La suppression d'un utilisateur de base de données entraîne également la suppression automatique des autorisations associées à cet utilisateur ainsi que tous les rôles de base de données dont l'utilisateur est membre.  
  
 **sp_dropuser** ne peut pas être utilisé pour supprimer le propriétaire de la base de données (**dbo**) **INFORMATION_SCHEMA** les utilisateurs, ou le **invité** utilisateur à partir de la **master** ou **tempdb** bases de données. Dans les bases de données non-système, `EXEC sp_dropuser 'guest'` révoquer l’autorisation de se connecter à partir de l’utilisateur **invité**. Cependant, l'utilisateur lui-même n'est pas supprimé.  
  
 **sp_dropuser** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER ANY USER sur la base de données.  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant supprime l'utilisateur `Albert` de la base de données active.  
  
```  
EXEC sp_dropuser 'Albert';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [DROP USER &#40; Transact-SQL &#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
