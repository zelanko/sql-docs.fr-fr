---
title: sp_srvrolepermission (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/20/2017
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
- sp_srvrolepermission_TSQL
- sp_srvrolepermission
dev_langs:
- TSQL
helpviewer_keywords:
- sp_srvrolepermission
ms.assetid: 5709667f-e3e4-48a2-93ec-af5e22a2ac58
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a2cf4b670588739a7c6232b27bf6a592ef82daaa
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="spsrvrolepermission-transact-sql"></a>sp_srvrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche les autorisations d'un rôle serveur fixe.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_srvrolepermission [ [ @srvrolename = ] 'role']  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@srvrolename =** ] **'***rôle***'**  
 Nom du rôle serveur fixe pour lequel les autorisations sont retournées. *rôle* est **sysname**, avec NULL comme valeur par défaut. Si aucun rôle n'est spécifié, les autorisations de tous les rôles serveur fixes sont retournées. *rôle* peut avoir l’une des valeurs suivantes.  
  
|Valeur| Description|  
|-----------|-----------------|  
|**sysadmin**|Administrateurs système|  
|**securityadmin**|Administrateurs de la sécurité|  
|**serveradmin**|Administrateurs du serveur|  
|**setupadmin**|Administrateurs de l'installation et de la configuration|  
|**processadmin**|Administrateurs de processus|  
|**diskadmin**|Administrateurs de disques|  
|**dbcreator**|Créateurs de bases de données|  
|**bulkadmin**|Exécute les instructions BULK INSERT.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**ServerRole**|**sysname**|Nom d'un rôle serveur fixe|  
|**Autorisation**|**sysname**|Autorisation associée **ServerRole**|  
  
## <a name="remarks"></a>Notes  
 Les autorisations répertoriées comprennent les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qu'il est possible d'exécuter, ainsi que d'autres actions spéciales que les membres du rôle serveur fixe sont en mesure d'accomplir. Pour afficher une liste des rôles serveur fixes, exécutez **sp_helpsrvrole**.  
  
 Le **sysadmin** rôle serveur fixe dispose des autorisations de tous les autres rôles de serveur fixe.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 La requête suivante retourne les autorisations associées au rôle serveur fixe `sysadmin`.  
  
```  
EXEC sp_srvrolepermission 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrole &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
