---
title: Agent de lecture de la file d’attente de réplication | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7ba560e46aaebc1aa5bc6901a3c0067fae91bdb2
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68085940"
---
# <a name="replication-queue-reader-agent"></a>Agent de lecture de la file d'attente de réplication
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L’Agent de lecture de la file d’attente de réplication est un fichier exécutable qui lit les messages stockés dans une file d’attente [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou une file d’attente de messages [!INCLUDE[msCoName](../../../includes/msconame-md.md)], puis qui applique ces messages au serveur de publication. L'Agent de lecture de la file d'attente est utilisé avec les publications transactionnelles et les publications d'instantané qui autorisent la mise à jour en attente.  
  
> [!NOTE]  
>  Les paramètres peuvent être spécifiés dans n'importe quel ordre. Lorsque les paramètres optionnels ne sont pas spécifiés, les valeurs prédéfinies basées sur le profil d'agent par défaut sont utilisées.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="arguments"></a>Arguments  
 **-?**  
 Affiche des informations sur l’utilisation.  
  
 **-Continuous**  
 Spécifie si l'agent tente de traiter les transactions en attente de manière continue. S'il est spécifié, l'agent poursuit l'exécution même si aucune transaction n'est en attente au niveau des Abonnés.  
  
 **-DefinitionFile** _def_path_and_file_name_  
 Chemin d'accès du fichier de définition d'agent. Un fichier de définition d'agent contient des arguments de ligne de commande pour l'agent. Le contenu du fichier est analysé en tant que fichier exécutable. Utilisez des guillemets doubles (") pour spécifier des valeurs d'argument qui contiennent des caractères arbitraires.  
  
 **-Distributor** _server_name_[ **\\** _instance_name_]  
 Nom du serveur de distribution. Spécifiez *server_name* pour l'instance par défaut de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur ce serveur. Spécifiez *server_name*\\*instance_name* pour une instance nommée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur ce serveur. S'il n'est pas spécifié, le nom a comme valeur par défaut le nom de l'instance par défaut de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur l'ordinateur local.  
  
 **-DistributionDB** _distribution_database_  
 Nom de la base de données de distribution.  
  
 **-DistributorLogin** _distributor_login_  
 Nom de connexion du serveur de distribution.  
  
 **-DistributorPassword** _distributor_password_  
 Mot de passe du serveur de distribution.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Spécifie le mode de sécurité du serveur de distribution. La valeur **0** indique le mode d'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (par défaut), tandis que la valeur **1** indique le mode d'authentification Windows.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Niveau du chiffrement SSL (Secure Sockets Layer) utilisé par l'Agent de lecture de la file d'attente lors de l'établissement de connexions.  
  
|Valeur EncryptionLevel|Description|  
|---------------------------|-----------------|  
|**0**|Spécifie que le chiffrement SSL n'est pas utilisé.|  
|**1**|Spécifie que le chiffrement SSL est utilisé, mais que l'agent ne vérifie pas si le certificat de serveur SSL est signé par un émetteur de confiance.|  
|**2**|Spécifie que le chiffrement SSL est utilisé et que le certificat est vérifié.|  

 > [!NOTE]  
 >  Un certificat SSL valide est défini avec le nom de domaine complet de l’instance SQL Server. Pour que l’agent puisse se connecter lorsque vous définissez EncryptionLevel sur 2, créez un alias sur l’instance locale de SQL Server. Le paramètre « Nom de l’alias » doit correspondre au nom du serveur, et le paramètre « Serveur » doit être défini sur le nom complet de l’instance SQL Server.
  
 Pour plus d’informations, consultez [Afficher et modifier les paramètres de sécurité de la réplication](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]  
 Spécifie la quantité d'informations d'historique journalisées pendant une opération de lecture de la file d'attente. Vous pouvez réduire l'effet de la journalisation d'historique sur les performances en sélectionnant **1**.  
  
|Valeur HistoryVerboseLevel|Description|  
|-------------------------------|-----------------|  
|**0**|Aucune journalisation d'historique (non recommandé).|  
|**1**|Par défaut. Met toujours à jour un message d'historique précédent du même état (démarrage, progression, succès, et ainsi de suite). Si aucun enregistrement précédent du même état n'existe, insère un nouvel enregistrement.|  
|**2**|Insère de nouveaux enregistrements d'historique, y compris des messages inactifs ou des messages de travail de longue durée.|  
|**3**|Insère de nouveaux enregistrements d'historique incluant des détails supplémentaires qui peuvent s'avérer utiles pour le dépannage.|  
  
 **-LoginTimeOut** _login_time_out_seconds_  
 Nombre de secondes avant l'expiration de la connexion. La valeur par défaut est 15 secondes.  
  
 **-Output** _output_path_and_file_name_  
 Chemin d'accès du fichier de sortie de l'agent. Si le nom du fichier n'est pas spécifié, la sortie est envoyée à la console. Si le nom de fichier spécifié existe, la sortie est ajoutée au fichier.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Spécifie si la sortie doit être en clair. Si le niveau de détail est **0**, seuls les messages d'erreur sont imprimés. Si le niveau de détail est **1**, tous les messages du rapport de progression sont imprimés. Si le niveau de détail est **2** (valeur par défaut), tous les messages d'erreur et tous les messages du rapport de progression sont imprimés, ce qui peut s'avérer utile lors du débogage.  
  
 **-PollingInterval** _polling_interval_  
 Ne s'applique qu'à la mise à jour d'abonnements qui utilisent des files d'attente basées sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Spécifie la fréquence, en secondes, à laquelle la file d'attente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est interrogée au sujet des transactions de file d'attente en cours. La valeur peut être comprise entre 0 et 240 secondes. La valeur par défaut est 5 secondes.  
  
 **-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]  
 Spécifie l'instance du partenaire de basculement de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participant à une session de mise en miroir de bases de données avec la base de données de publication. Pour plus d’informations, consultez [Mise en miroir de bases de données et réplication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-ProfileName** _agent_profile_name_  
 Nom d'un profil d'agent utilisé pour fournir un jeu de valeurs par défaut à l'agent. Pour plus d’informations, consultez [Profils de l’Agent de réplication](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-QueryTimeOut** _query_time_out_seconds_  
 Nombre de secondes avant l'expiration de la requête. La valeur par défaut est 1800 secondes.  
  
 **-ResolverState** [ **1**| **2**| **3**]  
 Spécifie comment les conflits de mise à jour en attente sont résolus. La valeur **1** indique que le serveur de publication remporte le conflit. Dans ce cas, la transaction en file d'attente actuellement en conflit est restaurée sur le serveur de publication et sur l'Abonné de mise à jour d'origine ; le traitement des transactions en file d'attente suivantes continue. La valeur **2** indique que l'Abonné remporte le conflit, et la transaction en file d'attente remplace les valeurs sur le serveur de publication. La valeur **3** indique que tout conflit provoquera la réinitialisation de l'Abonné ; le serveur de publication remporte le conflit, le traitement des transactions en file d'attente suivantes est terminé, et l'abonnement est réinitialisé. Le paramètre par défaut est **1** pour les publications transactionnelles et **3** pour les publications d'instantané.  
  
## <a name="remarks"></a>Notes  
 Pour démarrer l'Agent de lecture de la file d'attente, exécutez **qrdrsvc.exe** à l'invite de commandes. Pour plus d'informations, consultez [Concepts des exécutables de l'agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de l’Agent de réplication](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
