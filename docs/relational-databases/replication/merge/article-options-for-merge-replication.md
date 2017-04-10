---
title: "Options d&#39;articles pour la r&#233;plication de fusion | Microsoft Docs"
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
  - "réplication de fusion [réplication SQL Server], ordre d’article"
  - "articles [réplication SQL Server], options de réplication de fusion"
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Options d&#39;articles pour la r&#233;plication de fusion
  Les articles de table de fusion proposent de nombreuses options vous permettant de personnaliser le comportement de réplication en fonction des besoins de vos applications. La réplication de fusion vous offre les possibilités suivantes :  
  
-   Utiliser les filtres de lignes, de jointure et de colonnes. Le filtrage des articles d'une table vous permet de créer des partitions de données à publier. Pour plus d’informations, consultez [filtrer les données publiées](../../../relational-databases/replication/publish/filter-published-data.md).  
  
-   Spécifier si les modifications sur l'Abonné sont chargées sur le serveur de publication. Pour les applications dans lesquelles toute ou partie des données doit être en lecture seule sur l'Abonné, le téléchargement seul des articles procure un avantage au niveau des performances. Pour plus d’informations, consultez [optimiser les performances de réplication de fusion avec des Articles avec](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
-   Spécifier que les suppressions d'un ou plusieurs articles ne soient pas suivies par les déclencheurs de réplication et les tables système. Cette option peut être utile dans de nombreux scénarios d'application, comme ceux qui utilisent des suppressions par lot qu'il n'est pas nécessaire de répliquer. Pour plus d’informations, consultez [optimiser les performances de réplication de fusion avec le suivi conditionnel supprimer](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md).  
  
-   Spécifier l'ordre de traitement des articles pour s'assurer que les articles sont traités dans l'ordre requis par votre application. Pour plus d’informations, consultez [spécifier le traitement ordre de fusion Articles](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
-   Spécifier qu'un ensemble d'enregistrements associés soit traité comme une unité (par défaut, la réplication de fusion traite les modifications sur les tables ligne par ligne). Pour plus d’informations, consultez [modifications du groupe de lignes associées avec les enregistrements logiques](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
-   Utiliser la détection et la résolution des conflits dans les cas où les mêmes données ont pu être modifiées sur plus d'un seul nœud dans la topologie. Pour plus d'informations, consultez [Detect and Resolve Merge Replication Conflicts](../../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md).  
  
-   Spécifier les options de schéma, par exemple si les contraintes et déclencheurs sont copiés sur l'Abonné. Pour plus d’informations, consultez [spécifier les Options de schéma](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Utiliser un gestionnaire de logique métier pour répondre à de nombreuses conditions au cours de la synchronisation. Celles-ci incluent les modifications de données, les conflits et les erreurs. Pour plus d’informations, consultez [exécution logique au cours de fusion synchronisation professionnels](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
## Voir aussi  
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  