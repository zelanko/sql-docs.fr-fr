---
title: sysmail_update_principalprofile_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_update_principalprofile_sp
- sysmail_update_principalprofile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_principalprofile_sp
ms.assetid: 9fe96e9a-4758-4e4a-baee-3e1217c4426c
caps.latest.revision: 46
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: e4e6a55660f3b5a4acc17147de269271fd2c2b1f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022768"
---
# <a name="sysmailupdateprincipalprofilesp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Met à jour les informations d'une association entre un principal et un profil.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_update_principalprofile_sp { @principal_id = principal_id | @principal_name = 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    [ @is_default = ] 'is_default'  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@principal_id** =] *principal_id*  
 L’ID de l’utilisateur de base de données ou d’un rôle dans le **msdb** base de données pour l’association à modifier. *principal_id* est **int**, avec NULL comme valeur par défaut. Soit *principal_id* ou *principal_name* doit être spécifié.  
  
 [ **@principal_name** =] **'***principal_name***'**  
 Le nom de l’utilisateur de base de données ou d’un rôle dans le **msdb** base de données pour l’association à mettre à jour. *principal_name* est **sysname**, avec NULL comme valeur par défaut. Soit *principal_id* ou *principal_name* peut être spécifié.  
  
 [ **@profile_id** =] *profile_id*  
 Identificateur du profil pour l'association à modifier. *profile_id* est **int**, avec NULL comme valeur par défaut. Soit *profile_id* ou *profile_name* doit être spécifié.  
  
 [ **@profile_name** =] **'***profile_name***'**  
 Nom du profil pour l'association à modifier. *nom_profil* est **sysname**, avec NULL comme valeur par défaut. Soit *profile_id* ou *profile_name* doit être spécifié.  
  
 [ **@is_default** =] **'***is_default***'**  
 Indique si ce profil représente le profil par défaut pour l'utilisateur de la base de données. Un utilisateur de base de données ne peut avoir plus d'un seul profil par défaut. *is_default* est **bits**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Cette procédure stockée est modifiée si le profil spécifié est ou non le profil par défaut pour l'utilisateur de la base de données. Un utilisateur de base de données peut avoir uniquement un profil privé par défaut.  
  
 Lorsque le nom principal de l’association est **public** ou l’id du principal pour l’association est **0**, cette procédure stockée modifie le profil public. Il ne peut y avoir qu'un seul profil public par défaut.  
  
 Lorsque **@is_default** est «**1**» et le principal est associé à plusieurs profils, le profil spécifié devient le profil par défaut pour le principal. Le précédent profil par défaut est toujours associé au principal, mais il ne représente plus le profil par défaut.  
  
 La procédure stockée **sysmail_update_principalprofile_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 **A. Définition du profil public par défaut pour une base de données**  
  
 L’exemple suivant définit le profil `General Use Profile` le profil public par défaut pour les utilisateurs dans le **msdb** base de données.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'General Use Profile',  
    @is_default = '1';  
```  
  
 **B. Définition du profil privé par défaut pour un utilisateur**  
  
 L’exemple suivant définit le profil `AdventureWorks Administrator` à définir comme profil par défaut pour le principal `ApplicationUser` dans le **msdb** base de données. Le profil doit déjà être associé au principal. Le précédent profil par défaut est toujours associé au principal, mais il ne représente plus le profil par défaut.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator',  
    @is_default = '1' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Objets de Configuration de messagerie de base de données](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Procédures stockées de messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
