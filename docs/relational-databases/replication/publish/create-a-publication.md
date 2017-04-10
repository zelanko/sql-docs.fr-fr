---
title: "Cr&#233;er une publication | Microsoft Docs"
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
  - "publications [SQL Server replication], creating"
  - "articles [SQL Server replication], defining"
  - "adding articles"
  - "articles [réplication SQL Server], ajout"
ms.assetid: 52ee6de9-1d58-4cb9-8711-372bddbe7154
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Cr&#233;er une publication
  Cette rubrique explique comment créer une publication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer une publication et définir des articles à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les noms de publication et d’article ne peut pas contenir les caractères suivants : %, \* , [,], |, :, «, ? , ' , \ , / , \< , >. Si vous souhaitez répliquer les objets dans la base de données incluent les caractères suivants, vous devez spécifier un nom d’article différent du nom d’objet dans le **Propriétés de l’Article - \< Article>** boîte de dialogue, qui est disponible depuis le **Articles** page de l’Assistant.  
  
###  <a name="Security"></a> Sécurité  
 Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez stocker des informations d'identification, utilisez les [Services de chiffrement](http://go.microsoft.com/fwlink/?LinkId=34733) fournis par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Créez des publication et définissez des articles avec l'Assistant Nouvelle publication. Après la création d’une publication, afficher et modifier les propriétés de la publication dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur la création d’une publication à partir d’une base de données Oracle, consultez [créer une Publication à partir d’une base de données Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
#### Pour créer une publication et définir des articles  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le **réplication** dossier et avec le bouton droit puis le **Publications locales** dossier.  
  
3.  Cliquez sur **Nouvelle publication**.  
  
4.  Exécutez les pages de l'Assistant Nouvelle publication pour.  
  
    -   Spécifier un serveur de distribution si la distribution n'a pas été configurée sur le serveur. Pour plus d’informations sur la configuration de la distribution, consultez [configurer la publication et Distribution](../../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
         Si vous spécifiez sur la **distributeur** page qui agit comme son propre distributeur (distributeur local) le serveur de publication et le serveur n’est pas configuré comme un serveur de distribution, l’Assistant Nouvelle Publication configure le serveur. Vous spécifierez un dossier d'instantanés par défaut pour le serveur de distribution dans la page **Dossier d'instantanés** . Le dossier d'instantanés correspond à un simple répertoire que vous définissez sous la forme d'un partage ; les agents qui lisent et écrivent dans le dossier doivent disposer des autorisations suffisantes pour pouvoir y accéder. Pour plus d’informations sur la sécurisation du dossier de manière appropriée, consultez [sécuriser le dossier de capture instantanée](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
         Si vous spécifiez qu'un autre serveur doit jouer le rôle de serveur de distribution, vous devez entrer un mot de passe dans la page **Mot de passe d'administration** pour les connexions effectuées du serveur de publication sur le serveur de distribution. Ce mot de passe doit correspondre à celui qui a été spécifié lorsque le serveur de publication a été activé sur le serveur de distribution distant.  
  
         Pour plus d’informations, consultez [configurer la Distribution](../../../relational-databases/replication/configure-distribution.md).  
  
    -   Choisissez une base de données de publication.  
  
    -   Sélectionnez un type de publication. Pour plus d’informations, consultez la page [Types de réplication](../../../relational-databases/replication/types-of-replication.md).  
  
    -   Spécifiez les données et les objets de base de données à publier ; en option, filtrez les colonnes des articles des tables, et définissez des propriétés d'articles.  
  
    -   En option, filtrez les lignes des articles des tables. Pour plus d’informations, consultez [filtrer les données publiées](../../../relational-databases/replication/publish/filter-published-data.md).  
  
    -   Définissez la planification de l'Agent d'instantané.  
  
    -   Spécifiez les informations de connexion sous lesquelles les Agents de réplication suivants s'exécuteront et se connecteront :  
  
         \- Agent de capture instantanée pour toutes les publications.  
  
         \- Agent de lecteur de journal pour toutes les publications transactionnelles.  
  
         \- Agent de lecture de file d’attente pour les publications transactionnelles qui autorisent les abonnements mis à jour.  
  
         Pour plus d'informations, consultez [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) et [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
    -   En option, scriptez la publication. Pour plus d'informations, voir [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
    -   Spécifiez le nom de la publication.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Il est possible de créer des publications par programme en utilisant les procédures stockées de réplication. Les procédures stockées à utiliser dépendent du type de publication à créer.  
  
#### Pour créer une publication d'instantané ou une publication transactionnelle  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_replicationdboption & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Pour activer la publication de la base de données actuelle à l’aide de la réplication transactionnelle ou capture instantanée.  
  
2.  Pour une publication transactionnelle, déterminez si un travail de l'Agent de lecture du journal existe pour la base de données de publication. (Cette étape n'est pas requise pour les publications d'instantané.)  
  
    -   Si un travail de l'Agent de lecture du journal existe pour la base de données de publication, passez à l'étape 3.  
  
    -   Si vous ne savez pas si un travail d’Agent de lecture du journal existe pour une base de données publiée, exécutez [sp_helplogreader_agent & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) sur la base de données de publication de l’éditeur.  
  
    -   Si le jeu de résultats est vide, créez un travail de l'Agent de lecture du journal. Sur le serveur de publication, exécutez [sp_addlogreader_agent & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Spécifiez le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] informations d’identification Windows sous lequel l’agent s’exécute pour **@job_name** et **@password**. Si l’agent doit utiliser l’authentification SQL Server lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informations de connexion pour **@publisher_login** et **@publisher_password**. Passez à l'étape 3.  
  
3.  Sur le serveur de publication, exécutez [sp_addpublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Spécifiez un nom de publication pour **@publication**, et, pour le **@repl_freq** paramètre, spécifiez la valeur **instantané** pour une publication de capture instantanée ou une valeur de **continu** pour une publication transactionnelle. Spécifiez d'autres options de publication éventuelles. Cela définit la publication.  
  
    > [!NOTE]  
    >  Un nom de publication ne doit pas contenir les caractères suivants :  
    >   
    >  % * [ ] | : " ? \ / \< >  
  
4.  Sur le serveur de publication, exécutez [sp_addpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez le nom de publication utilisé à l’étape 3 pour **@publication** et les informations d’identification Windows sous lequel l’Agent de capture instantanée s’exécute pour **@snapshot_job_name** et **@password**. Si l’agent doit utiliser l’authentification SQL Server lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les informations de connexion pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication.  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
5.  Ajoutez des articles à la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Démarrez le travail de l'Agent d'instantané pour générer l'instantané initial pour cette publication. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
#### Pour créer une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_replicationdboption & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Pour activer la publication de la base de données actuelle à l’aide de la réplication de fusion.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Spécifiez le nom de la publication pour **@publication** et d'autres options de publication éventuelles. Cela définit la publication.  
  
    > [!NOTE]  
    >  Un nom de publication ne doit pas contenir les caractères suivants :  
    >   
    >  % * [ ] | : " ? \ / \< >  
  
3.  Sur le serveur de publication, exécutez [sp_addpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez le nom de publication utilisé à l’étape 2 pour **@publication** et les informations d’identification Windows sous lequel l’Agent de capture instantanée s’exécute pour **@snapshot_job_name** et **@password**. Si l’agent doit utiliser l’authentification SQL Server lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les informations de connexion pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication.  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
4.  Ajoutez des articles à la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Démarrez le travail de l'Agent d'instantané pour générer l'instantané initial pour cette publication. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Cet exemple crée une publication transactionnelle. Des variables de script sont utilisées pour transmettre les informations d'identification Windows nécessaires pour créer les travaux pour l'Agent d'instantané et l'Agent de lecture du journal.  
  
 [!code-sql[HowTo#sp_AddTranPub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_1.sql)]  
  
 Cet exemple crée une publication de fusion. Des variables de script sont utilisées pour transmettre les informations d'identification Windows nécessaires pour créer le travail pour l'Agent d'instantané.  
  
 [!code-sql[HowTo#sp_AddMergePub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez créer des publications par programme à l'aide d'objets RMO (Replication Management Objects). Les classes RMO que vous utilisez pour créer une publication dépendent du type de publication créé.  
  
#### Pour créer une publication d'instantané ou une publication transactionnelle  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créer une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe pour la base de données de publication, définissez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à l’instance de <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à partir de l’étape 1, puis appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> (méthode). Si <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> retourne **false**, vérifier l’existence de la base de données.  
  
3.  Si le <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> propriété **false**, affectez-lui la valeur **true**.  
  
4.  Pour une publication transactionnelle, vérifiez la valeur de la <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentExists%2A> propriété. Si elle a la valeur **true**, un travail de l’Agent de lecture du journal existe déjà pour cette base de données. Si elle a la valeur **false**, procédez comme suit :  
  
    -   Définissez la <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> et <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> ou <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> champs de <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> pour fournir les informations d’identification pour la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] du compte Windows sous lequel s’exécute l’Agent de lecture du journal.  
  
        > [!NOTE]  
        >  Paramètre <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> n’est pas requise lorsque la publication est créée par un membre de la **sysadmin** rôle serveur fixe. Dans ce cas, l'Agent va emprunter l'identité du compte de l'Agent SQL Server. Pour plus d'informations, voir [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facultatif) Définir le <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> et <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> ou <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> champs de <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentPublisherSecurity%2A> lors de l’utilisation de l’authentification SQL Server pour se connecter au serveur de publication.  
  
    -   Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.CreateLogReaderAgent%2A> méthode pour créer le travail de l’Agent de lecture du journal pour la base de données.  
  
5.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransPublication> puis définissez les propriétés suivantes pour cet objet :  
  
    -   Le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Le nom de la base de données publiée pour <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Un nom de la publication de <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Un <xref:Microsoft.SqlServer.Replication.PublicationType> du <xref:Microsoft.SqlServer.Replication.PublicationType.Transactional> ou <xref:Microsoft.SqlServer.Replication.PublicationType.Snapshot>.  
  
    -   Le <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> et <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> champs de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> pour fournir les informations d’identification du compte Windows sous lequel s’exécute l’Agent de capture instantanée. Ce compte est également utilisé lorsque l'Agent d'instantané établit des connexions au serveur de distribution local et pour toute connexion distante lors de l'utilisation de l'authentification Windows.  
  
        > [!NOTE]  
        >  Paramètre <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> n’est pas requise lorsque la publication est créée par un membre de la **sysadmin** rôle serveur fixe. Dans ce cas, l'Agent va emprunter l'identité du compte de l'Agent SQL Server. Pour plus d'informations, voir [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facultatif) Le <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> et <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> ou <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> champs de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentPublisherSecurity%2A> lors de l’utilisation de l’authentification SQL Server pour se connecter au serveur de publication.  
  
    -   (Facultatif) Utiliser l’opérateur OR logique inclusif (**|** en Visual c# et **ou** en Visual Basic) et l’opérateur OR logique exclusif (**^** en Visual c# et **Xor** en Visual Basic) pour définir le <xref:Microsoft.SqlServer.Replication.PublicationAttributes> valeurs pour le <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propriété.  
  
    -   (Facultatif) Le nom du serveur de publication pour <xref:Microsoft.SqlServer.Replication.TransPublication.PublisherName%2A> lorsque le serveur de publication est un serveur de publication non-SQL.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> méthode pour créer la publication.  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour toutes les propriétés, y compris <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et serveur de distribution distant avant d’appeler le <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> méthode. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
7.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> méthode pour créer le travail de l’Agent de capture instantanée pour la publication.  
  
#### Pour créer une publication de fusion  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créer une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe pour la base de données de publication, définissez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à l’instance de <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à partir de l’étape 1, puis appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> (méthode). Si <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> retourne **false**, vérifier l’existence de la base de données.  
  
3.  Si <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> propriété **false**, affectez-lui la valeur **true**, et appelez <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> puis définissez les propriétés suivantes pour cet objet :  
  
    -   Le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Le nom de la base de données publiée pour <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Un nom de la publication de <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Le <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> et <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> champs de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> pour fournir les informations d’identification du compte Windows sous lequel s’exécute l’Agent de capture instantanée. Ce compte est également utilisé lorsque l'Agent d'instantané établit des connexions au serveur de distribution local et pour toute connexion distante lors de l'utilisation de l'authentification Windows.  
  
        > [!NOTE]  
        >  Paramètre <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> n’est pas requise lorsque la publication est créée par un membre de la **sysadmin** rôle serveur fixe. Pour plus d'informations, voir [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facultatif) Utiliser l’opérateur OR logique inclusif (**|** en Visual c# et **ou** en Visual Basic) et l’opérateur OR logique exclusif (**^** en Visual c# et **Xor** en Visual Basic) pour définir le <xref:Microsoft.SqlServer.Replication.PublicationAttributes> valeurs pour le <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propriété.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> méthode pour créer la publication.  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour toutes les propriétés, y compris <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et serveur de distribution distant avant d’appeler le <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> méthode. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> méthode pour créer le travail de l’Agent de capture instantanée pour la publication.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple active la base de données AdventureWorks pour une publication transactionnelle, définit un travail de l'Agent de lecture du journal et crée la publication AdvWorksProductTran. Un article doit être défini pour cette publication. Les informations d'identification du compte Windows nécessaires pour créer le travail de l'Agent de lecture du journal et de l'Agent d'instantané sont passées au moment de l'exécution. Pour savoir comment utiliser des objets RMO pour définir des articles d'instantané et des articles transactionnels, consultez [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
 [!code-csharp[HowTo#rmo_CreateTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpub)]  
  
 Cet exemple active la base de données AdventureWorks pour la publication de fusion et crée la publication AdvWorksSalesOrdersMerge. Des articles doivent encore être définis pour cette publication. Les informations d'identification du compte Windows nécessaires pour créer le travail de l'Agent d'instantané sont passées au moment de l'exécution. Pour savoir comment utiliser des objets RMO pour définir des articles de fusion, consultez [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
## Voir aussi  
 [Utiliser sqlcmd avec des variables de script](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)   
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Concepts liés à Replication Management Objects](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [Afficher et modifier les propriétés d'une publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Configurer la distribution](../../../relational-databases/replication/configure-distribution.md)   
 [Protéger le serveur de distribution](../../../relational-databases/replication/security/secure-the-distributor.md)   
 [Sécuriser le serveur de publication](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  