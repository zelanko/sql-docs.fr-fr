---
title: Afficher et modifier les paramètres d’invite de commandes de l’agent de réplication (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e64551075920f2f08bf84fe22086c06387b4439a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068750"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a>Afficher et modifier des paramètres d'invite de commandes d'un Agent de réplication (SQL Server Management Studio)
  Les Agents de réplication sont des fichiers exécutables qui acceptent des paramètres de ligne de commande. Par défaut, les agents s’exécutent sous [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les étapes de travail de l’agent. par conséquent, ces paramètres peuvent être affichés et modifiés à l’aide de la boîte **de dialogue Propriétés du travail- \<Job> ** . Cette boîte de dialogue est disponible dans le dossier **Travaux** de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et sous l'onglet **Agents** du moniteur de réplication. Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](../monitor/start-the-replication-monitor.md).  
  
> [!NOTE]  
>  Les modifications apportées aux paramètres prennent effet au prochain démarrage de l'Agent. Si l'Agent fonctionne en continu, vous devez l'arrêter, puis le redémarrer.  
  
 Bien que les paramètres puissent être modifiés directement, il est plus courant de les modifier dans un profil d'Agent. Pour plus d'informations, voir [Replication Agent Profiles](replication-agent-profiles.md).  
  
 Si vous accédez à des travaux d'Agent à partir du dossier **Travaux** , utilisez la table ci-dessous pour déterminer le nom du travail d'Agent et les paramètres disponibles pour chaque Agent.  
  
|Agent|Nom du travail|Pour obtenir une liste de paramètres, consultez...|  
|-----------|--------------|------------------------------------|  
|Agent d'instantané|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<integer>**|[Replication Snapshot Agent](replication-snapshot-agent.md)|  
|Agent d'instantané pour une partition de publication de fusion|**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**|[Replication Snapshot Agent](replication-snapshot-agent.md)|  
|l'Agent de lecture du journal ;|**\<Publisher>-\<PublicationDatabase>-\<integer>**|[Agent de lecture du journal des réplications](replication-log-reader-agent.md)|  
|Agent de fusion pour les abonnements extraits|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|[Replication Merge Agent](replication-merge-agent.md)|  
|Agent de fusion pour abonnements par envoi de données (push)|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[Replication Merge Agent](replication-merge-agent.md)|  
|Agent de distribution pour abonnements par envoi de données (push)|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**<sup>1</sup>|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de distribution pour abonnements par extraction de données (pull)|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>**<sup>2</sup>|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de distribution pour les abonnements par envoi de données aux Abonnés non SQL Server|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de lecture de la file d'attente|**[\<Distributor>].\<integer>**|[Agent de lecture de la file d’attente de réplication](replication-queue-reader-agent.md)|  
  
 <sup>1</sup> pour les abonnements par envoi de notification aux publications Oracle, il s’agit de * * \<Publisher> - \<Publisher**> plutôt que**\<Publisher>-\<PublicationDatabase>**  
  
 <sup>2</sup> pour les abonnements par extraction aux publications Oracle, il s’agit de * * \<Publisher> - \<DistributionDatabase**> plutôt que**\<Publisher>-\<PublicationDatabase>**  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent de réplication à partir de Management Studio  
  
1.  Connectez-vous à l'ordinateur approprié dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur :  
  
    -   Pour l'Agent de distribution et l'Agent de fusion pour les abonnements par extraction de données, connectez-vous à l'Abonné.  
  
    -   Pour tous les autres agents, connectez-vous au serveur de distribution.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez avec le bouton droit sur un travail, puis sélectionnez **Propriétés**.  
  
4.  Sur la page **étapes** de la boîte de dialogue **Propriétés du travail- \<Job> ** , sélectionnez l’étape **exécuter l’agent**, puis cliquez sur **modifier**.  
  
5.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
6.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent de distribution et de l'Agent de fusion à partir du Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
3.  Cliquez avec le bouton droit sur un abonnement, puis cliquez sur **Afficher les détails**.  
  
4.  Dans la fenêtre d' **abonnement \< SubscriptionName> ** , cliquez sur **action**, puis sur ** \<AgentName> Propriétés du travail**.  
  
5.  Sur la page **étapes** de la boîte de dialogue **Propriétés du travail- \<Job> ** , sélectionnez l’étape **exécuter l’agent**, puis cliquez sur **modifier**.  
  
6.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
7.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent d'instantané, de l'Agent de lecture du journal et de l'Agent de lecture de la file d'attente à partir du Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez avec le bouton droit sur un Agent dans la grille puis cliquez sur **Propriétés**.  
  
4.  Sur la page **étapes** de la boîte de dialogue **Propriétés du travail- \<Job> ** , sélectionnez l’étape **exécuter l’agent**, puis cliquez sur **modifier**.  
  
5.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
6.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de l’agent de réplication](replication-agent-administration.md)   
 [Concepts des exécutables de l’agent de réplication](../concepts/replication-agent-executables-concepts.md)   
 [Présentation des Agents de réplication](replication-agents-overview.md)  
  
  
