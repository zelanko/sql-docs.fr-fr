---
title: Optimiser les filtres de lignes paramétrables | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
caps.latest.revision: 42
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95cd675d8c774b7b0321eb3ffc15e1c15a213f20
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242259"
---
# <a name="optimize-parameterized-row-filters"></a>Optimiser les filtres de lignes paramétrables
  Cette rubrique explique comment optimiser les filtres de lignes paramétrables dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour optimiser les filtres de lignes paramétrables à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Lorsque vous utilisez des filtres paramétrables, vous pouvez contrôler le traitement de ces filtres par la réplication de fusion en spécifiant l'option **use partition groups** ou l'option **keep partition changes** au moment de la création d'une publication. Ces options améliorent les performances de la synchronisation des publications avec articles filtrés en stockant des métadonnées supplémentaires dans la base de données de publication. Vous pouvez contrôler le partage des données entre les Abonnés en définissant **partition options** au moment de la création d'un article. Pour plus d'informations sur ces conditions requises, consultez [Filtres de lignes paramétrable](../merge/parameterized-filters-parameterized-row-filters.md).  
  
     Avec les abonnés SQL Server Compact de [!INCLUDE[ssEW](../../../includes/ssew-md.md)], keep_partition_changes doit avoir la valeur true afin que les suppressions soient correctement propagées. Lorsque la valeur est false, l'abonné peut avoir plus de lignes que prévu.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Les paramètres suivants permettent d'optimiser les filtres de lignes paramétrés :  
  
 **Partition Options**  
 Définissez cette option dans la page **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>**, ou dans la boîte de dialogue **Ajouter un filtre**. Ces deux boîtes de dialogue sont disponibles dans l’Assistant Nouvelle publication et dans la boîte de dialogue **Propriétés de la publication - \<Publication>**. La boîte de dialogue **Propriétés de l’article - \<Article>** permet de spécifier pour cette option des valeurs supplémentaires qui ne sont pas disponibles dans la boîte de dialogue **Ajouter un filtre**.  
  
 **Précalculer les partitions**  
 Par défaut, cette option est définie à **True** si les articles de votre publication satisfont à un ensemble de conditions. Pour plus d’informations sur ces exigences, consultez [Optimiser les performances des filtres paramétrables avec des partitions précalculées](../merge/parameterized-filters-optimize-for-precomputed-partitions.md). Modifiez cette option dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**.  
  
 **Optimiser la synchronisation**  
 Cette option ne doit être définie à **True** que si **Précalculer les partitions** est défini à **False**. Définissez cette option dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**.  
  
 Pour plus d’informations sur l’utilisation de l’Assistant Nouvelle publication et sur l’accès à la boîte de dialogue **Propriétés de la publication- \<Publication>**, consultez [Créer une publication](create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a>Pour définir les options de la partition dans la boîte de dialogue Ajouter un filtre ou Modifier le filtre  
  
1.  Dans la page **Filtrer les lignes de la table** de l’Assistant Nouvelle publication, ou la page **Filtrer les lignes** de la boîte de dialogue **Propriétés de la Publication - \<Publication>**, cliquez sur **Ajouter**, puis sur **Ajouter un filtre**.  
  
2.  Créer un filtre paramétrable. Pour plus d'informations, consultez [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
3.  Sélectionnez l'option qui correspond aux données qui seront partagées entre des Abonnés :  
  
    -   **Une ligne de cette table ira à plusieurs abonnements**  
  
    -   **Filtre paramétré créant des partitions qui ne se chevauchent pas, avec un seul abonnement par partition**  
  
     Si vous sélectionnez **Filtre paramétré créant des partitions qui ne se chevauchent pas, avec un seul abonnement par partition**, la réplication de fusion peut optimiser les performances en stockant et en traitant moins de métadonnées. Cependant, vous devez vérifier que les données sont partitionnées de telle façon qu'une ligne ne peut pas être répliquée sur plus d'un Abonné. Pour plus d'informations, consultez la section « Définition de « partition options » » dans la rubrique [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>**, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a>Pour définir Options de la partition dans la boîte de dialogue Propriétés de l’article - \<Article>  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez une table et cliquez sur **Propriétés de l’article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de la table en surbrillance** ou **Définir les propriétés de tous les articles de la table**.  
  
3.  Dans la section **Objet de destination** de l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>**, spécifiez l’une des valeurs suivantes pour **Options de la partition** :  
  
    -   **Chevauchement**  
  
    -   **Chevauchement ; refus des modifications de données hors partition**  
  
    -   **Non-chevauchement ; abonnement unique**  
  
    -   **Non-chevauchement ; partage entre les abonnements**  
  
     Pour plus d'informations sur ces options et sur leurs liens avec les options disponibles dans les boîtes de dialogue **Ajouter un filtre** et **Modifier le filtre** , consultez la section relative à la définition de la propriété « partition options » dans la rubrique [Filtres de lignes paramétrables](../merge/parameterized-filters-parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>**, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### <a name="to-set-precompute-partitions"></a>Pour définir Précalculer les partitions  
  
1.  Dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez une valeur pour l’option **Précalculer les partitions**. Cette propriété est en lecture seule si :  
  
    -   La publication ne satisfait pas aux conditions requises pour les partitions précalculées.  
  
    -   Aucun instantané n'a encore été généré pour la publication. Dans ce cas, l'option affiche la valeur **Définir automatiquement lorsqu'un instantané est créé**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a>Pour définir Optimiser la synchronisation  
  
1.  Dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication**, sélectionnez la valeur **True** pour l’option **Optimiser la synchronisation**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Pour connaître la définition des options de filtrage **@keep_partition_changes** et **@use_partition_groups**, consultez [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a>Pour spécifier des optimisations du filtre de fusion au moment de la création d'une publication  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Spécifiez **@publication** et la valeur `true` pour l’une les paramètres suivants :  
  
    -   **@use_partition_groups**- optimisation maximale des performances, à condition que les articles soient conformes aux spécifications pour les partitions précalculées. Pour plus d’informations, consultez [Optimiser les performances des filtres paramétrés avec des partitions précalculées](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
    -   **@keep_partition_changes** - utilisez cette optimisation si les partitions précalculées ne peuvent pas être utilisées.  
  
2.  Ajoutez un travail d'instantané pour la publication. Pour plus d’informations, consultez [Créer une publication](create-a-publication.md).  
  
3.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) en spécifiant les paramètres suivants :  
  
    -   **@publication** - nom de la publication de l'étape 1  
  
    -   **@article** - nom de l'article  
  
    -   **@source_object** - objet de base de données qui est publié  
  
    -   **@subset_filterclause** - clause de filtre paramétrable facultative utilisée pour filtrer horizontalement l'article  
  
    -   **@partition_options** - options de partition pour l'article filtré  
  
4.  Répétez l'étape 3 pour chaque article de la publication.  
  
5.  (Facultatif) Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) pour définir un filtre de jointure entre deux articles. Pour plus d'informations, voir [Définir et modifier un filtre de jointure entre des articles de fusion](define-and-modify-a-join-filter-between-merge-articles.md).  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a>Pour afficher et modifier les comportements de filtre de fusion d'une publication existante  
  
1.  (Facultatif) Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), en spécifiant **@publication**. Notez la valeur de **keep_partition_changes** et **use_partition_groups** dans le jeu de résultats.  
  
2.  (Facultatif) Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Spécifiez la valeur **use_partition_groups** pour **@property** et `true` ou `false` pour **@value**.  
  
3.  (Facultatif) Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Spécifiez la valeur **keep_partition_changes** pour **@property** et `true` ou `false` pour **@value**.  
  
    > [!NOTE]  
    >  Si vous activez **keep_partition_changes**, vous devez commencer par désactiver **use_partition_groups** et affecter la valeur **1** à **@force_reinit_subscription**.  
  
4.  (Facultatif) Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Affectez la valeur **partition_options** à **@property** et la valeur appropriée à **@value**. Pour connaître la définition de ces options de filtrage, consultez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) .  
  
5.  (Facultatif) Lancez l'Agent d'instantané afin de régénérer l'instantané si nécessaire. Pour plus d’informations sur les modifications qui requièrent un nouvel instantané, consultez [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Générer automatiquement un ensemble de filtres de jointure entre des articles de fusion &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md)   
 [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Filtres de lignes paramétrables](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
