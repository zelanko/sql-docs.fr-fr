---
title: sysmail_help_profile_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_profile_sp_TSQL
- sysmail_help_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profile_sp
ms.assetid: d7169a8e-92b1-49eb-9124-3b2f69755ddb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d8f2af3894377cc0922274ca26c231c003f3bd6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044499"
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
`[ @profile_id = ] profile_id` Identificateur du profil pour retourner des informations pour. *profile_id* est **int**, avec NULL comme valeur par défaut.  
  
`[ @profile_name = ] 'profile_name'` Le nom du profil pour retourner des informations pour. *nom_profil* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne un jeu de résultats comportant les colonnes suivantes.  
  
||||  
|-|-|-|  
|Nom de la colonne|Type de données|Description|  
|**profile_id**|**int**|L’id de profil pour le profil.|  
|**name**|**sysname**|Le nom du profil pour le profil.|  
|**description**|**nvarchar (256)**|La description du profil.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un nom de profil ou un id de profil est spécifié, **sysmail_help_profile_sp** retourne des informations sur ce profil. Sinon, **sysmail_help_profile_sp** retourne des informations sur chacun des profils dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
 La procédure stockée **sysmail_help_profile_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 **A. Afficher tous les profils**  
  
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
 [Procédures stockées de messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
