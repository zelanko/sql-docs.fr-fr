---
title: "Surveiller des Agents de r&#233;plication | Microsoft Docs"
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
  - "analyse des performances [réplication SQL Server], agents"
  - "Agent de lecture du journal, surveillance"
  - "Moniteur de réplication, agents"
  - "Agent de fusion, surveillance"
  - "Agent de lecture de la file d’attente, analyse"
  - "Agent d’instantané, surveillance"
  - "agents [réplication SQL Server], surveillance"
  - "Agent de distribution, surveillance"
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Surveiller des Agents de r&#233;plication
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Moniteur de réplication fournit une vue systémique de l’activité de réplication, mais il permet aussi simple rechercher des informations sur un agent spécifique. La liste suivante comprend chacun des agents, les onglets du moniteur de réplication sur lesquels ils peuvent être trouvés et un lien vers une rubrique qui explique comment accéder à ces onglets :  
  
-   Les agents suivants sont associés à des publications dans le moniteur de réplication :  
  
    -   Agent d'instantané  
  
    -   l'Agent de lecture du journal ;  
  
    -   Agent de lecture de la file d'attente  
  
     Accéder aux informations et les tâches associées à ces agents via les onglets suivants : **Agents** (disponible pour chaque éditeur et la publication) et **avertissements** (disponible pour chaque publication). Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
-   Les agents suivants sont associés à des abonnements dans le moniteur de réplication :  
  
    -   Agent de distribution  
  
    -   Agent de fusion  
  
     Accéder aux informations et les tâches associées à ces agents via les onglets suivants : **liste de suivi** (disponible pour chaque serveur de publication) ou le **tous les abonnements** (disponible pour chaque publication). Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Utiliser SQL Server Management Studio pour surveiller les agents de réplication  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Fournit des boîtes de dialogue suivantes pour surveiller les agents de réplication :  
  
-   **Afficher l’état de l’Agent de capture instantanée** (pour toutes les publications)  
  
-   **Afficher l’état de l’Agent de lecture du journal** (pour toutes les publications transactionnelles)  
  
-   **Afficher l’état de synchronisation** (pour tous les abonnements ; cette boîte de dialogue permet d’accéder à l’Agent de Distribution et l’Agent de fusion)  
  
 Le moniteur de réplication donne des informations supplémentaires sur chaque agent et permet la surveillance de l'Agent de lecture de la file d'attente, s'il est utilisé. Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md), [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md), et [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
#### Pour surveiller l'Agent d'instantané et l'Agent de lecture du journal  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Cliquez sur une publication, puis cliquez sur **Afficher l’état de l’Agent lecteur de journal** ou **Afficher l’état de l’Agent capture instantanée**.  
  
4.  Dans la **Afficher l’état de l’Agent lecteur de journal** ou **Afficher l’état de l’Agent capture instantanée** boîte de dialogue :  
  
    -   Affichez l'état de l'agent.  
  
    -   Démarrez ou arrêtez l'agent si nécessaire.  
  
    -   Cliquez sur **analyse** pour lancer **Moniteur de réplication**.  
  
5.  Cliquez sur **Fermer**.  
  
#### Pour surveiller l'Agent de distribution et l'Agent de fusion (à partir du serveur de publication)  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Développez la publication pour l'abonnement que vous voulez surveiller.  
  
4.  Cliquez sur l’abonnement, puis cliquez sur **Afficher l’état de synchronisation**.  
  
5.  Dans la **Afficher l’état de synchronisation** boîte de dialogue :  
  
    -   Affichez l'état de l'agent.  
  
    -   Démarrez ou arrêtez l'agent si nécessaire.  
  
    -   Pour les abonnements envoyés, cliquez sur **analyse** pour lancer **Moniteur de réplication**.  
  
    -   Pour les abonnements par extraction de données, cliquez sur **Afficher l’historique des travaux** pour lancer le **visionneuse du fichier journal**, qui affiche le contenu du journal de l’agent.  
  
6.  Cliquez sur **Fermer**.  
  
#### Pour surveiller l'Agent de distribution et l'Agent de fusion (à partir de l'Abonné)  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Cliquez sur l’abonnement que vous souhaitez surveiller, puis cliquez sur **Afficher l’état de synchronisation**.  
  
4.  Dans la **Afficher l’état de synchronisation** boîte de dialogue :  
  
    -   Affichez l'état de l'agent.  
  
    -   Démarrez ou arrêtez l'agent si nécessaire.  
  
    -   Cliquez sur **Afficher l’historique des travaux** pour lancer le **visionneuse du fichier journal**, qui affiche le contenu du journal de l’agent.  
  
5.  Cliquez sur **Fermer**.  
  
## Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Présentation des Agents de réplication](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  