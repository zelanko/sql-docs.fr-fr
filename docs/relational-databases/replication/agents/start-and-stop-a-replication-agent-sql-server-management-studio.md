---
title: "D&#233;marrer et arr&#234;ter un Agent de r&#233;plication (SQL Server Management Studio) | Microsoft Docs"
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
  - "agents [réplication SQL Server], arrêt"
  - "agents [réplication SQL Server], démarrage"
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# D&#233;marrer et arr&#234;ter un Agent de r&#233;plication (SQL Server Management Studio)
  Démarrer et arrêter des agents à partir de le **travaux** dossier et le **réplication** dossier [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et du moniteur de réplication. Démarrez et arrêtez les Agents et les travaux suivants :  
  
-   Agent d'instantané, utilisé par toutes les publications  
  
-   Agent de lecture du journal, utilisé par toutes les publications transactionnelles  
  
-   Agent de lecture de la file d'attente, utilisé par les publications transactionnelles qui possèdent des abonnements mis à jour en attente  
  
-   Agent de distribution, qui synchronise les abonnements aux publications transactionnelles et d'instantané  
  
-   Agent de fusion, qui synchronise les abonnements aux publications de fusion  
  
-   Travaux de maintenance de la réplication  
  
 Pour plus d’informations sur le démarrage de l’Agent de fusion et l’Agent de Distribution, consultez [synchroniser un abonnement Push](../../../relational-databases/replication/synchronize-a-push-subscription.md) et [synchroniser un abonnement extrait](../../../relational-databases/replication/synchronize-a-pull-subscription.md). Pour plus d’informations sur les tâches de maintenance, consultez [exécuter des tâches de Maintenance réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md).  
  
 Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Pour démarrer et arrêter un Agent d'instantané ou un Agent de lecture du journal à partir de Management Studio  
  
1.  Se connecter au serveur de publication dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur et le **réplication** dossier.  
  
2.  Développez le **Publications locales** dossier et avec le bouton droit puis une publication.  
  
3.  Cliquez sur **Afficher l’état de l’Agent de capture instantanée** ou **Afficher l’état de l’Agent de lecture du journal**.  
  
4.  Cliquez sur **Démarrer** ou **arrêter**.  
  
### Pour démarrer et arrêter un Agent de lecture de file d'attente à partir de Management Studio  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Avec le bouton droit de la tâche de l’agent, puis cliquez sur **Démarrer le travail** ou **Arrêter le travail**. Le nom du travail de l’Agent de lecture de file d’attente est sous la forme **[\< serveur de distribution>]. \< entier>**.  
  
### Pour démarrer et arrêter un Agent d'instantané, un Agent de lecture du journal ou un Agent de lecture de file d'attente dans le moniteur de réplication  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez sur un agent, puis cliquez sur **Démarrer l’Agent** ou **Arrêter l’Agent**.  
  
## Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Concepts des exécutables de l'agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Présentation des Agents de réplication](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  