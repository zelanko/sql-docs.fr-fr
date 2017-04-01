---
title: "Cr&#233;er et appliquer l&#39;instantan&#233; initial | Microsoft Docs"
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
  - "instantanés [réplication SQL Server], création."
  - "réplication d'instantané [SQL Server], instantanés initiaux"
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Cr&#233;er et appliquer l&#39;instantan&#233; initial
  Cette rubrique explique comment créer et appliquer l'instantané initial dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des objets RMO (Replication Management Objects). Les publications de fusion qui utilisent des filtres paramétrés nécessitent un instantané en deux parties. Pour plus d'informations, voir [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 **Dans cette rubrique**  
  
-   **Pour créer et appliquer l'instantané initial à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Par défaut, si l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d'exécution, un instantané est généré par l'Agent d'instantané immédiatement après la création d'une publication par l'Assistant Nouvelle publication. Il est ensuite appliqué par défaut par l'Agent de distribution (pour la réplication d'instantané et transactionnelle) ou l'Agent de fusion (pour les abonnements de fusion) pour tous les abonnements. Il est également possible de générer un instantané à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et du Moniteur de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Pour créer un instantané dans Management Studio  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Avec le bouton droit de la publication pour laquelle vous souhaitez créer un instantané, puis cliquez sur **Afficher l’état de l’Agent capture instantanée**.  
  
4.  Dans la **Afficher l’état de l’Agent capture instantanée - \< Publication>** boîte de dialogue, cliquez sur **Démarrer**.  
  
 Lorsque l'Agent d'instantané termine la génération de l'instantané, un message comme celui-ci s'affiche : « [100 %] Un instantané de 17 article(s) a été généré ».  
  
#### Pour créer un instantané dans le Moniteur de réplication  
  
1.  Dans le moniteur de réplication, développez un groupe de serveurs de publication dans le volet gauche, puis développez un serveur de publication.  
  
2.  Avec le bouton droit de la publication pour laquelle vous souhaitez générer un instantané, puis cliquez sur **Générer l’instantané**.  
  
3.  Pour afficher le statut de l'Agent d'instantané, cliquez sur l'onglet **Agents** . Pour plus d’informations, cliquez sur l’Agent de capture instantanée dans la grille, puis cliquez sur **Afficher les détails**.  
  
#### Pour appliquer un instantané  
  
1.  Une fois que l'instantané est généré, il est appliqué en synchronisant l'abonnement avec l'Agent de distribution ou l'Agent de fusion :  
  
    -   Si l'Agent est paramétré pour une exécution en continu (par défaut pour la réplication transactionnelle); l'instantané est appliqué automatiquement après avoir été généré.  
  
    -   Si l'Agent est paramétré pour une exécution planifiée, l'instantané est appliqué à la prochaine exécution planifiée de l'Agent.  
  
    -   Si l'Agent est paramétré pour une exécution à la demande, l'instantané est appliqué la prochaine fois que vous exécutez l'Agent.  
  
     Pour plus d’informations sur la synchronisation des abonnements, consultez [synchroniser un abonnement Push](../../relational-databases/replication/synchronize-a-push-subscription.md) et [synchroniser un abonnement extrait](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les instantanés initiaux peuvent être créés par programme en créant et exécutant un travail de l'Agent d'instantané ou en exécutant le fichier exécutable de l'Agent d'instantané à partir d'un fichier de commandes. Une fois qu'un instantané initial a été généré, il est transféré et appliqué sur l'Abonné lorsque l'abonnement est synchronisé pour la première fois. Si vous exécutez l'Agent d'instantané à partir d'une invite de commandes ou d'un fichier de commandes, vous devrez exécuter de nouveau l'agent chaque fois que l'instantané existant deviendra non valide.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
#### Pour créer et exécuter un travail de l'Agent d'instantané pour générer l'instantané initial  
  
1.  Créez une publication d'instantané, transactionnelle ou de fusion. Pour plus d'informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Exécutez [sp_addpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez **@publication** et les paramètres suivants :  
  
    -   **@Job_login, laquelle spécifie** les informations d’identification de l’authentification Windows sous lequel l’Agent de capture instantanée s’exécute sur le serveur de distribution.  
  
    -   **@Job_password**, qui est le mot de passe pour les informations d’identification Windows fournies.  
  
    -   (Facultatif) Une valeur de **0** pour **@publisher_security_mode** Si l’agent doit utiliser l’authentification SQL Server lors de la connexion au serveur de publication. Dans ce cas, vous devez également spécifier les informations de connexion d’authentification SQL Server pour **@publisher_login** et **@publisher_password**.  
  
    -   (Facultatif) Une planification de synchronisation pour le travail de l'Agent d'instantané. Pour plus d'informations, voir [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Ajoutez des articles à la publication. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
4.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_startpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md), en spécifiant la valeur de **@publication** à l’étape 1.  
  
#### Pour exécuter l'Agent d'instantané afin de générer l'instantané initial  
  
1.  Créez une publication d'instantané, transactionnelle ou de fusion. Pour plus d'informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Ajoutez des articles à la publication. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  À partir de l’invite de commandes ou dans un fichier de commandes, démarrez le [Agent de capture instantanée de réplication](../../relational-databases/replication/agents/replication-snapshot-agent.md) en exécutant **snapshot.exe**, en spécifiant les arguments de ligne de commande suivantes :  
  
    -   **-Publication**  
  
    -   **-Publisher**  
  
    -   **-Distributor**  
  
    -   **-PublisherDB**  
  
    -   **-ReplicationType**  
  
     Si vous utilisez l'authentification SQL Server, vous devez également spécifier les arguments suivants :  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple montre comment créer une publication transactionnelle et d’ajouter un travail d’Agent de capture instantanée pour la nouvelle publication (à l’aide de **sqlcmd** variables de script). L'exemple démarre également le travail.  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_1.sql)]  
  
 Cet exemple crée une publication de fusion et ajoute un travail de l’Agent de capture instantanée (à l’aide de **sqlcmd** variables) pour la publication. Cet exemple démarre également le travail.  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_2.sql)]  
  
 Les arguments de ligne de commande suivants démarrent l'Agent d'instantané pour générer l'instantané pour une publication de fusion.  
  
> [!NOTE]  
>  Des sauts de ligne ont été ajoutés pour améliorer la lisibilité. Dans un fichier de commandes, les commandes doivent figurer sur une seule ligne.  
  
```  
  
REM -- Declare variables  
SET Publisher=%InstanceName%  
SET PublicationDB=AdventureWorks2012   
SET Publication=AdvWorksSalesOrdersMerge   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 L'Agent d'instantané génère des instantanés après qu'une publication a été créée. Vous pouvez générer ces instantanés par programme en utilisant les Replication Management Objects et l'accès direct par code managé aux fonctionnalités de l'Agent de réplication. Les objets à utiliser dépendent du type de réplication. L'Agent d'instantané peut être démarré de façon synchrone à l'aide de l'objet <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> ou de façon asynchrone à l'aide du travail de l'agent. Une fois l'instantané initial généré, il est transféré et appliqué sur l'Abonné lorsque l'abonnement est synchronisé pour la première fois. Vous devrez exécuter de nouveau l'agent chaque fois que l'instantané existant ne contiendra plus de données valides à jour. Pour plus d’informations, consultez [mettre à jour des Publications](../../relational-databases/replication/publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez stocker des informations d'identification, utilisez les [Services de chiffrement](http://go.microsoft.com/fwlink/?LinkId=34733) fournis par [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Pour générer l'instantané initial pour une publication transactionnelle ou d'instantané en démarrant le travail de l'Agent d'instantané (asynchrone)  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransPublication> classe. Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour charger les autres propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  Si la valeur de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> est **false**, appelez <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> pour créer le travail de l’agent de capture instantanée pour cette publication.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> méthode pour démarrer le travail de l’agent qui génère l’instantané pour cette publication.  
  
6.  (Facultatif) Lorsque la valeur de <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> est **true**, l’instantané n’est disponible pour les abonnés.  
  
#### Pour générer l'instantané initial pour une publication transactionnelle ou d'instantané en exécutant l'Agent d'instantané (synchrone)  
  
1.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> et définissez les propriétés requises suivantes :  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - nom du serveur de publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - nom de la base de données de publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - nom de la publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - nom du serveur de distribution  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -valeur <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> pour utiliser l’authentification Windows pour se connecter au serveur de publication ou une valeur de <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> et valeurs pour <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> et <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> à utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification lors de la connexion au serveur de publication. L'authentification Windows est recommandée.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -valeur <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> pour utiliser l’authentification Windows pour se connecter au serveur de distribution ou la valeur <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> et valeurs pour <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> et <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> à utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification lors de la connexion au serveur de distribution. L'authentification Windows est recommandée.  
  
2.  Définir une valeur de <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> ou <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> pour <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
#### Pour générer l'instantané initial pour une publication de fusion en démarrant le travail de l'Agent d'instantané (asynchrone)  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe. Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour charger les autres propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  Si la valeur de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> est **false**, appelez <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> pour créer le travail de l’agent de capture instantanée pour cette publication.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> méthode pour démarrer le travail de l’agent qui génère l’instantané pour cette publication.  
  
6.  (Facultatif) Lorsque la valeur de <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> est **true**, l’instantané n’est disponible pour les abonnés.  
  
#### Pour générer l'instantané initial pour une publication de fusion en exécutant l'Agent d'instantané (synchrone)  
  
1.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> et définissez les propriétés requises suivantes :  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - nom du serveur de publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - nom de la base de données de publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - nom de la publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - nom du serveur de distribution  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -valeur <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> pour utiliser l’authentification Windows pour se connecter au serveur de publication ou une valeur de <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> et valeurs pour <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> et <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> à utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification lors de la connexion au serveur de publication. L'authentification Windows est recommandée.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -valeur <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> pour utiliser l’authentification Windows pour se connecter au serveur de distribution ou la valeur <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> et valeurs pour <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> et <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> à utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification lors de la connexion au serveur de distribution. L'authentification Windows est recommandée.  
  
2.  Définir une valeur de <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> pour <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple exécute de façon synchrone l'Agent d'instantané pour générer l'instantané initial pour une publication transactionnelle.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 Cet exemple démarre de façon asynchrone le travail de l'agent pour générer l'instantané initial pour une publication transactionnelle.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)   
 [Créer et appliquer un instantané](../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Concepts liés à Replication Management Objects](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Concepts liés aux procédures stockées système de réplication](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Utiliser sqlcmd avec des variables de script](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  