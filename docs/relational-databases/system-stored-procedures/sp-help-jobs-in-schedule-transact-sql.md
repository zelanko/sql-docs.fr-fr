---
title: sp_help_jobs_in_schedule (Transact-SQL) | Microsoft Docs
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
- sp_help_jobs_in_schedule_TSQL
- sp_help_jobs_in_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobs_in_schedule
ms.assetid: 1168aa2c-136b-4ba3-b18e-9070d95a26fa
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5160cd777567d671a170d31d3638e7ef9dc74a34
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395899"
---
# <a name="sphelpjobsinschedule-transact-sql"></a>sp_help_jobs_in_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les travaux auxquels une planification particulière est attachée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobs_in_schedule   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@schedule_id =** ] *id_de_la_planification*  
 Identificateur de la planification pour laquelle répertorier des informations. *id_de_la_planification* est **int**, sans valeur par défaut. Soit *id_de_la_planification* ou *nom_de_la_planification* peut être spécifié.  
  
 [  **@schedule_name =** ] **'***nom_de_la_planification***'**  
 Nom de la planification pour laquelle répertorier des informations. *nom_de_la_planification* est **sysname**, sans valeur par défaut. Soit *id_de_la_planification* ou *nom_de_la_planification* peut être spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne le jeu de résultats suivant :  
  
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
|**notify_level_eventlog**|**Int**|Masque binaire indiquant les circonstances entraînant la consignation d'une notification d'événement dans le journal des applications Microsoft Windows. Peut prendre l'une des valeurs suivantes :<br /><br /> **0** = jamais<br /><br /> **1** = en cas de succès du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_level_email**|**Int**|Masque de bits indiquant les conditions d'envoi d'un message électronique en fin de travail. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_level_netsend**|**Int**|Masque de bits précisant les conditions d'envoi d'un message réseau en fin de travail. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_level_page**|**Int**|Masque de bits indiquant les conditions d'envoi d'une page en fin de travail. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
|**notify_email_operator**|**sysname**|Nom d'adresse électronique de l'opérateur à avertir.|  
|**notify_netsend_operator**|**sysname**|Nom de l'utilisateur ou de l'ordinateur utilisé pour envoyer les messages sur le réseau.|  
|**notify_page_operator**|**sysname**|Nom de l'utilisateur ou de l'ordinateur utilisé pour envoyer une page.|  
|**delete_level**|**Int**|Masque de bits indiquant les conditions de suppression du travail en fin de travail. Les valeurs possibles sont les mêmes que pour **notify_level_eventlog**.|  
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
|**type**|**Int**|Type du travail :<br /><br /> **1** = travail local.<br /><br /> **2** = travail multiserveur.<br /><br /> **0** = travail ne comprend aucun serveur cible.|  
  
## <a name="remarks"></a>Notes  
 Cette procédure affiche des informations sur les travaux attachés à la planification spécifiée.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Membres de **SQLAgentUserRole** peut uniquement afficher l’état des travaux dont ils sont propriétaires.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant affiche les travaux attachés à la planification `NightlyJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobs_in_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
