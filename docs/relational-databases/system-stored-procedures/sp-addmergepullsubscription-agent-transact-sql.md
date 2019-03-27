---
title: sp_addmergepullsubscription_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_agent
- sp_addmergepullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addmergepullsubscription_agent
ms.assetid: a2f4b086-078d-49b5-8971-8a1e3f6a6feb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5859d7e4c026375d5e9ade69628b9cf9e4a76ed0
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494361"
---
# <a name="spaddmergepullsubscriptionagent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un nouveau travail d'Agent permettant de planifier la synchronisation d'un abonnement par extraction de données (pull) à une publication de fusion. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addmergepullsubscription_agent [ [ @name = ] 'name' ]   
        , [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication =] 'publication'   
    [ , [ @publisher_security_mod e= ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher_encrypted_password = ] publisher_encrypted_password ]   
    [ , [ @subscriber = ] 'subscriber' ]   
    [ , [ @subscriber_db = ] 'subscriber_db' ]   
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]   
    [ , [ @subscriber_login = ] 'subscriber_login' ]   
    [ , [ @subscriber_password= ] 'subscriber_password' ]   
    [ , [ @distributor = ] 'distributor' ]   
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @encrypted_password = ] encrypted_password ]   
    [ , [ @frequency_type = ] frequency_type ]   
    [ , [ @frequency_interval = ] frequency_interval ]   
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]   
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]   
    [ , [ @frequency_subday = ] frequency_subday ]   
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]   
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]   
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @optional_command_line = ] 'optional_command_line' ]   
    [ , [ @merge_jobid = ] merge_jobid ]   
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]    
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @working_directory = ] 'working_directory' ]   
    [ , [ @use_ftp = ] 'use_ftp' ]   
    [ , [ @reserved = ] 'reserved' ]   
    [ , [ @use_interactive_resolver = ] 'use_interactive_resolver' ]   
    [ , [ @offloadagent = ] 'remote_agent_activation' ]   
    [ , [ @offloadserver = ] 'remote_agent_server_name']   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]  
    [ , [ @use_web_sync = ] use_web_sync ]  
        [ , [ @internet_url = ] 'internet_url' ]  
    [ , [ @internet_login = ] 'internet_login' ]  
        [ , [ @internet_password = ] 'internet_password' ]  
    [ , [ @internet_security_mode = ] internet_security_mode ]  
        [ , [ @internet_timeout = ] internet_timeout ]  
    [ , [ @hostname = ] 'hostname' ]  
        [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @name = ] 'name'` Est le nom de l’agent. *nom* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données du serveur de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Est le mode de sécurité à utiliser lors de la connexion à un serveur de publication lors de la synchronisation. *publisher_security_mode* est **int**, avec 1 comme valeur par défaut. Si **0**, spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. Si **1**, spécifie l’authentification Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Est la connexion à utiliser lors de la connexion à un serveur de publication lors de la synchronisation. *publisher_login* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @publisher_password = ] 'publisher_password'` Est le mot de passe utilisé lors de la connexion au serveur de publication. *publisher_password* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Si possible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password` Paramètre *mot_de_passe_éditeur_crypté* n’est plus pris en charge. Tentez de définir cela **bits** paramètre **1** entraîne une erreur.  
  
`[ @subscriber = ] 'subscriber'` Est le nom de l’abonné. *abonné* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @subscriber_db = ] 'subscriber_db'` Est le nom de la base de données d’abonnement. *bd_abonné* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` Est le mode de sécurité à utiliser lors de la connexion à un abonné lors de la synchronisation. *subscriber_security_mode* est **int**, avec 1 comme valeur par défaut. Si **0**, spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. Si **1**, spécifie l’authentification Windows.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. L'Agent de fusion se connecte toujours à l'Abonné local à l'aide de l'authentification Windows. Si une valeur est spécifiée pour ce paramètre, un message d'avertissement est retourné, mais la valeur est ignorée.  
  
`[ @subscriber_login = ] 'subscriber_login'` Est la connexion à l’abonné à utiliser lors de la connexion à un abonné lors de la synchronisation. *subscriber_login* est requise si *subscriber_security_mode* a la valeur **0**. *subscriber_login* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. Si une valeur est spécifiée pour ce paramètre, un message d'avertissement est retourné, mais la valeur est ignorée.  
  
`[ @subscriber_password = ] 'subscriber_password'` Le mot de passe de l’abonné pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. *subscriber_password* est requise si *subscriber_security_mode* a la valeur **0**. *subscriber_password* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. Si une valeur est spécifiée pour ce paramètre, un message d'avertissement est retourné, mais la valeur est ignorée.  
  
`[ @distributor = ] 'distributor'` Est le nom du serveur de distribution. *serveur de distribution* est **sysname**, avec une valeur par défaut *publisher*; autrement dit, le serveur de publication est également le serveur de distribution.  
  
`[ @distributor_security_mode = ] distributor_security_mode` Est le mode de sécurité à utiliser lors de la connexion à un serveur de distribution lors de la synchronisation. *distributor_security_mode* est **int**, avec 0 comme valeur par défaut. **0** spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. **1** Spécifie l’authentification Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` Est la connexion du serveur de distribution à utiliser lors de la connexion à un serveur de distribution lors de la synchronisation. *distributor_login* est requise si *distributor_security_mode* a la valeur **0**. *distributor_login* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @distributor_password = ] 'distributor_password'` Est le mot de passe du serveur de distribution. *distributor_password* est requise si *distributor_security_mode* a la valeur **0**. *distributor_password* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Si possible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
`[ @encrypted_password = ] encrypted_password` Paramètre *encrypted_password* n’est plus pris en charge. Tentez de définir cela **bits** paramètre **1** entraîne une erreur.  
  
`[ @frequency_type = ] frequency_type` Est la fréquence de planification de l’Agent de fusion. *frequency_type* est **int**, et peut prendre l’une des valeurs suivantes.  
  
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
  
> [!NOTE]  
>  La valeur **64** , l’Agent de fusion s’exécute en mode continu. Cela correspond au paramètre la **-continue** paramètre pour l’agent. Pour plus d’informations, voir [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
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
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Est la date de l’Agent de fusion. Ce paramètre est utilisé lorsque *frequency_type* a la valeur **32** (fréquence mensuelle relative). *frequency_relative_interval* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Première|  
|**2**|Seconde|  
|**4**|Troisième|  
|**8**|Quatrième|  
|**16**|Dernière|  
|NULL (par défaut)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Facteur de récurrence utilisé par *frequency_type*. *frequency_recurrence_factor* est **int**, avec NULL comme valeur par défaut.  
  
`[ @frequency_subday = ] frequency_subday` Est la fréquence de replanification nécessaire pendant la période définie. *frequency_subday* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|Seconde|  
|**4**|Minute|  
|**8**|Heure|  
|NULL (par défaut)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Intervalle de *frequency_subday*. *frequency_subday_interval* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Est l’heure de la journée à laquelle l’Agent de fusion est premier planifié, au format HHMMSS. *active_start_time_of_day* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` L’heure de la journée à laquelle l’Agent de fusion cesse d’être planifié, représentée au format HHMMSS. *active_end_time_of_day* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_start_date = ] active_start_date` Est la date à laquelle l’Agent de fusion est premier planifiée, au format AAAAMMJJ. *active_start_date* est **int**, avec NULL comme valeur par défaut.  
  
`[ @active_end_date = ] active_end_date` Date à laquelle l’Agent de fusion cesse d’être planifié, représentée au format AAAAMMJJ. *active_end_date* est **int**, avec NULL comme valeur par défaut.  
  
`[ @optional_command_line = ] 'optional_command_line'` Est une invite de commandes facultative qui est fournie à l’Agent de fusion. *optional_command_line* est **nvarchar (255)**, avec une valeur par défaut « ». Permet de fournir des paramètres supplémentaires à l'Agent de fusion, comme dans l'exemple suivant où le délai d'expiration par défaut de la requête est augmenté jusqu'à `600` secondes :  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid` Est le paramètre de sortie pour l’ID de travail. *id_travail_de_fusion* est **Binary (16)**, avec NULL comme valeur par défaut.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Spécifie si l’abonnement peut être synchronisé par le biais du Gestionnaire de synchronisation Windows. *l’argument enabled_for_syncmgr* est **nvarchar (5)**, avec FALSE comme valeur par défaut. Si **false**, l’abonnement n’est pas inscrit avec le Gestionnaire de synchronisation. Si **true**, l’abonnement est enregistré avec le Gestionnaire de synchronisation et peuvent être synchronisée sans démarrer [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @ftp_address = ] 'ftp_address'` Pour la compatibilité descendante uniquement.  
  
`[ @ftp_port = ] ftp_port` Pour la compatibilité descendante uniquement.  
  
`[ @ftp_login = ] 'ftp_login'` Pour la compatibilité descendante uniquement.  
  
`[ @ftp_password = ] 'ftp_password'` Pour la compatibilité descendante uniquement.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'` Spécifie l’emplacement à partir duquel récupérer les fichiers de capture instantanée. *alternate_snapshot_folder* est **nvarchar (255)**, avec NULL comme valeur par défaut. Si la valeur est NULL, les fichiers d'instantané sont extraits à partir de l'emplacement par défaut spécifié par le serveur de publication.  
  
`[ @working_directory = ] 'working_directory'` Est le nom du répertoire de travail utilisé pour stocker temporairement les fichiers de données et le schéma de la publication lorsque FTP est utilisé pour transférer des fichiers d’instantanés. *working_directory* est **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
`[ @use_ftp = ] 'use_ftp'` Spécifie l’utilisation de FTP au lieu du protocole usuel pour extraire les instantanés. *use_ftp* est **nvarchar (5)**, avec FALSE comme valeur par défaut.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]` Utiliser le résolveur interactif pour résoudre les conflits pour tous les articles autorisant la résolution interactive. *use_interactive_resolver* est **nvarchar (5)**, avec FALSE comme valeur par défaut.  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  L'activation d'agent distant est déconseillée et n'est plus prise en charge. Ce paramètre est uniquement pris en charge pour assurer la compatibilité descendante des scripts. Paramètre *remote_agent_activation* à une valeur autre que **false** générera une erreur.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  L'activation d'agent distant est déconseillée et n'est plus prise en charge. Ce paramètre est uniquement pris en charge pour assurer la compatibilité descendante des scripts. Paramètre *remote_agent_server_name* à n’importe quelle valeur non NULL générera une erreur.  
  
`[ @job_name = ] 'job_name' ]` Est le nom d’un travail d’agent existant. *job_name* est **sysname**, avec NULL comme valeur par défaut. Ce paramètre n'est indiqué que lorsque l'abonnement est synchronisé grâce à un travail existant plutôt qu'un nouveau travail (étant le comportement par défaut). Si vous n’êtes pas membre de la **sysadmin** rôle serveur fixe, vous devez spécifier *job_login* et *job_password* lorsque vous spécifiez *nom_travail*.  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]` Le chemin d’accès au dossier où les fichiers d’instantanés seront lues à partir de si un instantané de données filtrées doit être utilisé. *dynamic_snapshot_location* est **nvarchar (260)**, avec NULL comme valeur par défaut. Pour plus d'informations, voir [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @use_web_sync = ] use_web_sync` Indique que la synchronisation Web est activée. *use_web_sync* est **bits**, avec 0 comme valeur par défaut. **1** Spécifie que l’abonnement par extraction peut être synchronisé via internet à l’aide de HTTP.  
  
`[ @internet_url = ] 'internet_url'` Est l’emplacement de l’écouteur de réplication (REPLISAPI. DLL) pour la synchronisation Web. *internet_url* est **nvarchar (260)**, avec NULL comme valeur par défaut. *internet_url* est une URL qualifiée complète, au format `http://server.domain.com/directory/replisapi.dll`. Si le serveur est configuré de manière à être à l'écoute sur un port autre que le port 80, le numéro de port doit également être fourni sous la forme `http://server.domain.com:portnumber/directory/replisapi.dll`, où `portnumber` représente le port.  
  
`[ @internet_login = ] 'internet_login'` La connexion de l’Agent de fusion utilise pour se connecter au serveur Web qui héberge la synchronisation Web est à l’aide de l’authentification de base HTTP. *internet_login* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @internet_password = ] 'internet_password'` Le mot de passe utilisé par l’Agent de fusion lors de la connexion au serveur Web qui héberge la synchronisation Web est à l’aide de l’authentification de base HTTP. *internet_password* est **nvarchar (524)**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode` Est la méthode d’authentification utilisée par l’Agent de fusion lors de la connexion au serveur Web pendant la synchronisation Web à l’aide de HTTPS. *internet_security_mode* est **int** et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0**|L'authentification de base est utilisée.|  
|**1** (par défaut)|L'authentification intégrée de Windows est utilisée.|  
  
> [!NOTE]  
>  Il est recommandé d'utiliser l'authentification de base pour la synchronisation Web. Pour utiliser la synchronisation Web, vous devez établir une connexion SSL au serveur Web. Pour plus d’informations, consultez [Configurer la synchronisation Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
`[ @internet_timeout = ] internet_timeout` Est la durée, en secondes, avant l’expiration de la demande de synchronisation Web. *internet_timeout* est **int**, avec une valeur par défaut **300** secondes.  
  
`[ @hostname = ] 'hostname'` Remplace la valeur de HOST_NAME() lorsque cette fonction est utilisée dans la clause WHERE d’un filtre paramétré. *nom d’hôte* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @job_login = ] 'job_login'` Est la connexion pour le compte Windows sous lequel l’agent s’exécute. *job_login* est **nvarchar (257)**, sans valeur par défaut. Ce compte Windows est toujours utilisé pour les connexions d'Agent à l'Abonné et pour les connexions au serveur de distribution et au serveur de publication lors de l'utilisation de l'authentification intégrée de Windows.  
  
`[ @job_password = ] 'job_password'` Est le mot de passe pour le compte Windows sous lequel l’agent s’exécute. *job_password* est **sysname**, sans valeur par défaut.  
  
> [!IMPORTANT]  
>  Ne stockez pas les informations d'authentification dans des fichiers de script. Pour une sécurité optimale, les noms de connexion et les mots de passe doivent être fournis au moment de l'exécution.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addmergepullsubscription_agent** est utilisée dans la réplication de fusion et utilise des fonctionnalités similaires à celles [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
 Pour obtenir un exemple montrant comment spécifier correctement les paramètres de sécurité lors de l’exécution **sp_addmergepullsubscription_agent**, consultez [Créer un abonnement par extraction de données ](../../relational-databases/replication/create-a-pull-subscription.md).  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addmergepullsubscription_agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement par extraction de données ](../../relational-databases/replication/create-a-pull-subscription.md)   
 [S’abonner aux Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
