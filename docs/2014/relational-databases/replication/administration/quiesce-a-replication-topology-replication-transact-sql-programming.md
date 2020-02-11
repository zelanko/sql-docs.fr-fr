---
title: Suspendre une topologie de réplication (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- administering replication, quiescing
- quiesce [SQL Server replication]
- transactional replication, backup and restore
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 59c179c81c1b6b60787603f5953b85e583668c80
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63161724"
---
# <a name="quiesce-a-replication-topology-replication-transact-sql-programming"></a>Suspendre une topologie de réplication (programmation Transact-SQL de la réplication)
  *Suspendre* un système revient à interrompre toute activité sur les tables publiées de tous les nœuds et à vérifier que chaque nœud a reçu toutes les modifications des autres nœuds. Cette rubrique explique comment suspendre une topologie de réplication, requise pour plusieurs tâches d'administration et comment garantir qu'un nœud a reçu toutes les modifications d'autres nœuds.  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-read-only-subscriptions"></a>Pour suspendre une topologie de réplication transactionnelle avec les abonnements en lecture seule  
  
1.  Arrêtez l'activité sur toutes les tables publiées sur le serveur de publication.  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).  
  
3.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).  
  
4.  Assurez-vous que chaque Abonné a reçu le jeton de suivi.  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-updatable-subscriptions"></a>Pour suspendre une topologie de réplication transactionnelle avec les abonnements pouvant être mis à jour  
  
1.  Arrêtez l'activité sur toutes les tables publiées sur le serveur de publication et sur tous les Abonnés.  
  
2.  Si tous les Abonnés utilisent des abonnements de mise à jour en attente :  
  
    1.  Si l'Agent de lecture de la file d'attente ne s'exécute pas en mode continu, exécutez l'Agent. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’agent de réplication](../concepts/replication-agent-executables-concepts.md) ou [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    2.  Pour vérifier que la file d'attente est vide, exécutez [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) sur chaque Abonné.  
  
3.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).  
  
4.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).  
  
5.  Assurez-vous que chaque Abonné a reçu le jeton de suivi.  
  
### <a name="to-quiesce-a-peer-to-peer-transactional-replication-topology"></a>Pour suspendre une topologie de réplication transactionnelle d'égal à égal  
  
1.  Arrêtez l'activité sur toutes les tables publiées sur tous les nœuds.  
  
2.  Exécutez [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) sur chaque base de données de publication dans la topologie.  
  
3.  Si l'Agent de lecture du journal ou l'Agent de distribution ne s'exécute pas en mode continu, exécutez l'Agent. L'Agent de lecture du journal doit être démarré avant l'Agent de distribution. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’agent de réplication](../concepts/replication-agent-executables-concepts.md) ou [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
4.  Exécutez [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) sur chaque base de données de publication dans la topologie. Vérifiez que le jeu de résultats contient des réponses de chacun des autres nœuds.  
  
### <a name="to-ensure-a-peer-to-peer-node-has-received-all-prior-changes"></a>Pour garantir qu'un nœud d'égal à égal a reçu toutes les modifications antérieures  
  
1.  Exécutez [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) sur la base de données de publication au nœud que vous contrôlez.  
  
2.  Si l'Agent de lecture du journal ou l'Agent de distribution ne s'exécute pas en mode continu, exécutez l'Agent. L'Agent de lecture du journal doit être démarré avant l'Agent de distribution. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’agent de réplication](../concepts/replication-agent-executables-concepts.md) ou [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  Exécutez [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) sur la base de données de publication au nœud que vous contrôlez. Vérifiez que le jeu de résultats contient des réponses de chacun des autres nœuds.  
  
### <a name="to-quiesce-a-merge-replication-topology"></a>Pour suspendre une topologie de réplication de fusion  
  
1.  Arrêtez l'activité sur toutes les tables publiées sur le serveur de publication et sur tous les Abonnés.  
  
2.  Exécutez l'Agent de fusion pour chaque abonnement deux fois : synchronisez tous les abonnements une fois, puis synchronisez chaque abonnement une deuxième fois. Cela garantit que toutes les modifications sont répliquées sur tous les nœuds. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’agent de réplication](../concepts/replication-agent-executables-concepts.md) ou [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    > [!NOTE]  
    >  Si les conflits se produisent pendant la synchronisation, il est possible que les modifications requises par la résolution de conflit ne soient pas propagées à tous les nœuds après que l'Agent de fusion a été exécuté deux fois.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer une topologie d’égal à égal &#40;programmation Transact-SQL de la réplication&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Mesurer la latence et valider les connexions pour la réplication transactionnelle](../monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
