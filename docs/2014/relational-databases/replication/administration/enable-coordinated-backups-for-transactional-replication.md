---
title: Activer les sauvegardes coordonnées pour la réplication transactionnelle (programmation Transact-SQL de la réplication) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3023fba0270e619a45a1670003928ef7f296623b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141782"
---
# <a name="enable-coordinated-backups-for-transactional-replication-replication-transact-sql-programming"></a>Activer les sauvegardes coordonnées pour la réplication transactionnelle (programmation Transact-SQL de la réplication)
  Lorsque vous activez une base de données pour la réplication transactionnelle, vous pouvez spécifier que toutes les transactions doivent être sauvegardées avant d'être remises à la base de données de distribution. Vous pouvez activer la sauvegarde coordonnée également sur la base de données de distribution afin que le journal des transactions de la base de données de publication ne soit pas tronqué tant que les transactions qui ont été propagées sur le serveur de distribution n'ont pas été sauvegardées. Pour plus d’informations, consultez [Stratégies de sauvegarde et de restauration de la réplication transactionnelle et d’instantané](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a>Pour activer les sauvegardes coordonnées d'une base de données publiée avec la réplication transactionnelle  
  
1.  Sur le serveur de publication, utilisez la fonction [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) pour retourner la propriété **IsSyncWithBackup** de la base de données de publication. Si la fonction retourne **1**, les sauvegardes coordonnées sont déjà activées pour la base de données publiée.  
  
2.  Si la fonction de l’étape 1 retourne **0**, exécutez [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) sur le serveur de publication de la base de données de publication. Spécifiez la valeur **sync with backup** pour **@optname**et **true** pour **@value**.  
  
    > [!NOTE]  
    >  Si vous modifiez l'option **sync with backup** en **false**, le point de troncation de la base de données de publication sera mis à jour après que l'Agent de lecture du journal se soit exécuté ou après un intervalle si l'Agent de lecture du journal s'exécute continuellement. L'intervalle maximal est contrôlé par le paramètre d'agent **-MessageInterval** (lequel a une valeur par défaut de 30 secondes).  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a>Pour activer des sauvegardes coordonnées pour une base de données de distribution  
  
1.  Sur le serveur de distribution, utilisez la fonction [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) pour retourner la propriété **IsSyncWithBackup** de la base de données de distribution. Si la fonction retourne **1**, les sauvegardes coordonnées sont déjà activées pour la base de données de distribution.  
  
2.  Si la fonction de l’étape 1 retourne **0**, exécutez [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) sur le serveur de distribution de la base de données de distribution. Spécifiez la valeur **sync with backup** pour **@optname** et **true** pour **@value**.  
  
### <a name="to-disable-coordinated-backups"></a>Pour désactiver les sauvegardes coordonnées  
  
1.  Sur le serveur de publication de la base de données de publication ou sur le serveur de distribution de la base de données de distribution, exécutez [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql). Spécifiez la valeur **sync with backup** pour **@optname** et **false** pour **@value**.  
  
  
