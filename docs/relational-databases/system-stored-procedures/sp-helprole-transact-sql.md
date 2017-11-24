---
title: sp_helprole (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helprole_TSQL
- sp_helprole
dev_langs: TSQL
helpviewer_keywords: sp_helprole
ms.assetid: b023103f-ccf3-44e2-b418-4be9bdd49f4a
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a912cb79346ea35e7da110ed336138231e28ee1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sphelprole-transact-sql"></a>sp_helprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie les informations concernant les rôles de la base de données active.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helprole [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@rolename =** ] **'***rôle***'**  
 Nom d'un rôle dans la base de données active. *rôle* est **sysname**, avec NULL comme valeur par défaut. *rôle* doit exister dans la base de données actuelle. Si *rôle* est ne pas spécifié, informations sur tous les rôles de base de données active sont renvoyées.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**RoleName**|**sysname**|Nom du rôle dans la base de données en cours.|  
|**RoleId**|**smallint**|ID de **RoleName**.|  
|**IsAppRole**|**int**|0 = **RoleName** n’est pas un rôle d’application.<br /><br /> 1 = **RoleName** est un rôle d’application.|  
  
## <a name="remarks"></a>Notes  
 Pour afficher les autorisations associées au rôle, utilisez **sp_helprotect**. Pour afficher les membres d’un rôle de base de données, utilisez **sp_helprolemember**.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 La requête suivante renvoie tous les rôles de la base de données active.  
  
```  
EXEC sp_helprole  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md)   
 [sp_addapprole &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [sp_droprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_helprolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [sp_helpsrvrolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
