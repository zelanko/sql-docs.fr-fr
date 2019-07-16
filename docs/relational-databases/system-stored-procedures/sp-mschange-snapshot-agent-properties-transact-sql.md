---
title: sp_MSchange_snapshot_agent_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_snapshot_agent_properties_TSQL
- sp_MSchange_snapshot_agent_properties
helpviewer_keywords:
- sp_MSchange_snapshot_agent_properties
ms.assetid: 7947a788-3fd7-469f-84db-b03ba89a153c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9c4dcd79945644f0bc44d9ca3e948fa4f85d4e40
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905184"
---
# <a name="spmschangesnapshotagentproperties-transact-sql"></a>sp_MSchange_snapshot_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d’un travail d’Agent d’instantané s’exécute sur un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure du serveur de distribution. Cette procédure stockée est utilisée pour modifier les propriétés lorsque le serveur de publication s’exécute sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Cette procédure stockée est exécutée au niveau du serveur de distribution sur la base de données de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_MSchange_snapshot_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @frequency_type= ] frequency_type  
        , [ @frequency_interval= ] frequency_interval  
        , [ @frequency_subday= ] frequency_subday  
        , [ @frequency_subday_interval= ] frequency_subday_interval  
        , [ @frequency_relative_interval= ] frequency_relative_interval  
        , [ @frequency_recurrence_factor= ] frequency_recurrence_factor  
        , [ @active_start_date= ] active_start_date  
        , [ @active_end_date= ] active_end_date  
        , [ @active_start_time_of_day= ] active_start_time_of_day  
        , [ @active_end_time_of_day= ] active_end_time_of_day  
        , [ @snapshot_job_name = ] 'snapshot_agent_name'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @frequency_type = ] frequency_type` Est la fréquence d’exécution de l’Agent d’instantané. *frequency_type* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|À la demande|  
|**4**|Tous les jours|  
|**8**|Semaine|  
|**10**|Mois|  
|**20**|Mensuellement, en fonction de l'intervalle de fréquence|  
|**40**|Au démarrage de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
`[ @frequency_interval = ] frequency_interval` Est la valeur à appliquer à la fréquence définie par *frequency_type*. *frequency_interval* est **int**, sans valeur par défaut.  
  
`[ @frequency_subday = ] frequency_subday` Unités pour *freq_subday_interval*. *frequency_subday* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|Seconde|  
|**4**|Minute|  
|**8**|Heure|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Intervalle de *frequency_subday*. *frequency_subday_interval* est **int**, sans valeur par défaut.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Est la date de que l’Agent d’instantané s’exécute. *frequency_relative_interval* est **int**, sans valeur par défaut.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Facteur de récurrence utilisé par *frequency_type*. *frequency_recurrence_factor* est **int**, sans valeur par défaut.  
  
`[ @active_start_date = ] active_start_date` Est la date à laquelle l’Agent d’instantané est premier planifiée, au format AAAAMMJJ. *active_start_date* est **int**, sans valeur par défaut.  
  
`[ @active_end_date = ] active_end_date` Date à laquelle l’Agent d’instantané cesse d’être planifié, représentée au format AAAAMMJJ. *active_end_date* est **int**, sans valeur par défaut.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Est l’heure de la journée à laquelle l’Agent d’instantané est la première planifié, au format HHMMSS. *active_start_time_of_day* est **int**, sans valeur par défaut.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` L’heure de la journée à laquelle l’Agent d’instantané cesse d’être planifié, représentée au format HHMMSS. *active_end_time_of_day* est **int**, sans valeur par défaut.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'` Est le nom d’un nom de travail d’Agent d’instantané existant si un travail existant est utilisé. *snapshot_agent_name* est **nvarchar (100)** , sans valeur par défaut.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Le mode de sécurité utilisé par l’agent lors de la connexion au serveur de publication. *publisher_security_mode* est **int**, sans valeur par défaut. **0** spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, et **1** Spécifie l’authentification Windows. La valeur **0** doit être spécifié pour les non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Est le nom de connexion utilisé lors de la connexion au serveur de publication. *publisher_login* est **sysname**, sans valeur par défaut. *publisher_login* doit être spécifié lorsque *publisher_security_mode* est **0**. Si *publisher_login* est NULL et le serveur de publication *_ ** security_mode* est **1**, le compte Windows spécifié dans *job_login* sera utilisé lors de la connexion au serveur de publication.  
  
`[ @publisher_password = ] 'publisher_password'` Est le mot de passe utilisé lors de la connexion au serveur de publication. *publisher_password* est **nvarchar (524)** , sans valeur par défaut.  
  
> [!IMPORTANT]  
>  Ne stockez pas les informations d'authentification dans des fichiers de script. Pour améliorer la sécurité, nous vous recommandons de fournir les noms de connexion et les mots de passe au moment de l'exécution.  
  
`[ @job_login = ] 'job_login'` Est la connexion pour le compte Windows sous lequel l’agent s’exécute. *job_login* est **nvarchar (257)** , sans valeur par défaut. Ce compte Windows est toujours utilisé pour les connexions des agents au serveur de distribution. Vous devez fournir ce paramètre lorsque vous créez un nouveau travail d'Agent d'instantané. *Cela ne peut pas être modifié pour non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *serveur de publication.*  
  
`[ @job_password = ] 'job_password'` Est le mot de passe pour le compte Windows sous lequel l’agent s’exécute. *job_password* est **sysname**, sans valeur par défaut. Vous devez fournir ce paramètre lorsque vous créez un nouveau travail d'Agent d'instantané.  
  
> [!IMPORTANT]  
>  Ne stockez pas les informations d'authentification dans des fichiers de script. Pour améliorer la sécurité, nous vous recommandons de fournir les noms de connexion et les mots de passe au moment de l'exécution.  
  
`[ @publisher_type = ] 'publisher_type'` Spécifie le type de serveur de publication lorsque le serveur de publication n’est pas en cours d’exécution dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *publisher_type* est **sysname**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Spécifie un serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Spécifie un serveur de publication Oracle standard.|  
|**ORACLE GATEWAY**|Spécifie un serveur de publication Oracle Gateway.|  
  
 Pour plus d’informations sur les différences entre un serveur de publication Oracle et un serveur de publication Oracle Gateway, consultez [vue d’ensemble de la publication Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_MSchange_snapshot_agent_properties** est utilisé dans la réplication de capture instantanée, la réplication transactionnelle et la réplication de fusion.  
  
 Vous devez spécifier tous les paramètres lors de l’exécution **sp_MSchange_snapshot_agent_properties**. Exécutez [sp_helppublication_snapshot](../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md) pour retourner les propriétés actuelles de la tâche de l’Agent d’instantané.  
  
 Lorsque le serveur de publication s’exécute sur une instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, vous devez utiliser [sp_changepublication_snapshot](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) pour modifier les propriétés d’un travail d’Agent d’instantané.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe sur le serveur de distribution peuvent exécuter **sp_MSchange_snapshot_agent_properties**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
  
