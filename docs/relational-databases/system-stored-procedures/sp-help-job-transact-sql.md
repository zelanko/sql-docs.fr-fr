---
title: sp_help_job (Transact-SQL) Microsoft Docs
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
ms.openlocfilehash: 29870a0ffb3d2c3b1872acbb40266aef0d16b62c
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "75546566"
---
# <a name="sp_help_job-transact-sql"></a>sp_help_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les travaux utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour effectuer des opérations automatisées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @job_id = ] job_id`Le numéro d’identification d’emploi. *job_id* est **uniqueidentifier**, avec un défaut de NULL.  
  
`[ @job_name = ] 'job_name'`Le nom du boulot. *job_name* est **sysname**, avec un défaut de NULL.  
  
> [!NOTE]  
>  Pour afficher un emploi spécifique, *job_id* ou *job_name* doit être spécifié.  Omettre *à la* fois job_id et *job_name* de retourner des informations sur tous les emplois.
  
`[ @job_aspect = ] 'job_aspect'`L’attribut de travail à afficher. *job_aspect* est **varchar(9)**, avec un défaut de NULL, et peut être l’une de ces valeurs.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**ALL**|Informations sur l'aspect du travail.|  
|**Travail**|Informations sur le travail.|  
|**Horaires**|Informations sur la planification.|  
|**Étapes**|Informations sur l'étape du travail|  
|**Cibles**|Informations sur la cible|  
  
`[ @job_type = ] 'job_type'`Le type d’emplois à inclure dans le rapport. *job_type* est **varchar(12)**, avec un défaut de NULL. *job_type* peut être **LOCAL** ou **MULTI-SERVER**.  
  
`[ @owner_login_name = ] 'login_name'`Le nom de connexion du propriétaire de l’emploi. *login_name* est **sysname**, avec un défaut de NULL.  
  
`[ @subsystem = ] 'subsystem'`Le nom du sous-système. *sous-système* est **nvarchar(40)**, avec un défaut de NULL.  
  
`[ @category_name = ] 'category'`Le nom de la catégorie. *catégorie* est **sysname**, avec un défaut de NULL.  
  
`[ @enabled = ] enabled`Un nombre indiquant si des informations sont affichées pour les emplois autorisés ou les emplois handicapés. *activé* est **tinyint**, avec un défaut de NULL. **1** indique les emplois autorisés, et **0** indique les emplois handicapés.  
  
`[ @execution_status = ] status`Le statut d’exécution pour les emplois. *statut* est **int**, avec un défaut de NULL, et peut être l’une de ces valeurs.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Renvoie uniquement les travaux qui ne sont ni inactifs ni suspendus.|  
|**1**|En cours d'exécution.|  
|**2**|Attente du thread.|  
|**3**|Entre deux reprises.|  
|**4**|Inactif.|  
|**5**|Suspendu.|  
|**7**|Effectue le travail.|  
  
`[ @date_comparator = ] 'date_comparison'`L’opérateur de comparaison à utiliser en comparaison de *date_created* et *date_modified*. *date_comparison* est **char(1)**, et peut \<être , , ou >.  
  
`[ @date_created = ] date_created`La date de création du travail. *date_created*est **datetime**, avec un défaut de NULL.  
  
`[ @date_last_modified = ] date_modified`La date à laquelle le travail a été modifié pour la dernière fois. *date_modified* est **datetime**, avec un défaut de NULL.  
  
`[ @description = ] 'description_pattern'`La description du travail. *description_pattern* est **nvarchar(512)**, avec un défaut de NULL. *description_pattern* pouvez inclure les caractères de wildcard SQL Server pour l’appariement des motifs.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Si aucun argument n’est spécifié, **sp_help_job** renvoie cet ensemble de résultats.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID unique du travail.|  
|**originating_server**|**nvarchar(30)**|Nom du serveur d'origine du travail|  
|**name**|**sysname**|Nom du travail.|  
|**Activé**|**tinyint**|Indique si le travail est activé pour être exécuté.|  
|**Description**|**nvarchar(512)**|Description du travail.|  
|**start_step_id**|**int**|Identificateur de l'étape du travail à partir de laquelle l'exécution doit débuter.|  
|**Catégorie**|**sysname**|Catégorie de travail.|  
|**Propriétaire**|**sysname**|Propriétaire du travail.|  
|**notify_level_eventlog**|**int**|**Bitmask** indiquant dans quelles circonstances un événement de notification doit être enregistré dans le journal d’application Microsoft Windows. Peut prendre l'une des valeurs suivantes :<br /><br /> **0** - Jamais<br /><br /> **1** - Quand un emploi réussit<br /><br /> **2** - Lorsque le travail échoue<br /><br /> **3** - Chaque fois que le travail est terminé (quel que soit le résultat de l’emploi)|  
|**notify_level_email**|**int**|**Bitmask** indiquant dans quelles circonstances un e-mail de notification doit être envoyé lorsqu’un emploi est terminé. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_level_netsend**|**int**|**Bitmask** indiquant dans quelles circonstances un message réseau doit être envoyé lorsqu’un emploi est terminé. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_level_page**|**int**|**Bitmask** indiquant dans quelles circonstances une page doit être envoyée lorsqu’un emploi est terminé. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_email_operator**|**sysname**|Nom d'adresse électronique de l'opérateur à avertir.|  
|**notify_netsend_operator**|**sysname**|Nom de l'utilisateur ou de l'ordinateur utilisé pour envoyer les messages sur le réseau.|  
|**notify_page_operator**|**sysname**|Nom de l'utilisateur ou de l'ordinateur utilisé pour envoyer une page.|  
|**delete_level**|**int**|**Bitmask** indiquant dans quelles circonstances le travail doit être supprimé quand un travail se termine. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**date_created**|**datetime**|Date de la création du travail.|  
|**date_modified**|**datetime**|Date de dernière modification du travail.|  
|**version_number**|**int**|Version du travail (mise à jour automatique à chaque modification).|  
|**last_run_date**|**int**|Date du début de la dernière exécution du travail.|  
|**last_run_time**|**int**|Heure du début de la dernière exécution du travail.|  
|**last_run_outcome**|**int**|Résultat du travail lors de sa dernière exécution :<br /><br /> **0** - Échec<br /><br /> **1** - A réussi<br /><br /> **3** - Annulé<br /><br /> **5** - Inconnu|  
|**next_run_date**|**int**|Date prévue pour la prochaine exécution du travail.|  
|**next_run_time**|**int**|Heure prévue pour la prochaine exécution du travail.|  
|**next_run_schedule_id**|**int**|Numéro d'identification de la prochaine exécution planifiée.|  
|**current_execution_status**|**int**|État d’exécution actuel :<br /><br /> **1** - Exécution<br /><br /> **2** - En attente de fil<br /><br /> **3** - Entre les retries<br /><br /> **4** - Inactif<br /><br /> **5** - Suspendu<br /><br /> **6** - Obsolète<br /><br /> **7** - PerformingCompletionActions|  
|**current_execution_step**|**sysname**|Étape d'exécution du travail en cours.|  
|**current_retry_attempt**|**int**|Si le travail est en cours d'exécution et que l'étape est effectuée plusieurs fois, ce paramètre correspond à la tentative en cours.|  
|**has_step**|**int**|Nombre d'étapes du travail.|  
|**has_schedule**|**int**|Nombre de planifications d'un travail.|  
|**has_target**|**int**|Nombre de serveurs cibles d'un travail.|  
|**type**|**int**|Type du travail.<br /><br /> 1 = Travail local.<br /><br /> **2** - Travail multiservateur.<br /><br /> **0** - Job n’a pas de serveurs cibles.|  
  
 Si *job_id* ou *job_name* est spécifiée, **sp_help_job** retourne ces ensembles de résultats supplémentaires pour les étapes d’emploi, les horaires d’emploi et les serveurs cibles d’emploi.  
  
 Voici le jeu de résultats des étapes de travail :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|Identificateur unique de cette étape (pour ce travail).|  
|**step_name**|**sysname**|Nom de l'étape|  
|**Sous-système**|**nvarchar(40)**|Sous-système dans lequel la commande d'étape doit être exécutée.|  
|**Commande**|**nvarchar(3200)**|Commandez d’exécuter.|  
|**Drapeaux**|**nvarchar(4000)**|**Bitmask** de valeurs qui contrôlent le comportement d’étape.|  
|**cmdexec_success_code**|**int**|Pour une étape **CmdExec,** c’est le code de sortie de processus d’une commande réussie.|  
|**on_success_action**|**nvarchar(4000)**|Que faire si l'étape est exécutée correctement :<br /><br /> **1** - Arrêtez avec succès.<br /><br /> **2** - Arrêter avec échec.<br /><br /> **3** - Passez à l’étape suivante.<br /><br /> **4** - Allez à l’étape.|  
|**on_success_step_id**|**int**|Si **on_success_action** est **de 4**, cela indique la prochaine étape à exécuter.|  
|**on_fail_action**|**nvarchar(4000)**|Action à exécuter si l'exécution de l'étape échoue. Les valeurs sont les mêmes que pour **on_success_action**.|  
|**on_fail_step_id**|**int**|Si **on_fail_action** est **de 4**, cela indique la prochaine étape à exécuter.|  
|**Serveur**|**sysname**|Réservé.|  
|**database_name**|**sysname**|Pour une étape [!INCLUDE[tsql](../../includes/tsql-md.md)], c'est la base de données dans laquelle la commande sera exécutée.|  
|**database_user_name**|**sysname**|Pour une étape [!INCLUDE[tsql](../../includes/tsql-md.md)], c'est le contexte de l'utilisateur de la base de données dans lequel la commande est exécutée.|  
|**retry_attempts**|**int**|Nombre de tentatives maximum de la commande (si elle échoue) avant que l'étape soit considérée comme un échec.|  
|**retry_interval**|**int**|Intervalle (en minutes) entre chaque tentative.|  
|**os_run_priority**|**varchar(4000)**|Réservé.|  
|**output_file_name**|**varchar(200)**|Fichier à laquelle la sortie[!INCLUDE[tsql](../../includes/tsql-md.md)] de commande doit être écrite (et Les étapes **CmdExec** seulement).|  
|**last_run_outcome**|**int**|Résultat de l'étape lors de sa dernière exécution.<br /><br /> **0** - Échec<br /><br /> **1** - A réussi<br /><br /> **3** - Annulé<br /><br /> **5** - Inconnu|  
|**last_run_duration**|**int**|Durée (en secondes) de l'étape lors de sa dernière exécution.|  
|**last_run_retries**|**int**|Nombre de tentatives de la commande lors de la dernière exécution de l'étape.|  
|**last_run_date**|**int**|Date de début de la dernière exécution de l'étape.|  
|**last_run_time**|**int**|Heure de début de la dernière exécution de l'étape.|  
|**proxy_id**|**int**|Proxy pour les étapes du travail.|  
  
 Voici le jeu de résultats des planifications de travail.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Identificateur de la planification (unique pour tous les travaux).|  
|**schedule_name**|**sysname**|Nom de la planification (unique pour ce travail).|  
|**Activé**|**int**|Que l’horaire soit actif (**1**) ou non (**0**).|  
|**freq_type**|**int**|Valeur indiquant la fréquence d'exécution du travail.<br /><br /> **1** - Une fois<br /><br /> **4** - Tous les jours<br /><br /> **8** - Hebdomadaire<br /><br /> **16** ans et moins<br /><br /> **32** ans et plus mensuel, par rapport au **freq_interval**<br /><br /> **64** - Exécuter lorsque le service **SQLServerAgent** commence.|  
|**freq_interval**|**int**|Jours où le travail est exécuté. La valeur dépend de la valeur de **freq_type**. Pour plus d’informations, voir [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**Int**|Unités pour **freq_subday_interval**. Pour plus d’informations, voir [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**int**|Nombre de **périodes freq_subday_type** à prendre entre chaque exécution du travail. Pour plus d’informations, voir [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**int**|L’accident de l’emploi prévu de la **freq_interval** chaque mois. Pour plus d’informations, voir [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**int**|Nombre de mois devant s'écouler entre les exécutions planifiées du travail.|  
|**active_start_date**|**int**|Date de démarrage de l'exécution du travail.|  
|**active_end_date**|**int**|Date pour mettre fin à l’exécution du travail.|  
|**active_start_time**|**int**|Il est temps de commencer l’exécution du travail sur **active_start_date.**|  
|**active_end_time**|**int**|Il est temps de mettre fin à l’exécution du travail sur **active_end_date**.|  
|**date_created**|**datetime**|Date de création de la planification.|  
|**schedule_description**|**nvarchar(4000)**|Description en anglais de la planification (sur demande).|  
|**next_run_date**|**int**|Date à laquelle la planification va lancer l'exécution du travail.|  
|**next_run_time**|**int**|Heure à laquelle la planification va lancer l'exécution du travail.|  
|**schedule_uid**|**uniqueidentifier**|Identificateur de la planification.|  
|**job_count**|**int**|Retourne le nombre de travaux qui référencent cette planification.|  
  
 Jeu de résultats pour les serveurs cibles de travaux.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Identificateur du serveur cible.|  
|**server_name**|**nvarchar(30)**|Nom de l'ordinateur du serveur cible.|  
|**enlist_date**|**datetime**|Date d'inscription du serveur cible sur le serveur maître.|  
|**last_poll_date**|**datetime**|Date à laquelle le serveur cible a interrogé pour la dernière fois le serveur maître.|  
|**last_run_date**|**int**|Date du début de la dernière exécution du travail sur ce serveur cible.|  
|**last_run_time**|**int**|Heure du début de la dernière exécution du travail sur ce serveur cible.|  
|**last_run_duration**|**int**|Durée du travail lors de sa dernière exécution sur ce serveur cible.|  
|**last_run_outcome**|**tinyint**|Résultat du travail à l'issue de sa dernière exécution sur ce serveur.<br /><br /> **0** - Échec<br /><br /> **1** - A réussi<br /><br /> **3** - Annulé<br /><br /> **5** - Inconnu|  
|**last_outcome_message**|**nvarchar(1024)**|Message indiquant le résultat du travail lors de sa dernière exécution sur ce serveur cible.|  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle du serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Les membres de **SQLAgentUserRole** ne peuvent voir que les emplois qu’ils possèdent. Les membres de **sysadmin**, **SQLAgentReaderRole**, et **SQLAgentOperatorRole** peuvent voir tous les emplois locaux et multiservateurs.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-list-information-for-all-jobs"></a>R. Création de la liste des informations sur tous les travaux  
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
 [sp_add_job &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
