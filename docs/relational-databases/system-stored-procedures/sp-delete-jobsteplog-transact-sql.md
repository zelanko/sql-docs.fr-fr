---
title: sp_delete_jobsteplog (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobsteplog
- sp_delete_jobsteplog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobsteplog
ms.assetid: e9ef4c99-abde-4038-b6a3-a25dcbaf0958
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f3a3140c154f5d4eb224259001333747ce410e67
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533869"
---
# <a name="spdeletejobsteplog-transact-sql"></a>sp_delete_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime tous les journaux d'étapes de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont spécifiés via les arguments. Utilisez cette procédure stockée pour maintenir la **sysjobstepslogs** table dans le **msdb** base de données.  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
       [ , [ @step_id = ] step_id | [ @step_name = ] 'step_name' ]  
       [ , [ @older_than = ] 'date' ]  
       [ , [ @larger_than = ] 'size_in_bytes' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] 'job_id'` Le numéro d’identification du travail qui contient le journal d’étapes de travail à supprimer. *job_id* est **int**, avec NULL comme valeur par défaut.  
  
`[ @job_name = ] 'job_name'` Le nom de la tâche. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
> **REMARQUE :** Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
`[ @step_id = ] step_id` Le numéro d’identification de l’étape du travail pour lequel le journal d’étapes doit être supprimé. Si ne pas inclus, tous les journaux d’étapes du travail sont supprimés, sauf si **@older_than** ou **@larger_than** sont spécifiés. *l’argument id_étape* est **int**, avec NULL comme valeur par défaut.  
  
`[ @step_name = ] 'step_name'` Le nom de l’étape du travail pour lequel le journal d’étapes doit être supprimé. *nom_de_l* est **sysname**, avec NULL comme valeur par défaut.  
  
> **REMARQUE :** Soit *id_de_l* ou *nom_de_l* peut être spécifié, mais ne peut pas être spécifiés.  
  
`[ @older_than = ] 'date'` La date et l’heure du journal d’étapes de travail plus ancien que vous souhaitez conserver. Tous les journaux d'étapes de travail antérieurs à cette date/heure sont supprimés. *date* est **datetime**, avec NULL comme valeur par défaut. Les deux **@older_than** et **@larger_than** peut être spécifié.  
  
`[ @larger_than = ] 'size_in_bytes'` La taille en octets du journal d’étapes de travail plus grande que vous souhaitez conserver. Tous les journaux d'étapes de travail dont la taille est supérieure à celle spécifiée sont supprimés. Les deux **@larger_than** et **@older_than** peut être spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 **sp_delete_jobsteplog** est dans le **msdb** base de données.  
  
 Si aucun argument sauf **@job_id** ou **@job_name** sont spécifiés, tous les journaux d’étape de travail pour le travail spécifié sont supprimés.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Seuls les membres du **sysadmin** peut supprimer un journal d’étapes de travail appartenant à un autre utilisateur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-removing-all-job-step-logs-from-a-job"></a>A. Suppression de tous les journaux d'étapes d'un travail particulier  
 L'exemple suivant montre la suppression de tous les journaux d'étapes du travail `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup';  
GO  
```  
  
### <a name="b-removing-the-job-step-log-for-a-particular-job-step"></a>B. Suppression du journal d'étapes de travail pour une étape particulière  
 L'exemple suivant montre la suppression du journal d'étapes de travail pour l'étape 2 du travail `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 2;  
GO  
```  
  
### <a name="c-removing-all-job-step-logs-based-on-age-and-size"></a>C. Suppression de tous les journaux d'étapes de travail en fonction de l'ancienneté et de la taille.  
 L'exemple suivant montre la suppression de tous les journaux d'étapes de travail créés avant le 25 octobre 2005 à midi et dont la taille est supérieure à 100 mégaoctets (Mo) pour le travail `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @older_than = '10/25/2005 12:00:00',  
    @larger_than = 104857600;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_help_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
