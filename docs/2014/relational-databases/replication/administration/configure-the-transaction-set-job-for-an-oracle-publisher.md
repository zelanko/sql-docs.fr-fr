---
title: Configurer le travail du jeu de transactions pour un serveur de publication Oracle (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bfa83609f4040fc9875a63217b0e86d6a3ff99bc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63187017"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a>Configurer le travail d'un jeu de transactions pour un serveur de publication Oracle (programmation Transact-SQL de la réplication)
  Le travail **Xactset** est un travail de base de données Oracle créé par la réplication qui s'exécute sur un serveur de publication Oracle pour créer des jeux de transactions lorsque l'Agent de lecture du journal n'est pas connecté au serveur de publication. Vous pouvez activer et configurer par programmation ce travail du serveur de distribution à l'aide de procédures stockées de réplication. Pour plus d’informations, consultez [Réglage des performances pour les serveurs de publication Oracle](../non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Pour activer le travail du jeu de transactions  
  
1.  Sur le serveur de publication Oracle, définissez le paramètre d'initialisation **job_queue_processes** avec une valeur suffisante pour autoriser l'exécution du travail Xactset. Pour plus d'informations sur ce paramètre, consultez la documentation de base de données du serveur de publication Oracle.  
  
2.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication Oracle pour **@publisher** , une valeur de `xactsetbatching` pour **@propertyname** et la valeur `enabled` pour **@propertyvalue** .  
  
3.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication Oracle pour **@publisher** , une valeur de `xactsetjobinterval` pour **@propertyname** et l’intervalle du travail, en minutes, pour **@propertyvalue** .  
  
4.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication Oracle pour **@publisher** , une valeur de `xactsetjob` pour **@propertyname** et la valeur `enabled` pour **@propertyvalue** .  
  
### <a name="to-configure-the-transaction-set-job"></a>Pour configurer le travail du jeu de transactions  
  
1.  (Facultatif) Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication Oracle pour **@publisher** . Les propriétés du travail **Xactset** sur le serveur de publication sont ainsi retournées.  
  
2.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication Oracle pour **@publisher** , le nom de la propriété du travail Xactset en cours de définition pour **@propertyname** et une nouvelle valeur pour **@propertyvalue** .  
  
3.  (Facultatif) Répétez l'étape 2 pour chaque propriété de travail Xactset définie. Lorsque vous modifiez le `xactsetjobinterval` propriété, vous devez redémarrer le travail sur le serveur de publication Oracle pour le nouvel intervalle prenne effet.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Pour afficher les propriétés du travail du jeu de transactions  
  
1.  Sur le serveur de distribution, exécutez [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql). Spécifiez le nom du serveur de publication Oracle pour **@publisher** .  
  
### <a name="to-disable-the-transaction-set-job"></a>Pour désactiver le travail du jeu de transactions  
  
1.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication Oracle pour **@publisher** , une valeur de `xactsetjob` pour **@propertyname** et la valeur `disabled` pour **@propertyvalue** .  
  
## <a name="example"></a>Exemple  
 L'exemple suivant active le `Xactset` travail et définit un intervalle de trois minutes entre deux exécutions.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a>Voir aussi  
 [Réglage des performances pour les serveurs de publication Oracle](../non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
