---
title: "Afficher les commandes r&#233;pliqu&#233;es et autres informations dans la base de donn&#233;es de distribution (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
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
  - "sp_browsereplcmds"
  - "réplication transactionnelle, analyse"
  - "bases de données [réplication SQL Server], affichage de commandes répliquées"
  - "affichage des commandes répliquées"
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Afficher les commandes r&#233;pliqu&#233;es et autres informations dans la base de donn&#233;es de distribution (programmation Transact-SQL de la r&#233;plication)
  Lors de l'utilisation de la réplication transactionnelle, les commandes de transaction sont stockées dans la base de données de distribution jusqu'à ce que l'Agent de distribution les propage sur tous les Abonnés ou qu'un Agent de distribution sur l'Abonné extrait les modifications. Ces commandes en attente dans la base de données de distribution peuvent être affichées par programmation à l'aide de procédures stockées de réplication. Pour plus d’informations, consultez [procédures stockées de réplication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).  
  
### Pour afficher les commandes répliquées de toutes les publications transactionnelles de la base de données de distribution  
  
1.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md).  
  
### Pour afficher les commandes répliquées de la base de données de distribution à partir d'un article spécifique ou d'une base de données spécifique publiée à l'aide de la réplication transactionnelle  
  
1.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md). Spécifiez **@publication** et **@article**. Notez la valeur de **id d’article** du résultat défini.  
  
2.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md). (Facultatif) Spécifiez l’ID de l’article à l’étape 2 pour **@article_id**. (Facultatif) Spécifiez l’ID de la base de données de publication pour **@publisher_database_id**, qui peut être obtenu à partir de la **database_id** colonne dans la [sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) affichage catalogue.  
  
## Voir aussi  
 [Programmatically Monitor Replication](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  