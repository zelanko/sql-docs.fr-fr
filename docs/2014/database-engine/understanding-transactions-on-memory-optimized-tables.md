---
title: Présentation des Transactions sur les Tables mémoire optimisées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 06075248-705e-4563-9371-b64cd609793c
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 11b6becc192fcb8257f2f4dc88965c95222d2d44
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249289"
---
# <a name="understanding-transactions-on-memory-optimized-tables"></a>Comprendre les transactions sur les tables mémoire optimisées
  Les transactions accèdent aux tables mémoire optimisées à l'aide d'un type de contrôle d'accès concurrentiel optimiste et multiversion. Cela signifie qu'il existe différentes versions de données. Chaque transaction opère sur sa propre version de base de données cohérente d'un point de vue transactionnel, indépendamment des autres transactions exécutées simultanément. De plus, les transactions opèrent dans l'hypothèse optimiste qu'il n'y a aucun conflit avec d'autres transactions simultanées. Cela évite d'utiliser des verrous, mais nécessite que le système détecte les conflits et mette fin à l'une des transactions impliquées. Des conflits peuvent se produire uniquement pour les transactions d'écriture-écriture et les transactions de lecture-écriture. S'il existe un conflit d'écriture-écriture, une transaction d'écriture est terminée.  
  
 Il existe des similitudes entre le contrôle d'accès concurrentiel des tables mémoire optimisées et le contrôle d'accès concurrentiel des tables sur disque pour les niveaux d'isolation des transactions READ_COMMITTED_SNAPSHOT et SNAPSHOT. (Pour plus d’informations sur les tables sur disque, consultez [basée sur le contrôle de version de ligne des niveaux d’Isolation dans le moteur de base de données](http://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx).)  
  
## <a name="topics-in-this-section"></a>Rubriques de cette Section  
 Cette section sur les transactions dans les tables mémoire optimisées contient les rubriques suivantes :  
  
-   [Instructions pour les niveaux d’isolement des transactions sur les tables à mémoire optimisée](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
-   [Instructions pour la logique de nouvelle tentative des transactions sur des tables à mémoire optimisée](guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
-   [Transactions dans les tables à mémoire optimisée](transactions-in-memory-optimized-tables.md)  
  
-   [Niveaux d’isolation de la transaction](transaction-isolation-levels.md)  
  
-   [Transactions entre conteneurs](cross-container-transactions.md)  
  
 Pour plus d’informations, consultez [Contrôler la durabilité d’une transaction](../relational-databases/logs/control-transaction-durability.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
