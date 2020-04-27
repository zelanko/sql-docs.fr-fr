---
title: Synchroniser un abonnement par extraction | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], synchronizing
- synchronization [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
ms.assetid: 3ca24b23-fdc3-408e-8208-a2ace48fc8e3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c8a7a607221599d599438352eab5add1cc94e5d7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63186230"
---
# <a name="synchronize-a-pull-subscription"></a>Synchroniser un abonnement par extraction
  Cette rubrique explique comment synchroniser un abonnement par extraction de données (pull) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], d' [agents de réplication](agents/replication-agents-overview.md)ou d'objets RMO (Replication Management Objects).  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Les abonnements sont synchronisés par l'Agent de distribution (pour la réplication transactionnelle et d'instantané) ou l'Agent de fusion (pour la réplication de fusion). Les agents peuvent s'exécuter en continu, à la demande ou selon une planification. Pour plus d’informations sur la spécification de planifications de synchronisation, consultez [Spécifier des planifications de synchronisation](specify-synchronization-schedules.md).  
  
 Synchronisez un abonnement à la demande à partir du dossier **Publications locales** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-synchronize-a-pull-subscription-on-demand-in-management-studio"></a>Pour synchroniser à la demande un abonnement par extraction de données dans Management Studio  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Cliquez avec le bouton droit sur l'abonnement à synchroniser, puis cliquez sur **Afficher l'état de synchronisation**.  
  
4.  Dans la boîte de dialogue **Afficher l’état de synchronisation - \<Abonné> : \<Base_de_données_Abonnement>**, cliquez sur **Démarrer**. Lorsque la synchronisation est terminée, le message **Synchronisation terminée** s'affiche.  
  
5.  Cliquez sur **Fermer**.  
  
##  <a name="replication-agents"></a><a name="ReplProg"></a>Agents de réplication  
 Les abonnements par extraction de données (pull) peuvent être synchronisés par le biais de la programmation et à la demande en appelant le fichier exécutable de l'Agent de réplication approprié à partir de l'invite de commandes. Le fichier exécutable de l'Agent de réplication qui est appelé dépend du type de publication à laquelle l'abonnement par extraction de données (pull) appartient. Pour plus d'informations, voir [Replication Agents](agents/replication-agents-overview.md).  
  
> [!NOTE]  
>  Les Agents de réplication se connectent au serveur local au moyen des informations d'identification d'authentification Windows de l'utilisateur qui a démarré l'agent à partir de l'invite de commandes. Ces informations d'identification Windows sont également utilisées lors de la connexion à des serveurs distants au moyen de l'authentification intégrée Windows.  
  
#### <a name="to-start-the-distribution-agent-from-the-command-prompt-or-from-a-batch-file"></a>Pour démarrer l'Agent de distribution à partir de l'invite de commandes ou à partir d'un fichier de commandes  
  
1.  À partir de l'invite de commandes ou dans un fichier de commandes, démarrez l' [Agent de distribution de réplication](agents/replication-distribution-agent.md) en exécutant **distrib.exe**et en spécifiant les arguments suivant sur la ligne de commande :  
  
    -   **-Serveur de publication**  
  
    -   **-PublisherDB**  
  
    -   **-Serveur de distribution**  
  
    -   **-DistributorSecurityMode** = **1**  
  
    -   **-Abonné**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriberSecurityMode** = **1**  
  
    -   **-SubscriptionType** = **1**  
  
     Si vous utilisez l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez également spécifier les arguments suivants :  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode** = **0**  
  
#### <a name="to-start-the-merge-agent-from-the-command-prompt-or-from-a-batch-file"></a>Pour démarrer l'Agent de fusion à partir de l'invite de commandes ou à partir d'un fichier de commandes  
  
1.  À partir de l'invite de commandes ou dans un fichier de commandes, démarrez l' [Agent de fusion de réplication](agents/replication-merge-agent.md) en exécutant **replmerg.exe**et en spécifiant les arguments suivant sur la ligne de commande :  
  
    -   **-Serveur de publication**  
  
    -   **-PublisherDB**  
  
    -   **-PublisherSecurityMode** = **1**  
  
    -   **-Publication**  
  
    -   **-Serveur de distribution**  
  
    -   **-DistributorSecurityMode** = **1**  
  
    -   **-Abonné**  
  
    -   **-SubscriberSecurityMode** = **1**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType** = **1**  
  
     Si vous utilisez l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez également spécifier les arguments suivants :  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode** = **0**  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> Exemples (Agents de réplication)  
 L'exemple suivant démarre l'Agent de distribution pour synchroniser un abonnement par extraction de données (pull). Toutes les connexions sont effectuées au moyen de l'authentification Windows.  
  
 [!code-sql[HowTo#bat_synctranpullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/synctranpullsub_10.bat)]  
  
 L'exemple suivant démarre l'Agent de fusion pour synchroniser un abonnement par extraction de données (pull). Toutes les connexions sont effectuées au moyen de l'authentification Windows.  
  
 [!code-sql[HowTo#bat_syncmergepullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/syncmergepullsub_10.bat)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez synchroniser des abonnements par extraction de données (pull) au moyen d'objets RMO (Replication Management Objects) et d'un accès par code managé aux fonctionnalités de l'Agent de réplication. Les classes que vous utilisez pour synchroniser un abonnement par extraction de données (pull) sont fonction du type de publication à laquelle l'abonnement appartient.  
  
> [!NOTE]  
>  Si vous voulez démarrer une synchronisation qui s'exécute de façon autonome sans affecter votre application, démarrez l'agent en mode asynchrone. Toutefois, si vous voulez analyser le résultat de la synchronisation et recevoir des rappels à partir de l'agent au cours du processus de synchronisation (par exemple, pour afficher une barre de progression), démarrez l'agent en mode synchrone. Pour Abonnés [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] , vous devez démarrer l’agent en mode synchrone.  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Pour synchroniser un abonnement par extraction vers une publication d'instantané ou transactionnelle  
  
1.  Créez une connexion à l'Abonné en utilisant la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.TransPullSubscription> et définissez les propriétés suivantes :  
  
    -   Le nom de la base de données d'abonnement pour <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Le nom de la publication à laquelle l'abonnement appartient pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   le nom de la base de données de publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>;  
  
    -   Le nom du serveur de publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   La connexion créée à l'étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> pour obtenir les propriétés d'abonnement restantes. Si cette méthode retourne `false`, vérifiez que l'abonnement existe.  
  
4.  Démarrez l'Agent de distribution sur l'Abonné de l'une des façons suivantes :  
  
    -   Appelez la méthode <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> sur l'instance de <xref:Microsoft.SqlServer.Replication.TransPullSubscription> obtenue à l'étape 2. Cette méthode démarre l'Agent de distribution en mode asynchrone et votre application récupère immédiatement le contrôle pendant l'exécution du travail de l'agent. Vous ne pouvez pas appeler cette méthode pour les Abonnés [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] ou si l'abonnement a été créé avec la valeur `false` pour <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (la valeur par défaut).  
  
    -   Obtenez une instance de la classe <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> à partir de la propriété <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> et appelez la méthode <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> . Cette méthode démarre l'agent en mode synchrone, et le travail d'agent en cours d'exécution conserve le contrôle. Au cours de l'exécution synchrone, vous pouvez gérer l'événement <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> pendant que l'agent est en cours d'exécution.  
  
        > [!NOTE]  
        >  Si vous avez spécifié la valeur `false` pour <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (valeur par défaut) lorsque vous avez créé l’abonnement par extraction, vous devez <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A>également <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A>spécifier, et éventuellement <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> , <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> et parce que les métadonnées liées au travail de l’agent pour l’abonnement ne sont pas disponibles dans [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-merge-publication"></a>Pour synchroniser un abonnement par extraction de données (pull) vers une publication de fusion  
  
1.  Créez une connexion à l'Abonné en utilisant la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.MergePullSubscription> et définissez les propriétés suivantes :  
  
    -   Le nom de la base de données d'abonnement pour <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Le nom de la publication à laquelle l'abonnement appartient pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Le nom de la base de données publiée pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Le nom du serveur de publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   La connexion créée à l'étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> pour obtenir les propriétés d'abonnement restantes. Si cette méthode retourne `false`, vérifiez que l'abonnement existe.  
  
4.  Démarrez l'Agent de fusion sur l'Abonné de l'une des façons suivantes :  
  
    -   Appelez la méthode <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> sur l'instance de <xref:Microsoft.SqlServer.Replication.MergePullSubscription> obtenue à l'étape 2. Cette méthode démarre l'Agent de fusion en mode asynchrone et votre application récupère immédiatement le contrôle pendant l'exécution du travail de l'agent. Vous ne pouvez pas appeler cette méthode pour les Abonnés [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] ou si l'abonnement a été créé avec la valeur `false` pour <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (la valeur par défaut).  
  
    -   Obtenez une instance de la classe <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> à partir de la propriété <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> et appelez la méthode <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> . Cette méthode démarre l'Agent de fusion en mode synchrone, et le travail d'agent en cours d'exécution conserve le contrôle. Au cours de l'exécution synchrone, vous pouvez gérer l'événement <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> pendant que l'agent est en cours d'exécution.  
  
        > [!NOTE]  
        >  Si vous avez spécifié la valeur `false` pour <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (valeur par défaut) lorsque vous avez créé l’abonnement par extraction, vous devez <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A>également <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A>spécifier <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A>,, et <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A>, éventuellement <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A>, et <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> parce que les métadonnées associées au travail de l’agent pour l’abonnement ne sont pas disponibles dans [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple synchronise un abonnement par envoi de données (pull) vers une publication transactionnelle, où l'agent est démarré en mode asynchrone au moyen du travail d'agent.  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub_withjob)]  
  
 Cet exemple synchronise un abonnement par envoi de données (pull) vers une publication transactionnelle, où l'agent est démarré en mode synchrone.  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub)]  
  
 Cet exemple synchronise un abonnement par envoi de données (pull) vers une publication de fusion, où l'agent est démarré en mode asynchrone au moyen du travail d'agent.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_withjob)]  
  
 Cet exemple synchronise un abonnement par envoi de données (pull) vers une publication de fusion, où l'agent est démarré en mode synchrone.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub)]  
  
 Cet exemple synchronise un abonnement par extraction de données (pull) vers une publication de fusion au moyen de la synchronisation Web. Dans la mesure où l'abonnement a été créé sans le travail d'agent et les métadonnées d'abonnement associées, l'agent doit être démarré en mode synchrone et des informations d'abonnement supplémentaires sont fournies.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_NoJobWebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_nojobwebsync)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_NoJobWebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_nojobwebsync)]  
  
## <a name="see-also"></a>Voir aussi  
 [Synchroniser les données](synchronize-data.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Méthodes préconisées en matière de sécurité de réplication](security/replication-security-best-practices.md)  
  
  
