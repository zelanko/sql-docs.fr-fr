---
title: "Afficher l&#39;&#233;tat des publications et des abonnements dans le Moniteur de r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Agent de lecture du journal, surveillance"
  - "Agent de fusion, surveillance"
  - "Agent de lecture de la file d’attente, surveillance"
  - "publications [réplication SQL Server], affichage des informations"
  - "Agent d’instantané, surveillance"
  - "Agent de distribution, surveillance"
  - "surveillance des performances [réplication SQL Server], état de la publication"
  - "surveillance des performances [réplication SQL Server], état de l’abonnement"
  - "abonnements [réplication SQL Server], affichage de l’état"
  - "Moniteur de réplication, état de la publication et de l’abonnement"
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Afficher l&#39;&#233;tat des publications et des abonnements dans le Moniteur de r&#233;plication
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] présente des informations sur l'état des publications et des abonnements :  
  
-   L'état d'une publication est déterminé par l'état de la priorité la plus élevée de ses abonnements. Par exemple, si un abonnement à une publication comporte une erreur et qu'un autre présente un problème de performances, un état d'erreur est affiché pour la publication.  
  
-   L'état d'une publication est déterminé par l'état des agents qui servent l'abonnement. Pour la réplication de fusion, il s'agit de l'Agent de fusion. Pour la réplication transactionnelle, il s'agit de l'Agent de lecture du journal ou de l'Agent de distribution (l'état de la priorité la plus élevée est affiché ; l'état peut également être déterminé par l'Agent de lecture de la file d'attente en cas d'utilisation d'abonnements de mise à jour en attente). Pour la réplication d'instantané, il s'agit de l'Agent d'instantané ou de l'Agent de distribution (l'état de priorité la plus élevée est affiché).  
  
 Les tableaux présentés dans les sections suivantes répertorient les valeurs d'état possibles pour les publications et les abonnements. Trois valeurs d'état sont affichées uniquement si un seuil est atteint ou dépassé :  
  
-   Expiration de l'abonnement  
  
     Cette valeur d'état s'applique à tous les types de réplication. Pour plus d’informations, consultez [définition des seuils et des avertissements dans le moniteur de réplication](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
-   Critique pour les performances  
  
     Cette valeur d'état s'applique à la réplication transactionnelle et à la réplication de fusion. Pour plus d’informations, consultez [analyser les performances avec le moniteur de réplication](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
-   Fusion longue  
  
     Cette valeur d'état s'applique à la réplication de fusion. Pour plus d’informations, consultez [analyser les performances avec le moniteur de réplication](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
 Outre l'état des publications et des abonnements, la réplication de fusion fournit des statistiques au niveau de l'article qui donnent des informations détaillées sur : la durée d'achèvement d'une phase de fusion, le temps passé pour traiter un article donné, le type de connexion utilisé par un Abonné et bien d'autres informations encore. Les statistiques sont affichées dans la fenêtre de l'Agent de fusion dans le moniteur de réplication. La réplication d'instantané et la réplication transactionnelle fournissent des informations détaillées sur le traitement de l'Agent de distribution.  
  
 **Pour afficher l'état des publications et des abonnements**  
  
-   Moniteur de réplication : [afficher des informations et effectuer des tâches pour une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md) et [afficher des informations et effectuer des tâches pour un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
  
 **Pour afficher des informations détaillées pour les agents**  
  
-   Moniteur de réplication : [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md) et [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Valeurs d'état des publications  
 Le tableau suivant montre les valeurs d'état des publications et leurs icônes correspondantes dans l'ordre de la priorité.  
  
|État|Icône|  
|------------|----------|  
|Erreur|![Icône d'interface utilisateur : error](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "Icône d'interface utilisateur : error")|  
|Critique pour les performances|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Nouvelle tentative de la commande qui a échoué|![Icône d'interface utilisateur : nouvelle tentative de l'agent de réplication](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "Icône d'interface utilisateur : nouvelle tentative de l'agent de réplication")|  
|OK|aucun|  
  
## Valeurs d'état des abonnements  
 Les tableaux suivants montrent les valeurs d'état des abonnements et leurs icônes correspondantes dans l'ordre de la priorité. Il est possible pour un abonnement peut avoir deux États en même temps, telles que **expire bientôt/expiré** et **Retrying Échec de la commande**; l’état de priorité la plus élevée est affiché.  
  
 Les valeurs d’état **critique pour les performances**, **expire bientôt/expiré**, et **Uninitialized** sont des avertissements. Lorsqu'un avertissement est affiché, le moniteur de réplication indique également si un agent est en cours d'exécution. Par exemple, l'état peut être **En cours d'exécution, Critique pour les performances**.  
  
### Abonnements transactionnels  
  
|État|Icône|  
|------------|----------|  
|Erreur|![Icône d'interface utilisateur : error](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "Icône d'interface utilisateur : error")|  
|Critique pour les performances|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Expire bientôt/Expiré|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Abonnement non initialisé|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Nouvelle tentative de la commande qui a échoué|![Icône d'interface utilisateur : nouvelle tentative de l'agent de réplication](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "Icône d'interface utilisateur : nouvelle tentative de l'agent de réplication")|  
|Non exécuté|![Icône d'interface utilisateur : agent de réplication arrêté](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "Icône d'interface utilisateur : agent de réplication arrêté")|  
|Exécution en cours|![Icône d'interface utilisateur : agent de réplication en cours d'exécution](../../../relational-databases/replication/monitor/media/repl-icon-running.png "Icône d'interface utilisateur : agent de réplication en cours d'exécution")|  
  
### Abonnements de fusion  
  
|État|Icône|  
|------------|----------|  
|Erreur|![Icône d'interface utilisateur : error](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "Icône d'interface utilisateur : error")|  
|Critique pour les performances|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Fusion longue|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Expire bientôt/Expiré|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Abonnement non initialisé|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Nouvelle tentative de la commande qui a échoué|![Icône d'interface utilisateur : nouvelle tentative de l'agent de réplication](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "Icône d'interface utilisateur : nouvelle tentative de l'agent de réplication")|  
|Synchronisation|![Icône d'interface utilisateur : agent de réplication en cours d'exécution](../../../relational-databases/replication/monitor/media/repl-icon-running.png "Icône d'interface utilisateur : agent de réplication en cours d'exécution")|  
|Sans synchronisation|![Icône d'interface utilisateur : agent de réplication arrêté](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "Icône d'interface utilisateur : agent de réplication arrêté")|  
  
### Abonnements d'instantanés  
  
|État|Icône|  
|------------|----------|  
|Erreur|![Icône d'interface utilisateur : error](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "Icône d'interface utilisateur : error")|  
|Expire bientôt/Expiré|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Abonnement non initialisé|![Icône d'interface utilisateur : warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icône d'interface utilisateur : warning")|  
|Nouvelle tentative de la commande qui a échoué|![Icône d'interface utilisateur : nouvelle tentative de l'agent de réplication](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "Icône d'interface utilisateur : nouvelle tentative de l'agent de réplication")|  
|Synchronisation|![Icône d'interface utilisateur : agent de réplication en cours d'exécution](../../../relational-databases/replication/monitor/media/repl-icon-running.png "Icône d'interface utilisateur : agent de réplication en cours d'exécution")|  
|Sans synchronisation|![Icône d'interface utilisateur : agent de réplication arrêté](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "Icône d'interface utilisateur : agent de réplication arrêté")|  
  
## Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  