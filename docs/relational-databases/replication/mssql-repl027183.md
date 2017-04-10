---
title: "MSSQL_REPL027183 | Microsoft Docs"
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
  - "MSSQL_REPL027183 (erreur)"
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027183
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|27183|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le processus de fusion n'a pas pu énumérer les modifications apportées aux articles via le filtre de lignes paramétrable. Si le problème persiste, augmentez le délai de requête du processus, réduisez la période de rétention de la publication, puis améliorez les index des tables publiées.|  
  
## Explication  
 Cette erreur est émise si le délai d'attente d'un Agent de fusion est dépassé lors du traitement des modifications dans une publication filtrée. Le dépassement du délai d'attente peut être causé par l'un des problèmes suivants :  
  
-   Non-utilisation de l'optimisation des partitions précalculées.  
  
-   Fragmentation de l'index sur les colonnes utilisées pour le filtrage.  
  
-   Métadonnées de fusion de grandes tables, telles que **MSmerge_tombstone**, **MSmerge_contents**, et **MSmerge_genhistory**.  
  
-   Tables filtrées qui ne sont pas jointes sur une clé unique, et filtres de jointures qui impliquent un grand nombre de tables.  
  
## Action de l'utilisateur  
 Pour résoudre ce problème :  
  
-   Augmentez la valeur de la **- QueryTimeOut** émet de paramètre pour l’Agent de fusion permettre au traitement de continuer pendant que vous résolvez sous-jacent à l’origine de l’erreur. Les paramètres des agents peuvent être spécifiés dans des profils d'agent et sur la ligne de commande. Pour plus d'informations, consultez :  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Afficher et modifier les paramètres d’invite de l’Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concepts des exécutables de l’Agent réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Utilisez si possible l'optimisation des partitions précalculées. Cette optimisation est utilisée par défaut si un certain nombre de conditions de publication sont remplies. Pour plus d’informations sur ces exigences, consultez [optimiser les performances de filtre paramétré avec des Partitions précalculées](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md). Si la publication ne remplit pas ces conditions, envisagez de modifier sa conception.  
  
-   Spécifiez la valeur la plus basse possible pour la période de rétention de la publication, parce que la réplication ne peut pas nettoyer les métadonnées de la publication et des bases de données d'abonnement tant que la période de rétention n'est pas achevée. Pour plus d'informations, voir [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   Dans le cadre de la gestion de la réplication de fusion, contrôlez la croissance des tables système associées à la réplication de fusion : **MSmerge_contents**, **MSmerge_genhistory**, et **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, et **MSmerge_past_partition_mappings**. Réindexez périodiquement ces tables. Pour plus d’informations, consultez [réorganisation et reconstruction des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Assurez-vous que les colonnes utilisées pour le filtrage sont correctement indexées et le cas échéant rebâtissez les index. Pour plus d’informations, consultez [réorganisation et reconstruction des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Définir le **join_unique_key** propriété pour les filtres de jointure qui reposent sur des colonnes uniques. Pour plus d’informations, voir [Join Filters](../../relational-databases/replication/merge/join-filters.md).  
  
-   Limitez le nombre de tables dans la hiérarchie du filtre de jointure. Si vous générez des filtres de jointure pour au moins cinq tables, envisagez d'autres solutions : ne filtrez pas les petites tables, les tables qui ne changent pas ou les tables de recherche principales. Utilisez des filtres de jointure seulement entre des tables qui doivent être partitionnées entre des abonnements.  
  
-   Réduisez entre les synchronisations le nombre de changements apportés aux tables filtrées, ou exécutez l'Agent de fusion plus souvent. Pour plus d’informations sur les planifications de synchronisation de paramètre, consultez la page [spécifier des planifications de synchronisation](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  