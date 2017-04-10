---
title: "Afficher des informations et effectuer des t&#226;ches relatives &#224; une publication (moniteur de r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "affichage des informations relatives à une publication"
  - "publications [réplication SQL Server], affichage des informations"
  - "publications [réplication SQL Server], tâches du moniteur de réplication"
ms.assetid: 92e28a07-d6a7-461b-a0b3-bd9bc6afcbe5
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Afficher des informations et effectuer des t&#226;ches relatives &#224; une publication (moniteur de r&#233;plication)
  Le moniteur de réplication comporte plusieurs onglets contenant des informations relatives à la publication sélectionnée :  
  
-   **Tous les abonnements**  
  
     Cet onglet montre des informations sur tous les abonnements à la publication sélectionnée.  
  
-   **Agents**  
  
     Cet onglet affiche les informations sur tous les agents utilisés par une publication :  
  
    -   Agent d'instantané, utilisé par toutes les publications  
  
    -   Agent de lecture du journal, utilisé par toutes les publications transactionnelles  
  
    -   Agent de lecture de la file d'attente, utilisé par les publications transactionnelles qui possèdent des abonnements mis à jour en attente  
  
-   **Avertissements** (pour les distributeurs en cours d’exécution [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures)  
  
    -   Cet onglet permet de spécifier des avertissements et des alertes pour les agents.  
  
-   **Les jetons de suivi** (réplication transactionnelle uniquement, pour les distributeurs exécutant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures)  
  
     Cet onglet permet de mesurer la latence, à savoir le temps écoulé entre la validation d'une transaction sur le serveur de publication et la validation de la transaction correspondante sur l'Abonné.  
  
 Pour plus d’informations sur les options de chaque onglet, cliquez sur l’onglet dans le volet droit, puis cliquez sur **aide** sur la barre de menus. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Pour afficher des informations et effectuer des tâches relatives à une publication  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Pour afficher et modifier les propriétés de la publication, avec le bouton droit de la publication, puis cliquez sur **propriétés**.  
  
3.  Pour afficher des informations sur les abonnements, cliquez sur le **tous les abonnements** onglet.  
  
     Pour afficher et modifier les propriétés d’un abonnement, cliquez sur l’abonnement, puis cliquez sur **propriétés**. Vous pouvez également accéder à des informations plus détaillées et effectuer certaines tâches dans cet onglet. Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
4.  Pour afficher des informations sur les agents, cliquez sur le **Agents** onglet. Vous pouvez également accéder à des informations plus détaillées et effectuer certaines tâches dans cet onglet. Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
5.  Pour afficher des informations sur les seuils et avertissements de l’agent, cliquez sur le **avertissements** onglet. Pour plus d’informations, consultez [définition des seuils et des avertissements dans le moniteur de réplication](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
6.  Pour afficher des informations sur les jetons de suivi, cliquez sur le **les jetons de suivi** onglet. Pour plus d’informations sur l’utilisation des jetons de suivi, consultez [mesure la latence et valider les connexions pour la réplication transactionnelle](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
## Voir aussi  
 [Afficher et modifier les propriétés d'une publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  