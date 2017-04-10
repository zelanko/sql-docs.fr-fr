---
title: "Afficher des informations et effectuer des t&#226;ches relatives &#224; un abonnement (moniteur de r&#233;plication) | Microsoft Docs"
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
  - "abonnements [réplication SQL Server], affichage des informations"
  - "abonnements [réplication SQL Server], tâches du moniteur de réplication"
  - "affichage des informations relatives à un abonnement"
ms.assetid: 54aac83b-6f29-40d7-8901-cf059749867f
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Afficher des informations et effectuer des t&#226;ches relatives &#224; un abonnement (moniteur de r&#233;plication)
  Le Moniteur de réplication propose les onglets suivants, qui comportent des informations sur les abonnements :  
  
-   **Tous les abonnements**  
  
     Cet onglet montre des informations sur tous les abonnements à la publication sélectionnée.  
  
-   **Liste de suivi des abonnements**  
  
     Cet onglet est destiné à afficher des informations sur les abonnements de toutes les publications disponibles sur le serveur de publication sélectionné, qui ont des erreurs, des avertissements ou les performances les plus faibles. Cet onglet n’est pas affiché pour les distributeurs exécutant des versions antérieures à [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Pour plus d’informations sur les options de chaque onglet, cliquez sur l’onglet dans le volet droit, puis cliquez sur **aide** sur la barre de menus. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Pour afficher des informations et exécuter des tâches dans l'onglet Tous les abonnements  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Pour afficher des informations sur les abonnements, cliquez sur le **tous les abonnements** onglet. Pour afficher uniquement les abonnements dans un état donné, telles que la synchronisation, sélectionnez une option dans le **Afficher** liste déroulante.  
  
3.  Pour afficher et modifier les propriétés d’un abonnement, cliquez sur l’abonnement, puis cliquez sur **propriétés**. Vous pouvez également accéder à des informations plus détaillées et effectuer certaines tâches dans cet onglet. Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
### Pour afficher des informations et exécuter des tâches dans l'onglet Liste de suivi des abonnements  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, puis développez un serveur de publication.  
  
2.  Pour afficher des informations sur les abonnements, cliquez sur le **liste de suivi** onglet.  
  
3.  Sélectionnez le type d’abonnement à afficher dans la **Afficher \< SubscriptionType> abonnements** liste déroulante. Pour afficher uniquement les abonnements dans un état donné, telles que la synchronisation, sélectionnez une option dans le **Afficher** liste déroulante.  
  
4.  Pour afficher et modifier les propriétés d’un abonnement, cliquez sur l’abonnement, puis cliquez sur **propriétés**. Vous pouvez également accéder à des informations plus détaillées et effectuer certaines tâches dans cet onglet. Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Voir aussi  
 [View and Modify Push Subscription Properties](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [View and Modify Pull Subscription Properties](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  