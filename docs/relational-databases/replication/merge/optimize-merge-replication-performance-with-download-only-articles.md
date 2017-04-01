---
title: "Optimiser les performances de la r&#233;plication de fusion avec les articles en t&#233;l&#233;chargement seul | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "merge replication [SQL Server replication], download-only articles"
  - "articles [SQL Server replication], download-only"
  - "articles disponibles uniquement par téléchargement"
ms.assetid: 8851faa6-e6df-4ea5-a6ea-2a3471680fa3
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Optimiser les performances de la r&#233;plication de fusion avec les articles en t&#233;l&#233;chargement seul
  La réplication de fusion propose deux types d'articles différents permettant de répondre aux différents besoins des applications. Les publications peuvent contenir un ou plusieurs de chacun de ces types d'articles en fonction de l'application :  
  
-   Articles standards  
  
-   Articles en téléchargement seul  
  
 Les articles en téléchargement seul offrent de meilleures performances par rapport aux articles standards et doivent être utilisés au moment opportun.  
  
> [!NOTE]  
>  Afin d'utiliser les articles en téléchargement seul, le niveau de compatibilité de la publication doit être au moins 90RTM.  
  
## Articles standards  
 Les articles standards sont les articles par défaut, et offrent la gamme complète des fonctionnalités de la réplication de fusion, y compris la détection et la résolution des conflits. Les articles standard sont appropriés aux tables mises à jour par plusieurs abonnés ; les objets autres que les tables, comme les procédures stockées et les vues, sont toujours publiés en tant qu'articles standard.  
  
## Articles en téléchargement seul  
 Les articles en téléchargement seul sont conçus pour les applications dont les données ne sont pas mises à jour sur les abonnés, comme un ensemble d'articles ne faisant pas partie d'un catalogue de produits. Un catalogue de produits est généralement mis à jour sur le serveur de publication, mais pas sur les abonnés. Étant donné que les articles disponibles uniquement par téléchargement ne peuvent pas être mis à jour sur l'abonné, le suivi des métadonnées n'est pas envoyé aux abonnés. Cela peut aboutir à une réduction du stockage sur les abonnés et à un gain de performances, notamment si la connexion réseau est lente.  
  
 Les articles en téléchargement uniquement fonctionnent conjointement avec les abonnements clients : si un article est considéré comme en téléchargement seul, les lignes de cet article ne peuvent pas être insérées, mises à jour ou supprimées pour les abonnés utilisant des abonnements clients. Les serveurs de publication et les abonnés qui utilisent le type d'abonnement serveur (généralement les abonnés qui publient à nouveau des données sur d'autres abonnés) peuvent insérer, mettre à jour et supprimer des données. Pour plus d’informations sur les abonnements clients, consultez la page [s’abonner aux Publications](../../../relational-databases/replication/subscribe-to-publications.md).  
  
 Pour spécifier qu’un article est en téléchargement uniquement, consultez [spécifier une Table de fusion est uniquement](../../../relational-databases/replication/publish/specify-that-a-merge-table-article-is-download-only.md).  
  
## Utilisation de différents types d'articles dans vos applications  
 Grâce à la compréhension des besoins de votre application, vous pouvez faire des compromis entre flexibilité maximale et performance optimale. Par exemple, les applications comportant de nombreux conflits et modifications, à la fois sur le serveur de publication et sur les abonnés, utiliseront une publication composée d'articles standards. Certaines applications, comme une application d'automatisation des forces de vente, peuvent comporter des articles potentiellement conflictuels et d'autres articles fonctionnant comme des tables de correspondances, pouvant être spécifiés comme étant en téléchargement seul. Les applications d'entrée de données, comme les systèmes de points de vente et les applications d'automatisation des groupes opérationnels, partitionnent souvent les données de façon à éliminer les conflits, et les données d'un abonné ne vont jamais vers un autre. Dans ces situations, une combinaison de partitions ne se chevauchant pas, d'articles en téléchargement seul et de partitions précalculées offre des performances et une évolutivité maximales. Pour plus d’informations sur les partitions ne se chevauchant pas et les partitions précalculées, consultez [filtres de lignes paramétrable](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
## Voir aussi  
 [Options d'articles pour la réplication de fusion](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Optimiser les performances de la réplication de fusion avec le suivi conditionnel des suppressions](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  