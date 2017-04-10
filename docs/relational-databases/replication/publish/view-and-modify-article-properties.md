---
title: "Afficher et modifier les propri&#233;t&#233;s d&#39;un article | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_changearticle"
  - "sp_helparticle"
  - "affichage des propriétés de réplication"
  - "sp_changemergearticle"
  - "sp_helpmergearticle"
  - "modification des propriétés de réplication, articles"
  - "articles [réplication SQL Server], modification"
  - "articles [réplication SQL Server], propriétés"
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Afficher et modifier les propri&#233;t&#233;s d&#39;un article
  Cette rubrique décrit comment afficher et modifier les propriétés de l'article dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
-   **Pour afficher et modifier les propriétés d'un article à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Certaines propriétés ne sont pas modifiables après la création d'une publication et d'autres s'il existe des abonnements à la publication. Les propriétés non modifiables sont affichées en lecture seule.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Après qu'une publication a été créée, certaines modifications de propriétés nécessitent un nouvel instantané. Si une publication dispose d'abonnements, ces abonnements pourraient devoir alors être réinitialisés selon les modifications que vous avez apportées. Pour plus d’informations, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) et [Ajouter et supprimer des Articles de Publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Afficher et modifier les propriétés de l’article dans la **Propriétés de la Publication - \< Publication>** boîte de dialogue, qui est disponible dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et le moniteur de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
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
  
#### Pour afficher et modifier les propriétés d'un article  
  
1.  Sur le **Articles** Page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez un article, puis cliquez sur **Propriétés de l’Article**.  
  
2.  Sélectionnez les articles auxquels les modifications des propriétés doivent s'appliquer :  
  
    -   Cliquez sur **définir les propriétés de sélectionné \< ObjectType> Article** pour lancer le **Propriétés de l’Article - \< ObjectName>** boîte de dialogue ; la propriété modifications apportées dans cette boîte de dialogue sont appliquées uniquement à l’objet qui est mis en surbrillance dans le volet de l’objet sur le **Articles** page.  
  
    -   Cliquez sur **Propriétés de tous \< ObjectType> Articles**, pour lancer le **pour toutes les propriétés de \< ObjectType> Articles** boîte de dialogue ; la propriété modifications apportées dans cette boîte de dialogue sont appliquées à tous les objets de ce type dans le volet de l’objet sur le **Articles** page, y compris celles non encore activée pour la publication.  
  
        > [!NOTE]  
        >  Apportées aux propriétés dans le **pour toutes les propriétés de \< ObjectType> Articles** boîte de dialogue remplacer celles effectuées précédemment dans le **Propriétés de l’Article - \< nomobjet>** boîte de dialogue. Ainsi, si vous voulez définir un certain nombre de valeurs par défaut applicables à tous les articles d'un type d'objet mais souhaitez également définir des propriétés pour des objets spécifiques, vous devez d'abord définir les valeurs par défaut pour tous les articles. Définissez ensuite les propriétés des objets individuels.  
  
3.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
4.  Cliquez sur **OK** sur la **Propriétés de la Publication - \< Publication>** boîte de dialogue.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les articles peuvent être modifiés et leurs propriétés retournées, par programme, à l'aide des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'article appartient.  
  
#### Pour afficher les propriétés d'un article appartenant à une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md), en spécifiant le nom de la publication pour le **@publication** paramètre et le nom de l’article pour la **@article** paramètre. Si vous ne spécifiez pas **@article**, des informations sont retournées pour tous les articles de la publication.  
  
2.  Exécutez [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) pour les articles de table pour répertorier toutes les colonnes disponibles dans la table de base.  
  
#### Pour modifier les propriétés d'un article appartenant à une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md), en spécifiant la propriété d’article en cours de modification dans le **@property** paramètre et la nouvelle valeur de cette propriété dans la **@value** paramètre.  
  
    > [!NOTE]  
    >  Si la modification nécessite la génération d’un instantané, vous devez également spécifier une valeur de **1** pour **@force_invalidate_snapshot**, et si la modification nécessite la réinitialisation des abonnés, vous devez également spécifier une valeur de **1** pour **@force_reinit_subscription**. Pour plus d’informations sur les propriétés, modification nécessite un nouvel instantané ou la réinitialisation, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Pour afficher les propriétés d'un article appartenant à une publication de fusion  
  
1.  Exécutez [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md), en spécifiant le nom de la publication pour le **@publication** paramètre et le nom de l’article pour la **@article** paramètre. Si vous ne spécifiez pas ces paramètres, des informations sont retournées pour tous les articles d'une publication ou sur l'Abonné.  
  
2.  Exécutez [sp_helpmergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql.md) pour les articles de table pour répertorier toutes les colonnes disponibles dans la table de base.  
  
#### Pour modifier les propriétés d'un article appartenant à une publication de fusion  
  
1.  Exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), en spécifiant la propriété d’article en cours de modification dans le **@property** paramètre et la nouvelle valeur de cette propriété dans la **@value** paramètre.  
  
    > [!NOTE]  
    >  Si la modification nécessite la génération d’un instantané, vous devez également spécifier une valeur de **1** pour **@force_invalidate_snapshot**, et si la modification nécessite la réinitialisation des abonnés, vous devez également spécifier une valeur de **1** pour **@force_reinit_subscription**. Pour plus d’informations sur les propriétés, modification nécessite un nouvel instantané ou la réinitialisation, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Cet exemple de réplication transactionnelle retourne les propriétés de l'article publié.  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_1.sql)]  
  
 Cet exemple de réplication transactionnelle modifie les options de schéma pour l'article publié.  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_2.sql)]  
  
 Cet exemple de réplication de fusion retourne les propriétés de l'article publié.  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_3.sql)]  
  
 Cet exemple de réplication de fusion modifie les paramètres de détection de conflit pour un article publié.  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_4.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez modifier des articles et accéder à leurs propriétés, par programme, en utilisant les objets RMO (Replication Management Objects). Les classes RMO à utiliser pour afficher ou modifier les propriétés d'un article dépendent du type de publication auquel l'article appartient.  
  
#### Pour afficher ou modifier les propriétés d'un article qui appartient à une publication transactionnelle ou d'instantané  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransArticle> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Propriétés.  
  
4.  Configuration de la connexion à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de l'article ont été définies de manière incorrecte à l'étape 3, soit l'article n'existe pas.  
  
6.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l’un de le <xref:Microsoft.SqlServer.Replication.TransArticle> Propriétés pouvant être définies.  
  
7.  (Facultatif) Si vous avez spécifié une valeur de **true** pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> méthode pour valider les modifications sur le serveur. Si vous avez spécifié une valeur de **false** pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (la valeur par défaut), les modifications sont envoyées au serveur immédiatement.  
  
#### Pour afficher ou modifier les propriétés d'un article qui appartient à une publication de fusion  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeArticle> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Propriétés.  
  
4.  Configuration de la connexion à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de l'article ont été définies de manière incorrecte à l'étape 3, soit l'article n'existe pas.  
  
6.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l’un de le <xref:Microsoft.SqlServer.Replication.MergeArticle> Propriétés pouvant être définies.  
  
7.  (Facultatif) Si vous avez spécifié une valeur de **true** pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> méthode pour valider les modifications sur le serveur. Si vous avez spécifié une valeur de **false** pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (la valeur par défaut), les modifications sont envoyées au serveur immédiatement.  
  
###  <a name="PShellExample"></a> Exemple (RMO)  
 Cet exemple modifie un article de fusion pour spécifier le gestionnaire de logique métier utilisé par l'article.  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## Voir aussi  
 [Implémenter un gestionnaire de logique métier pour un article de fusion](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Détection et résolution avancées des conflits de réplication de fusion](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  