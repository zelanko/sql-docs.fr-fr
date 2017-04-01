---
title: "Suspendre une topologie de r&#233;plication (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "administration de la réplication, suspension"
  - "suspendre [réplication SQL Server]"
  - "réplication transactionnelle, sauvegarde et restauration"
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Suspendre une topologie de r&#233;plication (programmation Transact-SQL de la r&#233;plication)
  *Suspension* un système implique l’arrêt d’activité sur les tables publiées sur tous les nœuds et en garantissant que chaque nœud a reçu toutes les modifications de tous les autres nœuds. Cette rubrique explique comment suspendre une topologie de réplication, requise pour plusieurs tâches d'administration et comment garantir qu'un nœud a reçu toutes les modifications d'autres nœuds.  
  
### Pour suspendre une topologie de réplication transactionnelle avec les abonnements en lecture seule  
  
1.  Arrêtez l'activité sur toutes les tables publiées sur le serveur de publication.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_posttracertoken & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md).  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
4.  Assurez-vous que chaque Abonné a reçu le jeton de suivi.  
  
### Pour suspendre une topologie de réplication transactionnelle avec les abonnements pouvant être mis à jour  
  
1.  Arrêtez l'activité sur toutes les tables publiées sur le serveur de publication et sur tous les Abonnés.  
  
2.  Si tous les Abonnés utilisent des abonnements de mise à jour en attente :  
  
    1.  Si l'Agent de lecture de la file d'attente ne s'exécute pas en mode continu, exécutez l'Agent. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’Agent réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) ou [Démarrer et arrêter un Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    2.  Pour vérifier que la file d’attente est vide, exécutez [sp_replqueuemonitor](../../../relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql.md) sur chaque abonné.  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_posttracertoken](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md).  
  
4.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
5.  Assurez-vous que chaque Abonné a reçu le jeton de suivi.  
  
### Pour suspendre une topologie de réplication transactionnelle d'égal à égal  
  
1.  Arrêtez l'activité sur toutes les tables publiées sur tous les nœuds.  
  
2.  Exécutez [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) sur chaque base de données de publication dans la topologie.  
  
3.  Si l'Agent de lecture du journal ou l'Agent de distribution ne s'exécute pas en mode continu, exécutez l'Agent. L'Agent de lecture du journal doit être démarré avant l'Agent de distribution. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’Agent réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) ou [Démarrer et arrêter un Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
4.  Exécutez [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) sur chaque base de données de publication dans la topologie. Vérifiez que le jeu de résultats contient des réponses de chacun des autres nœuds.  
  
### Pour garantir qu'un nœud d'égal à égal a reçu toutes les modifications antérieures  
  
1.  Exécutez [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) sur la base de données de publication au niveau du nœud que vous voulez vérifier.  
  
2.  Si l'Agent de lecture du journal ou l'Agent de distribution ne s'exécute pas en mode continu, exécutez l'Agent. L'Agent de lecture du journal doit être démarré avant l'Agent de distribution. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’Agent réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) ou [Démarrer et arrêter un Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  Exécutez [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) sur la base de données de publication au niveau du nœud que vous voulez vérifier. Vérifiez que le jeu de résultats contient des réponses de chacun des autres nœuds.  
  
### Pour suspendre une topologie de réplication de fusion  
  
1.  Arrêtez l'activité sur toutes les tables publiées sur le serveur de publication et sur tous les Abonnés.  
  
2.  Exécutez l'Agent de fusion pour chaque abonnement deux fois : synchronisez tous les abonnements une fois, puis synchronisez chaque abonnement une deuxième fois. Cela garantit que toutes les modifications sont répliquées sur tous les nœuds. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’Agent réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) ou [Démarrer et arrêter un Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    > [!NOTE]  
    >  Si les conflits se produisent pendant la synchronisation, il est possible que les modifications requises par la résolution de conflit ne soient pas propagées à tous les nœuds après que l'Agent de fusion a été exécuté deux fois.  
  
## Voir aussi  
 [Administrer une topologie d’égal à égal & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Measure Latency and Validate Connections for Transactional Replication](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  