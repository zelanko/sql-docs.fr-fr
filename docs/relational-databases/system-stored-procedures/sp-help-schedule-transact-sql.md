---
title: sp_help_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_schedule
- sp_help_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_schedule
ms.assetid: b2fc4ce1-0a8e-44d2-b206-7dc7b258d8c9
author: stevestein
ms.author: sstein
ms.openlocfilehash: f5a68160c8aee1bcb399513051e1f4cc35cea970
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085215"
---
# <a name="sphelpschedule-transact-sql"></a>sp_help_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur les planifications.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_schedule   
     [ @schedule_id = ] id ,  
     [ @schedule_name = ] 'schedule_name'   
     [ , [ @attached_schedules_only = ] attached_schedules_only ]  
     [ , [ @include_description = ] include_description ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @schedule_id = ] id` Identificateur de la planification à répertorier. *nom_de_la_planification* est **int**, sans valeur par défaut. Soit *id_de_la_planification* ou *nom_de_la_planification* peut être spécifié.  
  
`[ @schedule_name = ] 'schedule_name'` Le nom de la planification à répertorier. *nom_de_la_planification* est **sysname**, sans valeur par défaut. Soit *id_de_la_planification* ou *nom_de_la_planification* peut être spécifié.  
  
`[ @attached_schedules_only = ] attached_schedules_only ]` Spécifie s’il faut afficher seulement les planifications auxquelles un travail est attaché. *attached_schedules_only* est **bits**, avec une valeur par défaut **0**. Lorsque *attached_schedules_only* est **0**, toutes les planifications sont affichées. Lorsque *attached_schedules_only* est **1**, le jeu de résultats contient uniquement les planifications qui sont attachées à un travail.  
  
`[ @include_description = ] include_description` Spécifie s’il faut inclure les descriptions dans le jeu de résultats. *include_description* est **bits**, avec une valeur par défaut **0**. Lorsque *include_description* est **0**, le *schedule_description* colonne du jeu de résultats contient un espace réservé. Lorsque *include_description* est **1**, la description de la planification est incluse dans le jeu de résultats.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Cette procédure retourne le jeu de résultats suivant :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**Int**|Numéro d'identificateur de la planification.|  
|**schedule_uid**|**uniqueidentifier**|Identificateur de la planification.|  
|**schedule_name**|**sysname**|Nom de la planification.|  
|**enabled**|**int**|Si la planification est activée (**1**) ou désactivée (**0**).|  
|**freq_type**|**int**|Valeur indiquant quand le travail doit être exécuté.<br /><br /> **1** = une fois<br /><br /> **4** = quotidienne<br /><br /> **8** = hebdomadaire<br /><br /> **16** = mensuelle<br /><br /> **32** = mensuellement, relatif à la **freq_interval**<br /><br /> **64** = lancé au démarrage du service SQLServerAgent.|  
|**freq_interval**|**Int**|Jours lorsque la tâche est exécutée. La valeur dépend de la valeur de **freq_type**. Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_type**|**int**|Unités pour **freq_subday_interval**. Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_interval**|**int**|Nombre de **freq_subday_type** périodes entre chaque exécution du travail. Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_relative_interval**|**int**|Planifiées du travail de le **freq_interval** dans chaque mois. Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_recurrence_factor**|**Int**|Nombre de mois devant s'écouler entre les exécutions planifiées du travail.|  
|**active_start_date**|**int**|Date d'activation de la planification.|  
|**active_end_date**|**int**|Date de fin de la planification.|  
|**active_start_time**|**int**|Heure de début de la planification.|  
|**active_end_time**|**Int**|Heure de fin de la planification.|  
|**date_created**|**datetime**|Date de création de la planification.|  
|**schedule_description**|**nvarchar(4000)**|Description en anglais de la planification (sur demande).|  
|**job_count**|**int**|Renvoie le nombre de travaux auxquels la planification fait référence.|  
  
## <a name="remarks"></a>Notes  
 Lorsque aucun paramètre n’est fourni, **sp_help_schedule** répertorie des informations sur toutes les planifications de l’instance.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Membres de **SQLAgentUserRole** peuvent uniquement afficher les planifications dont ils sont propriétaires.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-listing-information-for-all-schedules-in-the-instance"></a>R. Affichage d'informations sur toutes les planifications de l'instance  
 L'exemple suivant affiche des informations sur toutes les planifications de l'instance.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_schedule ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-schedule"></a>B. Affichage d'informations sur une planification spécifique  
 L'exemple suivant affiche des informations sur la planifications nommée `NightlyJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
