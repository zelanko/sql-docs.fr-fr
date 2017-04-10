---
title: "D&#233;finir un article | Microsoft Docs"
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
  - "articles [SQL Server replication], defining"
  - "sp_addmergearticle"
  - "adding articles"
  - "sp_addarticle"
  - "articles [réplication SQL Server], ajout"
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# D&#233;finir un article
  Cette rubrique explique comment définir un article dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)], ou des objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour définir un article, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les noms d'article ne peuvent inclure aucun des caractères suivants : % , * , [ , ] , | , : , " , ? , ' , \ , / , \< , >. Si des objets de la base de données incluent l'un de ces caractères et que vous souhaitez les répliquer, vous devez spécifier un nom d'article qui est différent du nom d'objet.  
  
##  <a name="Security"></a> Sécurité  
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
 Une fois une publication créée, des articles peuvent être créés par programme en utilisant des procédures stockées de réplication. Les procédures stockées utilisées pour créer un article dépendent du type de publication pour laquelle l'article est défini. Pour plus d'informations, voir [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Pour définir un article pour une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, un nom de l’article pour **@article**, l’objet de base de données qui est publiée pour **@source_object**, et tous les autres paramètres facultatifs. Utilisez **@source_owner** pour spécifier la propriété du schéma de l’objet, dans le cas contraire **dbo**. Si l’article n’est pas un article de table basé sur journal, spécifiez le type d’article pour **@type**; Pour plus d’informations, consultez [spécifier les Types d’Article & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md).  
  
2.  Pour horizontalement filtrer des lignes dans une table ou d’afficher un article, utilisez [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) pour définir la clause de filtre. Pour plus d'informations, voir [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Pour verticalement filtrer les colonnes dans une table ou d’afficher un article, utilisez [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Pour plus d’informations, voir [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
4.  Exécutez [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) Si l’article est filtré.  
  
5.  Si la publication a des abonnements existants et [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) renvoie la valeur **0** dans les **immediate_sync** colonne, vous devez appeler [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) pour ajouter l’article à chaque abonnement existant.  
  
6.  Si la publication existante abonnements par extraction, exécutez [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) sur le serveur de publication pour créer un nouvel instantané pour les abonnements par extraction de données existante qui contient uniquement le nouvel article.  
  
    > [!NOTE]  
    >  Pour les abonnements qui ne sont pas initialisés à l’aide d’un instantané, vous n’avez pas besoin exécuter [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) que cette procédure est exécutée par [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
#### Pour définir un article pour une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Spécifiez le nom de la publication pour **@publication**, un nom pour le nom de l’article pour **@article**, et l’objet qui est publié pour **@source_object**. Pour filtrer horizontalement les lignes de la table, spécifiez une valeur pour **@subset_filterclause**. Pour plus d'informations, consultez [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) et [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md). Si l'article n'est pas un article de table, spécifiez le type d'article pour **@type**. Pour plus d’informations, consultez [spécifier les Types d’Article & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md).  
  
2.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) pour définir un filtre de jointure entre deux articles. Pour plus d'informations, voir [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
3.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) pour filtrer les colonnes de table. Pour plus d’informations, voir [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple définit un article basé sur la table `Product` pour une publication transactionnelle, où l'article est filtré à la fois horizontalement et verticalement.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_1.sql)]  
  
 Cet exemple définit des articles pour une publication de fusion, où l'article `SalesOrderHeader` est filtré statiquement sur **SalesPersonID**et où l'article `SalesOrderDetail` est filtré avec un filtre de jointure sur `SalesOrderHeader`.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez définir des articles par programme à l'aide d'objets RMO (Replication Management Objects). Les classes RMO que vous utilisez pour définir un article dépendent du type de publication pour lequel l'article est défini.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 L'exemple suivant ajoute un article avec des filtres des lignes et de colonnes à une publication transactionnelle.  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 L'exemple suivant ajoute trois articles à une publication de fusion. Ces articles ont des filtres de colonnes, et deux filtres de jointure sont utilisés pour propager un filtre de lignes paramétrable aux autres articles.  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## Voir aussi  
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Ajouter et supprimer des articles de publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Filtrer des données publiées](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  