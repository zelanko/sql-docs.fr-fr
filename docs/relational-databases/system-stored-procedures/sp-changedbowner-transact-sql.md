---
title: sp_changedbowner (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 1a38be84e5f1980b680d674e1c04c2ba95d1a537
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794297"
---
# <a name="spchangedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie le propriétaire de la base de données active.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @loginame=] '*connexion*'  
 ID de connexion du nouveau propriétaire de la base de données active. *connexion* est **sysname**, sans valeur par défaut. *connexion* doit être déjà un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ou un utilisateur de Windows. *connexion* ne peut pas devenir le propriétaire de la base de données actuelle si elle a déjà accès à la base de données via un compte de sécurité utilisateur existant dans la base de données. Pour éviter cela, supprimez d'abord l'utilisateur de la base de données active.  
  
 [ @map=] *remap_alias_flag*  
 Le *remap_alias_flag* paramètre est déconseillé, car l’alias de connexion ont été supprimés de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. À l’aide de la *remap_alias_flag* paramètre ne génère pas d’erreur mais n’a aucun effet.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Après l'exécution de sp_changedbowner, le nouveau propriétaire est reconnu comme l'utilisateur dbo dans la base de données. Le dbo a les autorisations implicites nécessaires pour effectuer toutes les activités dans la base de données.  
  
 Le propriétaire des bases de données système master, model et tempdb ne peut pas être changé.  
  
 Pour afficher une liste valide de *connexion* valeurs, exécutez la procédure stockée sp_helplogins.  
  
 L’exécution de sp_changedbowner avec uniquement le *connexion* modifications apportées aux paramètres de base de données de la propriété à *connexion*.  
  
 Vous pouvez modifier le propriétaire de tout élément sécurisable à l'aide de l'instruction ALTER AUTHORIZATION. Pour plus d’informations, consultez [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 L'autorisation TAKE OWNERSHIP est nécessaire sur la base de données. Si le nouveau propriétaire correspond à un utilisateur existant dans la base de données, l'autorisation IMPERSONATE est nécessaire sur la connexion d'accès ; sinon, l'autorisation CONTROL SERVER est nécessaire sur le serveur.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant le nom de connexion `Albert` devient propriétaire de la base de données active.  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sp_dropalias &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
