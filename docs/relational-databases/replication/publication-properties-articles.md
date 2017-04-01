---
title: "Propri&#233;t&#233;s de la publication, Articles | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.articles.f1"
ms.assetid: bdeea318-a153-44b8-9e51-9155f3bad18b
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Propri&#233;t&#233;s de la publication, Articles
  Le **Articles** page de le **Propriétés de la Publication** boîte de dialogue : contient des informations sur les articles d’une publication ; permet d’ajouter ou de supprimer des articles de publications existantes, et vous permet de modifier les propriétés de l’article et le filtrage de colonne.  
  
> [!NOTE]  
>  Après qu'une publication a été créée, certaines modifications de propriétés nécessitent un nouvel instantané. Si une publication dispose d'abonnements, ces abonnements pourraient devoir alors être réinitialisés selon les modifications que vous avez apportées. Pour plus d’informations, consultez [Publication de modification et les propriétés de l’Article](../../relational-databases/replication/publish/change-publication-and-article-properties.md) et [Ajouter et supprimer des Articles de Publications existantes](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 Si vous publiez un objet de base de données qui dépend d'un ou de plusieurs autres objets de base de données, vous devez publier tous les objets référencés. Par exemple, si vous publiez une vue qui dépend d'une table, vous devez publier la table également.  
  
 Une icône rouge apparaît en regard des objets ne pouvant pas être publiés, avec une explication dans le panneau d'information se trouvant en bas de la page de l'Assistant. Les objets suivants ne peuvent pas être publiés :  
  
-   Les objets chiffrés.  
  
-   Les vues indexées contenant des colonnes autorisant la valeur NULL.  
  
-   Les tables ne possédant pas de clé primaire ne peuvent pas être publiées dans des publications transactionnelles.  
  
-   Les tables ne peuvent en effet pas être publiées à la fois dans une publication de fusion et une publication transactionnelle avec l'option de mise à jour d'abonnements en attente activée. Pour plus d’informations sur la publication d’un article dans plusieurs publications, consultez la section « Publication de Tables dans plusieurs publications » dans [publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
## Serveurs de publication Oracle  
 Des points supplémentaires sont également à prendre en compte dans le cas d'utilisation de serveur de publication Oracle :  
  
-   Pour obtenir la liste des objets qui peuvent être publiés à partir d’Oracle, consultez [Considérations et Limitations pour les serveurs de publication Oracle](../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md). Les objets qui ne peuvent pas être publiés ne sont pas affichés.  
  
-   Pour obtenir la liste des types de données qui peuvent être publiés, consultez [mappage de Type de données pour les serveurs de publication Oracle](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md). Les colonnes dont le type de données ne peut pas être publié ne sont pas affichées.  
  
## Filtres de colonnes  
 Filtrer les colonnes de cette page en développant une table dans la **objets à publier** volet, puis en sélectionnant uniquement les colonnes nécessaires (lignes peuvent être filtrés dans la **filtrer les lignes de Table** page de l’Assistant). Le filtrage de colonnes s'avère utile pour de nombreuses raisons, notamment en ce qui a trait à la sécurité (contribuant à protéger des données sensibles contre toute réplication) et aux performances (empêchant par exemple la réplication d'objets binaires volumineux, appelés également Blob pour Bynary Large OBjects). Pour plus d’informations sur le filtrage de colonne, y compris une liste des types de colonne ne peuvent pas être filtrées, consultez [filtrer les données publiées](../../relational-databases/replication/publish/filter-published-data.md).  
  
## Options  
 Le **objets à publier** volet vous permet de :  
  
-   d'afficher tous les objets disponibles à la réplication ;  
  
-   d'ajouter un article à une publication en activant la case à cocher en regard de l'objet ;  
  
-   de supprimer un article d'une publication en désactivant la case à cocher en regard de l'objet. Pour savoir quand les articles peuvent être supprimés, consultez [Ajouter et supprimer des Articles de Publications existantes](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Inclure tous les objets d’un type particulier (par exemple, une table) dans la publication en activant la case à cocher en regard de l’objet type (tel que **Tables**).  
  
-   de développer les nœuds de la table pour en afficher les colonnes ;  
  
-   de filtrer les colonnes d'une table d'une publication en désactivant la case à cocher en regard de la colonne, ou encore d'inclure les colonnes non publiées en activant au contraire leurs cases à cocher ;  
  
-   enfin, de cliquer sur un objet dans le volet avec le bouton droit de la souris afin d'afficher un menu répertoriant les commandes applicables à cet objet.  
  
 **Propriétés de l'article**  
 Cliquez sur **Propriétés de l’Article** , puis cliquez sur une des opérations suivantes :  
  
-   Cliquez sur **définir les propriétés de sélectionné \< ObjectType> Article** pour lancer le **Propriétés de l’Article - \< ObjectName>** boîte de dialogue ; la propriété modifications apportées dans cette boîte de dialogue sont appliquées uniquement à l’objet qui est mis en surbrillance dans le volet de l’objet sur le **Articles** page.  
  
-   Cliquez sur **Propriétés de tous \< ObjectType> Articles**, pour lancer le **pour toutes les propriétés de \< ObjectType> Articles** boîte de dialogue ; la propriété modifications apportées dans cette boîte de dialogue sont appliquées à tous les objets de ce type dans le volet de l’objet sur le **Articles** page, y compris celles non encore activée pour la publication.  
  
    > [!NOTE]  
    >  Apportées aux propriétés dans le **pour toutes les propriétés de \< ObjectType> Articles** boîte de dialogue remplacer celles effectuées précédemment dans le **Propriétés de l’Article - \< nomobjet>** boîte de dialogue. Ainsi, si vous voulez définir un certain nombre de valeurs par défaut applicables à tous les articles d'un type d'objet mais souhaitez également définir des propriétés pour des objets spécifiques, vous devez d'abord définir les valeurs par défaut pour tous les articles. Définissez ensuite les propriétés des objets individuels.  
  
 **La table sélectionnée est en téléchargement seul**  
 Réplication de fusion uniquement. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Permet d'indiquer que les modifications sont interdites au niveau de l'Abonné si l'abonnement d'un client est utilisé. Étant donné que les articles disponibles uniquement par téléchargement ne peuvent pas être mis à jour sur l'abonné, le suivi des métadonnées n'est pas envoyé aux abonnés. Cela peut aboutir à une réduction du stockage sur les abonnés et à un gain de performances, notamment si la connexion réseau est lente. Cette option correspond à la valeur **Téléchargement seul pour l’abonné, interdire les modifications de l’abonné** pour l’option **la direction de synchronisation** dans les **Propriétés de l’Article** boîte de dialogue. Pour plus d’informations, consultez [optimiser les performances de réplication de fusion avec des Articles avec](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **Afficher uniquement les objets activés dans la liste**  
 Activez cette case à cocher pour n'afficher que les articles sélectionnés dans le volet des objets.  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Créer et appliquer l'instantané initial](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Réinitialiser un abonnement](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  