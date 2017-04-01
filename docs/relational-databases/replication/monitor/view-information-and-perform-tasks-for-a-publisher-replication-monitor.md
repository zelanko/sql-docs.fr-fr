---
title: "Afficher des informations et ex&#233;cuter des t&#226;ches pour un serveur de publication (moniteur de r&#233;plication) | Microsoft Docs"
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
  - "Éditeurs [réplication SQL Server], tâches du moniteur de réplication"
  - "affichage des informations d'un serveur de publication"
  - "Éditeurs [réplication SQL Server], affichage des informations"
ms.assetid: 1e777e95-377a-4de3-b965-867464aadaaf
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Afficher des informations et ex&#233;cuter des t&#226;ches pour un serveur de publication (moniteur de r&#233;plication)
  Le moniteur de réplication contient les onglets ci-après qui donnent des informations sur le serveur de publication sélectionné :  
  
-   **Publications**  
  
     Cet onglet donne des informations sur toutes les publications sur le serveur de publication sélectionné.  
  
-   **Liste de suivi des abonnements**  
  
     Cet onglet est destiné à afficher des informations sur les abonnements de toutes les publications disponibles sur le serveur de publication sélectionné, qui ont des erreurs, des avertissements ou les performances les plus faibles. Cet onglet n’est pas affiché pour les distributeurs exécutant des versions antérieures à [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   **Agents** onglet  
  
     Cet onglet affiche les informations détaillées sur les agents et les travaux utilisés par tous les types de réplication. L'onglet permet également de démarrer et d'arrêter chaque agent ou travail.  
  
 Pour afficher plus d’informations sur les options de chaque onglet, cliquez sur l’onglet dans le volet droit, puis cliquez sur **aide** sur la barre de menus. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Pour afficher des informations et effectuer des tâches pour un serveur de publication  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, puis développez un serveur de publication.  
  
2.  Pour afficher des informations sur toutes les publications, cliquez sur le **Publications** onglet.  
  
3.  Pour afficher des informations sur les abonnements, cliquez sur le **liste de suivi** onglet. Vous pouvez également accéder à des informations plus détaillées et effectuer des tâches à partir de cet onglet :  
  
    -   Pour afficher des informations détaillées sur l’agent associé à un abonnement, cliquez sur l’abonnement, puis cliquez sur **Afficher les détails**.  
  
    -   Pour afficher les propriétés d’un abonnement, cliquez sur l’abonnement, puis cliquez sur **propriétés**.  
  
    -   Pour synchroniser un abonnement envoyé, cliquez sur l’abonnement, puis cliquez sur **Démarrer la synchronisation**.  
  
    -   Pour réinitialiser un abonnement, cliquez sur l’abonnement, puis cliquez sur **Réinitialiser l’abonnement**.  
  
4.  Pour afficher des informations sur les agents, cliquez sur le **Agents** onglet. Vous pouvez aussi accéder à des informations plus détaillées et effectuer des tâches sur cet onglet :  
  
    -   Pour afficher des informations détaillées sur un agent (par exemple, les messages d’information et des messages d’erreur), cliquez sur l’agent, puis cliquez sur **Afficher les détails**.  
  
    -   Pour afficher des informations détaillées sur la tâche qui exécute l’agent (par exemple, la planification, détails des étapes de travail et ainsi de suite), cliquez sur l’agent, puis cliquez sur **propriétés**.  
  
    -   Pour gérer les profils de l’agent, cliquez sur l’agent, puis cliquez sur **profil d’Agent**. Pour plus d’informations, consultez [utiliser des profils de l’Agent de réplication](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Pour démarrer un agent qui n’est pas en cours d’exécution, cliquez sur l’agent, puis cliquez sur **Démarrer l’Agent**.  
  
    -   Pour arrêter un agent est en cours d’exécution, cliquez sur l’agent, puis cliquez sur **Arrêter l’Agent**.  
  
## Voir aussi  
 [View and Modify Distributor and Publisher Properties](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  