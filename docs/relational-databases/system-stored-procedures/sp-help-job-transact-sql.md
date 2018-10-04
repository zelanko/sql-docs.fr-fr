---
title: sp_help_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_job_TSQL
- sp_help_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_job
ms.assetid: 8a8b6104-e0e4-4d07-a2c3-f4243ee0d6fa
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 18dde2c47f1da8c20457a9a0fbdd86c7adfe6e56
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818080"
---
# <a name="sphelpjob-transact-sql"></a>sp_help_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les travaux utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour effectuer des opérations automatisées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_job { [ @job_id = ] job_id  
[ @job_name = ] 'job_name' }   
     [ , [ @job_aspect = ] 'job_aspect' ]   
     [ , [ @job_type = ] 'job_type' ]   
     [ , [ @owner_login_name = ] 'login_name' ]   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @enabled = ] enabled ]   
     [ , [ @execution_status = ] status ]   
     [ , [ @date_comparator = ] 'date_comparison' ]   
     [ , [ @date_created = ] date_created ]   
     [ , [ @date_last_modified = ] date_modified ]   
     [ , [ @description = ] 'description_pattern' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id =**] *job_id*  
 Numéro d’identification. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
 [  **@job_name =**] **'***nom_travail***'**  
 Nom du travail. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Pour afficher un travail spécifique, soit *job_id* ou *nom_travail* doit être spécifié.  Omettre les deux *job_id* et *nom_travail* pour retourner des informations sur tous les travaux.
  
 [  **@job_aspect =**] **'***aspect_du_travail***'**  
 Attribut du travail à afficher. *aspect_du_travail* est **varchar (9)**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**ALL**|Informations sur l'aspect du travail.|  
|**JOB**|Informations sur le travail.|  
|**PLANIFICATIONS**|Informations sur la planification.|  
|**ÉTAPES**|Informations sur l'étape du travail|  
|**CIBLES**|Informations sur la cible|  
  
 [  **@job_type =**] **'***type_du_travail***'**  
 Type des travaux à inclure dans le rapport. *type_du_travail* est **varchar(12)**, avec NULL comme valeur par défaut. *type_du_travail* peut être **LOCAL** ou **multiserveur**.  
  
 [  **@owner_login_name =**] **'***login_name***'**  
 Nom de la connexion du propriétaire du travail. *login_name* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@subsystem =**] **'***sous-système***'**  
 Nom du sous-système. *sous-système* est **nvarchar (40)**, avec NULL comme valeur par défaut.  
  
 [  **@category_name =**] **'***catégorie***'**  
 Le nom de la catégorie. *catégorie* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@enabled =**] *activé*  
 Nombre qui indique si les informations sont affichées pour les travaux activés ou les travaux désactivés. *activé* est **tinyint**, avec NULL comme valeur par défaut. **1** indique les travaux sont activés et **0** indique les travaux désactivés.  
  
 [  **@execution_status =**] *état*  
 État de l'exécution des travaux. *état* est **int**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Renvoie uniquement les travaux qui ne sont ni inactifs ni suspendus.|  
|**1**|En cours d'exécution.|  
|**2**|Attente du thread.|  
|**3**|Entre deux reprises.|  
|**4**|Temps d’inactivité.|  
|**5**|Suspendu.|  
|**7**|Effectue le travail.|  
  
 [  **@date_comparator =**] **'***comparateur_de_dates***'**  
 L’opérateur de comparaison à utiliser dans les comparaisons de *date_created* et *date_de_modification*. *comparateur_de_dates* est **char (1)** et peut être =, \<, ou >.  
  
 [  **@date_created =**] *date_created*  
 Date de création du travail. *date_de_création*est **datetime**, avec NULL comme valeur par défaut.  
  
 [  **@date_last_modified =**] *date_de_modification*  
 Date de la dernière modification du travail. *date_de_modification* est **datetime**, avec NULL comme valeur par défaut.  
  
 [  **@description =**] **'***description***'**  
 Description du travail. *Description* est **nvarchar (512)**, avec NULL comme valeur par défaut. *Description* peut inclure les caractères génériques de SQL Server pour la correspondance de modèle.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Si aucun argument n’est spécifié, **sp_help_job** retourne ce jeu de résultats.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID unique de la tâche.|  
|**originating_server**|**nvarchar(30)**|Nom du serveur d'origine du travail|  
|**nom**|**sysname**|Nom du travail.|  
|**enabled**|**tinyint**|Indique si le travail est activé pour être exécuté.|  
|**description**|**nvarchar(512)**|Description pour le travail.|  
|**start_step_id**|**Int**|Identificateur de l'étape du travail à partir de laquelle l'exécution doit débuter.|  
|**Catégorie**|**sysname**|Catégorie de travail.|  
|**Propriétaire**|**sysname**|Propriétaire du travail.|  
|**notify_level_eventlog**|**Int**|**Masque de bits** qui indique dans quelles circonstances un événement de notification doit être journalisé dans le journal des applications Microsoft Windows. Peut prendre l'une des valeurs suivantes :<br /><br /> **0** = jamais<br /><br /> **1** = en cas de succès du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_level_email**|**Int**|**Masque de bits** qui indique dans quelles circonstances une notification par courrier électronique doit être envoyée à l’issue de l’exécution d’un travail. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_level_netsend**|**Int**|**Masque de bits** qui indique dans quelles circonstances un message de réseau doit être envoyé à l’issue de l’exécution d’un travail. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_level_page**|**Int**|**Masque de bits** qui indique dans quelles circonstances une page doit être envoyée à l’issue de l’exécution d’un travail. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_email_operator**|**sysname**|Nom d'adresse électronique de l'opérateur à avertir.|  
|**notify_netsend_operator**|**sysname**|Nom de l'utilisateur ou de l'ordinateur utilisé pour envoyer les messages sur le réseau.|  
|**notify_page_operator**|**sysname**|Nom de l'utilisateur ou de l'ordinateur utilisé pour envoyer une page.|  
|**delete_level**|**Int**|**Masque de bits** qui indique dans quelles circonstances le travail doit être supprimé à l’issue de l’exécution d’un travail. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**date_created**|**datetime**|Date de que création du travail.|  
|**date_modified**|**datetime**|Date de dernière modification du travail.|  
|**version_number**|**Int**|Version du travail (mise à jour automatique à chaque modification).|  
|**last_run_date**|**Int**|Date du début de la dernière exécution du travail.|  
|**last_run_time**|**Int**|Heure du début de la dernière exécution du travail.|  
|**last_run_outcome**|**Int**|Résultat du travail lors de sa dernière exécution :<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **3** = annulée<br /><br /> **5** = inconnu|  
|**next_run_date**|**Int**|Date prévue pour la prochaine exécution du travail.|  
|**next_run_time**|**Int**|Heure prévue pour la prochaine exécution du travail.|  
|**next_run_schedule_id**|**Int**|Numéro d'identification de la prochaine exécution planifiée.|  
|**current_execution_status**|**Int**|État en cours d’exécution.|  
|**current_execution_step**|**sysname**|Étape d'exécution du travail en cours.|  
|**current_retry_attempt**|**Int**|Si le travail est en cours d'exécution et que l'étape est effectuée plusieurs fois, ce paramètre correspond à la tentative en cours.|  
|**has_step**|**Int**|Nombre d'étapes du travail.|  
|**has_schedule**|**Int**|Nombre de planifications d'un travail.|  
|**has_target**|**Int**|Nombre de serveurs cibles d'un travail.|  
|**type**|**Int**|Type de la tâche.<br /><br /> 1 = Travail local.<br /><br /> **2** = travail multiserveur.<br /><br /> **0** = travail ne comprend aucun serveur cible.|  
  
 Si *job_id* ou *nom_travail* est spécifié, **sp_help_job** retourne ces jeux de résultats supplémentaires pour les étapes de travail, les planifications de travaux et les serveurs cibles du travail.  
  
 Voici le jeu de résultats des étapes de travail :  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**step_id**|**Int**|Identificateur unique de cette étape (pour ce travail).|  
|**step_name**|**sysname**|Nom de l'étape|  
|**subsystem**|**nvarchar(40)**|Sous-système dans lequel la commande d'étape doit être exécutée.|  
|**commande**|**nvarchar(3200)**|Commande à exécuter.|  
|**flags**|**nvarchar(4000)**|**Masque de bits** des valeurs qui contrôlent le comportement de l’étape.|  
|**cmdexec_success_code**|**Int**|Pour un **CmdExec** étape, voici le code de sortie d’une commande réussie.|  
|**on_success_action**|**nvarchar(4000)**|Que faire si l'étape est exécutée correctement :<br /><br /> **1** = sortie avec succès.<br /><br /> **2** = sortie avec échec.<br /><br /> **3** = passer à l’étape suivante.<br /><br /> **4** = passer à l’étape.|  
|**on_success_step_id**|**Int**|Si **on_success_action** est **4**, cela indique la prochaine étape à exécuter.|  
|**on_fail_action**|**nvarchar(4000)**|Action à exécuter si l'exécution de l'étape échoue. Les valeurs sont les mêmes que pour **on_success_action**.|  
|**on_fail_step_id**|**Int**|Si **on_fail_action** est **4**, cela indique la prochaine étape à exécuter.|  
|**server**|**sysname**|Réservé.|  
|**database_name**|**sysname**|Pour une étape [!INCLUDE[tsql](../../includes/tsql-md.md)], c'est la base de données dans laquelle la commande sera exécutée.|  
|**database_user_name**|**sysname**|Pour une étape [!INCLUDE[tsql](../../includes/tsql-md.md)], c'est le contexte de l'utilisateur de la base de données dans lequel la commande est exécutée.|  
|**retry_attempts**|**Int**|Nombre de tentatives maximum de la commande (si elle échoue) avant que l'étape soit considérée comme un échec.|  
|**retry_interval**|**Int**|Intervalle (en minutes) entre chaque tentative.|  
|**os_run_priority**|**varchar(4000)**|Réservé.|  
|**output_file_name**|**varchar(200)**|Fichier de commande de sortie doit être écrite ([!INCLUDE[tsql](../../includes/tsql-md.md)] et **CmdExec** étapes uniquement).|  
|**last_run_outcome**|**Int**|Résultat de l'étape lors de sa dernière exécution.<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **3** = annulée<br /><br /> **5** = inconnu|  
|**last_run_duration**|**Int**|Durée (en secondes) de l'étape lors de sa dernière exécution.|  
|**last_run_retries**|**Int**|Nombre de tentatives de la commande lors de la dernière exécution de l'étape.|  
|**last_run_date**|**Int**|Date de début de la dernière exécution de l'étape.|  
|**last_run_time**|**Int**|Heure de début de la dernière exécution de l'étape.|  
|**proxy_id**|**Int**|Proxy pour les étapes du travail.|  
  
 Voici le jeu de résultats des planifications de travail.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**Int**|Identificateur de la planification (unique pour tous les travaux).|  
|**schedule_name**|**sysname**|Nom de la planification (unique pour ce travail).|  
|**enabled**|**Int**|Indique si la planification est active (**1**) ou non (**0**).|  
|**freq_type**|**Int**|Valeur indiquant la fréquence d'exécution du travail.<br /><br /> **1** = une fois<br /><br /> **4** = quotidienne<br /><br /> **8** = hebdomadaire<br /><br /> **16** = mensuelle<br /><br /> **32** = mensuellement, relatif à la **freq_interval**<br /><br /> **64** = exécuter lorsque **SQLServerAgent** démarrage du service.|  
|**freq_interval**|**Int**|Jours lorsque la tâche est exécutée. La valeur dépend de la valeur de **freq_type**. Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**Int**|Unités pour **freq_subday_interval**. Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**Int**|Nombre de **freq_subday_type** périodes entre chaque exécution du travail. Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**Int**|Planifiées du travail de le **freq_interval** dans chaque mois. Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**Int**|Nombre de mois devant s'écouler entre les exécutions planifiées du travail.|  
|**active_start_date**|**Int**|Date de démarrage de l'exécution du travail.|  
|**active_end_date**|**Int**|Date de fin d’exécution du travail.|  
|**active_start_time**|**Int**|Heure de début de l’exécution du travail sur **active_start_date.**|  
|**active_end_time**|**Int**|Heure de fin d’exécution du travail sur **active_end_date**.|  
|**date_created**|**datetime**|Date de création de la planification.|  
|**schedule_description**|**nvarchar(4000)**|Description en anglais de la planification (sur demande).|  
|**next_run_date**|**Int**|Date à laquelle la planification va lancer l'exécution du travail.|  
|**next_run_time**|**Int**|Heure à laquelle la planification va lancer l'exécution du travail.|  
|**schedule_uid**|**uniqueidentifier**|Identificateur de la planification.|  
|**job_count**|**Int**|Retourne le nombre de travaux qui référencent cette planification.|  
  
 Jeu de résultats pour les serveurs cibles de travaux.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**Int**|Identificateur du serveur cible.|  
|**server_name**|**nvarchar(30)**|Nom de l'ordinateur du serveur cible.|  
|**enlist_date**|**datetime**|Date d'inscription du serveur cible sur le serveur maître.|  
|**last_poll_date**|**datetime**|Date à laquelle le serveur cible a interrogé pour la dernière fois le serveur maître.|  
|**last_run_date**|**Int**|Date du début de la dernière exécution du travail sur ce serveur cible.|  
|**last_run_time**|**Int**|Heure du début de la dernière exécution du travail sur ce serveur cible.|  
|**last_run_duration**|**Int**|Durée du travail lors de sa dernière exécution sur ce serveur cible.|  
|**last_run_outcome**|**tinyint**|Résultat du travail à l'issue de sa dernière exécution sur ce serveur.<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **3** = annulée<br /><br /> **5** = inconnu|  
|**last_outcome_message**|**nvarchar(1024)**|Message indiquant le résultat du travail lors de sa dernière exécution sur ce serveur cible.|  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Membres de **SQLAgentUserRole** peut afficher uniquement les travaux dont ils sont propriétaires. Membres de **sysadmin**, **SQLAgentReaderRole**, et **SQLAgentOperatorRole** peut afficher tous les travaux locaux et multiserveurs.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-list-information-for-all-jobs"></a>A. Création de la liste des informations sur tous les travaux  
 L'exemple suivant exécute la procédure `sp_help_job` sans aucun paramètre afin que des informations sur tous les travaux définis dans la base de données `msdb` soient retournées.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-matching-a-specific-criteria"></a>B. Création de la liste des informations pour les travaux correspondant à un critère spécifique  
 L'exemple suivant répertorie les informations sur les travaux multiserveurs détenus par `françoisa` lorsque les travaux sont activés et exécutés.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job   
   @job_type = N'MULTI-SERVER',  
   @owner_login_name = N'françoisa',  
   @enabled = 1,  
   @execution_status = 1 ;  
GO  
```  
  
### <a name="c-listing-all-aspects-of-information-for-a-job"></a>C. Création de la liste de tous les aspects des informations pour un travail  
 L'exemple suivant répertorie tous les aspects des informations pour le travail `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job  
    @job_name = N'NightlyBackups',  
    @job_aspect = N'ALL' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
