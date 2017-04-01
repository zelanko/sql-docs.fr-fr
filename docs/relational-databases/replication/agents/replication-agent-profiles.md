---
title: "Profils de l&#39;Agent de r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Agent de distribution, profils"
  - "réplication [SQL Server], agents et profils"
  - "profils d'agent de réplication [SQL Server]"
  - "Agent de fusion, profils"
  - "agents [réplication SQL Server], profils"
  - "Agent de lecture de la file d’attente, profils"
  - "profils [SQL Server], agents de réplication"
  - "Agent d’instantané, profils"
  - "Agent de lecture du journal, profils"
ms.assetid: 0e980725-e42f-4283-94cb-d8a6dba5df62
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Profils de l&#39;Agent de r&#233;plication
  Quand la réplication est configurée, un ensemble de profils d'agent est installé sur le serveur de distribution. Un profil d'agent contient un ensemble de paramètres qui sont utilisés chaque fois qu'un agent s'exécute : pendant le processus de démarrage, chaque agent se connecte au service de distribution et interroge les paramètres situés dans son profil. Pour les abonnements de fusion utilisant la synchronisation Web, les profils sont téléchargés et stockés sur l'Abonné. En cas de modification du profil, le profil sur l'Abonné est mis à jour à l'exécution suivante de l'Agent de fusion. Pour plus d'informations sur la synchronisation Web, consultez [Web Synchronization for Merge Replication](../../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 La réplication fournit un profil par défaut pour chaque agent et des profils supplémentaires prédéfinis pour l'Agent de lecture du journal, l'Agent de distribution et l'Agent de fusion. En plus des profils fournis, vous pouvez créer des profils adaptés aux besoins de vos applications. Un profil d'agent permet de modifier aisément les paramètres clés de tous les agents associés à ce profil. Par exemple, si vous disposez de 20 Agents de capture instantanée et que vous devez modifier la valeur du délai de requête (le **- QueryTimeout** paramètre), vous pouvez mettre à jour le profil utilisé par les Agents de capture instantanée et tous les agents de ce type commence à utiliser la nouvelle valeur automatiquement lors de leur prochaine exécution.  
  
 Vous pouvez également disposer de profils différents pour les diverses instances d'un agent. Par exemple, un Agent de fusion qui se connecte à l’éditeur et de distributeur via une connexion à distance peut utiliser un ensemble de paramètres qui sont mieux adaptés à la liaison de communication plus lente à l’aide de la **lente** profil.  
  
> [!NOTE]  
>  Si vous spécifiez une valeur pour un paramètre d'agent sur la ligne de commande, cette valeur supplante la valeur définie pour le même paramètre dans le profil d'agent.  
  
 **Pour utiliser et modifier des profils d'agents**  
  
-   [Work with Replication Agent Profiles](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
## Profils de l'Agent d'instantané  
 Le tableau suivant montre les paramètres définis dans le profil par défaut de l'Agent d'instantané. Pour plus d’informations sur ces paramètres, consultez la page [Agent de capture instantanée de réplication](../../../relational-databases/replication/agents/replication-snapshot-agent.md).  
  
||par défaut|  
|-|-------------|  
|**-BcpBatchSize**|100000|  
|**-HistoryVerboseLevel**|2|  
|**-LoginTimeout**|15|  
|**-QueryTimeout**|1800|  
  
## Profils de l'Agent de lecture du journal  
 Le tableau suivant montre les paramètres définis dans les profils de l'Agent de lecture du journal. Chaque colonne du tableau représente un profil nommé. Pour plus d’informations sur ces paramètres, consultez la page [Agent de lecture du journal de réplication](../../../relational-databases/replication/agents/replication-log-reader-agent.md).  
  
||par défaut|historique commenté|  
|-|-------------|---------------------|  
|**-HistoryVerboseLevel**|1|2|  
|**-LoginTimeout**|15|15|  
|**-LogScanThreshold**|500000|500000|  
|**-PollingInterval**|5|5|  
|**-QueryTimeout**|1800|1800|  
|**-ReadBatchSize**|500|500|  
  
## Profils de l'Agent de distribution  
 Le tableau suivant montre les paramètres définis dans les profils de l'Agent de distribution. Chaque colonne du tableau représente un profil nommé. Pour plus d’informations sur ces paramètres, consultez la page [Agent de Distribution](../../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
||par défaut|historique commenté|Gestionnaire de synchronisation Windows|Continuer avec les erreurs de cohérence des données|Profil de distribution du flux de données OLEDB|  
|-|-------------|---------------------|-------------------------------------|-----------------------------------------|----------------------------------------------|  
|**-BcpBatchSize**|100000|100000|1000|100000|2147473647|  
|**-CommitBatchSize**|100|100|100|100|100|  
|**-CommitBatchThreshold**|1000|1000|1000|1000|1000|  
|**-HistoryVerboseLevel**|1|2|1|1|1|  
|**-KeepAliveMessageInterval**|300|300|300|300|300|  
|**-LoginTimeout**|15|15|15|15|15|  
|**-MaxBcpThreads**|1|1|1|1|1|  
|**-MaxDeliveredTransactions**|0|0|0|0|0|  
|**-OledbStreamThreshold**|NULL|NULL|NULL|NULL|32768|  
|**-PacketSize**|NULL|NULL|NULL|NULL|32768|  
|**-PollingInterval**|5|5|5|5|5|  
|**-QueryTimeout**|1800|1800|1800|1800|1800|  
|**-SkipErrors**|NULL|NULL|NULL|**-SkipErrors** 2601:2627:20598|NULL|  
|**-TransactionsPerHistory**|100|100|100|100|100|  
|**-UseOledbStreaming**|NULL|NULL|NULL|NULL|**-UseOledbStreaming**|  
  
## Profils de l'Agent de fusion  
 Le tableau suivant montre les paramètres définis dans les profils de l'Agent de fusion. Chaque colonne du tableau représente un profil nommé. Pour plus d’informations sur ces paramètres, consultez [l’Agent de réplication de fusion](../../../relational-databases/replication/agents/replication-merge-agent.md).  
  
||par défaut|historique commenté|Gestionnaire de synchronisation Windows|validation du nombre de lignes|validation du nombre de lignes et du total de contrôle|liaison lente|serveur à serveur haut volume|  
|-|-------------|---------------------|-------------------------------------|-------------------------|--------------------------------------|---------------|------------------------------------|  
|**-BcpBatchSize**|100000|100000|1000|100000|100000|100000|100000|  
|**-ChangesPerHistory**|100|50|50|100|100|100|1000|  
|**-DestThreads**|2|1|1|1|1|1|4|  
|**-DownloadGenerationsPerBatch**|50|50|50|50|50|1|500|  
|**-DownloadReadChangesPerBatch**|100|100|100|100|100|100|100|  
|**-DownloadWriteChangesPerBatch**|100|100|100|100|100|100|100|  
|**-FastRowCount**|1|1|1|1|1|1|1|  
|**-HistoryVerboseLevel**|2|3|1|1|2|1|2|  
|**-KeepAliveMessageInterval**|300|300|300|300|300|300|300|  
|**-LoginTimeout**|15|15|15|15|15|15|15|  
|**-MaxDownloadChanges**|0|0|0|0|0|0|0|  
|**-MaxUploadChanges**|0|0|0|0|0|0|0|  
|**-MetadataRetentionCleanup**|1|1|1|1|1|1|1|  
|**-NumDeadlockRetries**|5|5|5|5|5|5|5|  
|**-ParallelUploadDownload**|NULL|NULL|NULL|NULL|NULL|NULL|1|  
|**-PollingInterval**|60|60|60|60|60|60|60|  
|**-QueryTimeout**|300|300|300|300|300|300|600|  
|**-QueueSizeMultiplier**|NULL|NULL|NULL|NULL|NULL|NULL|5|  
|**-SrcThreads**|2|2|2|2|2|1|3|  
|**-StartQueueTimeout**|0|0|0|0|0|0|0|  
|**-UploadGenerationsPerBatch**|50|50|50|50|50|1|500|  
|**-UploadReadChangesPerBatch**|100|100|100|100|100|100|100|  
|**-UploadWriteChangesPerBatch**|100|100|100|100|100|100|100|  
|**-Validate**|0|0|0|1|3|0|0|  
|**-ValidateInterval**|60|60|60|60|60|60|60|  
  
## Profils de l'Agent de lecture de la file d'attente  
 Le tableau suivant montre les paramètres définis dans le profil par défaut de l'Agent de lecture de la file d'attente. Pour plus d’informations sur ces paramètres, consultez la page [Agent de lecture de file d’attente de réplication](../../../relational-databases/replication/agents/replication-queue-reader-agent.md).  
  
||par défaut|  
|-|-------------|  
|**-HistoryVerboseLevel**|1|  
|**-LoginTimeout**|15|  
|**-PollingInterval**|5|  
|**-QueryTimeout**|1800|  
  
## Voir aussi  
 [Administration de l'Agent de réplication](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Afficher et modifier les paramètres d’invite de l’Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)   
 [Concepts des exécutables de l'agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
  