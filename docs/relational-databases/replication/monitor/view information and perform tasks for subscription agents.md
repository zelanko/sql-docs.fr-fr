---
title: "Afficher des informations et effectuer des t&#226;ches pour les agents associ&#233;s &#224; un abonnement (Moniteur de r&#233;plication) | Microsoft Docs"
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
  - "agents [réplication SQL Server], affichage des informations"
  - "affichage des informations de l'agent de réplication"
  - "agents [réplication SQL Server], tâches du moniteur de réplication"
ms.assetid: fbb59d31-2424-4552-9195-0da8d83e755f
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Afficher des informations et effectuer des t&#226;ches pour les agents associ&#233;s &#224; un abonnement (Moniteur de r&#233;plication)
  Le moniteur de réplication contient deux onglets qui permettent d'accéder à des informations sur le ou les agents associés à un abonnement :  
  
-   **Tous les abonnements**  
  
     Cet onglet montre des informations sur tous les abonnements à la publication sélectionnée.  
  
-   **Liste de suivi des abonnements**  
  
     Cet onglet est destiné à afficher des informations sur les abonnements de toutes les publications disponibles sur le serveur de publication sélectionné, qui ont des erreurs, des avertissements ou les performances les plus faibles. Cet onglet n’est pas affiché pour les distributeurs exécutant des versions antérieures à [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Pour plus d’informations sur les options de chaque onglet, cliquez sur l’onglet dans le volet droit, puis cliquez sur **aide** sur la barre de menus. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Pour afficher des informations et effectuer des tâches pour les agents associés à un abonnement (Onglet Tous les abonnements)  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Cliquez sur le **tous les abonnements** onglet pour afficher des informations sur les abonnements. Vous pouvez aussi accéder à des informations plus détaillées et effectuer des tâches sur cet onglet :  
  
    -   Pour afficher des informations détaillées sur l’agent associé à un abonnement, cliquez sur l’abonnement, puis cliquez sur **Afficher les détails**. Ces informations détaillées sont les suivantes : messages d'historique et d'erreur de l'agent, statistiques de performances pour la réplication transactionnelle et statistiques de synchronisation au niveau des articles pour la réplication de fusion.  
  
         Les onglets de la fenêtre des détails qui est lancé dépendent du type d’abonnement : pour les abonnements de capture instantanée, l’onglet est **distributeur à l’historique d’abonné**; pour les abonnements transactionnels, les onglets sont **Publisher à l’historique de distribution**, **distributeur à l’historique d’abonné**, et **commandes non distribuées**; pour les abonnements de fusion, l’onglet est **historique de synchronisation**.  
  
    -   Pour synchroniser un abonnement envoyé, cliquez sur l’abonnement, puis cliquez sur **Démarrer la synchronisation**.  
  
    -   Pour réinitialiser un abonnement, cliquez sur l’abonnement, puis cliquez sur **Réinitialiser l’abonnement**.  
  
    -   Pour valider un abonnement de fusion, cliquez sur l’abonnement, puis cliquez sur **valider l’abonnement**. Pour valider tous les abonnements à une publication de fusion, avec le bouton droit de la publication, puis cliquez sur **Valider tous les abonnements**; pour valider tous les abonnements pour une publication transactionnelle, avec le bouton droit de la publication, puis cliquez sur **valider les abonnements**.  
  
    -   Pour gérer les profils de l’agent, cliquez sur l’agent, puis cliquez sur **profil d’Agent**. Pour plus d’informations, consultez [utiliser des profils de l’Agent de réplication](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
### Pour afficher des informations et effectuer des tâches pour les agents associés à un abonnement (Onglet Liste de suivi des abonnements)  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, puis développez un serveur de publication.  
  
2.  Cliquez sur le **liste de suivi** onglet pour afficher des informations sur les abonnements. Vous pouvez aussi accéder à des informations plus détaillées et effectuer des tâches sur cet onglet :  
  
    -   Pour afficher des informations détaillées sur l’agent associé à un abonnement, cliquez sur l’abonnement, puis cliquez sur **Afficher les détails**. Ces informations détaillées sont les suivantes : messages d'historique et d'erreur de l'agent, statistiques de performances pour la réplication transactionnelle et statistiques de synchronisation au niveau des articles pour la réplication de fusion.  
  
         Les onglets de la fenêtre des détails qui est lancé dépendent du type d’abonnement : pour les abonnements de capture instantanée, l’onglet est **distributeur à l’historique d’abonné**; pour les abonnements transactionnels, les onglets sont **Publisher à l’historique de distribution**, **distributeur à l’historique d’abonné**, et **performances**; pour les abonnements de fusion, l’onglet est **historique de synchronisation**.  
  
    -   Pour synchroniser un abonnement envoyé, cliquez sur l’abonnement, puis cliquez sur **Démarrer la synchronisation**.  
  
    -   Pour réinitialiser un abonnement, cliquez sur l’abonnement, puis cliquez sur **Réinitialiser l’abonnement**.  
  
    -   Pour valider un abonnement de fusion, cliquez sur l’abonnement, puis cliquez sur **valider l’abonnement**. Pour valider tous les abonnements à une publication de fusion, avec le bouton droit de la publication, puis cliquez sur **Valider tous les abonnements**; pour valider tous les abonnements pour une publication transactionnelle, avec le bouton droit de la publication, puis cliquez sur **valider les abonnements**.  
  
    -   Pour gérer les profils de l’agent, cliquez sur l’agent, puis cliquez sur **profil d’Agent**. Pour plus d’informations, consultez [utiliser des profils de l’Agent de réplication](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
## Voir aussi  
 [Afficher des informations et effectuer des tâches pour un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  