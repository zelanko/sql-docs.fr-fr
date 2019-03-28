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
ms.openlocfilehash: c12e078505c8049511e59973c26d6a1417c7eae0
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537851"
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
`[ @job_id = ] job_id` Le numéro d’identification du travail à mettre à jour. *job_id*est **uniqueidentifier**.  
  
`[ @job_name = ] 'job_name'` Le nom de la tâche. *job_name* est **nvarchar (128)**.  
  
> **REMARQUE :** Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
`[ @new_name = ] 'new_name'` Le nouveau nom pour le travail. *new_name* est **nvarchar (128)**.  
  
`[ @enabled = ] enabled` Spécifie si le travail est activé (**1**) ou désactivée (**0**). *activé* est **tinyint**.  
  
`[ @description = ] 'description'` Description du travail. *description* is **nvarchar(512)**.  
  
`[ @start_step_id = ] step_id` Le numéro d’identification de la première étape à exécuter pour la tâche. *l’argument id_étape* est **int**.  
  
`[ @category_name = ] 'category'` La catégorie du travail. *catégorie* est **nvarchar (128)**.  
  
`[ @owner_login_name = ] 'login'` Le nom de la connexion propriétaire du travail. *connexion* est **nvarchar (128)** seuls les membres de la **sysadmin** rôle serveur fixe peut modifier l’appartenance des travaux.  
  
`[ @notify_level_eventlog = ] eventlog_level` Spécifie le moment auquel une entrée dans le journal des applications Microsoft Windows pour ce travail. *niveau_journal_événements*est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description (action)|  
|-----------|----------------------------|  
|**0**|Never|  
|**1**|Si succès|  
|**2**|Si échec|  
|**3**|Always|  
  
`[ @notify_level_email = ] email_level` Spécifie à quel moment envoyer un message électronique à l’achèvement de ce travail. *niveau_courrier_électronique*est **int**. *niveau_courrier_électronique*utilise les mêmes valeurs que *niveau_journal_événements*.  
  
`[ @notify_level_netsend = ] netsend_level` Spécifie à quel moment envoyer un message réseau une fois la fin de ce travail. *niveau_message_réseau*est **int**. *niveau_message_réseau*utilise les mêmes valeurs que *niveau_journal_événements*.  
  
`[ @notify_level_page = ] page_level` Spécifie à quel moment envoyer une page à la fin de ce travail. *niveau_page* est **int**. *niveau_page*utilise les mêmes valeurs que *niveau_journal_événements*.  
  
`[ @notify_email_operator_name = ] 'operator_name'` Le nom de l’opérateur auquel le message électronique est envoyé une fois *niveau_courrier_électronique* est atteinte. *nom_adresse* est **nvarchar (128)**.  
  
`[ @notify_netsend_operator_name = ] 'netsend_operator'` Le nom de l’opérateur auquel le message réseau est envoyé. *netsend_operator* is **nvarchar(128)**.  
  
`[ @notify_page_operator_name = ] 'page_operator'` Le nom de l’opérateur auquel une page est envoyée. *opérateur_page* est **nvarchar (128)**.  
  
`[ @delete_level = ] delete_level` Spécifie à quel moment supprimer le travail. *delete_leve*est **int**. *niveau_suppression*utilise les mêmes valeurs que *niveau_journal_événements*.  
  
`[ @automatic_post = ] automatic_post` Réservé.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_update_job** doit être exécuté à partir de la **msdb** base de données.  
  
 **sp_update_job** modifie uniquement les paramètres pour le paramètre auquel les valeurs sont fournies. Si un paramètre est manquant, la valeur actuelle est retenue.  
  
## <a name="permissions"></a>Autorisations  
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
  
  
