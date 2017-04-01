---
title: "Configurer le travail d&#39;un jeu de transactions pour un serveur de publication Oracle (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "sp_publisherproperty"
  - "publication Oracle [réplication SQL Server], configuration"
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Configurer le travail d&#39;un jeu de transactions pour un serveur de publication Oracle (programmation Transact-SQL de la r&#233;plication)
  Le **Xactset** tâche est une tâche de base de données Oracle créée par la réplication qui s’exécute sur un serveur de publication Oracle pour créer des ensembles de transaction lorsque l’Agent de lecture du journal n’est pas connecté au serveur de publication. Vous pouvez activer et configurer par programmation ce travail du serveur de distribution à l'aide de procédures stockées de réplication. Pour plus d’informations, consultez [Optimisation des performances pour les serveurs de publication Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### Pour activer le travail du jeu de transactions  
  
1.  Le serveur de publication Oracle, définissez la **job_queue_processes** paramètre d’initialisation avec une valeur suffisante pour permettre l’exécution du travail Xactset. Pour plus d'informations sur ce paramètre, consultez la documentation de base de données du serveur de publication Oracle.  
  
2.  Sur le serveur de distribution, exécutez [sp_publisherproperty & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Spécifiez le nom du serveur de publication Oracle pour **@publisher**, une valeur de **xactsetbatching** de **@propertyname**, et la valeur **activé** pour **@propertyvalue**.  
  
3.  Sur le serveur de distribution, exécutez [sp_publisherproperty & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Spécifiez le nom du serveur de publication Oracle pour **@publisher**, une valeur de **xactsetjobinterval** de **@propertyname**, et l’intervalle du travail, en minutes, pour **@propertyvalue**.  
  
4.  Sur le serveur de distribution, exécutez [sp_publisherproperty & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Spécifiez le nom du serveur de publication Oracle pour **@publisher**, une valeur de **xactsetjob** de **@propertyname**, et la valeur **activé** pour **@propertyvalue**.  
  
### Pour configurer le travail du jeu de transactions  
  
1.  (Facultatif) Sur le serveur de distribution, exécutez [sp_publisherproperty & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Spécifiez le nom du serveur de publication Oracle pour **@publisher**. Cela retourne les propriétés de la **Xactset** tâche sur le serveur de publication.  
  
2.  Sur le serveur de distribution, exécutez [sp_publisherproperty & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Spécifiez le nom du serveur de publication Oracle pour **@publisher**, le nom de la propriété du travail Xactset définie pour **@propertyname**, et une nouvelle valeur pour **@propertyvalue**.  
  
3.  (Facultatif) Répétez l'étape 2 pour chaque propriété de travail Xactset définie. Lorsque vous modifiez le **xactsetjobinterval** propriété, vous devez redémarrer le travail sur le serveur de publication Oracle pour le nouvel intervalle prenne effet.  
  
### Pour afficher les propriétés du travail du jeu de transactions  
  
1.  Sur le serveur de distribution, exécutez [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md). Spécifiez le nom du serveur de publication Oracle pour **@publisher**.  
  
### Pour désactiver le travail du jeu de transactions  
  
1.  Sur le serveur de distribution, exécutez [sp_publisherproperty & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Spécifiez le nom du serveur de publication Oracle pour **@publisher**, une valeur de **xactsetjob** de **@propertyname**, et la valeur **désactivé** pour **@propertyvalue**.  
  
## Exemple  
 L'exemple suivant active le `Xactset` travail et définit un intervalle de trois minutes entre deux exécutions.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure the transactio_1.sql)]  
  
## Voir aussi  
 [Réglage des performances pour les serveurs de publication Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  