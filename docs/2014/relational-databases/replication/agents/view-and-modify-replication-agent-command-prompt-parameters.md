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
manager: craigg
ms.openlocfilehash: 6e4327de10dd03b3ff8cf034ade64391d18d2a86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63192897"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a>Afficher et modifier des paramètres d'invite de commandes d'un Agent de réplication (SQL Server Management Studio)
  Les Agents de réplication sont des fichiers exécutables qui acceptent des paramètres de ligne de commande. Par défaut, les agents s’exécutent dans les étapes de travail de l’Agent [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ; ces paramètres peuvent être examinés et modifiés depuis la boîte de dialogue **Propriétés du travail - \<Travail>** . Cette boîte de dialogue est disponible dans le dossier **Travaux** de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et sous l'onglet **Agents** du moniteur de réplication. Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](../monitor/start-the-replication-monitor.md).  
  
> [!NOTE]  
>  Les modifications apportées aux paramètres prennent effet au prochain démarrage de l'Agent. Si l'Agent fonctionne en continu, vous devez l'arrêter, puis le redémarrer.  
  
 Bien que les paramètres puissent être modifiés directement, il est plus courant de les modifier dans un profil d'Agent. Pour plus d'informations, voir [Replication Agent Profiles](replication-agent-profiles.md).  
  
 Si vous accédez à des travaux d'Agent à partir du dossier **Travaux** , utilisez la table ci-dessous pour déterminer le nom du travail d'Agent et les paramètres disponibles pour chaque Agent.  
  
|Agent|Nom du travail|Pour obtenir une liste de paramètres, consultez...|  
|-----------|--------------|------------------------------------|  
|Agent d'instantané|**\<ServeurPublication>-\<BasededonnéesPublication>-\<Publication>-\<entier>**|[Replication Snapshot Agent](replication-snapshot-agent.md)|  
|Agent d'instantané pour une partition de publication de fusion|**Dyn_\<ServeurPublication>-\<BasededonnéesPublication>-\<Publication>-\<GUID>**|[Replication Snapshot Agent](replication-snapshot-agent.md)|  
|l'Agent de lecture du journal ;|**\<ServeurPublication>-\<BasededonnéesPublication>-\<entier>**|[Agent de lecture du journal des réplications](replication-log-reader-agent.md)|  
|Agent de fusion pour les abonnements extraits|**\<Serveur_Publication>-\<Base_de_données_Publication>-\<Publication>-\<Abonné>-\<Base_de_données_Abonnement>-\<entier>**|[Replication Merge Agent](replication-merge-agent.md)|  
|Agent de fusion pour abonnements par envoi de données (push)|**\<ServeurPublication>-\<BasededonnéesPublication>-\<Publication>-\<Abonné>-\<entier>**|[Replication Merge Agent](replication-merge-agent.md)|  
|Agent de distribution pour abonnements par envoi de données (push)|**\<\<\<Éditeur>-PublicationDatabase>-publication>-Subscriber\<>-Integer>1 \<** <sup></sup>|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de distribution pour abonnements par extraction de données (pull)|**\<\<\<\<Éditeur>-PublicationDatabase>-publication>-Subscriber>-SubscriptionDatabase\<>-GUID>2 \<** <sup></sup>|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de distribution pour les abonnements par envoi de données aux Abonnés non SQL Server|**\<ServeurPublication>-\<BasededonnéesPublication>-\<Publication>-\<Abonné>-\<entier>**|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de lecture de la file d'attente|**[\<Distributeur>].\<entier>**|[Agent de lecture de la file d’attente de réplication](replication-queue-reader-agent.md)|  
  
 <sup>1</sup> pour les abonnements par envoi de notification aux publications Oracle, il s’agit ** \<de Publisher>-\<Publisher**> plutôt que ** \<Publisher>-\<PublicationDatabase>**  
  
 <sup>2</sup> pour les abonnements par extraction aux publications Oracle, il s’agit ** \<du serveur de publication>-\<DistributionDatabase**> plutôt que ** \<de l’éditeur>\<-PublicationDatabase>**  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent de réplication à partir de Management Studio  
  
1.  Connectez-vous à l'ordinateur approprié dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur :  
  
    -   Pour l'Agent de distribution et l'Agent de fusion pour les abonnements par extraction de données, connectez-vous à l'Abonné.  
  
    -   Pour tous les autres agents, connectez-vous au serveur de distribution.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez avec le bouton droit sur un travail, puis sélectionnez **Propriétés**.  
  
4.  Dans la page **Étapes** de la boîte de dialogue **Propriétés du travail - \<travail>** , sélectionnez l’étape **Exécution de l’Agent**, puis cliquez sur **Modifier**.  
  
5.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
6.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent de distribution et de l'Agent de fusion à partir du Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
3.  Cliquez avec le bouton droit sur un abonnement, puis cliquez sur **Afficher les détails**.  
  
4.  Dans la **fenêtre \<>d’abonnement SubscriptionName** , cliquez sur **action**, puis sur ** \<AgentName> propriétés du travail**.  
  
5.  Dans la page **Étapes** de la boîte de dialogue **Propriétés du travail - \<travail>** , sélectionnez l’étape **Exécution de l’Agent**, puis cliquez sur **Modifier**.  
  
6.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
7.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent d'instantané, de l'Agent de lecture du journal et de l'Agent de lecture de la file d'attente à partir du Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez avec le bouton droit sur un Agent dans la grille puis cliquez sur **Propriétés**.  
  
4.  Dans la page **Étapes** de la boîte de dialogue **Propriétés du travail - \<travail>** , sélectionnez l’étape **Exécution de l’Agent**, puis cliquez sur **Modifier**.  
  
5.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
6.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de l’Agent de réplication](replication-agent-administration.md)   
 [Concepts des exécutables de l’Agent de réplication](../concepts/replication-agent-executables-concepts.md)   
 [Présentation des Agents de réplication](replication-agents-overview.md)  
  
  
