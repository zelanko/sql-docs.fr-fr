---
title: sp_helpsrvrolemember (Transact-SQL) | Microsoft Docs
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
- sp_helpsrvrolemember
- sp_helpsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsrvrolemember
ms.assetid: d0714913-8d6b-4de3-b042-3ae9934f839d
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4bbc6ed2343b9a659b30b737135c9f28cb2b401b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43035233"
---
# <a name="sphelpsrvrolemember-transact-sql"></a>sp_helpsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur les membres d'un rôle serveur fixe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpsrvrolemember [ [ @srvrolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@srvrolename =** ] **'***rôle***'**  
 Nom d'un rôle serveur fixe. *rôle* est **sysname**, avec NULL comme valeur par défaut. Si *rôle*n’est pas spécifié, le jeu de résultats inclut des informations sur tous les rôles serveur fixes.  
  
 *rôle* peut être une des valeurs suivantes.  
  
|Rôle serveur fixe|Description|  
|-----------------------|-----------------|  
|sysadmin|Administrateurs système|  
|securityadmin|Administrateurs de la sécurité|  
|serveradmin|Administrateurs du serveur|  
|setupadmin|Administrateurs de l'installation et de la configuration|  
|processadmin|Administrateurs de processus|  
|diskadmin|Administrateurs de disques|  
|dbcreator|Créateurs de bases de données|  
|bulkadmin|Exécute les instructions BULK INSERT.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|ServerRole|**sysname**|Nom du rôle de serveur|  
|MemberName|**sysname**|Nom d’un membre du rôle serveur|  
|MemberSID|**varbinary(85)**|Identificateur de sécurité de MemberName|  
  
## <a name="remarks"></a>Notes  
 Utilisez sp_helprolemember pour afficher les membres d’un rôle de base de données.  
  
 Toutes les connexions sont un membre public. sp_helpsrvrolemember ne reconnaît pas le rôle public, car, en interne, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’implémente pas publique en tant que rôle.  
  
 Pour ajouter ou de membres supprimés à partir de rôles de serveur, consultez [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 sp_helpsrvrolemember n’accepte pas un rôle de serveur défini par l’utilisateur en tant qu’argument. Pour déterminer les membres d’un rôle de serveur défini par l’utilisateur, consultez les exemples de [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant permet d'énumérer les membres du rôle serveur fixe `sysadmin`.  
  
```  
EXEC sp_helpsrvrolemember 'sysadmin';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_helprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
