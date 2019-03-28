---
title: sp_help_jobhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobhistory_TSQL
- sp_help_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobhistory
ms.assetid: a944d44e-411b-4735-8ce4-73888d4262d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0b2ee476694098f4734c31439b48a7ec9efdc892
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534431"
---
# <a name="sphelpjobhistory-transact-sql"></a>sp_help_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les travaux pour les serveurs dans le domaine d'administration multiserveur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobhistory [ [ @job_id = ] job_id ]   
     [ , [ @job_name = ] 'job_name' ]   
     [ , [ @step_id = ] step_id ]   
     [ , [ @sql_message_id = ] sql_message_id ]   
     [ , [ @sql_severity = ] sql_severity ]   
     [ , [ @start_run_date = ] start_run_date ]   
     [ , [ @end_run_date = ] end_run_date ]   
     [ , [ @start_run_time = ] start_run_time ]   
     [ , [ @end_run_time = ] end_run_time ]   
     [ , [ @minimum_run_duration = ] minimum_run_duration ]   
     [ , [ @run_status = ] run_status ]   
     [ , [ @minimum_retries = ] minimum_retries ]   
     [ , [ @oldest_first = ] oldest_first ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @mode = ] 'mode' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] job_id` Numéro d’identification. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
`[ @job_name = ] 'job_name'` Le nom de la tâche. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @step_id = ] step_id` Le numéro d’identification de l’étape. *l’argument id_étape* est **int**, avec NULL comme valeur par défaut.  
  
`[ @sql_message_id = ] sql_message_id` Numéro d’identification de message d’erreur renvoyé par Microsoft SQL Server lors de l’exécution du travail. *id_du_message_sql* est **int**, avec NULL comme valeur par défaut.  
  
`[ @sql_severity = ] sql_severity` Le niveau de gravité du message d’erreur retourné par SQL Server lors de l’exécution du travail. *gravité_sql* est **int**, avec NULL comme valeur par défaut.  
  
`[ @start_run_date = ] start_run_date` Date de que début de la tâche. *date_de_début_d*est **int**, avec NULL comme valeur par défaut. *date_de_début_d* doit respecter le format AAAAMMJJ, où AAAA représente une année à quatre caractères, MM est un nom de deux chiffres du mois et JJ est un nom de jour.  
  
`[ @end_run_date = ] end_run_date` Date de que la tâche a été terminée. *Ce paramètre* est **int**, avec NULL comme valeur par défaut. *Ce paramètre*doit respecter le format AAAAMMJJ, où AAAA représente une année à quatre chiffres, MM est un nom de deux chiffres du mois et JJ est un nom de jour.  
  
`[ @start_run_time = ] start_run_time` Heure de que la tâche a démarré. *heure_de_début_d* est **int**, avec NULL comme valeur par défaut. *heure_de_début_d*doit respecter le format HHMMSS, où HH correspond à une heure de la journée, MM est une minute de deux caractères de la journée et SS est une seconde de deux caractères de la journée.  
  
`[ @end_run_time = ] end_run_time` Le temps que le travail terminé son exécution. *heure_de_fin_d* est **int**, avec NULL comme valeur par défaut. *heure_de_fin_d*doit respecter le format HHMMSS, où HH correspond à une heure de la journée, MM est une minute de deux caractères de la journée et SS est une seconde de deux caractères de la journée.  
  
`[ @minimum_run_duration = ] minimum_run_duration` La longueur minimale de pour l’exécution du travail. *durée_d* est **int**, avec NULL comme valeur par défaut. *durée_d*doit respecter le format HHMMSS, où HH correspond à une heure de la journée, MM est une minute de deux caractères de la journée et SS est une seconde de deux caractères de la journée.  
  
`[ @run_status = ] run_status` L’état d’exécution du travail. *état_de_l* est **int**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0**|Échec|  
|**1**|Opération réussie|  
|**2**|Reprise (étape uniquement)|  
|**3**|Opération annulée|  
|**4**|Messages en cours d’exécution|  
|**5**|Unknown|  
  
`[ @minimum_retries = ] minimum_retries` Le nombre minimal de fois qu’un travail de tentatives d’exécution. *minimum_de_reprises* est **int**, avec NULL comme valeur par défaut.  
  
`[ @oldest_first = ] oldest_first` S’il faut présenter en premier la sortie des travaux plus ancien est. *le_plus_ancien_en_premier* est **int**, avec une valeur par défaut **0**, laquelle présente tout d’abord les travaux les plus récents. **1** présente tout d’abord les travaux les plus anciens.  
  
`[ @server = ] 'server'` Le nom du serveur sur lequel le travail a été effectué. *serveur* est **nvarchar (30)**, avec NULL comme valeur par défaut.  
  
`[ @mode = ] 'mode'` Si SQL Server doit imprimer toutes les colonnes du jeu de résultats (**complète**) ou un résumé des colonnes. *mode* est **varchar(7)**, avec une valeur par défaut **Résumé**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 La liste des colonnes dépend de la valeur de *mode*. L’ensemble de colonnes le plus complet est indiqué ci-dessous et est retourné quand *mode* est FULL.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**Int**|Numéro d'identification de l'entrée d'historique.|  
|**job_id**|**uniqueidentifier**|Numéro d’identification du travail.|  
|**job_name**|**sysname**|Nom du travail.|  
|**step_id**|**Int**|Numéro d’identification de l’étape (sera **0** pour un historique des travaux).|  
|**step_name**|**sysname**|Nom de l'étape (NULL pour un historique des travaux).|  
|**sql_message_id**|**Int**|Pour une étape [!INCLUDE[tsql](../../includes/tsql-md.md)], représente le numéro d'erreur [!INCLUDE[tsql](../../includes/tsql-md.md)] le plus récent affiché pendant l'exécution de la commande.|  
|**sql_severity**|**Int**|Pour une étape [!INCLUDE[tsql](../../includes/tsql-md.md)], représente le degré de gravité [!INCLUDE[tsql](../../includes/tsql-md.md)] le plus élevé obtenu pendant l'exécution de la commande.|  
|**message**|**nvarchar(1024)**|Message d'historique d'étape ou de travail.|  
|**run_status**|**Int**|Résultat du travail ou de l'étape.|  
|**run_date**|**Int**|Date de début d'exécution du travail ou de l'étape.|  
|**run_time**|**Int**|Heure de début d'exécution du travail ou de l'étape.|  
|**run_duration**|**Int**|Durée, au format HHMMSS, de l'exécution du travail ou de l'étape.|  
|**operator_emailed**|**nvarchar(20)**|Opérateur qui a reçu un courrier électronique concernant ce travail (NULL pour un historique d'étape).|  
|**operator_netsent**|**nvarchar(20)**|Opérateur qui a reçu un message réseau concernant ce travail (NULL pour un historique d'étape).|  
|**operator_paged**|**nvarchar(20)**|Opérateur qui a reçu un message par radiomessagerie concernant ce travail (NULL pour un historique d'étape).|  
|**retries_attempted**|**Int**|Nombre de reprises de l'étape (0 pour un historique d'étape).|  
|**server**|**nvarchar(30)**|Serveur sur lequel est exécutée l'étape ou le travail. Est toujours (**local**).|  
  
## <a name="remarks"></a>Notes  
 **sp_help_jobhistory** retourne un rapport contenant l’historique des tâches planifiées spécifiées. Si aucun paramètre n'est précisé, le rapport contient l'historique de tous les travaux planifiés.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Membres de la **SQLAgentUserRole** rôle de base de données peut uniquement afficher l’historique des travaux dont ils sont propriétaires.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-listing-all-job-information-for-a-job"></a>A. Affichage de toutes les informations d'un travail  
 L'exemple ci-dessous répertorie toutes les informations du travail `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobhistory   
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-that-match-certain-conditions"></a>B. Affichage des informations sur les travaux répondant à certaines conditions  
 L'exemple ci-dessous imprime toutes les colonnes et toutes les informations de tous les travaux et toutes les étapes de travail qui ont échoué avec un message d'erreur `50100` (message d'erreur personnalisé) et un degré de gravité égal à `20`.  
  
```  
USE msdb  
GO  
  
EXEC dbo.sp_help_jobhistory  
    @sql_message_id = 50100,  
    @sql_severity = 20,  
    @run_status = 0,  
    @mode = N'FULL' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
