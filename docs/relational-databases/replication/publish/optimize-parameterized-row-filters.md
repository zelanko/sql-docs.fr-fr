---
title: "Optimiser les filtres de lignes param&#233;trables | Microsoft Docs"
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
  - "partitions précalculées [réplication SQL Server]"
  - "filtres paramétrés [réplication SQL Server]"
  - "fusionner des partitions précalculées de réplication [réplication SQL Server], SQL Server Management Studio"
  - "filtres paramétrés [réplication SQL Server]"
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Optimiser les filtres de lignes param&#233;trables
  Cette rubrique explique comment optimiser les filtres de lignes paramétrables dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour optimiser les filtres de lignes paramétrables à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Lorsque vous utilisez des filtres paramétrables, vous pouvez contrôler le traitement de ces filtres par la réplication de fusion en spécifiant l'option **use partition groups** ou l'option **keep partition changes** au moment de la création d'une publication. Ces options améliorent les performances de la synchronisation des publications avec articles filtrés en stockant des métadonnées supplémentaires dans la base de données de publication. Vous pouvez contrôler le partage des données entre les Abonnés en définissant **partition options** au moment de la création d'un article. Pour plus d'informations sur ces conditions requises, consultez [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
     Avec les abonnés SQL Server Compact de [!INCLUDE[ssEW](../../../includes/ssew-md.md)], keep_partition_changes doit avoir la valeur true afin que les suppressions soient correctement propagées. Lorsque la valeur est false, l'abonné peut avoir plus de lignes que prévu.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Les paramètres suivants permettent d'optimiser les filtres de lignes paramétrés :  
  
 **Options de la partition**  
 Définir cette option sur le **propriétés** page de le **Propriétés de l’Article - \< Article>** boîte de dialogue, ou dans le **Ajouter un filtre** boîte de dialogue. Les deux boîtes de dialogue sont disponibles dans l’Assistant Nouvelle Publication et **Propriétés de la Publication - \< Publication>** boîte de dialogue. Le **Propriétés de l’Article - \< Article>** boîte de dialogue vous permet de spécifier des valeurs supplémentaires pour cette option qui ne sont pas disponibles dans le **Ajouter un filtre** boîte de dialogue.  
  
 **Précalculer les partitions**  
 Cette option est définie sur **True** par défaut si les articles de votre publication respectent un ensemble de spécifications. Pour plus d’informations sur ces exigences, consultez [optimiser les performances de filtre paramétré avec des Partitions précalculées](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md). Modifiez cette option dans la **Options d’abonnement** page de la **Propriétés de la Publication - \< Publication>** boîte de dialogue.  
  
 **Optimiser la synchronisation**  
 Cette option doit être définie sur **True** uniquement si **Précalculer les Partitions** est définie sur **False**. Définir cette option sur le **Options d’abonnement** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue.  
  
 Pour plus d’informations sur l’utilisation de l’Assistant Nouvelle Publication et l’accès à la **Propriétés de la Publication - \< Publication>** boîte de dialogue, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour définir les options de la partition dans la boîte de dialogue Ajouter un filtre ou Modifier le filtre  
  
1.  Sur le **filtrer les lignes de Table** page de l’Assistant Nouvelle Publication ou le **filtrer les lignes** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **Ajouter**, puis cliquez sur **Ajouter un filtre**.  
  
2.  Créer un filtre paramétré. Pour plus d'informations, consultez [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
3.  Sélectionnez l'option qui correspond aux données qui seront partagées entre des Abonnés :  
  
    -   **Une ligne de cette table ira à plusieurs abonnements**  
  
    -   **Filtre paramétré créant des partitions qui ne se chevauchent pas, avec un seul abonnement par partition**  
  
     Si vous sélectionnez **Filtre paramétré créant des partitions qui ne se chevauchent pas, avec un seul abonnement par partition**, la réplication de fusion peut optimiser les performances en stockant et en traitant moins de métadonnées. Cependant, vous devez vérifier que les données sont partitionnées de telle façon qu'une ligne ne peut pas être répliquée sur plus d'un Abonné. Pour plus d'informations, consultez la section « Définition de « partition options » » dans la rubrique [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### Pour définir les Options de Partition dans les propriétés de l’Article - \< Article> boîte de dialogue  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table, puis cliquez sur **Propriétés de l’Article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de la table en surbrillance** ou **Définir les propriétés de tous les articles de la table**.  
  
3.  Dans la **objet de Destination** section de la **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue, spécifiez une des valeurs suivantes pour **les Options de Partition**:  
  
    -   **Chevauchement**  
  
    -   **Chevauchement ; refus des modifications de données hors partition**  
  
    -   **Non-chevauchement ; abonnement unique**  
  
    -   **Non-chevauchement ; partage entre les abonnements**  
  
     Pour plus d'informations sur ces options et sur leurs liens avec les options disponibles dans les boîtes de dialogue **Ajouter un filtre** et **Modifier le filtre** , consultez la section relative à la définition de la propriété « partition options » dans la rubrique [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### Pour définir Précalculer les partitions  
  
1.  Sur le **Options d’abonnement** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une valeur pour le **Précalculer les Partitions** option. Cette propriété est en lecture seule si :  
  
    -   La publication ne satisfait pas aux conditions requises pour les partitions précalculées.  
  
    -   Aucun instantané n'a encore été généré pour la publication. Dans ce cas, l'option affiche la valeur **Définir automatiquement lorsqu'un instantané est créé**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Pour définir Optimiser la synchronisation  
  
1.  Sur le **Options d’abonnement** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez la valeur **True** pour la **optimiser la synchronisation** option.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Pour la définition des options de filtrage de **@keep_partition_changes** et **@use_partition_groups**, consultez [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
#### Pour spécifier des optimisations du filtre de fusion au moment de la création d'une publication  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Spécifiez **@publication** et affectez la valeur **true** à l'un des paramètres suivants :  
  
    -   **@use_partition_groups**:-l’optimisation des performances le plus élevée, fournie que les articles soient conformes à la configuration requise pour les partitions précalculées. Pour plus d’informations, consultez [optimiser les performances de filtre paramétré avec des Partitions précalculées](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
    -   **@keep_partition_changes** -Utilisez cette optimisation si les partitions précalculées ne peuvent pas être utilisées.  
  
2.  Ajoutez un travail d'instantané pour la publication. Pour plus d’informations, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), spécifiez les paramètres suivants :  
  
    -   **@publication** -le nom de la publication de l’étape 1.  
  
    -   **@article** -nom de l’article  
  
    -   **@source_object** - l’objet de base de données en cours de publication.  
  
    -   **@subset_filterclause** -la clause de filtre paramétrable facultative utilisée pour filtrer horizontalement l’article.  
  
    -   **@partition_options** -options de partition pour l’article filtré.  
  
4.  Répétez l'étape 3 pour chaque article de la publication.  
  
5.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) pour définir un filtre de jointure entre deux articles. Pour plus d'informations, voir [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
#### Pour afficher et modifier les comportements de filtre de fusion d'une publication existante  
  
1.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), en spécifiant **@publication**. Notez la valeur de **keep_partition_changes** et **use_partition_groups** dans le résultat défini.  
  
2.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Spécifiez la valeur **use_partition_groups** pour **@property** et **true** ou **false** pour **@value**.  
  
3.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Spécifiez la valeur **keep_partition_changes** pour **@property** et **true** ou **false** pour **@value**.  
  
    > [!NOTE]  
    >  Lors de l’activation **keep_partition_changes**, vous devez d’abord désactiver **use_partition_groups** et spécifiez une valeur de **1** pour **@force_reinit_subscription**.  
  
4.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez la valeur **partition_options** pour **@property** et la valeur appropriée pour **@value**. Consultez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) pour les définitions de ces options de filtrage.  
  
5.  (Facultatif) Lancez l'Agent d'instantané afin de régénérer l'instantané si nécessaire. Pour plus d’informations sur les modifications nécessitent un nouvel instantané doit être généré, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## Voir aussi  
 [Générer automatiquement un ensemble de filtres de jointure entre les Articles de fusion & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md)   
 [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Filtres de lignes paramétrés](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  