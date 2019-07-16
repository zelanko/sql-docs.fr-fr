---
title: sp_help_jobactivity (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobactivity_TSQL
- sp_help_jobactivity
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobactivity
ms.assetid: d344864f-b4d3-46b1-8933-b81dec71f511
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95283eee1a38dbafd9824986188df565103de06c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054979"
---
# <a name="sphelpjobactivity-transact-sql"></a>sp_help_jobactivity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les informations concernant l'état d'exécution des travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobactivity { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @session_id = ] session_id ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] job_id` Numéro d’identification. *job_id*est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
`[ @job_name = ] 'job_name'` Le nom de la tâche. *job_name*est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
`[ @session_id = ] session_id` L’id de session à des informations de rapport. *session_id* est **int**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne le jeu de résultats suivant :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**Int**|Numéro d'identification de la session de l'Agent.|  
|**job_id**|**uniqueidentifier**|Identificateur du travail.|  
|**job_name**|**sysname**|Nom du travail.|  
|**run_requested_date**|**datetime**|Moment auquel le travail devait s'exécuter.|  
|**run_requested_source**|**sysname**|Source de la requête pour exécuter le travail. Une des valeurs suivantes :<br /><br /> **1** = exécuter selon une planification<br /><br /> **2** = exécution en réponse à une alerte<br /><br /> **3** = exécution au démarrage<br /><br /> **4** = exécution par l’utilisateur<br /><br /> **6** = exécution en fonction de planification inactive de l’UC|  
|**queued_date**|**datetime**|Moment où la requête a intégré une file d'attente. NULL si le travail a été exécuté directement.|  
|**start_execution_date**|**datetime**|Moment où le travail a été attribué à un thread exécutable.|  
|**last_executed_step_id**|**int**|ID de l'étape du travail exécutée en dernier lieu.|  
|**last_exectued_step_date**|**datetime**|Heure à laquelle l'étape du travail exécutée en dernier lieu a démarré son exécution.|  
|**stop_execution_date**|**datetime**|Heure à laquelle l'exécution du travail s'est terminée.|  
|**next_scheduled_run_date**|**datetime**|Date et heure prévues pour la prochaine exécution du travail.|  
|**job_history_id**|**int**|Identificateur de l'historique des travaux dans la table d'historique des travaux.|  
|**message**|**nvarchar(1024)**|Message produit lors de la dernière exécution du travail.|  
|**run_status**|**int**|État retourné de la dernière exécution du travail :<br /><br /> **0** = erreur échoué<br /><br /> **1** = a réussi<br /><br /> **3** = annulée<br /><br /> **5** = état inconnu|  
|**operator_id_emailed**|**Int**|Numéro d'identification de l'opérateur notifié par courrier électronique en fin de travail.|  
|**operator_id_netsent**|**int**|Numéro d’identification de l’opérateur notifié par **envoi réseau** à l’achèvement du travail.|  
|**operator_id_paged**|**int**|Numéro d'identification de l'opérateur notifié par radiomessagerie en fin de travail.|  
  
## <a name="remarks"></a>Notes  
 Cette procédure fournit un instantané de l'état actuel des travaux. Les résultats renvoyés représentent des informations correspondant au moment du traitement de la requête.  
  
 L'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée un ID de session chaque fois que le service SQL Agent démarre. L’id de session est stocké dans la table **msdb.dbo.syssessions**.  
  
 En cas de non *session_id* est fourni, répertorie des informations sur la session la plus récente.  
  
 En cas de non *nom_travail* ou *job_id* est fourni, répertorie des informations pour tous les travaux.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres de la **sysadmin** rôle serveur fixe permettre exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Seuls les membres du **sysadmin** peuvent afficher l’activité des travaux appartenant à d’autres utilisateurs.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant répertorie les activités de tous les travaux que l'utilisateur actuel a l'autorisation d'afficher.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobactivity ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
