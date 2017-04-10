---
title: "Afficher des informations et effectuer des t&#226;ches pour les agents associ&#233;s &#224; une publication (moniteur de r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
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
ms.assetid: 2a420da2-66f4-4650-9bdd-1992221ed3fd
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Afficher des informations et effectuer des t&#226;ches pour les agents associ&#233;s &#224; une publication (moniteur de r&#233;plication)
  Moniteur de réplication fournit le **Agents** onglet, qui inclut des informations sur les agents associés à la publication sélectionnée. L’Agent de Distribution et l’Agent de fusion sont associés à des abonnements ; Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
 Cet onglet affiche des informations sur les agents suivants :  
  
-   Agent d'instantané, utilisé par toutes les publications  
  
-   Agent de lecture du journal, utilisé par toutes les publications transactionnelles  
  
-   Agent de lecture de la file d'attente, utilisé par les publications transactionnelles qui possèdent des abonnements mis à jour en attente  
  
 Pour afficher plus d'informations sur les options de cet onglet, sélectionnez **Aide** sur la barre de menus. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Pour afficher des informations et effectuer des tâches pour les agents associés à une publication  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Cliquez sur le **Agents** pour afficher des informations sur les agents. Vous pouvez aussi accéder à des informations plus détaillées et effectuer des tâches sur cet onglet :  
  
    -   Pour afficher des informations détaillées sur un agent (par exemple, les messages d’information et des messages d’erreur), cliquez sur l’agent, puis cliquez sur **Afficher les détails**.  
  
    -   Pour afficher des informations détaillées sur la tâche qui exécute l’agent (par exemple, la planification, détails des étapes de travail et ainsi de suite), cliquez sur l’agent, puis cliquez sur **propriétés**.  
  
    -   Pour gérer les profils de l’agent, cliquez sur l’agent, puis cliquez sur **profil d’Agent**. Pour plus d’informations, consultez [utiliser des profils de l’Agent de réplication](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Pour démarrer un agent qui n’est pas en cours d’exécution, cliquez sur l’agent, puis cliquez sur **Démarrer l’Agent**.  
  
    -   Pour arrêter un agent est en cours d’exécution, cliquez sur l’agent, puis cliquez sur **Arrêter l’Agent**.  
  
## Voir aussi  
 [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Administration de l'Agent de réplication](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  