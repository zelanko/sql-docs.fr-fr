---
title: "D&#233;finir et modifier un filtre de lignes statiques | Microsoft Docs"
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
  - "modifying filters, static row"
  - "static row filters"
  - "filtres [réplication SQL Server], ligne statique"
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# D&#233;finir et modifier un filtre de lignes statiques
  Cette rubrique explique comment définir et modifier un filtre de lignes statique dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
-   **Pour définir et modifier un filtre de lignes statique à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si vous ajoutez, modifiez ou supprimez un filtre de ligne statique après que les abonnements à la publication aient été initialisés, vous devez générer un nouvel instantané et réinitialiser tous les abonnements une fois la modification effectuée. Pour plus d’informations sur la configuration requise pour les modifications de propriété, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
-   Si la publication est activée pour la réplication transactionnelle d'égal à égal, les tables ne peuvent pas être filtrées.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Comme ces filtres sont statiques, tous les abonnés recevront le même sous-ensemble des données. Si vous devez filtrer dynamiquement des lignes dans un article de table qui appartient à une publication de fusion afin que chaque abonné reçoive une partition différente des données, consultez [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md). La réplication de fusion vous permet également de filtrer des lignes connexes en fonction d'un filtre de lignes existant. Pour plus d’informations, consultez [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Définir, modifier et supprimer des filtres de lignes statiques sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour définir un filtre de lignes statiques  
  
1.  Sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, l’action à entreprendre dépend du type de publication :  
  
    -   Pour une publication transactionnelle ou d'instantané, cliquez sur **Ajouter**.  
  
    -   Pour une publication de fusion, cliquez sur **Ajouter**puis sur **Ajouter un filtre**.  
  
2.  Dans le **Ajouter un filtre** boîte de dialogue, sélectionnez une table à filtrer dans la zone de liste déroulante.  
  
3.  Créez une instruction de filtrage dans la zone de texte **Instruction de filtrage** . Vous pouvez taper directement dans la zone de texte, mais vous pouvez aussi faire glisser et déposer des colonnes depuis la zone de liste **Colonnes** .  
  
    > [!NOTE]  
    >  La clause WHERE doit utiliser un nommage en deux parties ; les nommages en trois et en quatre parties ne sont pas pris en charge. Si la publication provient d'un serveur de publication Oracle, la clause WHERE doit respecter la syntaxe Oracle.  
  
    -   La zone de texte **Instruction de filtrage** comprend un texte par défaut, qui est de la forme suivante :  
  
        ```tsql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   Le texte par défaut ne peut pas être modifié ; tapez la clause du filtre après le mot clé WHERE en utilisant la syntaxe SQL standard. La clause de filtrage complète ressemble à ceci :  
  
        ```tsql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   Un filtre de lignes statiques peut inclure une fonction définie par l'utilisateur. La clause de filtrage complète pour un filtre de lignes statiques avec une fonction définie par l'utilisateur ressemble à ceci :  
  
        ```tsql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### Pour modifier un filtre de lignes statiques  
  
1.  Sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes de** page de la **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez un filtre dans le **Tables filtrées** volet, puis cliquez sur **Modifier**.  
  
2.  Dans la boîte de dialogue **Modifier le filtre** , modifiez le filtre.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Pour supprimer un filtre de lignes statiques  
  
1.  Sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes de** page de la **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez un filtre dans le **Tables filtrées** volet, puis cliquez sur **Supprimer**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Lorsque vous créez des articles de table, vous pouvez définir une clause WHERE pour éliminer par filtrage des lignes d'un article. Vous pouvez également modifier un filtre de lignes après qu'il a été défini. Les filtres de lignes statiques peuvent être créés et modifiés par programme à l'aide des procédures stockées de réplication.  
  
#### Pour définir un filtre de lignes statique pour une publication transactionnelle ou d'instantané  
  
1.  Définissez l'article à filtrer. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_articlefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md). Spécifiez le nom de l’article pour **@article**, le nom de la publication pour **@publication**, un nom pour le filtre pour **@filter_name**, et la clause de filtre pour **@filter_clause** (non compris `WHERE`).  
  
3.  Si un filtre de colonne doit encore être défini, consultez [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md). Sinon, exécutez [sp_articleview & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Spécifiez le nom de la publication **@publication**, le nom de l’article filtré pour **@article**, et la clause de filtre spécifiée à l’étape 2 pour **@filter_clause**. Les objets de synchronisation pour l'article filtré sont alors créés.  
  
#### Pour modifier un filtre de lignes statique pour une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_articlefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md). Spécifiez le nom de l’article pour **@article**, le nom de la publication pour **@publication**, un nom pour le nouveau filtre pour **@filter_name**, et la nouvelle clause de filtrage pour **@filter_clause** (non compris `WHERE`). Étant donné que cette modification invalidera des données dans les abonnements existants, spécifiez la valeur **1** pour **@force_reinit_subscription**.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_articleview & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Spécifiez le nom de la publication **@publication**, le nom de l’article filtré pour **@article**, et la clause de filtre spécifiée à l’étape 1 pour **@filter_clause**. Cela recrée la vue qui définit l'article filtré.  
  
3.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour. Pour plus d’informations, consultez [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
4.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Pour supprimer un filtre de lignes statique pour une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_articlefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md). Spécifiez le nom de l’article pour **@article**, le nom de la publication pour **@publication**, une valeur NULL pour **@filter_name**, et une valeur NULL pour **@filter_clause**. Étant donné que cette modification invalidera des données dans les abonnements existants, spécifiez la valeur **1** pour **@force_reinit_subscription**.  
  
2.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour. Pour plus d’informations, consultez [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
3.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Pour définir un filtre de lignes statique pour une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Spécifiez la clause de filtre pour **@subset_filterclause** (non compris `WHERE`). Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Si un filtre de colonne doit encore être défini, consultez [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
#### Pour modifier un filtre de lignes statique pour une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez le nom de la publication **@publication**, le nom de l’article filtré pour **@article**, une valeur de **subset_filterclause** pour **@property**, et la nouvelle clause de filtrage pour **@value** (non compris `WHERE`). Étant donné que cette modification invalidera des données dans les abonnements existants, spécifiez la valeur 1 pour **@force_reinit_subscription**.  
  
2.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour. Pour plus d’informations, consultez [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
3.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Dans cet exemple de réplication transactionnelle, l'article est filtré horizontalement pour que tous les produits ayant cessé d'être suivis soient supprimés.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-stat_1.sql)]  
  
 Dans cet exemple de réplication de fusion, les articles sont filtrés horizontalement pour que seules les lignes qui appartiennent au vendeur spécifié soient retournées. Un filtre de jointure est également utilisé. Pour plus d'informations, voir [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-stat_2.sql)]  
  
## Voir aussi  
 [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Filtrer des données publiées](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtrer des données publiées en vue de la réplication de fusion](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  