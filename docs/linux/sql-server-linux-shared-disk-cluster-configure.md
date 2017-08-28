---
title: "Configurer des clusters de disques partagés pour SQL Server sur Linux | Documents Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/23/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: b6e6cc415b01c6021a4ba7c52433543dc58a4452
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="shared-disk-cluster-for-sql-server-on-linux"></a>Cluster de disque partagé pour SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Vous pouvez configurer un cluster de haute disponibilité du stockage partagé avec Linux pour permettre à l’instance de SQL Server pour le basculement à partir d’un nœud à un autre. Dans un cluster classique, deux ou plusieurs serveurs sont connectés au stockage partagé. Les serveurs sont les nœuds de cluster. Clusters de basculement offrent la protection au niveau instance pour améliorer les temps de récupération par à l’autorisation de SQL Server pour le basculement entre deux nœuds ou plus. Les étapes de configuration dépendent de la distribution de Linux et les solutions de clustering. Le tableau suivant identifie les étapes spécifiques pour les solutions de cluster validé.  

|Distribution |Rubrique 
|----- |-----
|**Red Hat Enterprise Linux avec un module complémentaire à haute disponibilité** |[Configurer](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Fonctionnement](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server avec un module complémentaire à haute disponibilité** |[Configurer](sql-server-linux-shared-disk-cluster-sles-configure.md)

