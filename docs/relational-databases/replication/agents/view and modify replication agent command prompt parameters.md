---
title: "Afficher et modifier des param&#232;tres d&#39;invite de commandes d&#39;un Agent de r&#233;plication (SQL Server Management Studio) | Microsoft Docs"
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
  - "agents [réplication SQL Server], paramètres d’invite de commandes"
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Afficher et modifier des param&#232;tres d&#39;invite de commandes d&#39;un Agent de r&#233;plication (SQL Server Management Studio)
  Les Agents de réplication sont des fichiers exécutables qui acceptent des paramètres de ligne de commande. Par défaut, les agents s’exécutent sous [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les étapes de travail de l’Agent, donc ces paramètres peuvent être affichés et modifiés en utilisant le **Propriétés du travail - \< travail>** boîte de dialogue. Cette boîte de dialogue est disponible dans le dossier **Travaux** de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et sous l'onglet **Agents** du moniteur de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
> [!NOTE]  
>  Les modifications apportées aux paramètres prennent effet au prochain démarrage de l'Agent. Si l'Agent fonctionne en continu, vous devez l'arrêter, puis le redémarrer.  
  
 Bien que les paramètres puissent être modifiés directement, il est plus courant de les modifier dans un profil d'Agent. Pour plus d’informations, voir [Replication Agent Profiles](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 Si vous accédez à des travaux d'Agent à partir du dossier **Travaux** , utilisez la table ci-dessous pour déterminer le nom du travail d'Agent et les paramètres disponibles pour chaque Agent.  
  
|Agent|Nom du travail|Pour obtenir une liste des paramètres, voir…|  
|-----------|--------------|------------------------------------|  
|Agent d'instantané|**\< serveur de publication>-\< Basedonnéespublication>-\< Publication>-\< entier>**|[Agent d'instantané de réplication](../../../relational-databases/replication/agents/replication-snapshot-agent.md)|  
|Agent d'instantané pour une partition de publication de fusion|**Dyn_ \< serveur de publication>-\< Basedonnéespublication>-\< Publication>-\< GUID>**|[Agent d'instantané de réplication](../../../relational-databases/replication/agents/replication-snapshot-agent.md)|  
|l'Agent de lecture du journal ;|**\< serveur de publication>-\< Basedonnéespublication>-\< entier>**|[Agent de lecture du journal des réplications](../../../relational-databases/replication/agents/replication-log-reader-agent.md)|  
|Agent de fusion pour les abonnements extraits|**\< serveur de publication>-\< Basedonnéespublication>-\< Publication>-\< abonné>-\< BasededonnéesAbonnement>-\< entier>**|[Agent de fusion de réplication](../../../relational-databases/replication/agents/replication-merge-agent.md)|  
|Agent de fusion pour abonnements par envoi de données (push)|**\< serveur de publication>-\< Basedonnéespublication>-\< Publication>-\< abonné>-\< entier>**|[Agent de fusion de réplication](../../../relational-databases/replication/agents/replication-merge-agent.md)|  
|Agent de distribution pour abonnements par envoi de données (push)|**\< serveur de publication>-\< Basedonnéespublication>-\< Publication>-\< abonné>-\< entier>***|[Agent de distribution de réplication](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Agent de distribution pour abonnements par extraction de données (pull)|**\< serveur de publication>-\< Basedonnéespublication>-\< Publication>-\< abonné>-\< BasededonnéesAbonnement>-\< GUID>***\*|[Agent de distribution de réplication](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Agent de distribution pour les abonnements par envoi de données aux Abonnés non SQL Server|**\< serveur de publication>-\< Basedonnéespublication>-\< Publication>-\< abonné>-\< entier>**|[Agent de distribution de réplication](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Agent de lecture de la file d'attente|**[\< serveur de distribution>]. \< entier>**|[Agent de lecture de la file d'attente de réplication](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)|  
  
 \*Pour les abonnements aux publications Oracle, il est **\< serveur de publication>-\< serveur de publication**> plutôt que **\< serveur de publication>-\< Basedonnéespublication>**  
  
 \*\*Pour les abonnements extraits aux publications Oracle, il est **\< serveur de publication>-\< DistributionDatabase**> au lieu de **\< serveur de publication>-\< Basedonnéespublication>**  
  
### Pour afficher et modifier les paramètres de ligne de commande de l'Agent de réplication à partir de Management Studio  
  
1.  Connectez-vous à l'ordinateur approprié dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur :  
  
    -   Pour l'Agent de distribution et l'Agent de fusion pour les abonnements par extraction de données, connectez-vous à l'Abonné.  
  
    -   Pour tous les autres agents, connectez-vous au serveur de distribution.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez sur une tâche, puis cliquez sur **propriétés**.  
  
4.  Sur le **étapes** page de le **Propriétés du travail - \< travail>** boîte de dialogue, sélectionnez l’étape **exécuter l’agent**, puis cliquez sur **Modifier**.  
  
5.  Dans la **tâche Exécuter l’agent - propriétés de l’étape** boîte de dialogue Modifier la **commande** champ.  
  
6.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
### Pour afficher et modifier les paramètres de ligne de commande de l'Agent de distribution et de l'Agent de fusion à partir du Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
3.  Avec le bouton droit à un abonnement, puis cliquez sur **Afficher les détails**.  
  
4.  Dans la **abonnement \< SubscriptionName >** fenêtre, cliquez sur **Action**, puis cliquez sur **\< Nom_agent> Propriétés de la tâche**.  
  
5.  Sur le **étapes** page de le **Propriétés du travail - \< travail>** boîte de dialogue, sélectionnez l’étape **exécuter l’agent**, puis cliquez sur **Modifier**.  
  
6.  Dans la **tâche Exécuter l’agent - propriétés de l’étape** boîte de dialogue Modifier la **commande** champ.  
  
7.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
### Pour afficher et modifier les paramètres de ligne de commande de l'Agent d'instantané, de l'Agent de lecture du journal et de l'Agent de lecture de la file d'attente à partir du Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Droit d’un agent dans la grille, puis cliquez sur **propriétés**.  
  
4.  Sur le **étapes** page de le **Propriétés du travail - \< travail>** boîte de dialogue, sélectionnez l’étape **exécuter l’agent**, puis cliquez sur **Modifier**.  
  
5.  Dans la **tâche Exécuter l’agent - propriétés de l’étape** boîte de dialogue Modifier la **commande** champ.  
  
6.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
## Voir aussi  
 [Administration de l'Agent de réplication](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Concepts des exécutables de l'agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Présentation des Agents de réplication](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  