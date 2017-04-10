---
title: "Activer les sauvegardes coordonn&#233;es pour la r&#233;plication transactionnelle (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
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
  - "réplication transactionnelle, sauvegarde et restauration"
  - "sp_replicationdboption"
  - "sync with backup [réplication SQL Server]"
  - "sauvegardes coordonnées [réplication SQL Server]"
  - "sauvegardes [réplication SQL Server], réplication transactionnelle"
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Activer les sauvegardes coordonn&#233;es pour la r&#233;plication transactionnelle (programmation Transact-SQL de la r&#233;plication)
  Lorsque vous activez une base de données pour la réplication transactionnelle, vous pouvez spécifier que toutes les transactions doivent être sauvegardées avant d'être remises à la base de données de distribution. Vous pouvez activer la sauvegarde coordonnée également sur la base de données de distribution afin que le journal des transactions de la base de données de publication ne soit pas tronqué tant que les transactions qui ont été propagées sur le serveur de distribution n'ont pas été sauvegardées. Pour plus d’informations, consultez [stratégies de sauvegarde et restauration de capture instantanée et la réplication transactionnelle](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
### Pour activer les sauvegardes coordonnées d'une base de données publiée avec la réplication transactionnelle  
  
1.  Sur le serveur de publication, utilisez la [DATABASEPROPERTYEX & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/databasepropertyex-transact-sql.md) fonction pour renvoyer le **IsSyncWithBackup** propriété de la base de données de publication. Si la fonction retourne **1**, et coordonnée des sauvegardes sont déjà activées pour la base de données publiée.  
  
2.  Si la fonction à l’étape 1 retourne **0**, exécutez [sp_replicationdboption & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) sur la base de données de publication de l’éditeur. Spécifiez la valeur **synchronisation avec la sauvegarde** pour **@optname**, et **true** pour **@value**.  
  
    > [!NOTE]  
    >  Si vous modifiez la **la synchronisation avec la sauvegarde** option **false**, le point de troncation de la base de données de publication est actualisé après l’exécution de l’Agent de lecture du journal, ou après un intervalle si l’Agent de lecture du journal s’exécute en continu. L’intervalle maximal est contrôlé par la **– MessageInterval** paramètre d’agent (qui a une valeur par défaut de 30 secondes).  
  
### Pour activer des sauvegardes coordonnées pour une base de données de distribution  
  
1.  Sur le serveur de distribution, utilisez la [DATABASEPROPERTYEX & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/databasepropertyex-transact-sql.md) fonction pour renvoyer le **IsSyncWithBackup** propriété de la base de données de distribution. Si la fonction retourne **1**, et coordonnée des sauvegardes sont déjà activées pour la base de données de distribution.  
  
2.  Si la fonction à l’étape 1 retourne **0**, exécutez [sp_replicationdboption & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) sur la base de données de distribution du distributeur. Spécifiez la valeur **synchronisation avec la sauvegarde** pour **@optname** et **true** pour **@value**.  
  
### Pour désactiver les sauvegardes coordonnées  
  
1.  Serveur de la base de données de publication ou sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replicationdboption & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md). Spécifiez la valeur **synchronisation avec la sauvegarde** pour **@optname** et **false** pour **@value**.  
  
  