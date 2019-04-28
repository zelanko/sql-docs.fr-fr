---
title: sp_changepublication_snapshot (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changepublication_snapshot_TSQL
- sp_changepublication_snapshot
helpviewer_keywords:
- sp_changepublication_snapshot
ms.assetid: 518a4618-3592-4edc-8425-cbc33cdff891
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1a5b55d2ec6a8be0df305e2c1ce7121b638250c4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997838"
---
# <a name="spchangepublicationsnapshot-transact-sql"></a>sp_changepublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés de l'Agent d'instantané pour la publication spécifiée. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
> [!IMPORTANT]  
>  Lors de la configuration d'un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées en texte brut au serveur de distribution. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changepublication_snapshot [ @publication= ] 'publication'  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @snapshot_job_name = ] 'snapshot_agent_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @frequency_type = ] frequency_type` Est la fréquence de planification de l’agent. *frequency_type* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|À la demande|  
|**4**|Tous les jours|  
|**8**|Semaine|  
|**16**|Mois|  
|**32**|Mensuelle relative|  
|**64**|Démarrage automatique|  
|**128**|Périodique|  
|NULL (par défaut)||  
  
`[ @frequency_interval = ] frequency_interval` Spécifie les jours pendant lesquels l’agent s’exécute. *frequency_interval* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Dimanche|  
|**2**|Lundi|  
|**3**|Mardi|  
|**4**|Mercredi|  
|**5**|Jeudi|  
|**6**|Vendredi|  
|**7**|Samedi|  
|**8**|Jour|  
|**9**|Jours de la semaine|  
|**10**|Jours de week-end|  
|NULL (par défaut)||  
  
`[ @frequency_subday = ] frequency_subday` Unités pour *freq_subday_interval*. *frequency_subday* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|Seconde|  
|**4**|Minute|  
|**8**|Heure|  
|NULL (par défaut)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Intervalle de *frequency_subday*. *frequency_subday_interval* est **int**, avec NULL comme valeur par défaut.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Est la date de que l’Agent d’instantané s’exécute. *frequency_relative_interval* est **int**, avec NULL comme valeur par défaut.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Facteur de récurrence utilisé par *frequency_type*. *frequency_recurrence_factor* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_start_date = ] active_start_date` Est la date à laquelle l’Agent d’instantané est premier planifiée, au format AAAAMMJJ. *active_start_date* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_end_date = ] active_end_date` Date à laquelle l’Agent d’instantané cesse d’être planifié, représentée au format AAAAMMJJ. *active_end_date* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Est l’heure de la journée à laquelle l’Agent d’instantané est la première planifié, au format HHMMSS. *active_start_time_of_day* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` L’heure de la journée à laquelle l’Agent d’instantané cesse d’être planifié, représentée au format HHMMSS. *active_end_time_of_day* est **int**, avec NULL comme valeur par défaut.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'` Est le nom d’un nom de travail d’Agent d’instantané existant si un travail existant est utilisé. *snapshot_agent_name* est **nvarchar (100)** avec une valeur par défaut NULL.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Le mode de sécurité utilisé par l’agent lors de la connexion au serveur de publication. *publisher_security_mode* est **smallint**, avec NULL comme valeur par défaut. **0** spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, et **1** Spécifie l’authentification Windows. La valeur **0** doit être spécifié pour les non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Est le nom de connexion utilisé lors de la connexion au serveur de publication. *publisher_login* est **sysname**, avec NULL comme valeur par défaut. *publisher_login* doit être spécifié lorsque *publisher_security_mode* est **0**. Si *publisher_login* a la valeur NULL et *publisher_security_mode* est **1**, le compte Windows spécifié dans *job_login* est utilisé lorsque connexion au serveur de publication.  
  
`[ @publisher_password = ] 'publisher_password'` Est le mot de passe utilisé lors de la connexion au serveur de publication. *publisher_password* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  N'utilisez pas de mot de passe vide. Utilisez un mot de passe fort. Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
`[ @job_login = ] 'job_login'` Est la connexion pour le compte Windows sous lequel l’agent s’exécute. *job_login* est **nvarchar (257)**, avec NULL comme valeur par défaut. Ce compte Windows est toujours utilisé pour les connexions des agents au serveur de distribution. Vous devez fournir ce paramètre lorsque vous créez un nouveau travail d'Agent d'instantané. Cela ne peut pas être modifié pour non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
`[ @job_password = ] 'job_password'` Est le mot de passe pour le compte Windows sous lequel l’agent s’exécute. *job_password* est **sysname**, avec NULL comme valeur par défaut. Vous devez fournir ce paramètre lorsque vous créez un nouveau travail d'Agent d'instantané.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
`[ @publisher = ] 'publisher'` Spécifie un non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé lors de la création d’un Agent d’instantané à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changepublication_snapshot** est utilisé dans la réplication de capture instantanée, la réplication transactionnelle et la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_changepublication_snapshot**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Changer les propriétés des publications et des articles](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
