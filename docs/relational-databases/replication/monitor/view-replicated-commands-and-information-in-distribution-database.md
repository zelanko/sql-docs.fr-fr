---
title: Afficher les commandes répliquées et d’autres informations dans la base de données de distribution
description: Découvrez comment afficher les commandes répliquées et d’autres informations sur la réplication dans la base de données de distribution pour SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 3794d249002fb6038be6a6d27d88e5f70e042104
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "76286332"
---
# <a name="view-replicated-commands-and-information-in-distribution-database"></a>Afficher les commandes répliquées et des informations dans la base de données de distribution
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Lors de l'utilisation de la réplication transactionnelle, les commandes de transaction sont stockées dans la base de données de distribution jusqu'à ce que l'Agent de distribution les propage sur tous les Abonnés ou qu'un Agent de distribution sur l'Abonné extrait les modifications. Ces commandes en attente dans la base de données de distribution peuvent être affichées par programmation à l'aide de procédures stockées de réplication. Pour plus d’informations, consultez [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>Pour afficher les commandes répliquées de toutes les publications transactionnelles de la base de données de distribution  
  
1.  Sur la base de données de distribution du serveur de distribution, exécutez [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md).  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>Pour afficher les commandes répliquées de la base de données de distribution à partir d'un article spécifique ou d'une base de données spécifique publiée à l'aide de la réplication transactionnelle  
  
1.  (Facultatif) Sur la base de données de publication du serveur de publication, exécutez [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md). Spécifiez `@publication` et `@article`. Notez la valeur de **article_id** dans le jeu de résultats.  
  
2.  Sur la base de données de distribution du serveur de distribution, exécutez [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md). (Facultatif) Spécifiez l’ID d’article de l’étape 2 pour `@article_id`. (Facultatif) Spécifiez l’ID de la base de données de publication pour `@publisher_database_id`, qui peut être obtenu à partir de la colonne **database_id** de la vue catalogue [sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller la réplication par programmation](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
