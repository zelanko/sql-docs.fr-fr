---
title: Agent d’instantané de réplication | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 12050c8d2e5d440ef8f4d7f6584f6c08c210f4f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250589"
---
# <a name="replication-snapshot-agent"></a>Agent d'instantané de réplication
  L'Agent d'instantané de réplication est un fichier exécutable qui prépare les fichiers d'instantané contenant les schémas ainsi que les données des tables et des objets de base de données publiés, stocke les fichiers dans le dossier d'instantanés, et enregistre les travaux de synchronisation dans la base de données de distribution.  
  
> [!NOTE]  
>  Les paramètres peuvent être spécifiés dans n'importe quel ordre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      snapshot [ -?]   
-Publisherserver_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSizebcp_batch_size]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostNamedynamic_filter_host_name]  
[-DynamicFilterLogindynamic_filter_login]  
[-DynamicSnapshotLocationdynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiterfield_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocksnumber_of_blocks ]  
[-HRBcpBlockSizeblock_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageIntervalkeep_alive_interval]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreadsnumber_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSizepacket_size]
[-PrefetchTables [0|1] ]  
[-ProfileNameprofile_name]  
[-PublisherDBpublisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOutquery_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiterrow_delimiter]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-UsePerArticleContentsViewuse_per_article_contents_view]  
```  
  
## <a name="arguments"></a>Arguments  
 **-?**  
 Imprime tous les paramètres disponibles.  
  
 **-** _SERVER_NAME_du serveur**\\**de publication [_instance_name_]  
 Nom du serveur de publication. Spécifiez server_name pour l'instance par défaut de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur ce serveur. Spécifiez _SERVER_NAME_**\\**_instance_name_ pour une instance nommée [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de sur ce serveur.  
  
 **-Publication de publication** __  
 Nom de la publication. Ce paramètre est uniquement valide si la publication est configurée de telle sorte qu'un instantané soit toujours disponible pour les nouveaux abonnements ou les abonnements réinitialisés.  
  
 **-70Subscribers**  
 Doit être utilisé si des Abonnés exécutent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version 7.0.  
  
 **-** *Taille* de *lot* \_ BcpBatchSize _BCP_ \_  
 Nombre de lignes à envoyer dans une opération de copie en bloc. Lorsque vous effectuez une opération **bcp in** , la taille du lot correspond au nombre de lignes à envoyer au serveur en une transaction, mais aussi au nombre de lignes à envoyer avant que l’Agent de distribution ne journalise un message de progression **bcp** . Lorsque vous effectuez une opération **bcp out** , une taille de lot fixe de 1000 est utilisée. La valeur 0 indique qu'aucune journalisation de message n'est autorisée.  
  
 **-DefinitionFile** _def_path_and_file_name_  
 Chemin d'accès du fichier de définition d'agent. Un fichier de définition d'agent contient des arguments de ligne de commande pour l'agent. Le contenu du fichier est analysé en tant que fichier exécutable. Utilisez des guillemets doubles (") pour spécifier des valeurs d'argument qui contiennent des caractères arbitraires.  
  
 **-** _SERVER_NAME_du serveur**\\**de distribution [_instance_name_]  
 Nom du serveur de distribution. Spécifiez *server_name* pour l'instance par défaut de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur ce serveur. Spécifiez _SERVER_NAME_**\\**_instance_name_ pour une instance nommée [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de sur ce serveur.  
  
 **-DistributorDeadlockPriority** [**-1**|**0**|**1**]  
 Priorité de la connexion de l'Agent d'instantané au serveur de distribution lorsqu'un blocage se produit. Ce paramètre est spécifié pour résoudre les blocages qui peuvent se produire entre l'Agent d'instantané et les applications utilisateur lors de la génération d'instantané.  
  
|Valeur DistributorDeadlockPriority|Description|  
|---------------------------------------|-----------------|  
|**-1**|Les applications autres que l'Agent d'instantané ont priorité lorsqu'un blocage se produit au niveau du serveur de distribution.|  
|**0** (par défaut)|La priorité n'est pas assignée.|  
|**1**|L'Agent d'instantané a priorité lorsqu'un blocage se produit au niveau du serveur de distribution.|  
  
 **-DistributorLogin** _distributor_login_  
 Nom de connexion utilisé pour la connexion au serveur de distribution avec l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 **-DistributorPassword** _distributor_password_  
 Mot de passe utilisé pour la connexion au serveur de distribution avec l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . .  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Spécifie le mode de sécurité du serveur de distribution. La valeur **0** indique [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le mode d’authentification (valeur par défaut), tandis que la valeur **1** indique le mode d’authentification Windows.  
  
 **-DynamicFilterHostName** _dynamic_filter_host_name_  
 Est utilisé pour définir une valeur pour [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) pour le filtrage quand un instantané dynamique est créé. Par exemple, si la clause de filtre de sous-ensemble `rep_id = HOST_NAME()` est spécifiée pour un article et que vous attribuez à la propriété **DynamicFilterHostName** la valeur « FBJones » avant d'appeler l'Agent de fusion, seules les lignes contenant « FBJones » dans la colonne **rep_id** seront répliquées.  
  
 **-DynamicFilterLogin** _dynamic_filter_login_  
 Est utilisé pour définir une valeur pour [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) pour le filtrage quand un instantané dynamique est créé. Par exemple, si la clause de filtre de sous-ensemble `user_id = SUSER_SNAME()` est spécifiée pour un article et que vous attribuez à la propriété **DynamicFilterLogin** la valeur « rsmith » avant d'appeler la méthode **Run** de l'objet **SQLSnapshot** , seules les lignes contenant « rsmith » dans la colonne **user_id** seront incluses dans l'instantané.  
  
 **-DynamicSnapshotLocation** _dynamic_snapshot_location_  
 Emplacement où l'instantané dynamique doit être généré.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Niveau du chiffrement SSL (Secure Sockets Layer) utilisé par l'Agent d'instantané lors de l'établissement de connexions.  
  
|Valeur EncryptionLevel|Description|  
|---------------------------|-----------------|  
|**0**|Spécifie que le chiffrement SSL n'est pas utilisé.|  
|**1**|Spécifie que le chiffrement SSL est utilisé, mais que l'agent ne vérifie pas si le certificat de serveur SSL est signé par un émetteur de confiance.|  
|**2**|Spécifie que le chiffrement SSL est utilisé et que le certificat est vérifié.|  

 > [!NOTE]  
 >  Un certificat SSL valide est défini avec le nom de domaine complet de l’instance SQL Server. Pour que l’agent puisse se connecter lorsque vous définissez EncryptionLevel sur 2, créez un alias sur l’instance locale de SQL Server. Le paramètre « Nom de l’alias » doit correspondre au nom du serveur, et le paramètre « Serveur » doit être défini sur le nom complet de l’instance SQL Server.
  
 Pour plus d’informations, consultez [réplication SQL Server Security](../security/view-and-modify-replication-security-settings.md).  
  
 **-FieldDelimiter** _field_delimiter_  
 Caractère ou séquence de caractères qui marque la fin d'un champ dans le fichier de données de copie en bloc [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . La valeur par défaut est \n\<x$3>\n.  
  
 **-HistoryVerboseLevel** [ **1**| **2**| **3**]  
 Spécifie la quantité d'informations d'historique journalisées pendant une opération d'instantané. Vous pouvez réduire l'effet de la journalisation d'historique sur les performances en sélectionnant **1**.  
  
|Valeur HistoryVerboseLevel|Description|  
|-------------------------------|-----------------|  
|**0**|Les messages de progression sont écrits dans la console ou dans un fichier de sortie. Les enregistrements d'historique ne sont pas journalisés dans la base de données de distribution.|  
|**1**|Met toujours à jour un message d'historique précédent du même état (démarrage, progression, succès, et ainsi de suite). Si aucun enregistrement précédent du même état n'existe, insère un nouvel enregistrement.|  
|**2** (par défaut)|Insère de nouveaux enregistrements d'historique, sauf s'il s'agit d'un enregistrement concernant notamment un message inactif ou un message de travail de longue durée, auquel cas les enregistrements précédents sont mis à jour.|  
|**1,3**|Insère toujours de nouveaux enregistrements, sauf s'il s'agit de messages inactifs.|  
  
 **-HRBcpBlocks** _number_of_blocks_  
 Nombre des blocs de données **bcp** mis en file d'attente entre les threads de lecture/écriture. La valeur par défaut est 50. **HRBcpBlocks** est utilisé uniquement avec les publications Oracle.  
  
> [!NOTE]  
>  Ce paramètre est utilisé pour le réglage des performances de **bcp** pour un serveur de publication Oracle.  
  
 -**HRBcpBlockSize**_block_size_  
 Taille, en kilo-octets (Ko), de chaque bloc de données **bcp** . La valeur par défaut est 64 Ko. **HRBcpBlocks** est utilisé uniquement avec les publications Oracle.  
  
> [!NOTE]  
>  Ce paramètre est utilisé pour le réglage des performances de **bcp** pour un serveur de publication Oracle.  
  
 **-HRBcpDynamicBlocks**  
 Indique si la taille de chaque bloc de données **bcp** peut croître dynamiquement ou non. **HRBcpBlocks** est utilisé uniquement avec les publications Oracle.  
  
> [!NOTE]  
>  Ce paramètre est utilisé pour le réglage des performances de **bcp** pour un serveur de publication Oracle.  
  
 **-KeepAliveMessageInterval** _keep_alive_interval_  
 Durée, en secondes, de l'attente de l'Agent d'instantané avant de journaliser un message d'attente du système principal dans la table [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) . La valeur par défaut est 300 secondes.  
  
 **-LoginTimeOut** _login_time_out_seconds_  
 Nombre de secondes avant l’expiration du délai d’attente de la connexion. La valeur par défaut est **15** secondes.  
  
 **-MaxBcpThreads** _number_of_threads_  
 Spécifie le nombre d'opérations de copie en bloc pouvant être effectuées en parallèle. Le nombre maximal de threads et de connexions ODBC pouvant exister simultanément est, en privilégiant la valeur la plus petite, **MaxBcpThreads** ou le nombre de demandes de copie en bloc qui apparaissent dans la transaction de synchronisation dans la base de données de distribution. **MaxBcpThreads** doit avoir une valeur supérieure à **0** et n’a aucune limite supérieure codée en dur. La valeur par défaut est **1**.  
  
 \-**MaxNetworkOptimization** [ **0**| **1**]  
 Indique si les suppressions non pertinentes sont envoyées à l'Abonné. Les suppressions non pertinentes sont des commandes DELETE qui sont envoyées aux Abonnés pour les lignes qui n'appartiennent pas à la partition de l'Abonné. Les suppressions non pertinentes n'affectent ni l'intégrité ni la convergence des données, mais elles peuvent générer un trafic réseau inutile. La valeur par défaut de **MaxNetworkOptimization** est **0**. Le fait d'attribuer à **MaxNetworkOptimization** la valeur **1** réduit le risque d'obtention de suppressions non pertinentes, minimisant ainsi le trafic réseau et maximisant l'optimisation du réseau. L'attribution de la valeur **1** à ce paramètre peut aussi augmenter le stockage des métadonnées et entraîner une réduction des performances au niveau du serveur de publication si plusieurs niveaux de filtres de jointure et des filtres de sous-ensemble complexes sont présents. Vous devez évaluer avec soin votre topologie de réplication et attribuer uniquement à **MaxNetworkOptimization** la valeur **1** si le trafic réseau des suppressions non pertinentes est trop élevé.  
  
> [!NOTE]
>  L’affectation de la valeur **1** à ce paramètre n’est utile que si l’option d’optimisation de la synchronisation de la **@keep_partition_changes** publication de fusion est définie sur **true** (le paramètre de [sp_addmergepublication &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).  
  
 **-Output** _output_path_and_file_name_  
 Chemin d'accès du fichier de sortie de l'agent. Si le nom du fichier n'est pas spécifié, la sortie est envoyée à la console. Si le nom de fichier spécifié existe, la sortie est ajoutée au fichier.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Spécifie si la sortie doit être en clair.  
  
|Valeur OutputVerboseLevel|Description|  
|------------------------------|-----------------|  
|**0**|Seuls les messages d'erreur sont imprimés.|  
|**1** (par défaut)|Tous les messages du rapport de progression sont imprimés (valeur par défaut).|  
|**2**|Tous les messages d'erreur et tous les messages du rapport de progression sont imprimés, ce qui peut s'avérer utile lors du débogage.|  

 **-PrefetchTables** [ **0**| **1**]  
 Paramètre facultatif qui spécifie si les objets de table sont prérécupérés et mis en cache.  Le comportement par défaut consiste à prérécupérer certaines propriétés de la table à l’aide du composant SMO suivant un calcul interne.  Ce paramètre peut être utile dans les scénarios où l’opération de prérécupération SMO est considérablement plus longue. S’il n’est pas utilisé, cette décision est prise à l’exécution en fonction du pourcentage de tables ajoutées comme articles à la publication.  
  
|Valeur OutputVerboseLevel|Description|  
|------------------------------|-----------------|  
|**0**|L’appel de la méthode de prérécupération de composant SMO est désactivé.|  
|**1**|L’Agent d’instantané appellera la méthode prérécupération pour mettre en cache certaines propriétés de la table à l’aide de SMO.|  
  
 **-Taille paquet** _packet_size_  
 Taille du paquet (en octets) utilisée par l'Agent d'instantané lors de la connexion à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La valeur par défaut est 8 192 octets.  
  
> [!NOTE]  
>  Ne modifiez pas la taille des paquets, sauf si vous êtes certain que cela permettra d'accroître les performances. Pour la plupart des applications, la taille de paquet par défaut représente la meilleure solution.  
  
 **-ProfileName** _profile_name_  
 Spécifie un profil d'agent à utiliser pour les paramètres d'agent. Si **ProfileName** a la valeur NULL, le profil d'agent est désactivé. Si **ProfileName** n'est pas spécifié, le profil par défaut du type d'agent est utilisé. Pour plus d’informations, consultez [Profils de l’Agent de réplication](replication-agent-profiles.md).  
  
 **-PublisherDB** _publisher_database_  
 Nom de la base de données de publication. *Ce paramètre n’est pas pris en charge pour les serveurs de publication Oracle*.  
  
 **-PublisherDeadlockPriority** [**-1**|**0**|**1**]  
 Priorité de la connexion de l'Agent d'instantané au serveur de publication lorsqu'un blocage se produit. Ce paramètre est spécifié pour résoudre les blocages qui peuvent se produire entre l'Agent d'instantané et les applications utilisateur lors de la génération d'instantané.  
  
|Valeur PublisherDeadlockPriority|Description|  
|-------------------------------------|-----------------|  
|**-1**|Les applications autres que l'Agent d'instantané ont priorité lorsqu'un blocage se produit au niveau du serveur de publication.|  
|**0** (par défaut)|La priorité n'est pas assignée.|  
|**1**|L'Agent d'instantané a priorité lorsqu'un blocage se produit au niveau du serveur de publication.|  
  
 **-PublisherFailoverPartner** _SERVER_NAME_[**\\**_instance_name_]  
 Spécifie l'instance du partenaire de basculement de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participant à une session de mise en miroir de bases de données avec la base de données de publication. Pour plus d’informations, consultez [Mise en miroir de bases de données et réplication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** _publisher_login_  
 Nom de connexion utilisé pour la connexion au serveur de publication avec l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 **-PublisherPassword** _publisher_password_  
 Mot de passe utilisé pour la connexion au serveur de publication avec l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . .  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 Spécifie le mode de sécurité du serveur de publication. La valeur **0** indique le mode d'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (par défaut), tandis que la valeur **1** indique le mode d'authentification Windows.  
  
 **-QueryTimeOut** _query_time_out_seconds_  
 Nombre de secondes avant l’expiration de la requête. La valeur par défaut est 1800 secondes.  
  
 **-ReplicationType** [ **1**| **2**]  
 Spécifie le type de la réplication. La valeur **1** indique la réplication transactionnelle, tandis que la valeur **2** indique la réplication de fusion.  
  
 **-RowDelimiter** _row_delimiter_  
 Caractère ou séquence de caractères qui marque la fin d'une ligne dans le fichier de données de copie en bloc [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . La valeur par défaut est \n\<,@g>\n.  
  
 **-StartQueueTimeout** _start_queue_timeout_seconds_  
 Nombre maximal de secondes pendant lesquelles le Agent d’instantané attend lorsque le nombre de processus d’instantanés dynamiques simultanés s’exécute à la limite définie par **@max_concurrent_dynamic_snapshots** la propriété de [Sp_addmergepublication &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Si le nombre maximal de secondes est atteint et que l'Agent d'instantané attend toujours, celui-ci se ferme. La valeur 0 signifie que l'Agent attend indéfiniment, bien qu'il soit possible de l'annuler.  
  
 \-**UsePerArticleContentsView** _use_per_article_contents_view_  
 Ce paramètre est déconseillé et n'est pris en charge que dans un but de compatibilité ascendante.  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]  
>  Si vous avez installé l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour s'exécuter sous un compte système local plutôt que sous un compte d'utilisateur de domaine (option par défaut), le service peut uniquement accéder à l'ordinateur local. Si l'Agent d'instantané qui s'exécute sous l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est configuré pour utiliser le mode d'authentification Windows lorsqu'il se connecte à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'Agent d'instantané échoue. Le paramètre par défaut est l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Pour démarrer l'Agent d'instantané, exécutez **snapshot.exe** à l'invite de commandes. Pour plus d'informations, consultez [Concepts des exécutables de l'agent de réplication](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de l’Agent de réplication](replication-agent-administration.md)  
  
  
