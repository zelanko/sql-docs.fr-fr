---
title: sp_addmergepullsubscription_agent (Transact-SQL) Microsoft Docs
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
ms.openlocfilehash: 07cc514d615c86a90dcf37fbd4748c3ab1776f06
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528973"
---
# <a name="sp_addmergepullsubscription_agent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ajoute un nouveau travail d'Agent permettant de planifier la synchronisation d'un abonnement par extraction de données (pull) à une publication de fusion. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @name = ] 'name'`C’est le nom de l’agent. *nom* est **sysname**, avec un défaut de NULL.  
  
`[ @publisher = ] 'publisher'`Est le nom du serveur Editeur. *éditeur* est **sysname**, sans défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Est le nom de la base de données Publisher. *publisher_db* est **sysname**, sans défaut.  
  
`[ @publication = ] 'publication'`Est le nom de la publication. *publication* est **sysname**, sans défaut.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Est-ce le mode de sécurité à utiliser lors de la connexion à un éditeur lors de la synchronisation. *publisher_security_mode* est **int**, avec un défaut de 1. Si **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifie l’authentification. Si **1**, spécifie l’authentification de Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Est la connexion à utiliser lors de la connexion à un éditeur lors de la synchronisation. *publisher_login* est **sysname**, avec un défaut de NULL.  
  
`[ @publisher_password = ] 'publisher_password'`Est-ce que le mot de passe est utilisé lors de la connexion à l’éditeur. *publisher_password* est **sysname**, avec un défaut de NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Si possible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password`La *mise en publisher_encrypted_password* n’est plus prise en charge. Tenter de définir ce paramètre **bit** à **1** entraînera une erreur.  
  
`[ @subscriber = ] 'subscriber'`Est le nom de l’abonné. *l’abonné* est **sysname**, avec un défaut de NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'`Est le nom de la base de données d’abonnement. *subscriber_db* est **sysname**, avec un défaut de NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode`Est-ce le mode de sécurité à utiliser lors de la connexion à un abonné lors de la synchronisation. *subscriber_security_mode* est **int**, avec un défaut de 1. Si **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifie l’authentification. Si **1**, spécifie l’authentification de Windows.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. L'Agent de fusion se connecte toujours à l'Abonné local à l'aide de l'authentification Windows. Si une valeur est spécifiée pour ce paramètre, un message d'avertissement est retourné, mais la valeur est ignorée.  
  
`[ @subscriber_login = ] 'subscriber_login'`Est-ce que l’abonné est connecté à un abonné lors de la synchronisation. *subscriber_login* est nécessaire si *subscriber_security_mode* est réglée à **0**. *subscriber_login* est **sysname**, avec un défaut de NULL.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. Si une valeur est spécifiée pour ce paramètre, un message d'avertissement est retourné, mais la valeur est ignorée.  
  
`[ @subscriber_password = ] 'subscriber_password'`Est le mot [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de passe de l’abonné pour l’authentification. *subscriber_password* est nécessaire si *subscriber_security_mode* est réglée à **0**. *subscriber_password* est **sysname**, avec un défaut de NULL.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. Si une valeur est spécifiée pour ce paramètre, un message d'avertissement est retourné, mais la valeur est ignorée.  
  
`[ @distributor = ] 'distributor'`Est le nom du distributeur. *distributeur* est **sysname**, avec un défaut de l’éditeur; *publisher* c’est-à-dire que l’éditeur est aussi le distributeur.  
  
`[ @distributor_security_mode = ] distributor_security_mode`Est-ce le mode de sécurité à utiliser lors de la connexion à un distributeur lors de la synchronisation. *distributor_security_mode* est **int**, avec un défaut de 0. **0** spécifie l’authentification. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **1** spécifie l’authentification de Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'`Est-ce que le distributeur se connecte à un distributeur lors de la synchronisation. *distributor_login* est nécessaire si *distributor_security_mode* est réglée à **0**. *distributor_login* est **sysname**, avec un défaut de NULL.  
  
`[ @distributor_password = ] 'distributor_password'`Est le mot de passe du distributeur. *distributor_password* est nécessaire si *distributor_security_mode* est réglée à **0**. *distributor_password* est **sysname**, avec un défaut de NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Si possible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
`[ @encrypted_password = ] encrypted_password`La *mise en encrypted_password* n’est plus prise en charge. Tenter de définir ce paramètre **bit** à **1** entraînera une erreur.  
  
`[ @frequency_type = ] frequency_type`Est la fréquence avec laquelle planifier l’agent de fusion. *frequency_type* est **int**, et peut être l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Ponctuelle|  
|**2**|À la demande|  
|**4**|Quotidien|  
|**8**|Hebdomadaire|  
|**16**|Mensuelle|  
|**32**|Mensuelle relative|  
|**64**|Autostart|  
|**128**|Périodique|  
|NULL (par défaut)||  
  
> [!NOTE]  
>  Spécifier une valeur de **64** fait fonctionner l’agent de fusion en mode continu. Cela correspond à la définition du paramètre **-continu** pour l’agent. Pour plus d’informations, voir [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
`[ @frequency_interval = ] frequency_interval`Le jour ou les jours que l’agent de fusion court. *frequency_interval* est **int**, et peut être l’une de ces valeurs.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Dimanche|  
|**2**|Lundi|  
|**3**|Mardi|  
|**4**|Mercredi|  
|**5**|Jeudi|  
|**6**|Vendredi|  
|**7**|Samedi|  
|**8**|jour|  
|**9**|Jours de la semaine|  
|**10**|Jours de week-end|  
|NULL (par défaut)||  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Est la date de l’agent de fusion. Ce paramètre est utilisé lorsque *frequency_type* est réglé à **32** (parent mensuel). *frequency_relative_interval* est **int**, et peut être l’une de ces valeurs.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Premier|  
|**2**|Seconde|  
|**4**|Troisième|  
|**8**|Quatrième|  
|**16**|Dernier|  
|NULL (par défaut)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Est-ce le facteur de répétition utilisé par *frequency_type*. *frequency_recurrence_factor* est **int**, avec un défaut de NULL.  
  
`[ @frequency_subday = ] frequency_subday`Est la fréquence du report au cours de la période définie. *frequency_subday* est **int**, et peut être l’une de ces valeurs.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|Seconde|  
|**4**|Minute|  
|**8**|Heure|  
|NULL (par défaut)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Est l’intervalle pour *frequency_subday*. *frequency_subday_interval* est **int**, avec un défaut de NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Est l’heure de la journée où l’agent de fusion est d’abord prévu, formaté comme HHMMSS. *active_start_time_of_day* est **int**, avec un défaut de NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Est-ce l’heure de la journée où l’agent de fusion cesse d’être programmé, formaté comme HHMMSS. *active_end_time_of_day* est **int**, avec un défaut de NULL.  
  
`[ @active_start_date = ] active_start_date`Est la date à laquelle l’agent de fusion est prévu pour la première fois, formaté comme YYYYMMDD. *active_start_date* est **int**, avec un défaut de NULL.  
  
`[ @active_end_date = ] active_end_date`Est la date à laquelle l’agent de fusion cesse d’être programmé, formaté comme YYYYMMDD. *active_end_date* est **int**, avec un défaut de NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'`Est une invite de commande facultative qui est fournie à l’agent de fusion. *optional_command_line* est **nvarchar(255)**, avec un défaut de '. Permet de fournir des paramètres supplémentaires à l'Agent de fusion, comme dans l'exemple suivant où le délai d'expiration par défaut de la requête est augmenté jusqu'à `600` secondes :  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid`Est le paramètre de sortie pour l’ID de travail. *merge_jobid* est **binaire(16)**, avec un défaut de NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Précise si l’abonnement peut être synchronisé par Windows Synchronization Manager. *enabled_for_syncmgr* est **nvarchar(5)**, avec un défaut de FALSE. Si **faux,** l’abonnement n’est pas enregistré auprès de Synchronization Manager. Si **c’est vrai,** l’abonnement est enregistré auprès de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Synchronization Manager et peut être synchronisé sans commencer.  
  
`[ @ftp_address = ] 'ftp_address'`Pour la compatibilité vers l’arrière seulement.  
  
`[ @ftp_port = ] ftp_port`Pour la compatibilité vers l’arrière seulement.  
  
`[ @ftp_login = ] 'ftp_login'`Pour la compatibilité vers l’arrière seulement.  
  
`[ @ftp_password = ] 'ftp_password'`Pour la compatibilité vers l’arrière seulement.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'`Spécifie l’emplacement à partir duquel ramasser les fichiers instantanés. *alternate_snapshot_folder* est **nvarchar(255)**, avec un défaut de NULL. Si la valeur est NULL, les fichiers d'instantané sont extraits à partir de l'emplacement par défaut spécifié par le serveur de publication.  
  
`[ @working_directory = ] 'working_directory'`Est-ce le nom de l’annuaire de travail utilisé pour stocker temporairement des données et des fichiers schéma pour la publication lorsque FTP est utilisé pour transférer des fichiers instantanés. *working_directory* est **nvarchar(255)**, avec un défaut de NULL.  
  
`[ @use_ftp = ] 'use_ftp'`Spécifie l’utilisation de FTP au lieu du protocole typique pour récupérer les instantanés. *use_ftp* est **nvarchar(5)**, avec un défaut de FALSE.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]`Utilise un résolveur interactif pour résoudre les conflits pour tous les articles qui permettent une résolution interactive. *use_interactive_resolver* est **nvarchar(5)**, avec un défaut de FALSE.  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  L'activation d'agent distant est déconseillée et n'est plus prise en charge. Ce paramètre est uniquement pris en charge pour assurer la compatibilité descendante des scripts. La définition *remote_agent_activation* à une valeur autre que **fausse** générera une erreur.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  L'activation d'agent distant est déconseillée et n'est plus prise en charge. Ce paramètre est uniquement pris en charge pour assurer la compatibilité descendante des scripts. La *configuration remote_agent_server_name* à n’importe quelle valeur non-NULL générera une erreur.  
  
`[ @job_name = ] 'job_name' ]`Est le nom d’un emploi d’agent existant. *job_name* est **sysname**, avec une valeur par défaut de NULL. Ce paramètre n'est indiqué que lorsque l'abonnement est synchronisé grâce à un travail existant plutôt qu'un nouveau travail (étant le comportement par défaut). Si vous n’êtes pas membre du rôle de serveur fixe **sysadmin,** vous devez spécifier *job_login* et *job_password* lorsque vous spécifiez *job_name*.  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]`Le chemin vers le dossier où les fichiers instantanés seront lus si un instantané de données filtré doit être utilisé. *dynamic_snapshot_location* est **nvarchar(260)**, avec un défaut de NULL. Pour plus d'informations, voir [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @use_web_sync = ] use_web_sync`Indique que la synchronisation Web est activée. *use_web_sync* est **un peu**, avec un défaut de 0. **1** spécifie que l’abonnement de traction peut être synchronisé sur Internet en utilisant HTTP.  
  
`[ @internet_url = ] 'internet_url'`Est l’emplacement de l’auditeur de réplication (REPLISAPI. DLL) pour la synchronisation Web. *internet_url* est **nvarchar(260)**, avec un défaut de NULL. *internet_url* est une URL entièrement qualifiée, `http://server.domain.com/directory/replisapi.dll`dans le format . Si le serveur est configuré de manière à être à l'écoute sur un port autre que le port 80, le numéro de port doit également être fourni sous la forme `http://server.domain.com:portnumber/directory/replisapi.dll`, où `portnumber` représente le port.  
  
`[ @internet_login = ] 'internet_login'`Est la connexion que l’agent de fusion utilise lors de la connexion au serveur Web qui héberge la synchronisation Web en utilisant HTTP Basic Authentication. *internet_login* est **sysname**, avec un défaut de NULL.  
  
`[ @internet_password = ] 'internet_password'`Est le mot de passe que l’agent de fusion utilise lors de la connexion au serveur Web qui héberge la synchronisation Web en utilisant HTTP Basic Authentication. *internet_password* est **nvarchar(524)**, avec une valeur par défaut de NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode`Est la méthode d’authentification utilisée par l’agent de fusion lors de la connexion au serveur Web lors de la synchronisation Web à l’aide de HTTPS. *internet_security_mode* est **int** et peut être l’une de ces valeurs.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|L'authentification de base est utilisée.|  
|**1** (par défaut)|L'authentification intégrée de Windows est utilisée.|  
  
> [!NOTE]  
>  Il est recommandé d'utiliser l'authentification de base pour la synchronisation Web. Pour utiliser la synchronisation Web, vous devez effectuer une connexion TLS au serveur Web. Pour plus d’informations, consultez [Configurer la synchronisation Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
`[ @internet_timeout = ] internet_timeout`Est-ce la durée, en quelques secondes, avant l’expiration d’une demande de synchronisation Web. *internet_timeout* est **int**, avec un défaut de **300** secondes.  
  
`[ @hostname = ] 'hostname'`Remplace la valeur de HOST_NAME() lorsque cette fonction est utilisée dans la clause WHERE d’un filtre paramétré. *nom d’hôte* est **sysname**, avec un défaut de NULL.  
  
`[ @job_login = ] 'job_login'`Est la connexion pour le compte Windows en vertu de laquelle l’agent s’exécute. *job_login* est **nvarchar(257)**, sans défaut. Ce compte Windows est toujours utilisé pour les connexions d'Agent à l'Abonné et pour les connexions au serveur de distribution et au serveur de publication lors de l'utilisation de l'authentification intégrée de Windows.  
  
`[ @job_password = ] 'job_password'`Est le mot de passe pour le compte Windows en vertu duquel l’agent s’exécute. *job_password* est **sysname**, sans défaut.  
  
> [!IMPORTANT]  
>  Ne stockez pas les informations d'authentification dans des fichiers de script. Pour une sécurité optimale, les noms de connexion et les mots de passe doivent être fournis au moment de l'exécution.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addmergepullsubscription_agent** est utilisé dans la réplication de fusion et utilise des fonctionnalités similaires à [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
 Pour un exemple de comment spécifier correctement les paramètres de sécurité lors de **l’exécution de sp_addmergepullsubscription_agent**, voir Créer un abonnement [Pull](../../relational-databases/replication/create-a-pull-subscription.md).  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle de serveur fixe **sysadmin** ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addmergepullsubscription_agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement Pull](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Abonnez-vous à Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
