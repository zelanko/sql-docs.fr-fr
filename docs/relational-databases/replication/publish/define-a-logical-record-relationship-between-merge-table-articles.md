---
title: "D&#233;finir une relation d&#39;enregistrement logique entre des articles de table de fusion | Microsoft Docs"
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
  - "enregistrements logiques de la réplication de fusion [réplication SQL Server]"
  - "articles [réplication SQL Server], enregistrements logiques"
  - "enregistrements logiques [réplication SQL Server]"
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# D&#233;finir une relation d&#39;enregistrement logique entre des articles de table de fusion
  Cette rubrique explique comment définir une relation d'enregistrement logique entre des articles de table de fusion dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 La réplication de fusion vous permet de définir une relation entre des lignes connexes dans des tables distinctes. Ces lignes peuvent alors être traitées comme une unité transactionnelle au cours de la synchronisation. Un enregistrement logique peut être défini entre deux articles qu'ils aient ou non une relation de filtre de jointure. Pour plus d’informations, consultez [modifications du groupe de lignes associées avec les enregistrements logiques](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour définir une relation d'enregistrement logique entre des articles de table de fusion à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si vous ajoutez, modifiez ou supprimez un enregistrement logique après que les abonnements à la publication aient été initialisés, vous devez générer un nouvel instantané et réinitialiser tous les abonnements après avoir effectué la modification. Pour plus d’informations sur la configuration requise pour les modifications de propriété, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Définissent des enregistrements logiques dans le **Ajouter une jointure** boîte de dialogue, qui est disponible dans l’Assistant Nouvelle Publication et **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 Les enregistrements logiques peuvent être définis dans la boîte de dialogue **Ajouter une jointure** seulement s'ils sont appliqués à un filtre de jointure dans une publication de fusion, et si la publication satisfait aux conditions requises pour l'utilisation de partitions précalculées. Pour définir des enregistrements logiques qui ne sont pas appliqués à des filtres de jointure et pour définir la détection et la résolution des conflits au niveau des enregistrements logiques, vous devez utiliser des procédures stockées.  
  
#### Pour définir une relation d'enregistrement logique  
  
1.  Sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes** page de la **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez un filtre de lignes dans le **Tables filtrées** volet.  
  
     Une relation d'enregistrement logique est associée à un filtre de jointure, qui étend un filtre de lignes. Vous devez donc définir un filtre de lignes avant de pouvoir étendre le filtre avec une jointure et appliquer une relation d'enregistrement logique. Après avoir défini un filtre de jointure, vous pouvez l'étendre avec un autre filtre de jointure. Pour plus d'informations sur la définition de filtres de jointure, consultez [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
2.  Cliquez sur **Ajouter**, puis sur **Ajouter une jointure pour étendre le filtre sélectionné**.  
  
3.  Définissez un filtre de jointure dans la boîte de dialogue **Ajouter une jointure** , puis activez la case à cocher **Enregistrement logique**.  
  
4.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### Pour supprimer une relation d'enregistrement logique  
  
-   Supprimer seulement la relation d'enregistrement logique ou supprimer la relation d'enregistrement logique et le filtre de jointure qui y est associé.  
  
     Pour supprimer seulement la relation d'enregistrement logique :  
  
    1.  Sur le **filtrer les lignes de** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes de** page du **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez le filtre de jointure associé à la relation d’enregistrements logiques dans le **Tables filtrées** volet, puis cliquez sur **Modifier**.  
  
    2.  Dans la boîte de dialogue **Modifier une jointure** , désactivez la case à cocher **Enregistrement logique**.  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Pour supprimer la relation d'enregistrement logique et le filtre de jointure qui y est associé :  
  
    -   Sur le **filtrer les lignes** page de l’Assistant Nouvelle Publication ou **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez un filtre dans le **Tables filtrées** volet, puis cliquez sur **Supprimer**. Si le filtre de jointure que vous supprimez est lui-même étendu par d'autres jointures, ces jointures seront aussi supprimées.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez spécifier par programme des relations d'enregistrements logiques entre des articles en utilisant des procédures stockées de réplication.  
  
#### Pour définir une relation d'enregistrement logique sans filtre de jointure associé  
  
1.  Si la publication contient des articles filtrés, exécutez [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), et notez la valeur de **use_partition_groups** dans le résultat défini.  
  
    -   Si la valeur est **1**, les partitions précalculées sont déjà utilisées.  
  
    -   Si la valeur est **0**, puis exécutez [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) sur le serveur de publication sur la base de données de publication. Spécifiez la valeur **use_partition_groups** pour **@property** et la valeur **true** pour **@value**.  
  
        > [!NOTE]  
        >  Si la publication ne prend pas en charge les partitions précalculées, les enregistrements logiques ne peuvent pas être utilisés. Pour plus d’informations, voir Configuration requise pour l’utilisation des Partitions précalculées dans la rubrique [optimiser les performances de filtre paramétré avec des Partitions précalculées](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
    -   Si la valeur est NULL, l'Agent d'instantané doit être exécuté pour générer l'instantané initial de la publication.  
  
2.  Si les articles qui constitueront l’enregistrement logique n’existent pas, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) sur le serveur de publication sur la base de données de publication. Spécifiez l'une des options de détection et de résolution des conflits suivantes pour l'enregistrement logique :  
  
    -   Pour détecter et résoudre les conflits qui se produisent dans les lignes connexes de l’enregistrement logique, spécifiez la valeur **true** pour **@logical_record_level_conflict_detection** et **@logical_record_level_conflict_resolution**.  
  
    -   Pour utiliser la détection de conflit de niveau ligne ou colonne standard et la résolution, spécifiez la valeur **false** pour **@logical_record_level_conflict_detection** et **@logical_record_level_conflict_resolution**, qui est la valeur par défaut.  
  
3.  Répétez l'étape 2 pour chaque article qui constituera l'enregistrement logique. Vous devez utiliser la même option de détection et de résolution des conflits pour chaque article de l'enregistrement logique. Pour plus d'informations, voir [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
4.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md). Spécifiez **@publication**, le nom d’un article dans la relation de **@article**, le nom de l’article pour la deuxième **@join_articlename**, un nom pour la relation de **@filtername**, une clause qui définit la relation entre les deux articles pour **@join_filterclause**, le type de jointure pour **@join_unique_key** et une de ces valeurs pour **@filter_type**:  
  
    -   **2** -définit une relation logique.  
  
    -   **3** -définit une relation logique avec un filtre de jointure.  
  
    > [!NOTE]  
    >  Si aucun filtre de jointure n'est pas utilisé, la direction de la relation entre les deux articles n'est pas importante.  
  
5.  Répétez l'étape 2 pour chaque relation d'enregistrement logique restante dans la publication.  
  
#### Pour modifier la détection et la résolution des conflits pour les enregistrements logiques  
  
1.  Pour détecter et résoudre les conflits qui se produisent dans des lignes connexes de l'enregistrement logique :  
  
    -   Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez la valeur **logical_record_level_conflict_detection** pour **@property** et la valeur **true** pour **@value**. Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et **@force_reinit_subscription**.  
  
    -   Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez la valeur **logical_record_level_conflict_resolution** pour **@property** et la valeur **true** pour **@value**. Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et **@force_reinit_subscription**.  
  
2.  Pour utiliser la détection et la résolution standard des conflits au niveau des lignes ou des colonnes :  
  
    -   Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez la valeur **logical_record_level_conflict_detection** pour **@property** et la valeur **false** pour **@value**. Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et **@force_reinit_subscription**.  
  
    -   Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez la valeur **logical_record_level_conflict_resolution** pour **@property** et la valeur **false** pour **@value**. Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et **@force_reinit_subscription**.  
  
#### Pour supprimer une relation d'enregistrements logiques  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez la requête suivante afin que des informations sur toutes les relations d'enregistrements logiques définies pour la publication spécifiée soient retournées :  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_1.sql)]  
  
     Notez le nom de la relation d'enregistrements logiques en cours de suppression dans la colonne **filtername** du jeu de résultats.  
  
    > [!NOTE]  
    >  Cette requête renvoie les mêmes informations que [sp_helpmergefilter](../../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md); Toutefois, cette procédure stockée système uniquement renvoie des informations sur les relations d’enregistrements logiques qui sont également les filtres de jointure.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_dropmergefilter](../../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md). Spécifiez **@publication**, le nom de l'un des articles de la relation pour **@article**et le nom de la relation de l'étape 1 pour **@filtername**.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Cet exemple active les partitions précalculées sur une publication existante et crée un enregistrement logique qui comprend les deux nouveaux articles des tables `SalesOrderHeader` et `SalesOrderDetail` .  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
  
> [!NOTE]  
>  La réplication de fusion vous permet de spécifier que les conflits soient suivis et résolus au niveau des enregistrements logiques, mais ces options ne peuvent pas être définies à l'aide des objets RMO.  
  
#### Pour définir une relation d'enregistrement logique sans filtre de jointure associé  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe, définissez la <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  Si le <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> est définie sur <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, affectez-lui la valeur <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.  
  
5.  Si les articles devant inclure l’enregistrement logique n’existent pas, créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeArticle> puis définissez les propriétés suivantes :  
  
    -   Le nom de l’article pour <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Le nom de la publication pour <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   (Facultatif) Si l’article est filtré horizontalement, spécifiez la clause de filtre de lignes pour le <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> propriété. Utilisez cette propriété pour spécifier un filtre de lignes statique ou paramétrable. Pour plus d'informations, voir [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
     Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.Article.Create%2A> méthode.  
  
7.  Répétez les étapes 5 et 6 pour chaque article qui comprend l'enregistrement logique.  
  
8.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> classe pour définir la relation d’enregistrements logiques entre des articles. Définissez ensuite les propriétés suivantes :  
  
    -   Le nom de l’article enfant dans la relation d’enregistrements logiques pour le <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> propriété.  
  
    -   Le nom de l’article parent existant, dans la relation d’enregistrements logiques pour le <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> propriété.  
  
    -   Un nom pour la relation d’enregistrements logiques pour le <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> propriété.  
  
    -   L’expression qui définit la relation pour la <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> propriété.  
  
    -   Une valeur de <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> pour la <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> propriété. Si la relation d’enregistrements logiques est également un filtre de jointure, spécifiez une valeur de <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> pour cette propriété. Pour plus d’informations, consultez [modifications du groupe de lignes associées avec les enregistrements logiques](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
9. Appelez le <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> méthode sur l’objet qui représente l’article enfant dans la relation. Passez le <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> objet à l’étape 8 pour définir la relation.  
  
10. Répétez les étapes 8 et 9 pour chaque relation d'enregistrement logique restante dans la publication.  
  
###  <a name="PShellExample"></a> Exemple (RMO)  
 Cet exemple crée un enregistrement logique qui comprend les deux nouveaux articles pour les tables `SalesOrderHeader` et `SalesOrderDetail` .  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## Voir aussi  
 [Définir et modifier un filtre de jointure entre des articles de fusion](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [Regrouper les modifications apportées à des lignes connexes à l'aide d'enregistrements logiques](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [Optimiser les performances des filtres paramétrés avec des partitions précalculées](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)   
 [Regrouper les modifications apportées à des lignes connexes à l'aide d'enregistrements logiques](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)  
  
  