---
title: "D&#233;finir et modifier un filtre de colonne | Microsoft Docs"
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
  - "filters [SQL Server replication], column"
  - "modifying filters, column"
  - "modifying filters"
  - "filtres de colonne [réplication SQL Server]"
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# D&#233;finir et modifier un filtre de colonne
  Cette rubrique décrit comment définir et modifier un filtre de colonne dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour définir et modifier un filtre de colonne à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Certaines colonnes ne peuvent pas être filtrées ; Pour plus d’informations, consultez [filtrer les données publiées](../../../relational-databases/replication/publish/filter-published-data.md). Si vous modifiez un filtre de colonne après que des abonnements ont été initialisés, vous devez générer un nouvel instantané et réinitialiser tous les abonnements après avoir effectué la modification. Pour plus d’informations sur la configuration requise pour les modifications de propriété, consultez [modification de propriétés de Publication et l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Définissez des filtres de colonnes sur la page **Articles** de l'Assistant Nouvelle Publication. Pour plus d’informations sur l’utilisation de l’Assistant Nouvelle Publication, reportez-vous à la section [de créer une composition](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 Définir et modifier les filtres de colonne sur la **Articles** page de la **des propriétés de Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur les propriétés de publication et l’article, reportez-vous à la section [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour définir un filtre de colonne  
  
1.  Sur la page **Articles** de l'Assistant Nouvelle publication, développez la table à filtrer dans le volet **Objets à publier** .  
  
2.  Activez la case à cocher en regard des colonnes que vous voulez filtrer.  
  
#### Pour modifier le filtrage des colonnes  
  
1.  Sur le **Articles** page de la **des propriétés de Publication - \< Publication>** boîte de dialogue, développez la table à filtrer dans la **objets à publier** volet.  
  
2.  Désactivez la case à cocher en regard de chaque colonne que vous voulez filtrer, et vérifiez que la case à cocher est activée pour chaque colonne qui doit être incluse dans l'article.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Lors de la création d'articles de table, vous pouvez définir les colonnes à inclure dans l'article et modifier ces colonnes une fois l'article défini. Vous pouvez créer et modifier par programme des colonnes filtrées en utilisant des procédures stockées de réplication.  
  
> [!NOTE]  
>  Les procédures suivantes supposent que la table sous-jacente n'a pas été modifiée. Pour plus d’informations sur la réplication des modifications de langage (DDL) de définition de données aux tables publiées, consultez [effectuer des modifications de schéma dans les bases de données de Publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
#### Pour définir un filtre de colonne pour un article publié dans une publication transactionnelle ou d'instantané  
  
1.  Définissez l'article à filtrer. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Sur la base de données de publication de l’éditeur, exécutez [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Les colonnes à inclure ou à supprimer de l'article sont alors définies.  
  
    -   Si seulement quelques colonnes d’une table contenant de nombreuses colonnes de publication, exécutez [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) une fois pour chaque colonne ajoutée. Spécifiez le nom de la colonne pour **@column** et affectez la valeur **add** à **@operation**.  
  
    -   Si la publication de la plupart des colonnes dans une table contenant de nombreuses colonnes, exécutez [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), la valeur **null** pour **@column** et une valeur de **Ajouter** pour **@operation** pour ajouter toutes les colonnes. Puis exécutez [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), une fois pour chaque colonne exclue, spécifiant la valeur **Supprimer** pour **@operation** et le nom de la colonne exclue pour **@column**.  
  
3.  Sur la base de données de publication de l’éditeur, exécutez [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Spécifiez le nom de la publication pour **@publication** et le nom de l'article filtré pour **@article**. Les objets de synchronisation pour l'article filtré sont alors créés.  
  
#### Pour modifier un filtre de colonne de manière à inclure des colonnes supplémentaires pour un article publié dans une publication transactionnelle ou d'instantané  
  
1.  Sur la base de données de publication de l’éditeur, exécutez [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) une fois pour chaque colonne ajoutée. Spécifiez le nom de la colonne pour **@column** et affectez la valeur **add** à **@operation**.  
  
2.  Sur la base de données de publication de l’éditeur, exécutez [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Spécifiez le nom de la publication pour **@publication** et le nom de l'article filtré pour **@article**. Si la publication possède des abonnements existants, spécifiez une valeur de **1** de **@change_active**. Les objets de synchronisation pour l'article filtré sont alors recréés.  
  
3.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour.  
  
4.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Pour modifier un filtre de colonne de manière à supprimer des colonnes pour un article publié dans une publication transactionnelle ou d'instantané  
  
1.  Sur la base de données de publication de l’éditeur, exécutez [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) une fois pour chaque colonne en cours de suppression. Spécifiez le nom de la colonne pour **@column** et affectez la valeur **drop** à **@operation**.  
  
2.  Sur la base de données de publication de l’éditeur, exécutez [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Spécifiez le nom de la publication pour **@publication** et le nom de l'article filtré pour **@article**. Si la publication possède des abonnements existants, spécifiez une valeur de **1** de **@change_active**. Les objets de synchronisation pour l'article filtré sont alors recréés.  
  
3.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour.  
  
4.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Pour définir un filtre de colonne pour un article publié dans une publication de fusion  
  
1.  Définissez l'article à filtrer. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Sur la base de données de publication de l’éditeur, exécutez [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md). Les colonnes à inclure ou à supprimer de l'article sont alors définies.  
  
    -   Si seulement quelques colonnes d’une table contenant de nombreuses colonnes de publication, exécutez [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) une fois pour chaque colonne ajoutée. Spécifiez le nom de la colonne pour **@column** et affectez la valeur **add** à **@operation**.  
  
    -   Si la publication de la plupart des colonnes dans une table contenant de nombreuses colonnes, exécutez [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), la valeur **null** pour **@column** et une valeur de **Ajouter** pour **@operation** pour ajouter toutes les colonnes. Puis exécutez [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), une fois pour chaque colonne exclue, spécifiant la valeur **Supprimer** pour **@operation** et le nom de la colonne exclue pour **@column**.  
  
#### Pour modifier un filtre de colonne de manière à inclure des colonnes supplémentaires pour un article publié dans une publication de fusion  
  
1.  Sur la base de données de publication de l’éditeur, exécutez [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) une fois pour chaque colonne ajoutée. Spécifiez le nom de colonne pour **@column**, une valeur de **Ajouter** pour **@operation** et une valeur de **1** pour les deux **@force_invalidate_snapshot** et **@force_reinit_subscription**.  
  
2.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour.  
  
3.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Pour modifier un filtre de colonne de manière à supprimer des colonnes pour un article publié dans une publication de fusion  
  
1.  Sur la base de données de publication de l’éditeur, exécutez [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) une fois pour chaque colonne en cours de suppression. Spécifiez le nom de colonne pour **@column**, une valeur de **Supprimer** pour **@operation** et une valeur de **1** pour les deux **@force_invalidate_snapshot** et **@force_reinit_subscription**.  
  
2.  Exécutez de nouveau le travail de l'Agent d'instantané pour la publication afin de générer un instantané mis à jour.  
  
3.  Réinitialiser les abonnements. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Dans cet exemple de réplication transactionnelle, la colonne `DaysToManufacture` est supprimée d'un article reposant sur la table `Product` .  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_1.sql)]  
  
 Dans cet exemple de réplication de fusion, la colonne `CreditCardApprovalCode` est supprimée d'un article reposant sur la table `SalesOrderHeader` .  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_2.sql)]  
  
## Voir aussi  
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Filtrer des données publiées](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtrer des données publiées en vue de la réplication de fusion](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  