---
title: Prise en charge de la haute disponibilité pour les bases de données OLTP en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2113a916-3b1e-496c-8650-7f495e492510
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 699350a433233911bae7df4c8de430b670ef8362
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052601"
---
# <a name="high-availability-support-for-in-memory-oltp-databases"></a>Prise en charge de la haute disponibilité pour les bases de données OLTP en mémoire
  Les bases de données contenant des tables mémoire optimisées, avec ou sans procédures stockées compilées natives, sont entièrement prises en charge avec les groupes de disponibilité AlwaysOn.  Il n’existe aucune différence dans la configuration et la prise en charge des bases de données contenant des objets [!INCLUDE[hek_2](../../includes/hek-2-md.md)] et celles n’en comportant pas.  
  
## <a name="alwayson-availability-groups-and-in-memory-oltp-databases"></a>Groupes de disponibilité AlwaysOn et bases de données OLTP en mémoire  
 La configuration des bases de données avec des composants [!INCLUDE[hek_2](../../includes/hek-2-md.md)] fournit les éléments suivants :  
  
-   **Expérience entièrement intégrée**   
    Vous pouvez configurer vos bases de données contenant des tables optimisées en mémoire à l’aide du même assistant et avec le même niveau de prise en charge pour les réplicas secondaires synchrones et asynchrones. En outre, le contrôle d'intégrité est fourni par le tableau de bord AlwaysOn que vous connaissez dans SQL Server Management Studio.  
  
-   **Temps de basculement comparable**   
    Les réplicas secondaires maintiennent l’état en mémoire des tables optimisées en mémoire durables. En cas de basculement automatique ou forcé, le temps de basculement vers le nouveau réplica principal est comparable aux tables sur disque car aucune récupération n'est nécessaire. Les tables mémoire optimisées créées en tant que SCHEMA_ONLY sont prises en charge dans cette configuration. Toutefois, les modifications apportées à ces tables ne sont pas enregistrées et par conséquent, aucune donnée n'existera dans ces tables sur le réplica secondaire.  
  
-   **Secondaire accessible en lecture**   
    Vous pouvez accéder aux tables optimisées en mémoire sur le réplica secondaire et les interroger si le réplica secondaire a été configuré pour un accès en lecture. Pour plus d’informations, consultez [Secondaires actifs : réplicas secondaires lisibles (groupes de disponibilité AlwaysOn)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
## <a name="failover-clustering-instance-fci-and-in-memory-oltp-databases"></a>Instance de clustering de basculement (FCI) et bases de données OLTP en mémoire  
 Pour bénéficier d’une haute disponibilité dans une configuration de stockage partagé, vous pouvez configurer le clustering de basculement sur les instances comportant une ou plusieurs bases de données avec des tables mémoire optimisées. Vous devez tenir compte des facteurs suivants dans le cadre de la configuration d'une instance FCI.  
  
-   **Objectif de temps de récupération**   
    Le temps de basculement est susceptible d’être plus élevé, car les tables optimisées en mémoire doivent être chargées en mémoire avant que la base de données ne soit disponible.  
  
-   **Tables SCHEMA_ONLY**   
    Sachez que les tables SCHEMA_ONLY seront vides et ne comporteront aucune ligne après le basculement. C’est l’application qui conçoit et définit cela. Le comportement est identique quand vous redémarrez une base de données [!INCLUDE[hek_2](../../includes/hek-2-md.md)] avec une ou plusieurs tables SCHEMA_ONLY.  
  
## <a name="support-for-transaction-replication-in-in-memory-oltp"></a>Prise en charge de la réplication des transactions dans OLTP en mémoire  
 Les tables agissant comme des abonnés de réplication transactionnelle, à l'exclusion de la réplication transactionnelle d'égal à égal, peuvent être configurées en tant que tables mémoire optimisées. Les autres configurations de réplication ne sont pas compatibles avec les tables mémoire optimisées.  Pour plus d’informations, consultez [Abonnés à la réplication de tables optimisées en mémoire](../replication/replication-to-memory-optimized-table-subscribers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes de disponibilité AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Secondaires actifs : Réplicas secondaires lisibles &#40;groupes de disponibilité AlwaysOn&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [Abonnés à la réplication de tables optimisées en mémoire](../replication/replication-to-memory-optimized-table-subscribers.md)  
  
  