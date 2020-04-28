---
title: Créer un abonnement par extraction | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], creating
- merge replication subscribing [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 41d1886d-59c9-41fc-9bd6-a59b40e0af6e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f8868957d7c479de3a51a599deed42c34d6676eb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62721591"
---
# <a name="create-a-pull-subscription"></a>Créer un abonnement par extraction de données (pull)
  Cette rubrique explique comment créer un abonnement par extraction de données (pull) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou d'objets RMO (Replication Management Objects).  
  
 La définition d'un abonnement par extraction de données (pull) pour la réplication P2P est possible au moyen d'un script, mais n'est pas disponible via l'assistant.  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Créer un abonnement par extraction de données sur le serveur de publication ou sur l'Abonné à l'aide de l'Assistant Nouvel abonnement. Exécutez les étapes de l'Assistant pour :  
  
-   Spécifier le serveur de publication et la publication.  
  
-   Sélectionner l'emplacement d'exécution des Agents de réplication. Pour un abonnement par extraction de données, sélectionnez **Exécuter chaque Agent sur son Abonné (abonnements par extraction de données (pull))** dans la page **Emplacement de l'Agent de distribution** ou dans la page **Emplacement de l'Agent de fusion** , selon le type de publication.  
  
-   Spécifiez des Abonnés et des bases de données d'abonnement.  
  
-   Spécifiez les noms de connexion et mots de passe utilisés pour les connexions établies par les Agents de réplication :  
  
    -   Pour les abonnements aux publications d'instantané et transactionnelles, spécifiez les informations d'identification dans la page **Sécurité de l'Agent de distribution** .  
  
    -   Pour les abonnements aux publications de fusion, spécifiez les informations d'identification dans la page **Sécurité de l'Agent de fusion** .  
  
     Pour plus d’informations sur les autorisations requises par chaque agent, consultez [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md).  
  
-   Spécifiez une planification de la synchronisation et le moment choisi pour initialiser l'Abonné.  
  
-   Spécifiez les autres options pour les publications de fusion : type d'abonnement, valeurs pour le filtrage paramétré, informations pour la synchronisation via HTTPS si la publication est activée pour la synchronisation Web.  
  
-   Spécifiez les autres options pour les publications transactionnelles qui autorisent la mise à jour des abonnements : si les Abonnés doivent valider immédiatement les modifications sur le serveur de publication ou les écrire dans une file d'attente ou encore les informations d'identification utilisées pour la connexion de l'Abonné au serveur de publication.  
  
-   Créez éventuellement un script pour l'abonnement.  
  
#### <a name="to-create-a-pull-subscription-from-the-publisher"></a>Pour créer un abonnement par extraction de données à partir du serveur de publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Cliquez avec le bouton droit sur la publication pour laquelle vous souhaitez créer un ou plusieurs abonnements puis cliquez sur **Nouveaux abonnements**.  
  
4.  Exécutez les étapes de l'Assistant Nouvel abonnement.  
  
#### <a name="to-create-a-pull-subscription-from-the-subscriber"></a>Pour créer un abonnement par extraction de données à partir de l'Abonné  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** .  
  
3.  Cliquez avec le bouton droit sur le dossier **Abonnements locaux** , puis cliquez sur **Nouveaux abonnements**.  
  
4.  Dans la page **Publication** de l’Assistant Nouvel abonnement, sélectionnez **\<Rechercher un serveur de publication SQL>** ou **\<Rechercher un serveur de publication Oracle>** dans la liste déroulante **Serveur de publication**.  
  
5.  Connectez-vous au serveur de publication dans la boîte de dialogue **Se connecter au serveur** .  
  
6.  Sélectionnez une publication dans la page **Publication** .  
  
7.  Exécutez les étapes de l'Assistant Nouvel abonnement.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les abonnements par extraction de données peuvent être créés par programme en utilisant des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'abonnement appartient.  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Pour créer un abonnement par extraction vers une publication d'instantané ou transactionnelle  
  
1.  Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements par extraction en exécutant [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).  
  
    -   Si la valeur de **allow_pull** dans le jeu de résultats est **1**, la publication prend en charge les abonnements par extraction de données.  
  
    -   Si la valeur de **allow_pull** est **0**, exécutez [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), en **allow_pull** spécifiant **@property** allow_pull `true` pour **@value**et pour.  
  
2.  Sur l’Abonné, exécutez [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). **@publisher** Spécifiez **@publication**et. Pour plus d'informations sur la mise à jour des abonnements, consultez [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
3.  Sur l’Abonné, exécutez [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Spécifiez les éléments suivants :  
  
    -   Paramètres **@publisher**, **@publisher_db**et **@publication** .  
  
    -   Les [!INCLUDE[msCoName](../../includes/msconame-md.md)] informations d’identification Windows sous lesquelles l’agent de distribution sur l’abonné s' **@job_login** exécute **@job_password**pour et.  
  
        > [!NOTE]  
        >  Les connexions effectuées à l’aide de l’authentification intégrée Windows utilisent toujours les **@job_login** informations **@job_password**d’identification Windows spécifiées par et. L'Agent de distribution établit toujours la connexion locale à l'Abonné à l'aide de l'authentification intégrée Windows. Par défaut, l'Agent se connecte au serveur de distribution à l'aide de ces informations.  
  
    -   (Facultatif) La valeur **0** pour **@distributor_security_mode** et les informations de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour **@distributor_login** et **@distributor_password**, si vous devez utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lors de la connexion au serveur de distribution.  
  
    -   Planification du travail de l'Agent de distribution pour cet abonnement. Pour plus d’informations, consultez [Spécifier des planifications de synchronisation](specify-synchronization-schedules.md).  
  
4.  Sur le serveur de publication, exécutez [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) pour inscrire l’abonnement par extraction. **@publication**Spécifiez **@subscriber**, et **@destination_db**. Affectez la valeur **pull** à **@subscription_type**.  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication"></a>Pour créer un abonnement par extraction de données (pull) vers une publication de fusion  
  
1.  Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements par extraction en exécutant [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql).  
  
    -   Si la valeur de **allow_pull** dans le jeu de résultats est **1**, la publication prend en charge les abonnements par extraction de données.  
  
    -   Si la valeur de **allow_pull** est **0**, exécutez [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), en **allow_pull** spécifiant **@property** allow_pull `true` pour **@value**et pour.  
  
2.  Sur l’Abonné, exécutez [sp_addmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql). **@publisher**Spécifiez **@publisher_db**, **@publication**, et les paramètres suivants :  
  
    -   **@subscriber_type**-Spécifiez **local** pour un abonnement client et **Global** pour un abonnement serveur.  
  
    -   **@subscription_priority**-Spécifiez une priorité pour l’abonnement (**0,00** à **99,99**). Ceci est requis uniquement pour un abonnement serveur.  
  
         Pour plus d’informations, consultez [Détection et résolution avancées des conflits de réplication de fusion](merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  Sur l’Abonné, exécutez [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql). Spécifiez les paramètres suivants :  
  
    -   **@publisher**, **@publisher_db**et **@publication**.  
  
    -   Les informations d’identification Windows sous lesquelles l’Agent de fusion sur l’abonné s' **@job_login** exécute **@job_password**pour et.  
  
        > [!NOTE]  
        >  Les connexions effectuées à l’aide de l’authentification intégrée Windows utilisent toujours les **@job_login** informations **@job_password**d’identification Windows spécifiées par et. L'Agent de fusion crée toujours la connexion locale à l'abonné à l'aide de l'authentification intégrée Windows. Par défaut, l'Agent se connecte au serveur de distribution et au serveur de publication à l'aide de ces informations.  
  
    -   (Facultatif) La valeur **0** pour **@distributor_security_mode** et les informations de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour **@distributor_login** et **@distributor_password**, si vous devez utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lors de la connexion au serveur de distribution.  
  
    -   (Facultatif) La valeur **0** pour **@publisher_security_mode** et les informations de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour **@publisher_login** et **@publisher_password**, si vous devez utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lors de la connexion au serveur de publication.  
  
    -   Une planification du travail de l'Agent de fusion pour cet abonnement. Pour plus d'informations, voir [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
4.  Sur le serveur de publication, exécutez [sp_addmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql). **@publication**Spécifiez **@subscriber**, **@subscriber_db**, et la valeur **pull** pour **@subscription_type**. L'abonnement par extraction est inscrit.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Exemples (Transact-SQL)  
 L'exemple suivant crée un abonnement par extraction de données vers une publication transactionnelle. Le premier traitement est exécuté sur l'abonné, et le second sur le serveur de publication. Les valeurs de connexion et le mot de passe sont fournis lors de l'exécution à l'aide des variables de script sqlcmd.  
  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpullsub.sql#sp_addtranpullsubscriptionagent)]  
  
 [!code-sql[HowTo#sp_addtranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpullsub.sql#sp_addtranpullsubscription)]  
  
 L'exemple suivant crée un abonnement par extraction de données vers une publication de fusion. Le premier traitement est exécuté sur l'abonné, et le second sur le serveur de publication. Les valeurs de connexion et le mot de passe sont fournis lors de l'exécution à l'aide des variables de script **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsub.sql#sp_addmergepullsubscriptionagent)]  
  
 [!code-sql[HowTo#sp_addmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsub.sql#sp_addmergepullsubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Les classes RMO utilisées pour créer un abonnement par extraction de données (pull) sont fonction du type de publication à laquelle l'abonnement appartient.  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Pour créer un abonnement par extraction vers une publication d'instantané ou transactionnelle  
  
1.  Créez une connexion à l'Abonné et au serveur de publication à l'aide de la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.TransPublication> en utilisant la connexion au serveur de publication de l'étape 1. Spécifiez <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> et <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Si cette méthode retourne `false`, les propriétés spécifiées à l'étape 2 sont incorrectes ou la publication n'existe pas sur le serveur.  
  
4.  Effectuez une opération AND logique au niveau du bit (`&` dans Visual C# et `And` dans Visual Basic) entre la propriété <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> et <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Si le résultat est <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, appliquez à<xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> le résutat d'une opération OR logique au niveau du bit (`|` dans Visual C# et `Or` dans Visual Basic) entre <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> et <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Ensuite, appelez <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> pour activer les abonnements par extraction de données (pull).  
  
5.  Si la base de données d'abonnements n'existe pas, créez-la en utilisant la classe <xref:Microsoft.SqlServer.Management.Smo.Database> . Pour plus d’informations, consultez [Création, modification et suppression de bases de données](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.TransPullSubscription>.  
  
7.  Définissez les propriétés suivantes des abonnements :  
  
    -   La <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l'Abonné créée à l'étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Nom de la base de données d'abonnements pour <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Nom du serveur de publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   Nom de la base de données de publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Nom de la publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Les champs <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> et <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> ou <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> de <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> pour fournir les informations d'identification pour le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent de distribution s'exécute sur l'Abonné. Ce compte est utilisé pour effectuer des connexions locales à l'Abonné et pour effectuer des connexions distantes au moyen de l'authentification Windows.  
  
        > [!NOTE]  
        >  La configuration de <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> lorsqu'un abonnement est créé par un membre du rôle serveur fixe `sysadmin` n'est pas nécessaire, mais elle est néanmoins recommandée. Dans ce cas, l'Agent va emprunter l'identité du compte de l'Agent SQL Server. Pour plus d’informations, voir [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
    -   (Facultatif) La valeur `true` pour <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> afin de créer un travail d'agent qui sera utilisé pour synchroniser l'abonnement. Si vous spécifiez `false` (la valeur par défaut), l'abonnement peut uniquement être synchronisé par le biais de la programmation et vous devez spécifier des propriétés supplémentaires de <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> lorsque vous accédez à cet objet à partir de la propriété <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A>. Pour plus d’informations, consultez [Synchroniser un abonnement par extraction (pull)](synchronize-a-pull-subscription.md).  
  
        > [!NOTE]  
        >  SQL Server Agent n’est pas disponible dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Lorsque vous spécifiez la valeur `true` pour les Abonnés Express, le travail d'agent n'est pas créé. Toutefois, certaines métadonnées importantes liées à l'abonnement sont stockées sur l'Abonné.  
  
    -   (Facultatif) Définissez les champs <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> et <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> ou <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> de <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> lorsque vous utilisez l'authentification SQL Server pour vous connecter au serveur de distribution.  
  
8.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> .  
  
9. Au moyen de l'instance de la classe <xref:Microsoft.SqlServer.Replication.TransPublication> de l'étape 2, appelez la méthode <xref:Microsoft.SqlServer.Replication.TransPublication.MakePullSubscriptionWellKnown%2A> pour inscrire l'abonnement par extraction de données (pull) sur le serveur de publication. Si l'abonnement est déjà inscrit dans le Registre, une erreur se produit.  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication"></a>Pour créer un abonnement par extraction de données (pull) vers une publication de fusion  
  
1.  Créez des connexions à la fois à l'Abonné et au serveur de publication au moyen de la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.MergePublication> en utilisant la connexion au serveur de publication de l'étape 1. Spécifiez <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>et <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Si cette méthode retourne `false`, les propriétés spécifiées à l'étape 2 sont incorrectes ou la publication n'existe pas sur le serveur.  
  
4.  Effectuez une opération AND logique au niveau du bit (`&` dans Visual C# et `And` dans Visual Basic) entre la propriété <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> et <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Si le résultat est <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, appliquez à<xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> le résutat d'une opération OR logique au niveau du bit (`|` dans Visual C# et `Or` dans Visual Basic) entre <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> et <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Ensuite, appelez <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> pour activer les abonnements par extraction de données (pull).  
  
5.  Si la base de données d'abonnements n'existe pas, créez-la en utilisant la classe <xref:Microsoft.SqlServer.Management.Smo.Database> . Pour plus d’informations, consultez [Création, modification et suppression de bases de données](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.MergePullSubscription>.  
  
7.  Définissez les propriétés suivantes des abonnements :  
  
    -   La <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l'Abonné créée à l'étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Nom de la base de données d'abonnements pour <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Nom du serveur de publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   Nom de la base de données de publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Nom de la publication pour <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Les champs <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> et <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> ou <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> de <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> pour fournir les informations d'identification pour le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent de fusion s'exécute sur l'Abonné. Ce compte est utilisé pour effectuer des connexions locales à l'Abonné et pour effectuer des connexions distantes au moyen de l'authentification Windows.  
  
        > [!NOTE]  
        >  La configuration de <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> lorsqu'un abonnement est créé par un membre du rôle serveur fixe `sysadmin` n'est pas nécessaire, mais elle est néanmoins recommandée. Dans ce cas, l'Agent va emprunter l'identité du compte de l'Agent SQL Server. Pour plus d’informations, voir [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
    -   (Facultatif) La valeur `true` pour <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> afin de créer un travail d'agent qui sera utilisé pour synchroniser l'abonnement. Si vous spécifiez `false` (la valeur par défaut), l'abonnement peut uniquement être synchronisé par le biais de la programmation et vous devez spécifier des propriétés supplémentaires de <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> lorsque vous accédez à cet objet à partir de la propriété <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A>. Pour plus d’informations, consultez [Synchroniser un abonnement par extraction (pull)](synchronize-a-pull-subscription.md).  
  
    -   (Facultatif) Définissez les champs <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> et <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> ou <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> de <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> lorsque vous utilisez l'authentification SQL Server pour vous connecter au serveur de distribution.  
  
    -   (Facultatif) Définissez les champs <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> et <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> ou <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> de <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> lorsque vous utilisez l'authentification SQL Server pour vous connecter au serveur de publication.  
  
8.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> .  
  
9. Au moyen de l'instance de la classe <xref:Microsoft.SqlServer.Replication.MergePublication> de l'étape 2, appelez la méthode <xref:Microsoft.SqlServer.Replication.MergePublication.MakePullSubscriptionWellKnown%2A> pour inscrire l'abonnement par extraction de données (pull) sur le serveur de publication. Si l'abonnement est déjà inscrit dans le Registre, une erreur se produit.  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> Exemple (RMO)  
 Cet exemple crée un abonnement par extraction de données (pull) vers une publication transactionnelle. Les informations d'identification de compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilisées pour créer le travail d'agent de distribution sont transmises au moment de l'exécution.  
  
 [!code-csharp[HowTo#rmo_CreateTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranpullsub)]  
  
 Cet exemple crée un abonnement par extraction de données (pull) vers une publication de fusion. Les informations d'identification de compte Windows utilisées pour créer le travail d'agent de fusion sont transmises au moment de l'exécution.  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub)]  
  
 Cet exemple crée un abonnement par extraction de données (pull) vers une publication de fusion sans créer de travail d'agent et de métadonnées d'abonnement associés dans [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql). Les informations d'identification de compte Windows utilisées pour créer le travail d'agent de fusion sont transmises au moment de l'exécution.  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub_NoJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub_nojob)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub_NoJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub_nojob)]  
  
 Cet exemple crée un abonnement par envoi de données (pull) vers une publication de fusion qui peut être synchronisée via Internet au moyen de la synchronisation Web. Les informations d'identification de compte Windows utilisées pour créer le travail d'agent de fusion sont transmises au moment de l'exécution. Pour plus d’informations, consultez [Configurer la synchronisation Web](configure-web-synchronization.md).  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub_WebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub_websync)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub_WebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub_websync)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts liés à RMO (Replication Management Objects)](concepts/replication-management-objects-concepts.md)   
 [Afficher et modifier les propriétés d’un abonnement par extraction](view-and-modify-pull-subscription-properties.md)   
 [Configurer la synchronisation web](configure-web-synchronization.md)   
 [S’abonner aux Publications](subscribe-to-publications.md)   
 [Bonnes pratiques en matière de sécurité de la réplication](security/replication-security-best-practices.md)  
  
  
