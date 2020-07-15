---
title: Surveillance (réplication) | Microsoft Docs
description: Découvrez les outils de surveillance utilisés pour suivre l’activité et l’état de la réplication dans la topologie de réplication SQL Server.
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: c463b8e1a0726fcde961b418fb12a902d7ce9b4e
ms.sourcegitcommit: 19ff45e8a2f4193fe8827f39258d8040a88befc7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83807949"
---
# <a name="monitoring-replication"></a>Surveillance (réplication)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  L'analyse d'une topologie de réplication est un aspect important du déploiement de la réplication. L'activité de la réplication étant distribuée, il est essentiel de faire le suivi de cette activité et des états à travers tous les ordinateurs impliqués dans la réplication. À l’aide de différents outils de supervision, vous pouvez répondre à des questions courantes, notamment les suivantes : 

-   L'intégrité de mon système de réplication est-elle de bonne qualité ?
-   Quels sont les abonnements lents ?
-   Mon abonnement transactionnel est-il en retard ?
-   Combien de temps mettra une transaction validée maintenant pour atteindre un Abonné avec la réplication transactionnelle ?
-   Pourquoi mon abonnement de fusion est-il lent ?
-   Pourquoi un Agent de fonctionne pas ?  
  

Les outils suivants peuvent être utilisés pour surveiller la réplication :  
  
-   **Moniteur de réplication SQL Server** - Il s’agit de l’outil de contrôle de réplication le plus important. Il présente une vue axée sur le serveur de distribution de toute l’activité de réplication. Pour plus d'informations, voir [Monitoring Replication](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md). 
-   **SQL Server Management Studio** - Donne accès au moniteur de réplication. Il vous permet aussi d’afficher l’état actuel et le dernier message journalisé par les agents suivants ; il vous permet également de démarrer et d’arrêter chaque agent : Agent de lecture du journal, Agent d’instantané, Agent de fusion et Agent de distribution. Pour plus d’informations, voir [Monitor Replication Agents](../../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
-   **Transact-SQL (T-SQL) et Replication Management Objects (RMO)** - Les deux interfaces vous permettent de superviser tous les types de réplication à partir du serveur de distribution. La réplication de fusion donne également la possibilité de surveiller la réplication à partir de l'Abonné.  
  
-   **Alertes pour les événements des agents de réplication** : la réplication fournit plusieurs alertes prédéfinies pour les événements des agents de réplication. Vous pouvez si nécessaire créer des alertes supplémentaires. Les alertes peuvent être utilisées pour déclencher une réponse automatisée à un événement et/ou envoyer une notification à un administrateur. Pour plus d’informations, consultez [Utiliser les alertes pour les événements des agents de réplication](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md).  
  
-   **Moniteur système** - Il peut être utilisé pour superviser les performances à travers plusieurs compteurs dédiés à la réplication. Pour plus d’informations, voir [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md).  
  

## <a name="see-also"></a>Voir aussi  
 [Best Practices for Replication Administration](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   

  
  
