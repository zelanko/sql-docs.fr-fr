---
title: "ex&#233;cuter des travaux de maintenance de r&#233;plication (SQL Server Management Studio) | Microsoft Docs"
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
  - "travaux [réplication SQL Server]"
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# ex&#233;cuter des travaux de maintenance de r&#233;plication (SQL Server Management Studio)
  Les travaux de maintenance de la réplication sont les suivants :  
  
-   **Réinitialiser les abonnements présentant des erreurs de validation de données**  
  
-   **Nettoyage de l'historique de l'agent : distribution**  
  
-   **Actualisateur de surveillance de réplication pour la distribution.**  
  
-   **Contrôle des agents de réplication**  
  
-   **Nettoyage de la distribution : distribution**  
  
-   **Nettoyage de l'abonnement expiré**  
  
 Démarrez et arrêtez ces travaux à partir du dossier **Travaux** de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et à partir de l'onglet **Travaux communs** du moniteur de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md). Afficher et modifier les propriétés de chaque travail dans la **Propriétés du travail - \< travail>** boîte de dialogue est disponible à partir du même dossier et le même onglet.  
  
### Pour démarrer ou arrêter un travail de maintenance de réplication dans Management Studio  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez sur une tâche, puis cliquez sur **Démarrer le travail** ou **Arrêter le travail**.  
  
### Pour démarrer ou arrêter un travail de maintenance de réplication dans le moniteur de réplication  
  
1.  Développez un groupe du serveur de publication dans le moniteur de réplication, puis sélectionnez un serveur de publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez sur une tâche dans la grille, puis cliquez sur **Démarrer le travail** ou **Arrêter le travail**.  
  
### Pour afficher et modifier les propriétés d'un travail de maintenance de réplication dans Management Studio  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez sur une tâche, puis cliquez sur **propriétés**.  
  
4.  Dans la **Propriétés du travail - \< travail>** boîte de dialogue Modifier les propriétés si nécessaire, puis cliquez sur **OK**.  
  
### Pour afficher et modifier les propriétés d'un travail de maintenance de réplication dans le moniteur de réplication  
  
1.  Développez un groupe du serveur de publication dans le moniteur de réplication, puis sélectionnez un serveur de publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez sur une tâche dans la grille, puis cliquez sur **propriétés**.  
  
4.  Dans la **Propriétés du travail - \< travail>** boîte de dialogue Modifier les propriétés si nécessaire, puis cliquez sur **OK**.  
  
## Voir aussi  
 [Démarrer et arrêter un Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Afficher des informations et effectuer des tâches pour un serveur de publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Administration de l'Agent de réplication](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  