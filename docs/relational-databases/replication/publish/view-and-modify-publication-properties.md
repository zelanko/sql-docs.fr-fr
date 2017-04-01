---
title: "Afficher et modifier les propri&#233;t&#233;s d&#39;une publication | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "affichage des propriétés de réplication"
  - "modification des propriétés de réplication, articles"
  - "articles [réplication SQL Server], modification"
  - "publications [réplication SQL Server], propriétés"
  - "articles [réplication SQL Server], propriétés"
  - "modification des propriétés de réplication, publications"
  - "publications [réplication SQL Server], modification"
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Afficher et modifier les propri&#233;t&#233;s d&#39;une publication
  Cette rubrique décrit comment afficher et modifier les propriétés de la publication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
-   **Pour afficher et modifier les propriétés d'une publication à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Certaines propriétés ne sont pas modifiables après la création d'une publication et d'autres s'il existe des abonnements à la publication. Les propriétés non modifiables sont affichées en lecture seule.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Après qu'une publication a été créée, certaines modifications de propriétés nécessitent un nouvel instantané. Si une publication dispose d'abonnements, ces abonnements pourraient devoir alors être réinitialisés selon les modifications que vous avez apportées. Pour plus d’informations, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) et [Ajouter et supprimer des Articles de Publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Afficher et modifier les propriétés de la publication dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, qui est disponible dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et le moniteur de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
 Le **Propriétés de la Publication - \< Publication>** boîte de dialogue comprend les pages suivantes :  
  
-   La page **Général** contient le nom et la description de la publication, le nom de la base de données, le type de publication et les paramètres d'expiration des abonnements.  
  
-   La page **Articles** correspond à la page **Articles** de l'Assistant Nouvelle publication. Utilisez-la pour ajouter et supprimer des articles, ainsi que pour modifier des propriétés et le filtrage des colonnes pour des articles.  
  
-   La page **Filtrer les lignes** correspond à la page **Filtrer les lignes de la table** de l'Assistant Nouvelle publication. Utilisez-la pour ajouter, modifier et supprimer des filtres de lignes statiques pour tous les types de publications, ainsi que pour ajouter, modifier et supprimer des filtres de lignes paramétrés et des filtres de jointure pour des publications de fusion.  
  
-   La page **Instantané** permet de spécifier le format et l'emplacement de l'instantané, la compression éventuelle de l'instantané, ainsi que des scripts à exécuter avant et après l'application de l'instantané.  
  
-   Le **instantané FTP** page (de capture instantanée et les publications transactionnelles et les publications de fusion pour les serveurs de publication exécutant des versions antérieures de SQL Server 2005), vous pouvez spécifier si les abonnés peuvent télécharger les fichiers d’instantanés via FTP File Transfer Protocol ().  
  
-   Le **instantané FTP et Internet** page (pour les publications de fusion à partir des serveurs de publication exécutant SQL Server 2005 ou version ultérieure) vous permet de spécifier si les abonnés peuvent télécharger les fichiers d’instantanés via FTP, et indique si les abonnés peuvent synchroniser des abonnements via HTTPS.  
  
-   La page **Options d'abonnement** permet de définir diverses options qui s'appliquent à tous les abonnements. Les options diffèrent en fonction du type de publication.  
  
-   La page **Liste d'accès à la publication** permet de spécifier les connexions et les groupes qui peuvent accéder à une publication.  
  
-   La page **Sécurité de l'agent** permet d'accéder aux paramètres des comptes sous lesquels les agents ci-après s'exécutent et se connectent aux ordinateurs d'une topologie de réplication : l'Agent d'instantané pour toutes les publications, l'Agent de lecture du journal pour toutes les publications transactionnelles et l'Agent de lecture de la file d'attente pour les publications transactionnelles qui autorisent les abonnements mis à jour en attente.  
  
-   Le **des Partitions de données** page (pour les publications de fusion à partir des serveurs de publication exécutant SQL Server 2005 ou version ultérieure) permet de spécifier si les abonnés aux publications avec des filtres paramétrés peuvent demander un instantané si celle-ci n’est pas disponible. Elle permet de générer des instantanés pour une ou plusieurs partitions, soit au coup par coup, soit à intervalles récurrents.  
  
#### Pour afficher et modifier les propriétés d'une publication dans Management Studio  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Cliquez sur une publication, puis cliquez sur **propriétés**.  
  
4.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
#### Pour afficher et modifier les propriétés d'une publication dans le moniteur de réplication  
  
1.  Développez un groupe du serveur de publication dans le volet gauche du moniteur de réplication, puis développez un serveur de publication.  
  
2.  Cliquez sur une publication, puis cliquez sur **propriétés**.  
  
3.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les publications peuvent être modifiées et leurs propriétés retournées par programme à l'aide de procédures stockées de réplication. Les procédures stockées que vous utilisez dépendent du type de publication.  
  
#### Pour afficher les propriétés d'une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md), en spécifiant le nom de la publication pour le **@publication** paramètre. Si vous ne spécifiez pas ce paramètre, les informations sur toutes les publications sur le serveur de publication sont retournées.  
  
#### Pour modifier les propriétés d'une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), en spécifiant la propriété de publication à modifier dans le **@property** paramètre et la nouvelle valeur de cette propriété dans la **@value** paramètre.  
  
    > [!NOTE]  
    >  Si la modification nécessite la génération d’un instantané, vous devez également spécifier une valeur de **1** pour **@force_invalidate_snapshot**, et si la modification nécessite la réinitialisation des abonnés, vous devez spécifier une valeur de **1** pour **@force_reinit_subscription**. Pour plus d’informations sur les propriétés, modification nécessite un nouvel instantané ou la réinitialisation, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Pour afficher les propriétés d'une publication de fusion  
  
1.  Exécutez [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), en spécifiant le nom de la publication pour le **@publication** paramètre. Si vous ne spécifiez pas ce paramètre, les informations sur toutes les publications sur le serveur de publication sont retournées.  
  
#### Pour modifier les propriétés d'une publication de fusion  
  
1.  Exécutez [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), en spécifiant la propriété de publication en cours de modification dans le **@property** paramètre et la nouvelle valeur de cette propriété dans la **@value** paramètre.  
  
    > [!NOTE]  
    >  Si la modification nécessite la génération d’un instantané, vous devez également spécifier une valeur de **1** pour **@force_invalidate_snapshot**, et si la modification nécessite la réinitialisation des abonnés, vous devez spécifier une valeur de **1** pour **@force_reinit_subscription** Pour plus d’informations sur les propriétés, modification nécessite un nouvel instantané ou la réinitialisation, consultez [Modifier les propriétés de Publication et l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Pour afficher les propriétés d'un instantané  
  
1.  Exécutez [sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), en spécifiant le nom de la publication pour le **@publication** paramètre.  
  
#### Pour modifier les propriétés d'un instantané  
  
1.  Exécutez [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), en spécifiant une ou plusieurs des nouvelles propriétés d’instantané pour les paramètres de l’instantané approprié.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple de réplication transactionnelle retourne les propriétés de la publication.  
  
 [!code-sql[HowTo#sp_helppublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_1.sql)]  
  
 Cet exemple de réplication transactionnelle désactive la réplication du schéma pour la publication.  
  
 [!code-sql[HowTo#sp_changepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_2.sql)]  
  
 Cet exemple de réplication de fusion retourne les propriétés de la publication.  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_3.sql)]  
  
 Cet exemple de réplication de fusion désactive la réplication du schéma pour la publication.  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_4.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez modifier des publications et accéder par programme à leurs propriétés à l'aide d'objets RMO (Replication Management Objects). Les classes RMO utilisées pour afficher ou modifier les propriétés d'une publication dépendent du type de publication.  
  
#### Pour afficher ou modifier les propriétés d'une publication transactionnelle ou d'instantané  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créer une instance de la <xref:Microsoft.SqlServer.Replication.TransPublication> classe, définissez la <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l'une des propriétés paramétrables. Utiliser l’opérateur AND logique (**&** dans Microsoft Visual c# et **et** dans Microsoft Visual Basic) pour déterminer si une donnée <xref:Microsoft.SqlServer.Replication.PublicationAttributes> a la valeur pour le <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propriété. Utiliser l’opérateur OR logique inclusif (**|** en Visual c# et **ou** en Visual Basic) et l’opérateur OR logique exclusif (**^** en Visual c# et **Xor** en Visual Basic) pour modifier la <xref:Microsoft.SqlServer.Replication.PublicationAttributes> valeurs pour le <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propriété.  
  
5.  (Facultatif) Si vous avez spécifié une valeur de **true** pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> méthode pour valider les modifications sur le serveur. Si vous avez spécifié une valeur de **false** pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (la valeur par défaut), les modifications sont envoyées au serveur immédiatement.  
  
#### Pour afficher ou modifier les propriétés d'une publication de fusion  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créer une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe, définissez la <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l'une des propriétés paramétrables. Utiliser l’opérateur AND logique (**&** en Visual c# et **et** en Visual Basic) pour déterminer si une donnée <xref:Microsoft.SqlServer.Replication.PublicationAttributes> a la valeur de la <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propriété. Utiliser l’opérateur OR logique inclusif (**|** en Visual c# et **ou** en Visual Basic) et l’opérateur OR logique exclusif (**^** en Visual c# et **Xor** en Visual Basic) pour modifier la <xref:Microsoft.SqlServer.Replication.PublicationAttributes> valeurs pour le <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propriété.  
  
5.  (Facultatif) Si vous avez spécifié une valeur de **true** pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> méthode pour valider les modifications sur le serveur. Si vous avez spécifié une valeur de **false** pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (la valeur par défaut), les modifications sont envoyées au serveur immédiatement.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple définit des attributs de publication pour une publication transactionnelle. Les modifications sont mises en cache jusqu'à leur envoi explicite au serveur.  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 Cet exemple désactive la réplication DDL pour une publication de fusion.  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## Voir aussi  
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Modifier le schéma dans les bases de données de publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Ajouter et supprimer des Articles d’une Publication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)   
 [Afficher des informations et effectuer des tâches pour une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Afficher et modifier les propriétés d'un article](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  