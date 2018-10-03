---
title: sysmail_help_profileaccount_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_profileaccount_sp_TSQL
- sysmail_help_profileaccount_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profileaccount_sp
ms.assetid: 3ea68271-0a6b-4d77-991c-4757f48f747a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 779519ef5ba3098e205a70d8c5923adc993f44f6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700748"
---
# <a name="sysmailhelpprofileaccountsp-transact-sql"></a>sysmail_help_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche les comptes associés à un ou plusieurs profils de messagerie de base de données.  
    
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_profileaccount_sp  
   {   [ @profile_id = ] profile_id   
      | [ @profile_name = ] 'profile_name' }  
   [ , {   [ @account_id = ] account_id  
         | [ @account_name = ] 'account_name' } ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@profile_id** =] *profile_id*  
 ID du profil à répertorier. *profile_id* est **int**, avec NULL comme valeur par défaut. Soit *profile_id* ou *profile_name* doit être spécifié.  
  
 [ **@profile_name** =] **'***profile_name***'**  
 Nom du profil à répertorier. *nom_profil* est **sysname**, avec NULL comme valeur par défaut. Soit *profile_id* ou *profile_name* doit être spécifié.  
  
 [ **@account_id** =] *account_id*  
 ID du compte à répertorier. *account_id* est **int**, avec NULL comme valeur par défaut. Lorsque *account_id* et *account_name* sont les deux NULL, répertorie tous les comptes dans le profil.  
  
 [ **@account_name** =] **'***account_name***'**  
 Nom du compte à répertorier. *nom_compte* est **sysname**, avec NULL comme valeur par défaut. Lorsque *account_id* et *account_name* sont les deux NULL, répertorie tous les comptes dans le profil.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne un jeu de résultats comportant les colonnes suivantes.  
  
||||  
|-|-|-|  
|Nom de colonne|Type de données|Description|  
|**profile_id**|**Int**|Identificateur du profil du profil.|  
|**nom_profil**|**sysname**|Nom du profil|  
|**account_id**|**Int**|ID du compte.|  
|**account_name**|**sysname**|Nom du compte|  
|**sequence_number**|**Int**|Numéro de séquence du compte dans le profil.|  
  
## <a name="remarks"></a>Notes  
 En cas de non *profile_id* ou *profile_name* est spécifié, cette procédure stockée retourne des informations pour chaque profil dans l’instance.  
  
 La procédure stockée **sysmail_help_profileaccount_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 **A. Liste des comptes d’un profil spécifique par nom**  
  
 L'exemple suivant affiche la liste des informations pour le profil `AdventureWorks Administrator` en spécifiant le nom du profil.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp  
   @profile_name = 'AdventureWorks Administrator';  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
```  
  
 **B. Liste des comptes pour un ID de profil en profil spécifique**  
  
 L'exemple suivant affiche une liste des informations pour le profil `AdventureWorks Administrator` en spécifiant l'ID du profil.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp  
    @profile_id = 131 ;  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
```  
  
 **C. Liste des comptes pour tous les profils**  
  
 L'exemple suivant affiche une liste des comptes de tous les profils de l'instance.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp;  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
106         AdventureWorks Operator      210         Operator-MainServer  1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Objets de Configuration de messagerie de base de données](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Procédures stockées de messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
