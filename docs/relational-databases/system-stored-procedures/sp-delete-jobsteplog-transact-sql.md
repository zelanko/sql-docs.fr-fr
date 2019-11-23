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
ms.openlocfilehash: 66b353c7fc79b49cb9cd3fb9fe228075f3a0d473
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305096"
---
# <a name="sp_delete_jobsteplog-transact-sql"></a>sp_delete_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime tous les journaux d'étapes de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont spécifiés via les arguments. Utilisez cette procédure stockée pour tenir à jour la table **sysjobstepslogs** dans la base de données **msdb** .  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
       [ , [ @step_id = ] step_id | [ @step_name = ] 'step_name' ]  
       [ , [ @older_than = ] 'date' ]  
       [ , [ @larger_than = ] 'size_in_bytes' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] 'job_id'` le numéro d’identification du travail qui contient le journal d’étapes de travail à supprimer. *job_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @job_name = ] 'job_name'` le nom du travail. *job_name* est de **type sysname**, avec NULL comme valeur par défaut.  
  
> **Remarque :** *Job_id* ou *job_name* doivent être spécifiés, mais ne peuvent pas être spécifiés.  
  
`[ @step_id = ] step_id` le numéro d’identification de l’étape du travail pour lequel le journal d’étapes de travail doit être supprimé. Si ce n’est pas le cas, tous les journaux d’étapes de travail du travail sont supprimés, sauf si **\@older_than** ou **\@larger_than** sont spécifiés. *step_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @step_name = ] 'step_name'` le nom de l’étape du travail pour lequel le journal d’étapes de travail doit être supprimé. *step_name* est de **type sysname**, avec NULL comme valeur par défaut.  
  
> **Remarque :** *Step_id* ou *step_name* peuvent être spécifiés, mais ils ne peuvent pas être spécifiés.  
  
`[ @older_than = ] 'date'` la date et l’heure du journal d’étapes de travail le plus ancien que vous souhaitez conserver. Tous les journaux d'étapes de travail antérieurs à cette date/heure sont supprimés. *Date* est de **type DateTime**, avec NULL comme valeur par défaut. **\@older_than** et **\@larger_than** peuvent être spécifiés.  
  
`[ @larger_than = ] 'size_in_bytes'` la taille en octets du journal d’étapes de travail le plus volumineux que vous souhaitez conserver. Tous les journaux d'étapes de travail dont la taille est supérieure à celle spécifiée sont supprimés. **\@larger_than** et **\@older_than** peuvent être spécifiés.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 **sp_delete_jobsteplog** se trouve dans la base de données **msdb** .  
  
 Si aucun argument, à l’exception de **\@job_id** ou **\@job_name** n’est spécifié, tous les journaux d’étapes de travail pour le travail spécifié sont supprimés.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Seuls les membres de **sysadmin** peuvent supprimer un journal d’étapes de travail appartenant à un autre utilisateur.  
  
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
 [Procédures &#40;stockées SQL Server Agent Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
