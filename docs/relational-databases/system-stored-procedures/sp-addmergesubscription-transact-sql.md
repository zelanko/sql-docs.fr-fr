---
title: sp_addmergesubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergesubscription_TSQL
- sp_addmergesubscription
helpviewer_keywords:
- sp_addmergesubscription
ms.assetid: a191d817-0132-49ff-93ca-76f13e609b38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 639c090f1c133183dc4b864a3e0215e4c64b6773
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493011"
---
# <a name="spaddmergesubscription-transact-sql"></a>sp_addmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un abonnement de fusion par émission ( push) ou extraction (pull) de données. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addmergesubscription [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @subscriber_type= ] 'subscriber_type' ]  
    [ , [ @subscription_priority= ] subscription_priority ]  
    [ , [ @sync_type= ] 'sync_type' ]  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @optional_command_line= ] 'optional_command_line' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @use_interactive_resolver= ] 'use_interactive_resolver' ]  
    [ , [ @merge_job_name= ] 'merge_job_name' ]  
    [ , [ @hostname = ] 'hostname'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut. La publication doit déjà exister.  
  
`[ @subscriber = ] 'subscriber'` Est le nom de l’abonné. *abonné* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @subscriber_db = ] 'subscriber_db'` Est le nom de la base de données d’abonnement. *bd_abonné*est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @subscription_type = ] 'subscription_type'` Est le type d’abonnement. *subscription_type*est **nvarchar (15)**, avec PUSH comme valeur par défaut. Si **push**, un abonnement envoyé est ajouté et l’Agent de fusion est ajouté sur le serveur de distribution. Si **extraction**, un abonnement par extraction est ajouté sans ajouter un Agent de fusion sur le serveur de distribution.  
  
> [!NOTE]  
>  Les abonnements anonymes ne doivent pas utiliser cette procédure stockée.  
  
`[ @subscriber_type = ] 'subscriber_type'` Est le type d’abonné. *subscriber_type*est **nvarchar (15)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**local** (default)|Abonné connu uniquement sur le serveur de publication.|  
|**global**|Abonné connu sur tous les serveurs.|  
  
 Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures, les abonnements locaux sont des abonnements clients, et les abonnements globaux sont des abonnements serveur.  
  
`[ @subscription_priority = ] subscription_priority` Est un nombre indiquant la priorité de l’abonnement. *priorité_d*est **réel**, avec NULL comme valeur par défaut. Pour les abonnements de type local et anonyme, la valeur affectée à la priorité est 0.0. Pour les abonnements de type global, la valeur affectée à la priorité doit être inférieure à 100.0.  
  
`[ @sync_type = ] 'sync_type'` Est le type de synchronisation d’abonnement. *sync_type*est **nvarchar (15)**, avec une valeur par défaut **automatique**. Peut être **automatique** ou **aucun**. Si **automatique**, le schéma et les données initiales des tables publiées sont transférées vers l’abonné tout d’abord. Si **aucun**, il est supposé l’abonné possède déjà le schéma et les données initiales des tables publiées. Les données et les tables système sont toujours transférées.  
  
> [!NOTE]  
>  Nous vous recommandons de ne pas spécifier une valeur de **aucun**.  
  
`[ @frequency_type = ] frequency_type` Est une valeur qui indique où l’Agent de fusion doit s’exécuter. *frequency_type* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**4**|Tous les jours|  
|**8**|Semaine|  
|**10**|Mois|  
|**20**|Mensuellement, en fonction de l'intervalle de fréquence|  
|**40**|Au démarrage de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|NULL (par défaut)||  
  
`[ @frequency_interval = ] frequency_interval` L’ou les jours qui s’exécute l’Agent de fusion. *frequency_interval* est **int**, et peut prendre l’une des valeurs suivantes.  
  
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
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Est l’occurrence de fusion planifiée de l’intervalle de fréquence dans chaque mois. *frequency_relative_interval* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Première|  
|**2**|Seconde|  
|**4**|Troisième|  
|**8**|Quatrième|  
|**16**|Dernière|  
|NULL (par défaut)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Facteur de récurrence utilisé par *frequency_type*. *frequency_recurrence_factor*est **int**, avec NULL comme valeur par défaut.  
  
`[ @frequency_subday = ] frequency_subday` Unité de *frequency_subday_interval*. *frequency_subday* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|Seconde|  
|**4**|Minute|  
|**8**|Heure|  
|NULL (par défaut)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Fréquence à laquelle *frequency_subday* doit se produire entre chaque fusion. *frequency_subday_interval* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Est l’heure de la journée à laquelle l’Agent de fusion est premier planifié, au format HHMMSS. *active_start_time_of_day* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` L’heure de la journée à laquelle l’Agent de fusion cesse d’être planifié, représentée au format HHMMSS. *active_end_time_of_day* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_start_date = ] active_start_date` Est la date à laquelle l’Agent de fusion est premier planifiée, au format AAAAMMJJ. *active_start_date* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_end_date = ] active_end_date` Date à laquelle l’Agent de fusion cesse d’être planifié, représentée au format AAAAMMJJ. *active_end_date* est **int**, avec NULL comme valeur par défaut.  
  
`[ @optional_command_line = ] 'optional_command_line'` Est l’invite de commandes facultative à exécuter. *optional_command_line*est **nvarchar (4000)**, avec NULL comme valeur par défaut. Cet argument est utilisé pour ajouter une commande qui permet de capturer le résultat et de le sauvegarder dans un fichier ou de spécifier un fichier de configuration ou un attribut.  
  
`[ @description = ] 'description'` Est une brève description de cet abonnement de fusion. *Description*est **nvarchar (255)**, avec NULL comme valeur par défaut. Cette valeur est affichée par le moniteur de réplication dans le **nom convivial** colonne, qui peut être utilisé pour trier les abonnements pour une publication analysée.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Spécifie si l’abonnement peut être synchronisé par [!INCLUDE[msCoName](../../includes/msconame-md.md)] le Gestionnaire de synchronisation Windows. *l’argument enabled_for_syncmgr* est **nvarchar (5)**, avec FALSE comme valeur par défaut. Si **false**, l’abonnement n’est pas inscrit avec le Gestionnaire de synchronisation. Si **true**, l’abonnement est enregistré avec le Gestionnaire de synchronisation et peuvent être synchronisée sans démarrer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @offloadagent = ] remote_agent_activation` Spécifie que l’agent peut être activé à distance. *remote_agent_activation* est **bits** avec une valeur par défaut **0**.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est conservé que pour la compatibilité descendante des scripts.  
  
`[ @offloadserver = ] 'remote_agent_server_name'` Spécifie le nom réseau du serveur à utiliser pour l’activation de l’agent à distance. *remote_agent_server_name*est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver'` Permet d’être résolus de manière interactive pour tous les articles autorisant la résolution interactive des conflits. *use_interactive_resolver* est **nvarchar (5)**, avec FALSE comme valeur par défaut.  
  
`[ @merge_job_name = ] 'merge_job_name'` Le *@merge_job_name* paramètre est déconseillé et ne peut pas être définie. *merge_job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @hostname = ] 'hostname'` Remplace la valeur retournée par [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) lorsque cette fonction est utilisée dans la clause WHERE d’un filtre paramétré. *nom d’hôte* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  Pour des raisons de performance, il est recommandé de ne pas appliquer de fonctions aux noms de colonne dans les clauses des filtres de lignes paramétrables, telles que `LEFT([MyColumn]) = SUSER_SNAME()`. Si vous utilisez [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) dans une clause de filtre et que vous remplacez la valeur HOST_NAME, il peut être nécessaire de convertir les types de données à l’aide de [convertir](../../t-sql/functions/cast-and-convert-transact-sql.md). Pour plus d'informations sur la conduite à adopter dans cette situation, consultez la section « Substitution de la valeur de HOST_NAME » de la rubrique [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addmergesubscription** est utilisé dans la réplication de fusion.  
  
 Lorsque **sp_addmergesubscription** est exécutée par un membre de la **sysadmin** fixe le rôle de serveur pour créer un abonnement envoyé, le travail de l’Agent de fusion est implicitement créé et s’exécute sous le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent compte de service. Nous vous recommandons d’exécuter [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) et spécifiez les informations d’identification d’un compte Windows différent, spécifique à l’agent pour **@job_login** et **@job_password**. Pour plus d’informations, voir [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergesubscription-_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addmergesubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Créer un abonnement par extraction de données ](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Résolution interactive des conflits](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [S’abonner aux Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
