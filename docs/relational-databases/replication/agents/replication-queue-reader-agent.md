---
title: "Agent de lecture de la file d&#39;attente de r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agents [réplication SQL Server], Agent de lecture de la file d’attente"
  - "invite de commandes [réplication SQL Server]"
  - "Agent de lecture de la file d’attente, référence des paramètres"
  - "Agent de lecture de la file d’attente, exécutables"
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Agent de lecture de la file d&#39;attente de r&#233;plication
  L’Agent de lecture de file d’attente de réplication est un exécutable qui lit les messages stockés dans un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] file d’attente ou un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] file d’attente, puis applique ces messages au serveur de publication. L'Agent de lecture de la file d'attente est utilisé avec les publications transactionnelles et les publications d'instantané qui autorisent la mise à jour en attente.  
  
> [!NOTE]  
>  Les paramètres peuvent être spécifiés dans n'importe quel ordre. Lorsque les paramètres optionnels ne sont pas spécifiés, les valeurs prédéfinies basées sur le profil d'agent par défaut sont utilisées.  
  
## Syntaxe  
  
```  
  
qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFile definition_file]  
[-Distributor server_name[\instance_name]]  
[-DistributionDB distribution_database]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOut login_time_out_seconds]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingInterval polling_interval]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-ProfileName agent_profile_name]  
[-QueryTimeOut query_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## Arguments  
 **-?**  
 Affiche les informations d'utilisation.  
  
 **-Continuous**  
 Spécifie si l'agent tente de traiter les transactions en attente de manière continue. S'il est spécifié, l'agent poursuit l'exécution même si aucune transaction n'est en attente au niveau des Abonnés.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Chemin d'accès du fichier de définition d'agent. Un fichier de définition d'agent contient des arguments de ligne de commande pour l'agent. Le contenu du fichier est analysé en tant que fichier exécutable. Utilisez des guillemets doubles (") pour spécifier des valeurs d'argument qui contiennent des caractères arbitraires.  
  
 **-Le serveur de distribution** *nom_serveur*[**\\***instance_name*]  
 Nom du serveur de distribution. Spécifiez *nom_serveur* pour l’instance par défaut de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur ce serveur. Spécifiez *nom_serveur*\\*instance_name* pour une instance nommée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur ce serveur. S'il n'est pas spécifié, le nom a comme valeur par défaut le nom de l'instance par défaut de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur l'ordinateur local.  
  
 **-Bd_de_distribution** *distribution_database*  
 Nom de la base de données de distribution.  
  
 **-DistributorLogin** *distributor_login*  
 Nom de connexion du serveur de distribution.  
  
 **-DistributorPassword** *distributor_password*  
 Mot de passe du serveur de distribution.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Spécifie le mode de sécurité du serveur de distribution. Une valeur de **0** indique [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Mode d’authentification (par défaut) et la valeur **1** indique le Mode d’authentification Windows.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Niveau du chiffrement SSL (Secure Sockets Layer) utilisé par l'Agent de lecture de la file d'attente lors de l'établissement de connexions.  
  
|Valeur EncryptionLevel|Description|  
|---------------------------|-----------------|  
|**0**|Spécifie que le chiffrement SSL n'est pas utilisé.|  
|**1**|Spécifie que le chiffrement SSL est utilisé, mais que l'agent ne vérifie pas si le certificat de serveur SSL est signé par un émetteur de confiance.|  
|**2**|Spécifie que le chiffrement SSL est utilisé et que le certificat est vérifié.|  
  
 Pour plus d’informations, consultez [vue d’ensemble de la sécurité & #40 ; Réplication & #41 ;](../../../relational-databases/replication/security/security-overview-replication.md).  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]  
 Spécifie la quantité d'informations d'historique journalisées pendant une opération de lecture de la file d'attente. Vous pouvez réduire l'effet de la journalisation d'historique sur les performances en sélectionnant **1**.  
  
|Valeur HistoryVerboseLevel|Description|  
|-------------------------------|-----------------|  
|**0**|Aucune journalisation d'historique (non recommandé).|  
|**1**|Valeur par défaut. Met toujours à jour un message d'historique précédent du même état (démarrage, progression, succès, et ainsi de suite). Si aucun enregistrement précédent du même état n'existe, insère un nouvel enregistrement.|  
|**2**|Insère de nouveaux enregistrements d'historique, y compris des messages inactifs ou des messages de travail de longue durée.|  
|**3**|Insère de nouveaux enregistrements d'historique incluant des détails supplémentaires qui peuvent s'avérer utiles pour le dépannage.|  
  
 **-LoginTimeOut** *délai_de_connexion_en_secondes*  
 Nombre de secondes avant l'expiration de la connexion. La valeur par défaut est de 15 secondes.  
  
 **-Output** *output_path_and_file_name*  
 Chemin d'accès du fichier de sortie de l'agent. Si le nom du fichier n'est pas spécifié, la sortie est envoyée à la console. Si le nom de fichier spécifié existe, la sortie est ajoutée au fichier.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Spécifie si la sortie doit être en clair. Si le niveau de détail est **0**, seuls les messages d'erreur sont imprimés. Si le niveau de détail est **1**, tous les messages du rapport de progression sont imprimés. Si le niveau de détail est **2** (par défaut), tous les messages d’erreur et les messages de rapport de progression sont imprimés, ce qui est utile pour le débogage.  
  
 **-PollingInterval** *polling_interval*  
 Ne s'applique qu'à la mise à jour d'abonnements qui utilisent des files d'attente basées sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Spécifie la fréquence, en secondes, à laquelle la file d'attente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est interrogée au sujet des transactions de file d'attente en cours. La valeur peut être comprise entre 0 et 240 secondes. La valeur par défaut est 5 secondes.  
  
 **-PublisherFailoverPartner** *nom_serveur*[**\\***instance_name*]  
 Spécifie l'instance du partenaire de basculement de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participant à une session de mise en miroir de bases de données avec la base de données de publication. Pour plus d’informations, consultez [mise en miroir de base de données et réplication & #40 ; SQL Server & #41 ;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-ProfileName** *agent_profile_name*  
 Nom d'un profil d'agent utilisé pour fournir un jeu de valeurs par défaut à l'agent. Pour plus d’informations, consultez [profils d’Agent de réplication](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-QueryTimeOut** *délai_de_requête_en_secondes*  
 Nombre de secondes avant l'expiration de la requête. La valeur par défaut est 1800 secondes.  
  
 **-ResolverState** [ **1**| **2**| **3**]  
 Spécifie comment les conflits de mise à jour en attente sont résolus. Valeur **1** indique que le serveur de publication gagne le conflit et actuel en conflit en file d’attente de transaction sera restaurée sur le serveur de publication et l’abonné de mise à jour ; le traitement des transactions en file d’attente suivantes continue. Une valeur de **2** indique que l’abonné gagne le conflit, et la transaction en file d’attente se substituent aux valeurs sur le serveur de publication. Une valeur de **3** indique que tout conflit provoquera abonné ; l’éditeur gagne le conflit, traitement des transactions en file d’attente suivantes va être interrompu et l’abonnement est réinitialisé. Le paramètre par défaut est **1** pour les publications transactionnelles et **3** les publications d’instantané.  
  
## Notes  
 Pour démarrer l’Agent de lecture de file d’attente, exécutez **qrdrsvc.exe** à partir de l’invite de commandes. Pour plus d'informations, consultez [Concepts des exécutables de l'agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## Voir aussi  
 [Administration de l'Agent de réplication](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  