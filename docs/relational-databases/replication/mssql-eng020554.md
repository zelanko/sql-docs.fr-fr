---
title: "MSSQL_ENG020554 | Microsoft Docs"
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
  - "MSSQL_ENG020554 (erreur)"
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG020554
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|20554|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'agent de réplication n'a enregistré aucun message d'état d'avancement en %ld minutes. Il se peut que l'agent ne réponde pas ou que l'activité du système soit élevée. Vérifiez que les enregistrements sont répliqués vers la destination et que les connexions à l'Abonné, au serveur de publication et au serveur de distribution sont toujours actives.|  
  
## Explication  
 Le **contrôle des agents de réplication** tâche s’exécute à intervalles réguliers (10 minutes par défaut) pour vérifier l’état de chaque agent de réplication. Si un agent n'a consigné aucun message d'avancement depuis la dernière fois où le travail de vérification des agents s'est exécuté, une erreur MSSQL_ENG020554 peut être signalée. L'agent est supposé consigner au moins des messages d'historique, même si aucune autre activité de réplication ne se produit. Même si l'agent de réplication ne répond pas comme attendu, il n'est pas nécessairement arrêté ou en échec (si un agent a échoué, l'erreur MSSQL_ENG020536 est normalement signalée).  
  
 Les problèmes suivants peuvent provoquer l'apparition de l'erreur MSSQL_ENG020554 :  
  
-   L’Agent est occupé.  
  
     Si l'agent est trop occupé pour répondre quand il est interrogé par le travail de vérification des agents, ce travail ne peut pas rapporter si l'agent de réplication fonctionne correctement. Il y a plusieurs raisons pour lesquelles l'agent de réplication peut être occupé : il peut y avoir un grande quantité de données en cours de réplication, ou il peut y avoir des problèmes de conception ou de configuration de l'application qui aboutissent à des processus très longs à s'exécuter.  
  
-   L'agent ne peut pas se connecter à un des ordinateurs de la topologie.  
  
     Tous les agents ont un paramètre **- LoginTimeOut** (défini sur 15 secondes par défaut), qui détermine la durée pendant laquelle un agent tente de se connecter à un nœud de réplication, telles que l’Agent de fusion se connecter au serveur de publication. Si le **- LoginTimeOut** a la valeur supérieure à l’intervalle auquel le travail de vérification de l’agent de réplication s’exécute, un problème de connexion peut être la cause de l’erreur : erreur MSSQL_ENG020554 est déclenché avant que l’agent est en mesure de déclencher une erreur plus spécifique.  
  
## Action de l'utilisateur  
 L'action requise dépend de la cause de l'erreur :  
  
-   Dans tous les cas où cette erreur est signalée :  
  
     Vérifiez les détails de l'erreur dans le moniteur de réplication, puis redémarrez l'agent s'il s'est arrêté. Les détails de l'erreur devraient fournir des informations supplémentaires sur la raison pour laquelle l'agent ne fonctionnait pas correctement. Si l'agent ne fonctionne pas, n'arrêtez pas et ne redémarrez pas l'agent car cela peut aggraver le problème. Pour des informations sur l'affichage de l'état et des informations détaillées des erreurs des agents dans le moniteur de réplication, consultez les rubriques suivantes :  
  
    -   Pour l’Agent de capture instantanée, Agent de lecture du journal et l’Agent de lecture de file d’attente, consultez la page [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
    -   Pour l’Agent de Distribution et l’Agent de fusion, consultez [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
-   Si l'erreur est signalée fréquemment parce que l'agent est occupé :  
  
     Il peut être nécessaire de reconcevoir l'application de façon à ce que les traitements effectués par l'agent soient moins longs.  
  
     Vous pouvez augmenter l'intervalle auquel l'état de l'agent est vérifié à l'aide de la boîte de dialogue **Propriétés du travail** . Pour plus d’informations sur l’accès à cette boîte de dialogue pour les tâches de réplication, consultez [afficher des informations et effectuer des tâches pour un serveur de publication & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md).  
  
-   Si un agent ne peut pas se connecter à un des ordinateurs de la topologie :  
  
     Il est recommandé que le **- LoginTimeOut** valeur inférieure à la fréquence à laquelle le travail de vérification de l’agent de réplication s’exécute. Dans certains cas, la valeur de **- LoginTimeOut** est défini plus haut en raison de problèmes de réseau qui provoquent des connexions à un délai d’attente. Si le **- LoginTimeOut** est défini, la réplication peut signaler des erreurs plus spécifiques, ce qui vous permet de résoudre les problèmes de connexion qui peut être dû à des autorisations, des problèmes de réseau ou d’autres problèmes. Les paramètres des agents peuvent être spécifiés dans des profils d'agent et sur la ligne de commande. Pour plus d'informations, consultez :  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Afficher et modifier les paramètres d’invite de l’Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concepts des exécutables de l’Agent réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## Voir aussi  
 [Administration de l'Agent de réplication](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agent de distribution de réplication](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agent de lecture du journal des réplications](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agent de fusion de réplication](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agent de lecture de la file d'attente de réplication](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Agent d'instantané de réplication](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  