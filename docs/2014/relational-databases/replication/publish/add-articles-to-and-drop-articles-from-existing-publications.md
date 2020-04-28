---
title: Ajouter et supprimer des articles de publications existantes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- removing articles
- dropping articles
- adding articles
- administering replication, articles
- publications [SQL Server replication], adding and dropping articles
- articles [SQL Server replication], adding
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 523891f2f0005c7f6e6752e5d16d3680f680fdfa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73882340"
---
# <a name="add-articles-to-and-drop-articles-from-existing-publications"></a>Ajouter et supprimer des articles de publications existantes
  Après la création d'une publication, il est possible d'ajouter et de supprimer des articles. Vous pouvez ajouter des articles à tout moment ; en revanche, les actions visant à supprimer les articles dépendent du type de réplication et du moment de la suppression de l'article.  
  
## <a name="adding-articles"></a>ajout d'articles  
 L'ajout d'un article se déroule comme suit : ajout de l'article à la publication, création d'un nouvel instantané de la publication, synchronisation de l'abonnement pour appliquer le schéma et les données du nouvel article.  
  
> [!NOTE]
>  Si vous ajoutez un article à une publication de fusion et qu’un article existant dépend du nouvel article, vous devez spécifier un ordre de traitement pour les deux ** \@** Articles à l’aide du paramètre processing_order de [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) et [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Examinez le scénario suivant : vous publiez une table, mais vous ne publiez pas de fonction référencée par la table. Si vous ne publiez pas la fonction, la table ne peut pas être créée au niveau de l'abonné. Quand vous ajoutez la fonction à la publication : spécifiez la valeur **1** pour le paramètre **\@processing_order** de **sp_addmergearticle**, spécifiez la valeur **2** pour le paramètre **\@processing_order** de **sp_changemergearticle** et spécifiez le nom de la table pour le paramètre **\@article**. Cet ordre de traitement permet de créer la fonction au niveau de l'Abonné avant la table qui en dépend. Vous pouvez utiliser différents nombres pour chaque article tant que le nombre de la fonction est inférieur au nombre de la table.  
  
1.  Ajoutez un ou plusieurs articles à l'aide de l'une des méthodes suivantes :  
  
    -   [Ajouter et supprimer des articles dans une publication &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [Définir un article](define-an-article.md)  
  
2.  Après l'ajout d'un article à une publication, vous devez créer un nouvel instantané de celle-ci (et de toutes les partitions s'il s'agit d'une publication de fusion avec des filtres paramétrés). L'Agent de distribution ou de fusion copie ensuite le schéma et les données du nouvel article vers l'Abonné (il ne réinitialise pas l'ensemble de la publication).  
  
    -   Pour créer un nouvel instantané, consultez [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
    -   Pour créer un instantané d’une publication de fusion avec des filtres paramétrés, consultez [Créer un instantané pour une publication de fusion avec des filtres paramétrés](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
3.  Après la création de l'instantané, synchronisez l'abonnement pour copier le schéma et les données du nouvel article.  
  
    -   Pour synchroniser un abonnement par émission de données (push), consultez [Synchronize a Push Subscription](../synchronize-a-push-subscription.md).  
  
    -   Pour synchroniser un abonnement par extraction de données (pull), consultez [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).  
  
## <a name="dropping-articles"></a>abandon d'articles  
 Les articles peuvent être supprimés d'une publication à tout moment mais vous devez prendre en compte les comportements suivants :  
  
-   La suppression d'un article d'une publication ne supprime pas l'objet de la base de données de publication ou l'objet correspondant de la base de données d'abonnement. Utilisez DROP \<objet> pour supprimer ces objets, le cas échéant. Lorsque vous supprimez un article lié à d’autres articles publiés par l’intermédiaire de contraintes de clés étrangères, il est conseillé de supprimer manuellement la table sur l’Abonné ou d’avoir recours à une exécution de script à la demande : spécifiez un script qui comprend les instructions DROP \<objet> appropriées. Pour plus d’informations, consultez [Exécuter des scripts pendant la synchronisation &#40;programmation Transact-SQL de la réplication&#41;](../execute-scripts-during-synchronization-replication-transact-sql-programming.md).  
  
-   Pour les publications de fusion présentant un niveau de compatibilité égal ou supérieur à 90RTM, les articles peuvent être supprimés à tout moment mais un nouvel instantané s'impose. De plus :  
  
    -   Si l'article est un article parent dans une relation d'enregistrement logique ou de filtre de jointure, vous devez commencer par supprimer les relations, ce qui nécessite une réinitialisation.  
  
    -   Si un article possède le dernier filtre paramétré d'une publication, les abonnements doivent être réinitialisés.  
  
-   Pour les publications de fusion présentant un niveau de compatibilité inférieur à 90RTM, il est possible de supprimer les articles sans considérations particulières avant la synchronisation initiale des abonnements. Si un article est supprimé après la synchronisation d'un ou plusieurs abonnements, les abonnements doivent être supprimés, recréés et synchronisés.  
  
-   Pour les publications transactionnelles ou d'instantané, les articles peuvent être supprimés sans considérations particulières avant la création des abonnements. Si un article est supprimé après la création d'un ou plusieurs abonnements, les abonnements doivent être supprimés, recréés et synchronisés. Pour plus d’informations sur la suppression des abonnements, consultez [S’abonner à des publications](../subscribe-to-publications.md) et [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql). **sp_dropsubscription** permet de supprimer un seul article de l'abonnement au lieu de l'abonnement entier.  
  
1.  La suppression d'un article d'une publication consiste à supprimer l'article et à créer un nouvel instantané de la publication. Dans la mesure où la suppression d'un article invalide l'instantané actuel, un nouvel instantané doit être créé.  
  
    -   Pour supprimer un article d’une publication, consultez [Ajouter et supprimer des articles dans une publication &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) ou [Supprimer un article](delete-an-article.md).  
  
2.  Après la suppression d'un article d'une publication, vous devez créer un nouvel instantané de celle-ci (et de toutes les partitions s'il s'agit d'une publication de fusion avec des filtres paramétrés).  
  
    -   Pour créer un nouvel instantané, consultez [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
    -   Pour créer un instantané d’une publication de fusion avec des filtres paramétrés, consultez [Créer un instantané pour une publication de fusion avec des filtres paramétrés](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 Comme indiqué ci-dessus, la suppression d'un article exige parfois la suppression, la recréation et la synchronisation des abonnements. Pour plus d’informations, consultez [S’abonner à des publications](../subscribe-to-publications.md).et[Synchronisez les données](../synchronize-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](publish-data-and-database-objects.md)   
 [Réinitialiser les abonnements](../reinitialize-subscriptions.md)   
 [Modifier le schéma dans les bases de données de publication](make-schema-changes-on-publication-databases.md)  
  
  
