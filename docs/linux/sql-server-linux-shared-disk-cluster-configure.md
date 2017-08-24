---
title: "Configurer des clusters de disques partagés pour SQL Server sur Linux | Documents Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 92b4cb2500d4fd8a1643488593c40e97b1ff6454
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---

# <a name="shared-disk-cluster-for-sql-server-on-linux"></a>Cluster de disque partagé pour SQL Server sur Linux

Vous pouvez configurer un cluster de haute disponibilité du stockage partagé avec Linux pour permettre à l’instance de SQL Server pour le basculement à partir d’un nœud à un autre. Dans un cluster classique, deux ou plusieurs serveurs sont connectés au stockage partagé. Les serveurs sont les nœuds de cluster. Clusters de basculement offrent la protection au niveau instance pour améliorer les temps de récupération par à l’autorisation de SQL Server pour le basculement entre deux nœuds ou plus. Les étapes de configuration dépendent de la distribution de Linux et les solutions de clustering. Le tableau suivant identifie les étapes spécifiques pour les solutions de cluster validé.  

|Distribution |Rubrique 
|----- |-----
|**Red Hat Enterprise Linux avec un module complémentaire à haute disponibilité** |[Configurer](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Fonctionnement](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server avec un module complémentaire à haute disponibilité** |[Configurer](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>Étapes suivantes


