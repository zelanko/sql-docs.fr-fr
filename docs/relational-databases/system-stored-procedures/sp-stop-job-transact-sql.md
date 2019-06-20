---
title: sp_stop_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_stop_job_TSQL
- sp_stop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stop_job
ms.assetid: 64b4cc75-99a0-421e-b418-94e37595bbb0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eda439b53c72e41154d4891495470fc271028aee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63004261"
---
# <a name="spstopjob-transact-sql"></a>sp_stop_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Demande à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent d'arrêter l'exécution d'un travail.  

  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_stop_job   
      [@job_name =] 'job_name'  
    | [@job_id =] job_id   
    | [@originating_server =] 'master_server'  
    | [@server_name =] 'target_server'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_name = ] 'job_name'` Le nom du travail à arrêter. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @job_id = ] job_id` Le numéro d’identification du travail à arrêter. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
`[ @originating_server = ] 'master_server'` Le nom du serveur maître. Si ce nom est spécifié, tous les travaux multiserveurs sont arrêtés. *serveur_maître* est **nvarchar (128)** , avec NULL comme valeur par défaut. Spécifiez ce paramètre uniquement lorsque vous appelez **sp_stop_job** vers un serveur cible.  
  
> [!NOTE]  
>  Seul un des trois premiers paramètres peut être précisé.  
  
`[ @server_name = ] 'target_server'` Le nom du serveur cible spécifique sur lequel sera arrêté un travail multiserveur. *serveur_cible* est **nvarchar (128)** , avec NULL comme valeur par défaut. Spécifiez ce paramètre uniquement lorsque vous appelez **sp_stop_job** sur un serveur maître pour un travail multiserveur.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 **sp_stop_job** envoie un signal d’arrêt à la base de données. Certains processus peuvent être arrêtés immédiatement et certains doivent atteindre un point stable (ou un point d’entrée pour le chemin d’accès du code) avant qu’elles peuvent ne pas. Certaines instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] de longue durée telles que BACKUP, RESTORE et certaines commandes DBCC peuvent prendre beaucoup de temps. Lorsque ces éléments s’exécutent, peut prendre un certain temps avant que le travail est annulé. L'arrêt d'un travail provoque l'enregistrement d'une entrée « Travail annulé » dans l'historique des travaux.  
  
 Si un travail exécute actuellement une étape de type **CmdExec** ou **PowerShell**, le processus en cours d’exécution (par exemple, MyProgram.exe) est obligé de s’arrêter prématurément. La fin prématurée peut aboutir à un comportement imprévisible ; les fichiers que le processus utilise risquant, par exemple, d'être bloqués alors qu'ils sont ouverts. Par conséquent, **sp_stop_job** doit être utilisée uniquement dans des circonstances extrêmes si le travail contient des étapes de type **CmdExec** ou **PowerShell**.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Membres de **SQLAgentUserRole** et **SQLAgentReaderRole** peuvent interrompre uniquement les travaux dont ils sont propriétaires. Membres de **SQLAgentOperatorRole** peut arrêter tous les travaux locaux, y compris ceux qui sont détenus par d’autres utilisateurs. Membres de **sysadmin** peut arrêter tous les travaux locaux et multiserveurs.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant arrête un travail nommé `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_stop_job  
    N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
