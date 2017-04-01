---
title: "Ajouter et supprimer des articles de publications existantes | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "articles [réplication SQL Server], suppression"
  - "suppression d'articles"
  - "removing articles"
  - "abandon d'articles"
  - "ajout d'articles"
  - "administration de la réplication, articles"
  - "publications [réplication SQL Server], ajout et suppression d’articles"
  - "articles [réplication SQL Server], ajout"
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# Ajouter et supprimer des articles de publications existantes
  Après la création d'une publication, il est possible d'ajouter et de supprimer des articles. Vous pouvez ajouter des articles à tout moment ; en revanche, les actions visant à supprimer les articles dépendent du type de réplication et du moment de la suppression de l'article.  
  
## Ajout d'articles  
 L'ajout d'un article se déroule comme suit : ajout de l'article à la publication, création d'un nouvel instantané de la publication, synchronisation de l'abonnement pour appliquer le schéma et les données du nouvel article.  
  
> [!NOTE]  
>  Si vous ajoutez un article à une publication de fusion et un article existant dépend du nouvel article, vous devez spécifier un ordre de traitement pour les deux articles à l’aide de la **@processing_order** paramètre de [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) et [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Examinez le scénario suivant : vous publiez une table, mais vous ne publiez pas de fonction référencée par la table. Si vous ne publiez pas la fonction, la table ne peut pas être créée au niveau de l'abonné. Lorsque vous ajoutez la fonction à la publication : spécifiez la valeur **1** pour la **@processing_order** paramètre de **sp_addmergearticle**; et spécifiez une valeur de **2** pour la **@processing_order** paramètre de **sp_changemergearticle**, en spécifiant le nom de table pour le paramètre **@article**. Cet ordre de traitement permet de créer la fonction au niveau de l'Abonné avant la table qui en dépend. Vous pouvez utiliser différents nombres pour chaque article tant que le nombre de la fonction est inférieur au nombre de la table.  
  
1.  Ajoutez un ou plusieurs articles à l'aide de l'une des méthodes suivantes :  
  
    -   [Ajouter et supprimer des Articles d’une Publication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)  
  
2.  Après l'ajout d'un article à une publication, vous devez créer un nouvel instantané de celle-ci (et de toutes les partitions s'il s'agit d'une publication de fusion avec des filtres paramétrés). L'Agent de distribution ou de fusion copie ensuite le schéma et les données du nouvel article vers l'Abonné (il ne réinitialise pas l'ensemble de la publication).  
  
    -   Pour créer un nouvel instantané, consultez [créer et appliquer la capture instantanée initiale](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    -   Pour créer un nouvel instantané pour une publication de fusion avec des filtres paramétrés, consultez [créer un instantané pour une Publication de fusion avec des filtres paramétrés](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
3.  Après la création de l'instantané, synchronisez l'abonnement pour copier le schéma et les données du nouvel article.  
  
    -   Pour synchroniser un abonnement envoyé, consultez [synchroniser un abonnement envoyé](../../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
    -   Pour synchroniser un abonnement par extraction de données, consultez [synchroniser un abonnement par extraction de données](../../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
## Suppression d'articles  
 Les articles peuvent être supprimés d'une publication à tout moment mais vous devez prendre en compte les comportements suivants :  
  
-   La suppression d'un article d'une publication ne supprime pas l'objet de la base de données de publication ou l'objet correspondant de la base de données d'abonnement. Utilisez DROP \< objet> pour supprimer ces objets, si nécessaire. Lorsque vous supprimez un article qui est lié à d’autres articles publiés par le biais des contraintes de clé étrangères, nous vous recommandons de supprimer la table sur l’abonné manuellement ou à l’aide de l’exécution du script de la demande : spécifiez un script qui inclut le dépôt appropriée \< objet> instructions. Pour plus d’informations, consultez [exécuter les Scripts pendant la synchronisation & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md).  
  
-   Pour les publications de fusion présentant un niveau de compatibilité égal ou supérieur à 90RTM, les articles peuvent être supprimés à tout moment mais un nouvel instantané s'impose. De plus :  
  
    -   Si l'article est un article parent dans une relation d'enregistrement logique ou de filtre de jointure, vous devez commencer par supprimer les relations, ce qui nécessite une réinitialisation.  
  
    -   Si un article possède le dernier filtre paramétré d'une publication, les abonnements doivent être réinitialisés.  
  
-   Pour les publications de fusion présentant un niveau de compatibilité inférieur à 90RTM, il est possible de supprimer les articles sans considérations particulières avant la synchronisation initiale des abonnements. Si un article est supprimé après la synchronisation d'un ou plusieurs abonnements, les abonnements doivent être supprimés, recréés et synchronisés.  
  
-   Pour les publications transactionnelles ou d'instantané, les articles peuvent être supprimés sans considérations particulières avant la création des abonnements. Si un article est supprimé après la création d'un ou plusieurs abonnements, les abonnements doivent être supprimés, recréés et synchronisés. Pour plus d’informations sur la suppression des abonnements, consultez la page [s’abonner aux Publications](../../../relational-databases/replication/subscribe-to-publications.md) et [sp_dropsubscription & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). **sp_dropsubscription** vous permet de supprimer un article unique de l’abonnement au lieu de l’ensemble de l’abonnement.  
  
1.  La suppression d'un article d'une publication consiste à supprimer l'article et à créer un nouvel instantané de la publication. Dans la mesure où la suppression d'un article invalide l'instantané actuel, un nouvel instantané doit être créé.  
  
    -   Pour supprimer un article d’une publication, consultez [Ajouter et supprimer des Articles d’une Publication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md) ou [Supprimer un Article](../../../relational-databases/replication/publish/delete-an-article.md).  
  
2.  Après la suppression d'un article d'une publication, vous devez créer un nouvel instantané de celle-ci (et de toutes les partitions s'il s'agit d'une publication de fusion avec des filtres paramétrés).  
  
    -   Pour créer un nouvel instantané, consultez [créer et appliquer la capture instantanée initiale](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    -   Pour créer un nouvel instantané pour une publication de fusion avec des filtres paramétrés, consultez [créer un instantané pour une Publication de fusion avec des filtres paramétrés](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 Comme indiqué ci-dessus, la suppression d'un article exige parfois la suppression, la recréation et la synchronisation des abonnements. Pour plus d’informations, consultez la page [s’abonner aux Publications](../../../relational-databases/replication/subscribe-to-publications.md) et [synchroniser les données](../../../relational-databases/replication/synchronize-data.md).  
  
## Voir aussi  
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Réinitialiser des abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Modifier le schéma dans les bases de données de publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  