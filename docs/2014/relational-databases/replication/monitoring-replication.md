---
title: Surveillance de la réplication | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: e2b3441d98bc9226abce3a49fd28820df6ec99ab
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54134299"
---
# <a name="monitoring-replication"></a>Surveillance (réplication)
  L'analyse d'une topologie de réplication est un aspect important du déploiement de la réplication. L'activité de la réplication étant distribuée, il est essentiel de faire le suivi de cette activité et des états à travers tous les ordinateurs impliqués dans la réplication. Les outils suivants peuvent être utilisés pour surveiller la réplication :  
  
-   Moniteur de réplication de[!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]   
  
     Le moniteur de réplication est l'outil le plus important pour la surveillance de la réplication ; il donne une vision orientée serveur de publication de toute l'activité de réplication. Pour plus d’informations, consultez [analyser les performances avec le moniteur de réplication](monitor/monitor-performance-with-replication-monitor.md).  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] donne accès au moniteur de réplication. Par ailleurs, il vous permet d’afficher l’état actuel et le dernier message consigné par les agents suivants et vous permet de démarrerez et arrêtez chaque agent : Agent de lecture du journal, Agent d'instantané, Agent de fusion et Agent de distribution. Pour plus d’informations, voir [Monitor Replication Agents](monitor/monitor-replication-agents.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] et Replication Management Objects  
  
     Les deux interfaces vous permettent de surveiller tous les types de réplication à partir du serveur de distribution. La réplication de fusion donne également la possibilité de surveiller la réplication à partir de l'Abonné.  
  
-   Alertes pour les événements des agents de réplication  
  
     La réplication fournit plusieurs alertes prédéfinies pour les événements des agents de réplication ; vous pouvez si nécessaire créer des alertes supplémentaires. Les alertes peuvent être utilisées pour déclencher une réponse automatisée à un événement et/ou envoyer une notification à un administrateur. Pour plus d’informations, consultez [Utiliser les alertes pour les événements des agents de réplication](agents/use-alerts-for-replication-agent-events.md).  
  
-   Moniteur système  
  
     Le Moniteur système peut être utilisé pour surveiller les performances à travers plusieurs compteurs dédiés à la réplication. Pour plus d’informations, voir [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de réplication Forum aux questions](administration/frequently-asked-questions-for-replication-administrators.md)   
 [Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md)   

  
  
