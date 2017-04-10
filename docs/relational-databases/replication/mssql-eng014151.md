---
title: "MSSQL_ENG014151 | Microsoft Docs"
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
  - "MSSQL_ENG014151 (erreur)"
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# MSSQL_ENG014151
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14151|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Réplication-%s : échec de l'agent %s. %s|  
  
## Explication  
 Cette erreur est émise pour tout échec d'un Agent de réplication. Le texte de la fin du message dépend du contexte de l'échec.  
  
## Action de l'utilisateur  
 Cette erreur peut se produire dans un certain nombre de situations ; utilisez l'une des approches ci-dessous selon le cas :  
  
-   Redémarrez l'Agent en échec pour voir s'il s'exécutera sans erreur. Pour plus d’informations, consultez [Démarrer et arrêter un Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) et [Concepts des exécutables de l’Agent réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Vérifiez dans l'historique de l'Agent et des travaux si d'autres erreurs se sont produites vers la même heure. Pour des informations sur l'affichage de l'état et des informations détaillées des erreurs des agents dans le moniteur de réplication, consultez les rubriques suivantes :  
  
    -   Pour l’Agent de capture instantanée, Agent de lecture du journal et l’Agent de lecture de file d’attente, consultez la page [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
    -   Pour l’Agent de Distribution et l’Agent de fusion, consultez [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
-   Vérifiez que la connectivité de base fonctionne entre les ordinateurs auxquels accédés l’agent, puis connectez-vous à chaque ordinateur avec un utilitaire tel que le [utilitaire sqlcmd](../../tools/sqlcmd-utility.md). Lors de la connexion, utilisez le même compte que celui qu'utilise l'Agent pour se connecter. Pour plus d’informations sur les autorisations requises par le compte de l’agent, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Si l'erreur se produit lors de la création ou de l'application d'un instantané, vérifiez si les fichiers du répertoire d'instantané ne comportent pas d'erreurs.  
  
-   Si l'erreur continue de se produire, augmentez le facteur de journalisation de l'agent et spécifiez un fichier de sortie pour le journal. En fonction du contexte de l'erreur, cette action peut fournir des pistes conduisant à l'erreur et/ou à d'autres messages d'erreur.  
  
## Voir aussi  
 [Administration de l'Agent de réplication](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agent de distribution de réplication](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agent de lecture du journal des réplications](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agent de fusion de réplication](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agent de lecture de la file d'attente de réplication](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Agent d'instantané de réplication](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  