---
title: sp_help_jobserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6a1a2ce1208dcf359bb0586c3de1fe294644e3a5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68054879"
---
# <a name="sp_help_jobserver-transact-sql"></a>sp_help_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur le serveur pour un travail donné.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobserver  
     { [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name' }  
     [ , [ @show_last_run_details = ] show_last_run_details ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] job_id`Numéro d’identification du travail pour lequel des informations doivent être retournées. *job_id* est de type **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
`[ @job_name = ] 'job_name'`Nom du travail pour lequel des informations doivent être retournées. *job_name* est de **type sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *Job_id* ou *job_name* doivent être spécifiés, mais ne peuvent pas être spécifiés.  
  
`[ @show_last_run_details = ] show_last_run_details`Indique si les informations sur l’exécution de la dernière exécution font partie du jeu de résultats. *show_last_run_details* est de **type tinyint**, avec **0**comme valeur par défaut. **0** n’inclut pas les informations de dernière exécution, et **1** le fait.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Numéro d'identification du serveur cible.|  
|**server_name**|**nvarchar(30**|Nom de l'ordinateur du serveur cible.|  
|**enlist_date**|**DATETIME**|Date d'inscription du serveur cible sur le serveur maître.|  
|**last_poll_date**|**DATETIME**|Date à laquelle le serveur cible a interrogé pour la dernière fois le serveur maître.|  
  
 Si **sp_help_jobserver** est exécutée avec *show_last_run_details* défini sur **1**, le jeu de résultats contient ces colonnes supplémentaires.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**int**|Date du début de la dernière exécution du travail sur ce serveur cible.|  
|**last_run_time**|**int**|Heure du début de la dernière exécution du travail sur ce serveur.|  
|**last_run_duration**|**int**|Durée du travail lors de sa dernière exécution sur ce serveur cible (en secondes).|  
|**last_outcome_message**|**nvarchar(1024)**|Décrit le dernier résultat du travail.|  
|**last_run_outcome**|**int**|Résultat du travail à l'issue de sa dernière exécution sur ce serveur.<br /><br /> **0** = échec<br /><br /> **1** = réussite<br /><br /> **3** = annulé<br /><br /> **5** = inconnu|  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Les membres de **SQLAgentUserRole** peuvent uniquement afficher des informations sur les travaux dont ils sont propriétaires.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie des informations, dont les informations sur la dernière exécution, du travail `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobserver  
    @job_name = N'NightlyBackups',  
    @show_last_run_details = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
