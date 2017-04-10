---
title: "MSSQL_ENG018752 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG018752 (erreur)"
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG018752
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|18752|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Un seul Agent de lecture du journal ou une seule procédure liée au journal (sp_repldone, sp_replcmds et sp_replshowcmds) peut se connecter à une base de données à la fois. Si vous avez exécuté une procédure liée au journal, supprimez la connexion à travers laquelle fut exécutée la procédure ou exécutez sp_replflush sur cette connexion avant de démarrer l'Agent de lecture du journal ou d'exécuter toute autre procédure liée au journal.|  
  
## Explication  
 Plusieurs connexions en cours tentent d’exécuter une des opérations suivantes : **sp_repldone**, **sp_replcmds**, ou **sp_replshowcmds**. Les procédures stockées [sp_repldone & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md) et [sp_replcmds & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) procédures stockées sont utilisées par l’Agent de lecture du journal pour rechercher et mettre à jour les informations sur les transactions répliquées dans une base de données publiée. La procédure stockée [sp_replshowcmds & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md) permet de corriger certains types de problèmes avec la réplication transactionnelle.  
  
 Cette erreur se produit dans les circonstances suivantes :  
  
-   Si l'Agent de lecture du journal d'une base de données publiée est en cours d'exécution et si un deuxième Agent de lecture de journal tente de s'exécuter sur la même base de données, cette erreur est émise pour le second agent et apparaît dans l'historique de l'agent.  
  
     Dans les situations où plusieurs agents sont impliqués, il est possible que l'un d'entre eux résulte d'un processus orphelin.  
  
-   Si l’Agent de lecture du journal pour une base de données publiée est démarré et qu’un utilisateur exécute **sp_repldone**, **sp_replcmds**, ou **sp_replshowcmds** par rapport à la même base de données, l’erreur est générée dans l’application dans laquelle la procédure stockée a été exécutée (tel que **sqlcmd**).  
  
-   Si aucun Agent de lecture du journal n’est en cours d’exécution pour une base de données publiée et qu’un utilisateur exécute **sp_repldone**, **sp_replcmds**, ou **sp_replshowcmds** et puis ne ferme pas la connexion sur laquelle la procédure a été exécutée, l’erreur est générée lorsque l’Agent de lecture du journal se connecte à la base de données.  
  
## Action de l'utilisateur  
 La procédure suivante peut vous aider à résoudre ce problème. Si l'une des étapes permet à l'Agent de lecture de journal de démarrer sans erreur, il n'est pas nécessaire d'exécuter le reste de la procédure.  
  
-   Vérifiez dans l'historique de l'Agent de lecture de journal s'il y a d'autres erreurs qui pourraient être cause de cette erreur. Pour plus d’informations sur l’affichage des détails d’erreur et d’état de l’agent dans le moniteur de réplication, consultez [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
-   Vérifiez le résultat de [sp_who & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) des numéros d’identification de processus (SPID) qui sont connectés à la base de données publiée. Fermez toutes les connexions susceptible d’avoir exécuté **sp_repldone**, **sp_replcmds**, ou **sp_replshowcmds**.  
  
-   Redémarrez l'Agent de lecture du journal. Pour plus d’informations, consultez [Démarrer et arrêter un Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
-   Redémarrez le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (mettez-le hors ligne ou en ligne dans un cluster) sur le serveur de distribution. S’il est possible qu’une tâche planifiée ait exécuté **sp_repldone**, **sp_replcmds**, ou **sp_replshowcmds** à partir de n’importe quel autre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’instance, redémarrez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour ces instances également. Pour plus d’informations, consultez [Démarrer, arrêter ou suspendre le Service SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).  
  
-   Exécutez [sp_replflush & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md) sur le serveur de publication dans la base de données de publication, puis redémarrez l’Agent de lecture du journal.  
  
-   Si l'erreur continue de se produire, augmentez le facteur de journalisation de l'agent et spécifiez un fichier de sortie pour le journal. En fonction du contexte de l'erreur, cette action peut fournir des pistes conduisant à l'erreur et/ou à d'autres messages d'erreur.  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agent de lecture du journal des réplications](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
  