---
title: sysmail_help_profile_sp (Transact-SQL) | Microsoft Docs
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
- sysmail_help_profile_sp_TSQL
- sysmail_help_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profile_sp
ms.assetid: d7169a8e-92b1-49eb-9124-3b2f69755ddb
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 486d0b8e494cd4602c519cc6659460ea6ebef5b7
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysmailhelpprofilesp-transact-sql"></a>sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie des informations sur un ou plusieurs profils de messagerie.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@profile_id**  =] *profile_id*  
 Identificateur du profil pour lequel des informations doivent être renvoyées. *profile_id* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@profile_name**  =] **'***profile_name***'**  
 Nom du profil pour lequel des informations doivent être renvoyées. *profile_name* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne un jeu de résultats comportant les colonnes suivantes.  
  
||||  
|-|-|-|  
|Nom de colonne|Type de données| Description|  
|**profile_id**|**int**|Identificateur du profil pour le profil.|  
|**nom**|**sysname**|Le nom du profil pour le profil.|  
|**description**|**nvarchar (256)**|La description du profil.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un nom de profil ou d’un id de profil est spécifié, **sysmail_help_profile_sp** retourne des informations sur ce profil. Dans le cas contraire, **sysmail_help_profile_sp** retourne des informations sur tous les profils dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
 La procédure stockée **sysmail_help_profile_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 **A. Affichage de tous les profils**  
  
 Cet exemple montre comment afficher tous les profils de l'instance.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp;  
```  
  
 Exemple d'un ensemble de résultats remis en forme au niveau de la longueur de ligne :  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
57          AdventureWorks Operator       Operator mail profile.          
```  
  
 **B. Affichage d’un profil spécifique**  
  
 Cet exemple montre comment afficher des informations pour le profil `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Exemple d'un ensemble de résultats remis en forme au niveau de la longueur de ligne :  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Messagerie de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
