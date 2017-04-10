---
title: "D&#233;finir et modifier un filtre de jointure entre des articles de fusion | Microsoft Docs"
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
  - "filtres [réplication SQL Server], jointure"
  - "filtres de jointure de réplication de fusion [réplication SQL Server]"
  - "modification des filtres, jointure"
  - "filtres de jointure"
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# D&#233;finir et modifier un filtre de jointure entre des articles de fusion
  Cette rubrique décrit comment définir et modifier un filtre de jointure entre des articles de fusion dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La réplication de fusion prend en charge les filtres de jointure, qui sont en général utilisés conjointement aux filtres paramétrables pour étendre le partitionnement de table à d'autres articles de table connexes.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
-   **Pour définir et modifier un filtre de jointure entre des articles de fusion à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Pour qu'il soit possible de créer un filtre de jointure, la publication doit contenir au minimum deux tables associées. Un filtre de jointure permet d'étendre un filtre de lignes : vous devez donc définir un filtre de lignes sur une table pour pouvoir étendre le filtre à une autre table avec une jointure. Après avoir défini un filtre de jointure, vous pouvez l'étendre avec un autre filtre de jointure si la publication contient des tables associées supplémentaires.  
  
-   Si vous ajoutez, modifiez ou supprimez un filtre de jointure après que les abonnements à la publication aient été initialisés, vous devez générer un nouvel instantané et réinitialiser tous les abonnements après avoir effectué la modification. Pour plus d’informations sur la configuration requise pour les modifications de propriété, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Les filtres de jointure peuvent être créés manuellement pour un ensemble de tables, ou bien la réplication peut générer les filtres automatiquement sur la base des relations entre les clés étrangères et les clés primaires définies sur les tables. Pour plus d’informations sur la génération automatique d’un ensemble de filtres de jointure, consultez [Générer automatiquement une valeur de jointure filtres entre fusionner Articles & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Définir, modifier et supprimer des filtres de jointure sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [Création d’une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour définir un filtre de jointure  
  
1.  Sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes** page de la **Propriétés de la Publication - \< Publication>**, sélectionnez un filtre de lignes existant ou le filtre de jointure le **Tables filtrées** volet.  
  
2.  Cliquez sur **Ajouter**, puis sur **Ajouter une jointure pour étendre le filtre sélectionné**.  
  
3.  Créez l'instruction de jointure : sélectionnez **Utiliser le générateur pour créer l'instruction** ou **Créer manuellement l'instruction de jointure**.  
  
    -   Si vous choisissez d’utiliser le générateur, utilisez les colonnes de la grille (**association**, **colonne de table filtrée**, **opérateur**, et **colonne de table jointe**) pour créer une instruction de jointure.  
  
         Chaque colonne de la grille contient une zone de liste déroulante modifiable, ce qui vous permet de sélectionner deux colonnes et un opérateur (**=**, **<>**, **<=**, **\<**, **>=**, **>**, et **comme**). Les résultats s'affichent dans la zone de texte **Aperçu** . Si la jointure implique plusieurs paires de colonnes, sélectionnez une conjonction (et ou ou) à partir de la **association** colonne, puis entrez deux colonnes supplémentaires et un opérateur.  
  
    -   Si vous créez l'instruction manuellement, écrivez l'instruction de jointure dans la zone de texte **Instruction de jointure** . Utilisez la zone de liste **Colonnes de table filtrée** et la zone de liste **Colonnes de table jointe** pour faire glisser et déposer des colonnes dans la zone de texte **Instruction de jointure** .  
  
    -   L'instruction de jointure complète est par exemple celle-ci :  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         La clause JOIN doit utiliser un nommage en deux parties ; les nommages en trois et en quatre parties ne sont pas pris en charge.  
  
4.  Spécifiez les options de jointure :  
  
    -   Si la colonne sur laquelle vous la jointure de la table filtrée (la table parente) est unique, sélectionnez **clé Unique**.  
  
        > [!CAUTION]  
        >  La sélection de cette option indique que la relation entre les tables enfant et parent dans un filtre de jointure correspond à une relation Un à un ou Un à plusieurs. Sélectionnez cette option seulement si vous avez une contrainte sur la colonne de jointure dans la table enfant qui garantit l'unicité. Si vous ne définissez pas correctement l'option, des erreurs de non-convergence de données peuvent se produire.  
  
    -   Par défaut, la réplication de fusion traite les modifications ligne par ligne lors de la synchronisation. Pour les modifications dans les lignes de la table filtrée et la table jointe soient traitées en tant qu’unité associées, sélectionnez **enregistrement logique** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures uniquement). Cette option est disponible uniquement si les conditions d'article et de publication d'utilisation d'enregistrements logiques sont satisfaites. Pour plus d’informations, consultez la section « Considérations pour l’utilisation enregistrements logiques » dans [modifications du groupe de lignes associées avec les enregistrements logiques](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### Pour modifier un filtre de jointure  
  
1.  Sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes de** page de la **Propriétés de la Publication - \< Publication>**, sélectionnez un filtre dans le **Tables filtrées** volet, puis cliquez sur **Modifier**.  
  
2.  Dans la boîte de dialogue **Modifier une jointure** , modifiez le filtre.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Pour supprimer un filtre de jointure  
  
1.  Sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes de** page de la **Propriétés de la Publication - \< Publication>**, sélectionnez un filtre dans le **Tables filtrées** volet, puis cliquez sur **Supprimer**. Si le filtre de jointure que vous supprimez est lui-même étendu par d'autres jointures, ces jointures seront aussi supprimées.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Ces procédures montrent un filtre paramétrable sur un article parent avec des filtres de jointure entre cet article et des articles enfants connexes. Les filtres de jointure peuvent être définis et modifiés par programme à l'aide des procédures stockées de réplication.  
  
#### Pour définir un filtre de jointure pour étendre un filtre d'article aux articles connexes dans une publication de fusion  
  
1.  Définissez le filtrage pour l'article auquel s'effectue la jointure, qui est également connu comme l'article parent.  
  
    -   Pour un article filtré à l'aide d'un filtre de lignes paramétrable, consultez [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
    -   Pour un article filtré à l'aide d'un filtre de lignes statique, consultez [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Pour définir un ou plusieurs articles connexes, qui sont également appelés des articles enfants, pour la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md). Spécifiez **@publication**, un nom unique pour ce filtre pour **@filtername**, le nom de l’article enfant créé à l’étape 2 pour **@article**, le nom de l’article parent pour **@join_articlename**, et une de ces valeurs pour **@join_unique_key**:  
  
    -   **0** -indique une jointure plusieurs-à-un ou plusieurs-à-plusieurs entre les articles parents et enfants.  
  
    -   **1** -indique une jointure un à un ou un-à-plusieurs entre les articles parents et enfants.  
  
     Cela définit un filtre de jointure entre les deux articles.  
  
    > [!CAUTION]  
    >  Définissez uniquement **@join_unique_key** à **1** Si vous avez une contrainte sur la colonne de jointure dans la table sous-jacente pour l’article parent qui garantit l’unicité. Si **@join_unique_key** est définie sur **1** incorrecte, une non-convergence des données peut se produire.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple définit un article pour une publication de fusion, où l'article de la table `SalesOrderDetail` est filtré par rapport à la table `SalesOrderHeader` qui est elle-même filtrée à l'aide d'un filtre de ligne statique. Pour plus d'informations, voir [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-join_1.sql)]  
  
 Cet exemple définit un groupe d’articles dans une publication de fusion où les articles sont filtrés par une série de filtres de jointure contre les `Employee` de table qui est elle-même filtrée à l’aide d’un filtre de lignes paramétrable sur la valeur de [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md) dans les **LoginID** colonne. Pour plus d'informations, consultez [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-join_2.sql)]  
  
## Voir aussi  
 [Filtres de jointure](../../../relational-databases/replication/merge/join-filters.md)   
 [Filtres de lignes paramétrés](../../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Filtrer des données publiées en vue de la réplication de fusion](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)   
 [Procédure : définir et modifier un filtre de jointure entre des articles de fusion (SQL Server Management Studio)](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Définir une relation d'enregistrement logique entre des articles de table de fusion](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
  