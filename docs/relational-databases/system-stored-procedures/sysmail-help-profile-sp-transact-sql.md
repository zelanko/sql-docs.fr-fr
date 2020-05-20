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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 95660c293ef8a5efcca132407cd930ab0b721d89
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827419"
---
# <a name="sysmail_help_profile_sp-transact-sql"></a>sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie des informations sur un ou plusieurs profils de messagerie.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_id = ] profile_id`ID de profil pour lequel des informations doivent être retournées. *profile_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @profile_name = ] 'profile_name'`Nom du profil pour lequel des informations doivent être retournées. *profile_name* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne un jeu de résultats comportant les colonnes suivantes.  
  
||||  
|-|-|-|  
|Nom de la colonne|Type de données|Description|  
|**profile_id**|**int**|ID de profil du profil.|  
|**name**|**sysname**|Nom de profil du profil.|  
|**descriptive**|**nvarchar(256)**|Description du profil.|  
  
## <a name="remarks"></a>Remarques  
 Lorsqu’un nom de profil ou un ID de profil est spécifié, **sysmail_help_profile_sp** retourne des informations sur ce profil. Dans le cas contraire, **sysmail_help_profile_sp** retourne des informations sur chaque profil de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
 La procédure stockée **sysmail_help_profile_sp** se trouve dans la base de données **msdb** et appartient au schéma **dbo** . La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution pour cette procédure sont octroyées par défaut aux membres du rôle serveur fixe **sysadmin** .  
  
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
  
 **B. Affichage d'un profil spécifique**  
  
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
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
