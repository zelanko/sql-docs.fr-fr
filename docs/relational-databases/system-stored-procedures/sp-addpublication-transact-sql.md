---
title: sp_addpublication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpublication_TSQL
- sp_addpublication
helpviewer_keywords:
- sp_addpublication
ms.assetid: c7167ed1-2b7e-4824-b82b-65f4667c4407
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10d12ceed949a18c767e060cd35a738047ed6b74
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204979"
---
# <a name="spaddpublication-transact-sql"></a>sp_addpublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée une publication d'instantané ou transactionnelle. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addpublication [ @publication = ] 'publication'  
    [ , [ @taskid = ] tasked ]  
    [ , [ @restricted = ] 'restricted' ]  
    [ , [ @sync_method = ] 'sync_method' ]  
    [ , [ @repl_freq = ] 'repl_freq' ]  
    [ , [ @description = ] 'description' ]  
    [ , [ @status = ] 'status' ]  
    [ , [ @independent_agent = ] 'independent_agent' ]  
    [ , [ @immediate_sync = ] 'immediate_sync' ]  
    [ , [ @enabled_for_internet = ] 'enabled_for_internet' ]  
    [ , [ @allow_push = ] 'allow_push'  
    [ , [ @allow_pull = ] 'allow_pull' ]  
    [ , [ @allow_anonymous = ] 'allow_anonymous' ]  
    [ , [ @allow_sync_tran = ] 'allow_sync_tran' ]  
    [ , [ @autogen_sync_procs = ] 'autogen_sync_procs' ]  
    [ , [ @retention = ] retention ]  
    [ , [ @allow_queued_tran= ] 'allow_queued_updating' ]  
    [ , [ @snapshot_in_defaultfolder= ] 'snapshot_in_default_folder' ]  
    [ , [ @alt_snapshot_folder= ] 'alternate_snapshot_folder' ]  
    [ , [ @pre_snapshot_script= ] 'pre_snapshot_script' ]  
    [ , [ @post_snapshot_script= ] 'post_snapshot_script' ]  
    [ , [ @compress_snapshot= ] 'compress_snapshot' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port= ] ftp_port ]  
    [ , [ @ftp_subdirectory = ] 'ftp_subdirectory' ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @allow_dts = ] 'allow_dts' ]  
    [ , [ @allow_subscription_copy = ] 'allow_subscription_copy' ]  
    [ , [ @conflict_policy = ] 'conflict_policy' ]  
    [ , [ @centralized_conflicts = ] 'centralized_conflicts' ]   
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @queue_type = ] 'queue_type' ]  
    [ , [ @add_to_active_directory = ] 'add_to_active_directory' ]  
    [ , [ @logreader_job_name = ] 'logreader_agent_name' ]  
    [ , [ @qreader_job_name = ] 'queue_reader_agent_name' ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @allow_initialize_from_backup = ] 'allow_initialize_from_backup' ]  
    [ , [ @replicate_ddl = ] replicate_ddl ]  
    [ , [ @enabled_for_p2p = ] 'enabled_for_p2p' ]  
    [ , [ @publish_local_changes_only = ] 'publish_local_changes_only' ]  
    [ , [ @enabled_for_het_sub = ] 'enabled_for_het_sub' ]  
    [ , [ @p2p_conflictdetection = ] 'p2p_conflictdetection' ]  
    [ , [ @p2p_originator_id = ] p2p_originator_id  
    [ , [ @p2p_continue_onconflict = ] 'p2p_continue_onconflict'  
    [ , [ @allow_partition_switch = ] 'allow_partition_switch'  
    [ , [ @replicate_partition_switch = ]'replicate_partition_switch'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'**_publication_**'**  
 Nom de la publication à créer. *publication* est **sysname**, sans valeur par défaut. Le nom doit être unique au sein de la base de données.  
  
 [  **@taskid=**] *taskid*  
 Prise en charge pour la compatibilité descendante uniquement. Utilisez [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md).  
  
 [  **@restricted=**] **'**_restreint_**'**  
 Prise en charge pour la compatibilité descendante uniquement. Utilisez *accès_par_défaut*.  
  
 [  **@sync_method=**] _' sync_method_**'**  
 Mode de synchronisation. *sync_method* est **nvarchar(13)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**native**|Produit une copie par bloc en mode natif de toutes les tables. *Non pris en charge pour les serveurs de publication Oracle*.|  
|**character**|Produit une copie par bloc en mode caractère de toutes les tables. *Pour un serveur de publication Oracle,* **caractère** *est valide uniquement pour la réplication de capture instantanée*.|  
|**simultanées**|Produit une copie en bloc en mode natif de toutes les tables, mais ne verrouille pas les tables au cours de l'instantané. Pris en charge uniquement pour les publications transactionnelles. *Non pris en charge pour les serveurs de publication Oracle*.|  
|**concurrent_c**|Produit une copie en bloc en mode caractère de toutes les tables, mais ne verrouille pas les tables au cours de l'instantané. Pris en charge uniquement pour les publications transactionnelles.|  
|**Instantané de base de données**|Produit une copie en bloc en mode natif de toutes les tables à partir d'un instantané de base de données. Les instantanés de base de données ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prise en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).|  
|**caractère d’instantané de base de données**|Produit une copie en bloc en mode caractère de toutes les tables à partir d'un instantané de base de données. Les instantanés de base de données ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prise en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).|  
|NULL (par défaut)|Valeur par défaut est **natif** pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication. Pour non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication, valeur par défaut est **caractère** lorsque la valeur de *repl_freq* est **instantané** et **concurrent_c** pour tous les autres cas.|  
  
 [  **@repl_freq=**] **'**_repl_freq_**'**  
 Est le type de fréquence de réplication, *repl_freq* est **nvarchar (10)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**continue** (valeur par défaut)|Le serveur de publication fournit la sortie de toutes les transactions enregistrées dans le journal. Pour les non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les éditeurs, ceci nécessite que *sync_method* être définie sur **concurrent_c**.|  
|**Capture instantanée**|Le serveur de publication fournit uniquement les événements de synchronisation planifiés. Pour les non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les éditeurs, ceci nécessite que *sync_method* être définie sur **caractère**.|  
  
 [  **@description=**] **'**_description_**'**  
 Est une description facultative pour la publication. *Description* est **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
 [  **@status=**] **'**_état_**'**  
 Indique si les données de publication sont disponibles. *état* est **nvarchar (8)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**Active**|Les données de publication sont disponibles immédiatement pour les Abonnés.|  
|**inactif** (valeur par défaut)|Les données de la publication ne sont pas disponibles pour les Abonnés lors de la première création de la publication (ils peuvent s'abonner, mais les abonnements ne sont pas traités).|  
  
 *Non pris en charge pour les serveurs de publication Oracle*.  
  
 [  **@independent_agent=**] **'**_independent_agent_**'**  
 Spécifie s'il existe une version autonome de l'Agent de distribution pour cette publication *independent_agent* est **nvarchar (5)**, avec FALSE comme valeur par défaut. Si **true**, il existe un Agent de Distribution autonome pour cette publication. Si **false**, la publication utilise un Agent de Distribution partagé, et chaque paire de base de données de serveur de publication/abonné de base de données a un seul Agent partagé.  
  
 [  **@immediate_sync=**] **'**_qu’immediate_synchronization_**'**  
 Indique si les fichiers de synchronisation de la publication sont créés chaque fois que l'Agent d'instantané est exécuté. *qu’immediate_synchronization* est **nvarchar (5)**, avec FALSE comme valeur par défaut. Si **true**, les fichiers de synchronisation sont créés ou recréés chaque fois que l’Agent d’instantané s’exécute. Les Abonnés peuvent obtenir les fichiers de synchronisation immédiatement si l'Agent d'instantané a fini de s'exécuter avant la création de l'abonnement. Les nouveaux abonnements obtiennent les fichiers de synchronisation les plus récents, générés lors de la dernière exécution de l'Agent d'instantané. *independent_agent* doit être **true** pour *qu’immediate_synchronization* être **true**. Si **false**, les fichiers de synchronisation sont créés uniquement s’il existe de nouveaux abonnements. Vous devez appeler [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) pour chaque abonnement lorsque vous ajoutez progressivement un nouvel article à une publication existante. Les abonnés ne peuvent recevoir les fichiers de synchronisation après s'être abonnés qu'après le lancement et l'exécution des Agents d'instantané.  
  
 [  **@enabled_for_internet=**] **'**_enabled_for_internet_**'**  
 Indique si la publication est activée pour Internet et détermine si le protocole de transfert de fichiers (FTP) peut être utilisé pour le transfert des fichiers d'instantané à un abonné. *enabled_for_internet* est **nvarchar (5)**, avec FALSE comme valeur par défaut. Si **true**, les fichiers de synchronisation pour la publication sont placés dans le répertoire C:\Program Files\Microsoft SQL Server\MSSQL\MSSQL.x\Repldata\Ftp. L'utilisateur doit créer le répertoire FTP.  
  
 [  **@allow_push=**] **'**_allow_push_**'**  
 Indique si des abonnements par envoi de données (push) peuvent être créés pour la publication concernée. *allow_push* est **nvarchar (5)**, par défaut est TRUE, ce qui permet des abonnements envoyés sur la publication.  
  
 [  **@allow_pull=**] **'**_allow_pull_**'**  
 Indique si des abonnements par extraction de données (pull) peuvent être créés pour la publication concernée. *allow_pull* est **nvarchar (5)**, avec FALSE comme valeur par défaut. Si **false**, abonnements par extraction ne sont pas autorisés pour la publication.  
  
 [  **@allow_anonymous=**] **'**_allow_anonymous_**'**  
 Indique si des abonnements anonymes peuvent être créés pour la publication concernée. *allow_anonymous* est **nvarchar (5)**, avec FALSE comme valeur par défaut. Si **true**, *qu’immediate_synchronization* doit également être définie sur **true**. Si **false**, les abonnements anonymes ne sont pas autorisés pour la publication.  
  
 [  **@allow_sync_tran=**] **'**_allow_sync_tran_**'**  
 Indique si les abonnements de mise à jour immédiate sont autorisés sur la publication. *allow_sync_tran* est **nvarchar (5)**, avec FALSE comme valeur par défaut. **true** est *ne pas pris en charge pour les serveurs de publication Oracle*.  
  
 [  **@autogen_sync_procs=**] **'**_proc_sync_autogén_**'**  
 Indique si la procédure stockée de synchronisation pour la mise à jour des abonnements est générée par le serveur de publication. *proc_sync_autogén* est **nvarchar (5)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**true**|Défini automatiquement lorsque la mise à jour des abonnements est activée.|  
|**false**|Défini automatiquement lorsque la mise à jour des abonnements n'est pas activée, ou pour les serveurs de publication Oracle.|  
|NULL (par défaut)|Valeur par défaut est **true** lorsque la mise à jour des abonnements est activé et à **false** lorsque la mise à jour des abonnements n’est pas activé.|  
  
> [!NOTE]  
>  Valeur fournie par l’utilisateur *proc_sync_autogén*seront remplacées selon les valeurs spécifiées pour *allow_queued_tran* et *allow_sync_tran*.  
  
 [  **@retention=**] *rétention*  
 Période de rétention, exprimée en heures, pour l'activité d'abonnement. *rétention* est **int**, avec une valeur par défaut de 336 heures. Si un abonnement reste inactif durant la période de rétention, il arrive à expiration et est supprimé. La valeur peut être supérieure à la période de rétention maximale de la base de données de distribution utilisée par le serveur de publication. Si **0**, les abonnements connus à la publication n’expire jamais et supprimés par l’Agent de nettoyage abonnement arrivé à expiration.  
  
 [  **@allow_queued_tran=** ] **'**_allow_queued_updating_**'**  
 Active ou désactive la file d'attente des modifications sur l'Abonné jusqu'à ce que celles-ci soient appliquées au niveau du serveur de publication. *allow_queued_updating* est **nvarchar (5)** avec FALSE comme valeur par défaut. Si **false**, modifications sur l’abonné ne sont pas mises en attente. **true** est *ne pas pris en charge pour les serveurs de publication Oracle*.  
  
 [  **@snapshot_in_defaultfolder=** ] **'**_snapshot_in_default_folder_**'**  
 Indique si les fichiers d'instantané sont stockés dans le dossier par défaut. *snapshot_in_default_folder* est **nvarchar (5)** avec une valeur par défaut TRUE. Si **true**, vous trouverez les fichiers d’instantanés dans le dossier par défaut. Si **false**, fichiers d’instantanés ont été stockés dans l’emplacement secondaire spécifié par *alternate_snapshot_folder*. Les emplacements de remplacement peuvent se trouver sur un autre serveur, un lecteur réseau ou un support amovible (tel qu'un CD-ROM ou des disques amovibles). Vous pouvez également enregistrer les fichiers d'instantané sur un site FTP, pour qu'ils soient récupérés ultérieurement par l'Abonné. Notez que ce paramètre peut avoir la valeur true et néanmoins avoir un emplacement le **@alt_snapshot_folder** paramètre. Cette combinaison indique que les fichiers d'instantané sont stockés dans les emplacements par défaut et secondaires.  
  
 [  **@alt_snapshot_folder=** ] **'**_alternate_snapshot_folder_**'**  
 Indique l'emplacement du dossier de remplacement pour l'instantané. *alternate_snapshot_folder* est **nvarchar (255)** avec NULL comme valeur par défaut.  
  
 [  **@pre_snapshot_script=** ] **'**_pre_snapshot_script_**'**  
 Spécifie un pointeur vers un **.sql** emplacement du fichier. *pre_snapshot_script* est **nvarchar (255),** avec NULL comme valeur par défaut. L'Agent de distribution exécute le script de pré-instantané avant l'exécution des scripts d'objet répliqué, lors de l'application d'un instantané sur un Abonné. Le script est exécuté dans le contexte de sécurité utilisé par l'Agent de distribution lors de sa connexion à la base de données d'abonnement.  
  
 [  **@post_snapshot_script=** ] **'**_post_snapshot_script_**'**  
 Spécifie un pointeur vers un **.sql** emplacement du fichier. *post_snapshot_script* est **nvarchar (255)**, avec NULL comme valeur par défaut. L'Agent de distribution exécute le script de post-instantané après que tous les autres scripts et données d'objet répliqué ont été appliqués lors d'une synchronisation initiale. Le script est exécuté dans le contexte de sécurité utilisé par l'Agent de distribution lors de sa connexion à la base de données d'abonnement.  
  
 [  **@compress_snapshot=** ] **'**_compress_snapshot_**'**  
 Spécifie que l’instantané qui est écrite dans le **@alt_snapshot_folder** emplacement consiste à être compressées dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] format CAB. *compress_snapshot* est **nvarchar (5)**, avec FALSE comme valeur par défaut. **false** indique que l’instantané ne sera pas compressé ; **true** Spécifie que l’instantané sera compressé. Les fichiers d'instantané de plus de 2 Go (gigaoctets) ne peuvent pas être compressés. Les fichiers d'instantané compressés sont décompressés là où s'exécute l'Agent de distribution ; les abonnements par extraction de données (pull) sont en général utilisés avec des instantanés compressés et les fichiers sont décompressés sur l'Abonné. L'instantané se trouvant dans le dossier par défaut ne peut pas être compressé.  
  
 [  **@ftp_address =** ] **'**_ftp_address_**'**  
 Adresse réseau du service FTP du serveur de distribution. *ftp_address* est **sysname**, avec NULL comme valeur par défaut. Indique l'emplacement à partir duquel l'Agent de distribution ou l'Agent de fusion d'un abonné peut extraire les fichiers d'instantané de la publication. Dans la mesure où cette propriété est stockée pour chaque publication, chaque publication peut avoir un autre *ftp_address*. La publication doit prendre en charge la propagation des instantanés à l'aide du protocole FTP.  
  
 [  **@ftp_port=** ] *ftp_port*  
 Numéro de port du service FTP du serveur de distribution. *ftp_port* est **int**, avec la valeur par défaut est 21. Spécifie l'emplacement à partir duquel l'Agent de distribution ou l'Agent de fusion d'un Abonné peut extraire les fichiers d'instantané de la publication. Dans la mesure où cette propriété est stockée pour chaque publication, chaque publication peut avoir ses propres *ftp_port*.  
  
 [  **@ftp_subdirectory =** ] **'**_ftp_subdirectory_**'**  
 Indique l'emplacement à partir duquel l'Agent de distribution ou de fusion d'un abonné peut extraire les fichiers d'instantané si la publication prend en charge la propagation d'instantanés via FTP. *ftp_subdirectory* est **nvarchar (255)**, avec NULL comme valeur par défaut. Dans la mesure où cette propriété est stockée pour chaque publication, chaque publication peut avoir ses propres *ftp_subdirctory* ou choisir de n’avoir aucun sous-répertoire avec une valeur NULL.  
  
 [  **@ftp_login =** ] **'**_ftp_login_**'**  
 Le nom d’utilisateur est utilisé pour se connecter au service FTP. *ftp_login* est **sysname**, avec ANONYMOUS comme valeur par défaut.  
  
 [  **@ftp_password =** ] **'**_ftp_password_**'**  
 Mot de passe de l'utilisateur utilisé pour la connexion au service FTP. *ftp_password* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@allow_dts =** ] **'**_allow_dts_**'**  
 Indique que la publication autorise les transformations de données. Vous pouvez spécifier un package DTS lors de la création d'un abonnement. *allow_transformable_subscriptions* est **nvarchar (5)** avec une valeur FALSE par défaut, qui n’autorise pas les transformations DTS. Lorsque *allow_dts* a la valeur true, *sync_method* doit être définie avec la valeur **caractère** ou **concurrent_c**.  
  
 **true** est *ne pas pris en charge pour les serveurs de publication Oracle*.  
  
 [  **@allow_subscription_copy =** ] **'**_allow_subscription_copy_**'**  
 Active ou désactive la possibilité de copier les bases de données d'abonnement qui sont abonnées à la publication. *allow_subscription_copy* est**nvarchar (5)**, avec FALSE comme valeur par défaut.  
  
 [  **@conflict_policy =** ] **'**_conflict_policy_**'**  
 Spécifie la stratégie de résolution de conflits à suivre lorsque l'option d'abonné avec mise à jour en attente est utilisée. *conflict_policy* est **nvarchar (100)** avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**wins de pub**|Le serveur de publication remporte le conflit.|  
|**sub reinit**|Réinitialisez l'abonnement.|  
|**Sub wins**|L'Abonné remporte le conflit.|  
|NULL (par défaut)|Si NULL et la publication est une publication d’instantané, la stratégie par défaut devienne **sub reinit**. Si la valeur NULL et la publication n’est pas une publication d’instantané, la valeur par défaut devient **wins de pub**.|  
  
 *Non pris en charge pour les serveurs de publication Oracle*.  
  
 [  **@centralized_conflicts =** ] **'**_centralized_conflicts_**'**  
 Spécifie si les enregistrements en conflit sont stockés sur le serveur de publication. *centralized_conflicts* est **nvarchar (5)**, avec TRUE comme valeur par défaut. Si **true**, les enregistrements en conflit sont stockés sur le serveur de publication. Si **false**, les enregistrements en conflit sont stockés sur le serveur de publication et sur l’abonné qui a provoqué le conflit. *Non pris en charge pour les serveurs de publication Oracle*.  
  
 [  **@conflict_retention =** ] *conflict_retention*  
 Spécifie la durée de rétention des conflits en jours. Il s'agit de la période pendant laquelle les métadonnées en conflit sont stockées pour la réplication transactionnelle d'égal à égal et les abonnements mis à jour en attente. *conflict_retention* est **int**, avec une valeur par défaut de 14. *Non pris en charge pour les serveurs de publication Oracle*.  
  
 [  **@queue_type =** ] **'**_queue_type_**'**  
 Spécifie le type de file d'attente utilisé. *queue_type* est **nvarchar (10)**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**sql**|Utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour stocker les transactions.|  
|NULL (par défaut)|Valeur par défaut est **sql**, qui spécifie l’utilisation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour stocker les transactions.|  
  
> [!NOTE]  
>  La prise en charge de l'utilisation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing a été arrêtée. La valeur **msmq** entraîne un avertissement et la réplication définira automatiquement la valeur sur **sql**.  
  
 *Non pris en charge pour les serveurs de publication Oracle*.  
  
 [  **@add_to_active_directory =** ] **'**_ajouter_*\_*_to_active_directory_ **'**  
 Ce paramètre est déconseillé et il n'est pris en charge que pour la compatibilité descendante des scripts. Vous ne pouvez plus ajouter d'informations de publication à [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory.  
  
 [  **@logreader_job_name =** ] **'**_logreader_agent_name_**'**  
 Nom d'un travail de l'agent existant. *logreader_agent_name* est **sysname**, avec NULL comme valeur par défaut. Ce paramètre n'est spécifié que lorsque l'Agent de lecture du journal doit utiliser un travail existant et non pas un travail nouvellement créé.  
  
 [  **@qreader_job_name =** ] **'**_queue_reader_agent_name_**'**  
 Nom d'un travail de l'agent existant. *queue_reader_agent_name* est **sysname**, avec NULL comme valeur par défaut. Ce paramètre n'est spécifié que lorsque l'Agent de lecture de file d'attente doit utiliser un travail existant et non pas un travail nouvellement créé.  
  
 [  **@publisher =** ] **'**_publisher_**'**  
 Spécifie un non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé lors de l’ajout d’une publication à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
 [  **@allow_initialize_from_backup =** ] **'**_allow_initialize_from_backup_**'**  
 Indique si les Abonnés peuvent initialiser un abonnement à cette publication à partir d'une sauvegarde plutôt qu'à partir de son instantané initial. *allow_initialize_from_backup* est **nvarchar (5)**, et peut prendre l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**true**|Autorise l'initialisation à partir d'une sauvegarde.|  
|**false**|Interdit l'initialisation à partir d'une sauvegarde.|  
|NULL (par défaut)|Valeur par défaut est **true** pour une publication dans une topologie de réplication d’égal à égal et **false** pour toutes les autres publications.|  
  
 Pour plus d’informations, consultez [Initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
> [!WARNING]  
>  Afin d'éviter les données d'abonnés manquantes, lorsque vous utilisez **sp_addpublication** avec `@allow_initialize_from_backup = N'true'`, utilisez toujours `@immediate_sync = N'true'`.  
  
 [  **@replicate_ddl =** ] *replicate_ddl*  
 Précise si la réplication de schéma est prise en charge pour la publication. *replicate_ddl* est **int**, avec une valeur par défaut **1** pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] éditeurs et **0** pour non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication. **1** indique que les instructions data definition language (DDL) exécutées sur le serveur de publication sont répliquées, et **0** indique que les instructions DDL ne sont pas répliquées. *La réplication du schéma n’est pas pris en charge pour les serveurs de publication Oracle.* Pour plus d’informations, consultez [Modifier le schéma dans les bases de données de publication](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
 Le *@replicate_ddl* paramètre est honoré lorsqu’une instruction DDL ajoute une colonne. Le *@replicate_ddl* paramètre est ignoré quand une instruction DDL modifie ou supprime une colonne pour les raisons suivantes.  
  
-   Lorsqu’une colonne est supprimée, sysarticlecolumns doit être mis à jour pour empêcher les nouvelles instructions DML d’inclure la colonne supprimée, ce qui provoquerait l’échec de l’agent de la distribution. Le *@replicate_ddl* paramètre est ignoré, car la réplication doit toujours répliquer la modification de schéma.  
  
-   Lorsqu'une colonne est modifiée, le type de données source ou la possibilité d'une valeur NULL peuvent avoir changé et les instructions DML peuvent contenir une valeur non compatible avec la table sur l'abonné. Ces instructions DML peuvent entraîner l'échec de l'agent de distribution. Le *@replicate_ddl* paramètre est ignoré, car la réplication doit toujours répliquer la modification de schéma.  
  
-   Lorsqu’une instruction DDL ajoute une nouvelle colonne, sysarticlecolumns n’inclut pas la nouvelle colonne. Les instructions DML n'essayeront pas de répliquer les données pour la nouvelle colonne. Le paramètre est respecté parce que la réplication ou la réplication DDL est acceptable.  
  
 [  **@enabled_for_p2p =** ] **'**_enabled_for_p2p_**'**  
 Autorise l'utilisation de la publication dans une topologie de réplication d'égal à égal. *enabled_for_p2p* est **nvarchar (5)**, avec FALSE comme valeur par défaut. **true** indique que la publication prend en charge la réplication d’égal à égal. Lors de la définition *enabled_for_p2p* à **true**, les restrictions suivantes s’appliquent :  
  
-   *allow_anonymous* doit être **false**.  
  
-   *allow_dts* doit être **false**.  
  
-   *allow_initialize_from_backup* doit être **true**.  
  
-   *allow_queued_tran* doit être **false**.  
  
-   *allow_sync_tran* doit être **false**.  
  
-   *conflict_policy* doit être **false**.  
  
-   *independent_agent* doit être **true**.  
  
-   *repl_freq* doit être **continue**.  
  
-   *replicate_ddl* doit être **1**.  
  
 Pour plus d'informations, consultez [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 [  **@publish_local_changes_only =** ] **'**_publish_local_changes_only_**'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@enabled_for_het_sub=** ] **'**_enabled_for_het_sub_**'**  
 Permet à la publication de prendre en charge des Abonnés non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *enabled_for_het_sub* est **nvarchar (5)** valeur par défaut est false. La valeur **true** signifie que la publication prend en charge non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés. Lorsque *enabled_for_het_sub* est **true**, les restrictions suivantes s’appliquent :  
  
-   *allow_initialize_from_backup* doit être **false**.  
  
-   *allow_push* doit être **true**.  
  
-   *allow_queued_tran* doit être **false**.  
  
-   *allow_subscription_copy* doit être **false**.  
  
-   *allow_sync_tran* doit être **false**.  
  
-   *proc_sync_autogén* doit être **false**.  
  
-   *conflict_policy* doit être NULL.  
  
-   *enabled_for_internet* doit être **false**.  
  
-   *enabled_for_p2p* doit être **false**.  
  
-   *ftp_address* doit être NULL.  
  
-   *ftp_subdirectory* doit être NULL.  
  
-   *ftp_password* doit être NULL.  
  
-   *pre_snapshot_script* doit être NULL.  
  
-   *post_snapshot_script* doit être NULL.  
  
-   *replicate_ddl* doit être 0.  
  
-   *qreader_job_name* doit être NULL.  
  
-   *queue_type* doit être NULL.  
  
-   *sync_method* ne peut pas être **natif** ou **simultanées**.  
  
 Pour plus d’informations, consultez [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 [  **@p2p_conflictdetection=** ] **'**_p2p_conflictdetection_**'**  
 Autorise l'Agent de distribution à détecter les conflits si la publication est activée pour la réplication d'égal à égal. *p2p_conflictdetection* est **nvarchar (5)** avec une valeur par défaut true. Pour plus d’informations, voir [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
 [  **@p2p_originator_id=** ] *p2p_originator_id*  
 Spécifie un ID pour un nœud dans une topologie d'égal à égal. *p2p_originator_id* est **int**, avec NULL comme valeur par défaut. Cet ID est utilisé pour la détection de conflit si *p2p_conflictdetection* est définie sur TRUE. Spécifiez un ID positif différent de zéro qui n’a jamais été utilisé dans la topologie. Pour obtenir la liste d’ID qui ont déjà été utilisés, exécutez [sp_help_peerconflictdetection](../../relational-databases/system-stored-procedures/sp-help-peerconflictdetection-transact-sql.md).  
  
 [  **@p2p_continue_onconflict=** ] **'**_p2p_continue_onconflict_**'**  
 Détermine si l'Agent de distribution continue à traiter les modifications lorsqu'un conflit est détecté. *p2p_continue_onconflict* est **nvarchar (5)** valeur par défaut est false.  
  
> [!CAUTION]  
>  Nous vous recommandons de conserver la valeur par défaut FALSE. Lorsque cette option a la valeur TRUE, l'Agent de distribution tente de converger les données dans la topologie en appliquant la ligne en conflit du nœud doté de l'ID d'appelant le plus élevé. Cette méthode ne garantit pas la convergence. Vous devez vous assurer que la topologie est cohérente après la détection d'un conflit. Pour plus d'informations, consultez « Gestion des conflits » dans [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
  
 [  **@allow_partition_switch=** ] **'**_allow_partition_switch_**'**  
 Spécifie si ALTER TABLE... Instructions SWITCH peuvent être exécutées sur la base de données publiée. *allow_partition_switch* est **nvarchar (5)** valeur par défaut est false. Pour plus d’informations, consultez [Répliquer des tables et des index partitionnés](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md).  
  
 [  **@replicate_partition_switch=** ] **'**_replicate_partition_switch_**'**  
 Spécifie si ALTER TABLE... Instructions SWITCH qui sont exécutées sur la base de données publiée doivent être répliquées aux abonnés. *replicate_partition_switch* est **nvarchar (5)** valeur par défaut est false. Cette option est valide uniquement si *allow_partition_switch* est définie sur TRUE.  

## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addpublication** est utilisé dans la réplication d’instantané ou transactionnelle.  
  
 S’il existe plusieurs publications qui permettent de publier le même objet de base de données, seules les publications avec un *replicate_ddl* valeur **1** répliquera ALTER TABLE, ALTER VIEW, ALTER PROCEDURE, ALTER FUNCTION, et Instructions ALTER TRIGGER DDL. Cependant, une instruction ALTER TABLE DROP COLUMN DDL sera répliquée par toutes les publications publiant la colonne supprimée.  
  
 Avec la réplication DDL est activée (*replicate_ddl* = **1**) pour une publication, afin de rendre la DDL non répliquées des modifications à la publication, [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) doit tout d’abord être exécutée pour définir *replicate_ddl* à **0**. Une fois que les instructions DDL non répliquées ont été émises, [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) peut être exécuté à nouveau pour activer la réplication DDL.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-transa_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addpublication**. Les connexions d'authentification Windows doivent disposer d'un compte d'utilisateur dans la base de données, représentant leur compte d'utilisateur Windows. Un compte d'utilisateur représentant un groupe Windows n'est pas suffisant.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
