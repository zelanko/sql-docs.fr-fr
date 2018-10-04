---
title: Afficher et modifier les paramètres d’invite de commandes de l’Agent de réplication (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: efac904be2e062cc2c3ebdbbd32a09d57294de4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155069"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a>Afficher et modifier des paramètres d'invite de commandes d'un Agent de réplication (SQL Server Management Studio)
  Les Agents de réplication sont des fichiers exécutables qui acceptent des paramètres de ligne de commande. Par défaut, les agents s’exécutent dans des étapes de travail de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, et ces paramètres peuvent être affichés et modifiés à l’aide de la boîte de dialogue **Propriétés du travail - \<travail>**. Cette boîte de dialogue est disponible dans le dossier **Travaux** de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et sous l'onglet **Agents** du moniteur de réplication. Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](../monitor/start-the-replication-monitor.md).  
  
> [!NOTE]  
>  Les modifications apportées aux paramètres prennent effet au prochain démarrage de l'Agent. Si l'Agent fonctionne en continu, vous devez l'arrêter, puis le redémarrer.  
  
 Bien que les paramètres puissent être modifiés directement, il est plus courant de les modifier dans un profil d'Agent. Pour plus d'informations, voir [Replication Agent Profiles](replication-agent-profiles.md).  
  
 Si vous accédez à des travaux d'Agent à partir du dossier **Travaux** , utilisez la table ci-dessous pour déterminer le nom du travail d'Agent et les paramètres disponibles pour chaque Agent.  
  
|Agent|Nom du travail|Pour obtenir une liste des paramètres, voir…|  
|-----------|--------------|------------------------------------|  
|Agent d'instantané|**\<serveur_publication>-\<base_de_données_publication>-\<publication>-\<entier>**|[Replication Snapshot Agent](replication-snapshot-agent.md)|  
|Agent d'instantané pour une partition de publication de fusion|**Dyn_\<serveur_publication>-\<base_de_données_publication>-\<publication>-\<GUID>**|[Replication Snapshot Agent](replication-snapshot-agent.md)|  
|l'Agent de lecture du journal ;|**\<serveur_publication>-\<serveur_publication>-\<entier>**|[Agent de lecture du journal des réplications](replication-log-reader-agent.md)|  
|Agent de fusion pour les abonnements extraits|**\<serveur_publication>-\<base_de_données_publication>-\<publication>-\<abonné>-\<base_de_données_abonnement>-\<entier>**|[Agent de fusion de réplication](replication-merge-agent.md)|  
|Agent de fusion pour abonnements par envoi de données (push)|**\<serveur_publication>-\<base_de_données_publication>-\<publication>-\<abonné>-\<entier>**|[Agent de fusion de réplication](replication-merge-agent.md)|  
|Agent de distribution pour abonnements par envoi de données (push)|**\<Serveur_Publication>-\<Base_de_données_Publication>-\<Publication>-\<Abonné>-\<entier>** <sup>1</sup>|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de distribution pour abonnements par extraction de données (pull)|**\<Serveur_Publication>-\<Base_de_données_Publication>-\<Publication>-\<Abonné>-\<Base_de_données_Abonnement>-\<GUID>** <sup>2</sup>|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de distribution pour les abonnements par envoi de données aux Abonnés non SQL Server|**\<ServeurPublication>-\<BasededonnéesPublication>-\<Publication>-\<Abonné>-\<entier>**|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Agent de lecture de la file d'attente|**[\<base_de_données_distribution>].\<entier>**|[Agent de lecture de la file d’attente de réplication](replication-queue-reader-agent.md)|  
  
 <sup>1</sup> Pour les abonnements par émission de données aux publications Oracle, il s’agit de **\<Serveur_Publication>-\<Serveur_Publication**> au lieu de **\<Serveur_Publication>-\<Base_de_données_Publication>**  
  
 <sup>2</sup> Pour les abonnements par extraction aux publications Oracle, il s’agit de **\<Serveur_Publication>-\<Base_de_données_Distribution**> au lieu de **\<Serveur_Publication>-\<Base_de_données_Publication>**  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent de réplication à partir de Management Studio  
  
1.  Connectez-vous à l'ordinateur approprié dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur :  
  
    -   Pour l'Agent de distribution et l'Agent de fusion pour les abonnements par extraction de données, connectez-vous à l'Abonné.  
  
    -   Pour tous les autres agents, connectez-vous au serveur de distribution.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez avec le bouton droit sur un travail, puis sélectionnez **Propriétés**.  
  
4.  Dans la page **Étapes** de la boîte de dialogue **Propriétés du travail - \<travail>**, sélectionnez l’étape **Exécution de l’Agent**, puis cliquez sur **Modifier**.  
  
5.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
6.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent de distribution et de l'Agent de fusion à partir du Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
3.  Cliquez avec le bouton droit sur un abonnement, puis cliquez sur **Afficher les détails**.  
  
4.  Dans le **abonnement \< SubscriptionName >** fenêtre, cliquez sur **Action**, puis cliquez sur  **\<Nom_agent > Propriétés du travail**.  
  
5.  Dans la page **Étapes** de la boîte de dialogue **Propriétés du travail - \<travail>**, sélectionnez l’étape **Exécution de l’Agent**, puis cliquez sur **Modifier**.  
  
6.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
7.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a>Pour afficher et modifier les paramètres de ligne de commande de l'Agent d'instantané, de l'Agent de lecture du journal et de l'Agent de lecture de la file d'attente à partir du Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez avec le bouton droit sur un Agent dans la grille puis cliquez sur **Propriétés**.  
  
4.  Dans la page **Étapes** de la boîte de dialogue **Propriétés du travail - \<travail>**, sélectionnez l’étape **Exécution de l’Agent**, puis cliquez sur **Modifier**.  
  
5.  Dans la boîte de dialogue **Propriétés de l'étape du travail - Exécution de l'Agent** , modifiez le champ **Commande** .  
  
6.  Cliquez sur **OK** dans les deux boîtes de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de l’Agent de réplication](replication-agent-administration.md)   
 [Concepts des exécutables de l’Agent de réplication](../concepts/replication-agent-executables-concepts.md)   
 [Replication Agents Overview](replication-agents-overview.md)  
  
  
