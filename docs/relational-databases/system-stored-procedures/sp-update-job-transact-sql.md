---
title: sp_update_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_job
- sp_update_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_job
ms.assetid: cbdfea38-9e42-47f3-8fc8-5978b82e2623
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4371609b9d0c72d9d589d37f0edacc4d37a2996c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651557"
---
# <a name="spupdatejob-transact-sql"></a>sp_update_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les attributs d'un travail.  
  

  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_update_job [ @job_id =] job_id | [@job_name =] 'job_name'  
     [, [@new_name =] 'new_name' ]   
     [, [@enabled =] enabled ]  
     [, [@description =] 'description' ]   
     [, [@start_step_id =] step_id ]  
     [, [@category_name =] 'category' ]   
     [, [@owner_login_name =] 'login' ]  
     [, [@notify_level_eventlog =] eventlog_level ]  
     [, [@notify_level_email =] email_level ]  
     [, [@notify_level_netsend =] netsend_level ]  
     [, [@notify_level_page =] page_level ]  
     [, [@notify_email_operator_name =] 'operator_name' ]  
     [, [@notify_netsend_operator_name =] 'netsend_operator' ]  
     [, [@notify_page_operator_name =] 'page_operator' ]  
     [, [@delete_level =] delete_level ]   
     [, [@automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id =**] *job_id*  
 Numéro d'identification du travail à mettre à jour. *job_id*est **uniqueidentifier**.  
  
 [  **@job_name =**] **'***nom_travail***'**  
 Nom du travail. *job_name*est **nvarchar (128)**.  
  
> **Remarque :** soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [  **@new_name =**] **'***nouveau_nom***'**  
 Nouveau nom du travail. *new_name*est **nvarchar (128)**.  
  
 [  **@enabled =**] *activé*  
 Spécifie si le travail est activé (**1**) ou désactivée (**0**). *activé*est **tinyint**.  
  
 [  **@description =**] **'***description***'**  
 Description du travail. *Description* est **nvarchar (512)**.  
  
 [ **@start_step_id =**] *step_id*  
 Numéro d'identification de la première étape à exécuter pour le travail. *l’argument id_étape*est **int**.  
  
 [  **@category_name =**] **'***catégorie***'**  
 La catégorie du travail. *catégorie*est **nvarchar (128)**.  
  
 [  **@owner_login_name =**] **'***connexion***'**  
 Nom du compte de connexion propriétaire du travail. *connexion*est **nvarchar (128)** seuls les membres de la **sysadmin** rôle serveur fixe peut modifier l’appartenance des travaux.  
  
 [  **@notify_level_eventlog =**] *niveau_journal_événements*  
 Indique le moment auquel une entrée doit être ajoutée pour ce travail dans le journal des applications Microsoft Windows. *niveau_journal_événements*est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description (action)|  
|-----------|----------------------------|  
|**0**|Never|  
|**1**|Si succès|  
|**2**|Si échec|  
|**3**|Always|  
  
 [  **@notify_level_email =**] *niveau_courrier_électronique*  
 Indique le moment où un message électronique doit être envoyé à la fin de ce travail. *niveau_courrier_électronique*est **int**. *niveau_courrier_électronique*utilise les mêmes valeurs que *niveau_journal_événements*.  
  
 [  **@notify_level_netsend =**] *niveau_message_réseau*  
 Indique le moment où un message doit être envoyé sur le réseau à la fin de ce travail. *niveau_message_réseau*est **int**. *niveau_message_réseau*utilise les mêmes valeurs que *niveau_journal_événements*.  
  
 [  **@notify_level_page =**] *niveau_page*  
 Indique le moment où un message par radiomessagerie doit être envoyé à la fin de ce travail. *niveau_page*est **int**. *niveau_page*utilise les mêmes valeurs que *niveau_journal_événements*.  
  
 [  **@notify_email_operator_name =**] **'***nom_opérateur***'**  
 Le nom de l’opérateur auquel le message électronique est envoyé une fois *niveau_courrier_électronique* est atteinte. *nom_adresse* est **nvarchar (128)**.  
  
 [ **@notify_netsend_operator_name =**] **'***netsend_operator***'**  
 Nom de l'opérateur auquel le message est envoyé par réseau. *opérateur_message_réseau* est **nvarchar (128)**.  
  
 [  **@notify_page_operator_name =**] **'***opérateur_page***'**  
 Nom de l'opérateur auquel un message par radiomessagerie est envoyé. *opérateur_page* est **nvarchar (128)**.  
  
 [ **@delete_level =**] *delete_level*  
 Indique le moment où le travail doit être supprimé. *delete_leve*est **int**. *niveau_suppression*utilise les mêmes valeurs que *niveau_journal_événements*.  
  
 [  **@automatic_post =**] *envoi_automatique*  
 Réservé.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_update_job** doit être exécuté à partir de la **msdb** base de données.  
  
 **sp_update_job** modifie uniquement les paramètres pour le paramètre auquel les valeurs sont fournies. Si un paramètre est manquant, la valeur actuelle est retenue.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Seuls les membres du **sysadmin** pouvez utiliser cette procédure stockée pour modifier les attributs de travaux qui est détenus par d’autres utilisateurs.  
  
## <a name="examples"></a>Exemples  
 Cet exemple modifie le nom, la description et l'état (activé ou non) du travail `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_job  
    @job_name = N'NightlyBackups',  
    @new_name = N'NightlyBackups -- Disabled',  
    @description = N'Nightly backups disabled during server migration.',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
