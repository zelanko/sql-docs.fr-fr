---
title: "Définition de la durabilité des objets mémoire optimisés | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe85fbf-8e8d-4983-96fd-d04b3c7d6d65
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a2ac8eee8b74c7215ab1328693e22cdc78963f8f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="defining-durability-for-memory-optimized-objects"></a>Définition de la durabilité des objets mémoire optimisés
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Il existe deux options de durabilité pour les tables mémoire optimisées :  
  
 SCHEMA_AND_DATA (par défaut)  
 Cette option fournit la durabilité du schéma et des données. Le niveau de durabilité des données varie selon que vous choisissez de valider une transaction avec une durabilité complète ou avec durabilité retardée. Les transactions à durabilité complète offrent la même garantie de durabilité pour le schéma et les données qu'une table sur disque. La durabilité retardée améliore les performances, mais peut entraîner une perte de données en cas d'incident ou de basculement du serveur. (Pour plus d’informations sur la durabilité retardée, consultez [Contrôler la durabilité d’une transaction](../../relational-databases/logs/control-transaction-durability.md).)  
  
 SCHEMA_ONLY  
 Cette option garantit la durabilité du schéma de la table. Quand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est redémarré ou qu’une reconfiguration se produit dans une base de données SQL Azure, le schéma de table persiste, mais les données de la table sont perdues. (contrairement à une table dans tempdb, où ni la table ni ses données sont conservées au redémarrage). Selon un scénario classique, pour créer une table non durable, il faut stocker les données temporaires, comme une table de mise en lots pour un processus ETL. Avec une durabilité SCHEMA_ONLY, il n'y a pas de journalisation ni de point de contrôle des transactions, ce qui peut considérablement réduire les opérations d'E/S.  
  
 Quand vous utilisez les tables SCHEMA_AND_DATA par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit les mêmes garanties de durabilité que pour les tables sur disque :  
  
 Durabilité transactionnelle  
 Lorsque vous validez une transaction à durabilité complète ayant effectué des modifications (DDL ou DML) dans une table mémoire optimisée, les modifications apportées à une table durable mémoire optimisée sont conservées.  
  
 Lorsque vous validez une transaction durable retardée pour une table mémoire optimisée, la transaction devient durable uniquement après que le journal de transactions en mémoire a été enregistré sur le disque. (Pour plus d’informations sur la durabilité retardée, consultez [Contrôler la durabilité d’une transaction](../../relational-databases/logs/control-transaction-durability.md).)  
  
 Durabilité au redémarrage  
 Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] redémarre après un incident ou un arrêt programmé, les tables durables mémoire optimisées sont réinstanciées afin d'être restaurées à l'état précédant l'incident ou l'arrêt programmé.  
  
 Durabilité en cas de défaillance du support  
 Si un disque endommagé ou corrompu contient une ou plusieurs copies persistantes d'objets durables mémoire optimisés, la fonctionnalité de sauvegarde et de restauration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restaure les tables mémoire optimisées sur le nouveau support.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets mémoire optimisés](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
