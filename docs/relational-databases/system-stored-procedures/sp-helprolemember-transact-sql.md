---
title: sp_helprolemember (Transact-SQL) | Documents Microsoft
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
- sp_helprolemember_TSQL
- sp_helprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprolemember
ms.assetid: 42797510-aa5d-4564-85ac-27418419af9c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0d9b3b1a361b0e079d6c8d8fa844e86ed984fc66
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="sphelprolemember-transact-sql"></a>sp_helprolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les membres directs d'un rôle dans la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helprolemember [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@rolename =** ] **'** *rôle* **'**  
 Nom d'un rôle dans la base de données active. *rôle* est **sysname**, avec NULL comme valeur par défaut. *rôle* doit exister dans la base de données actuelle. Si *rôle* n’est pas spécifié, tous les rôles qui contiennent au moins un membre à partir de la base de données en cours sont retournées.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**DbRole**|**sysname**|Nom du rôle dans la base de données en cours.|  
|**Nom de membre**|**sysname**|Nom d’un membre de **DbRole.**|  
|**MemberSID**|**varbinary(85)**|Identificateur de sécurité de **MemberName.**|  
  
## <a name="remarks"></a>Notes  
 Si la base de données contient des rôles imbriqués, **MemberName** peut être le nom d’un rôle. **sp_helprolemember** n’affiche pas l’appartenance obtenue via des rôles imbriqués. Par exemple si User1 est membre de Role1, et Role1 est membre de Role2, `EXEC sp_helprolemember 'Role2'` ; retourne Role1, mais pas les membres de Role1 (User1 dans cet exemple). Pour obtenir les appartenances imbriquées, vous devez exécuter **sp_helprolemember** à plusieurs reprises pour chaque rôle imbriqué.  
  
 Utilisez **sp_helpsrvrolemember** pour afficher les membres d’un rôle de serveur fixe.  
  
 Utilisez [IS_ROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-rolemember-transact-sql.md) pour vérifier l’appartenance au rôle d’un utilisateur spécifié.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 Cet exemple affiche les membres du rôle `Sales`.  
  
```  
EXEC sp_helprolemember 'Sales';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helpsrvrolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
