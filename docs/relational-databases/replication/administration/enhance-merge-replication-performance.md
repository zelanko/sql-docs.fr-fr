---
title: "Am&#233;liorer les performances de r&#233;plication de fusion | Microsoft Docs"
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
  - "publications [réplication SQL Server], conception et performances"
  - "conception de bases de données [SQL Server], performances de réplication"
  - "Agent de fusion, performances"
  - "instantanés [réplication SQL Server], observations relatives aux performances"
  - "performances de la réplication de fusion [réplication SQL Server]"
  - "abonnements [réplication SQL Server], observations relatives aux performances"
  - "performances [réplication SQL Server], réplication de fusion"
  - "agents [réplication SQL Server], performances"
ms.assetid: f929226f-b83d-4900-a07c-a62f64527c7f
caps.latest.revision: 47
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 47
---
# Am&#233;liorer les performances de r&#233;plication de fusion
  Après avoir considéré les conseils en matière de performances qui sont décrits dans la rubrique [Amélioration des performances générales de la réplication](../../../relational-databases/replication/administration/enhance-general-replication-performance.md), considérez ces autres aspects spécifiques à la réplication de fusion.  
  
## Création de bases de données  
  
-   Colonnes d'index utilisées dans des filtres de lignes et des filtres de jointure.  
  
     Si vous utilisez un filtre de lignes sur un article publié, créez un index sur chacune des colonnes utilisées dans la clause WHERE du filtre. S'il n'y a pas d'index, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit lire chaque ligne de la table pour déterminer si la ligne doit être incluse dans la partition. Avec un index, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut localiser rapidement les lignes à inclure. Le traitement le plus rapide s'effectue si la réplication peut résoudre complètement la clause WHERE du filtre à partir de l'index seul.  
  
     L'indexation de toutes les colonnes utilisées dans des filtres de jointure est également importante. À chaque exécution, l'Agent de fusion recherche dans la table de base quelles lignes de la table parente et quelles lignes des tables associées sont incluses dans une partition. La création d'un index sur les colonnes jointes dispense [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de devoir lire chaque ligne de la table à chaque exécution de l'Agent de fusion.  
  
     Pour plus d’informations sur le filtrage, consultez [filtrer les données publiées pour la réplication de fusion](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md).  
  
-   Envisagez de surnormaliser les tables qui incluent des types de données LOB.  
  
     Lors d'une synchronisation, l'Agent de fusion peut avoir besoin de lire et de transférer la totalité de la ligne de données à partir d'un serveur de publication ou d'un Abonné. Si la ligne contient des colonnes utilisant des données de type LOB, ce processus peut nécessiter un surcroît d'allocation de mémoire et nuire aux performances, même si ces colonnes peuvent ne pas avoir été mises à jour. Pour limiter la probabilité d'une perte de performance, vous pouvez envisager de placer les colonnes LOB dans une table indépendante en les reliant aux autres données de la ligne avec une relation un-à-un. Les types de données **text**, **ntext**et **image** sont déconseillés. Si vous incluez LOB, nous vous recommandons d’utiliser les types de données **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, respectivement.  
  
## Conception de la publication  
  
-   Utilisez un niveau de compatibilité de la publication de 90RTM ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]) ou version ultérieure.  
  
     À moins qu'un ou plusieurs Abonnés n'utilisent une version différente de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], spécifiez que la publication doit uniquement prendre en charge [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Ceci permet à la publication de bénéficier des nouvelles fonctionnalités et optimisations des performances.  
  
-   Utilisez les paramètres de rétention de publication appropriés.  
  
     La période de rétention de publication, qui est la quantité maximale de temps avant qu'un abonnement doive être synchronisé, détermine le temps pendant lequel les métadonnées de suivi sont stockées. Une valeur élevée peut affecter les performances en matière de stockage et de traitement. Pour plus d'informations sur la définition de la période de rétention des publications, consultez [Subscription Expiration and Deactivation](../../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   Utilisez des articles en téléchargement seulement sur les tables qui sont modifiées seulement sur le serveur de publication. Pour plus d’informations, consultez [optimiser les performances de réplication de fusion avec des Articles avec](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
### Conception et utilisation des filtres  
  
-   Limitez la complexité des clauses des filtres de lignes.  
  
     La limitation de la complexité des critères de filtrage permet un gain de performance lorsque l'Agent de fusion évalue les modifications de lignes à envoyer aux Abonnés. Évitez l'utilisation de sous-sélections dans les clauses des filtres de lignes de fusion. Envisagez plutôt l'utilisation de filtres de jointure, généralement plus efficaces pour le partitionnement des données d'une table à partir de la clause de filtre de lignes d'une autre table. Pour plus d’informations sur le filtrage, consultez [filtrer les données publiées pour la réplication de fusion](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md).  
  
-   Utilisez des partitions précalculées avec des filtres paramétrés (cette fonctionnalité est utilisée par défaut). Pour plus d’informations, consultez [optimiser les performances de filtre paramétré avec des Partitions précalculées](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
     Les partitions précalculées imposent plusieurs limitations au fonctionnement du filtrage. Si votre application ne peut pas se conformer à ces limitations, définissez la **keep_partition_changes** option **True**, ce qui améliore les performances. Pour plus d'informations, voir [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
-   Utilisez des partitions qui ne se chevauchent pas si les données sont filtrées mais pas partagées entre les utilisateurs.  
  
     La réplication peut optimiser les performances pour les données qui ne sont pas partagées entre des partitions ou des abonnements. Pour plus d’informations, voir [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
-   Ne créez pas de hiérarchies de filtres de jointure complexes.  
  
     Les filtres de jointure avec cinq tables ou plus peuvent avoir un impact significatif sur les performances lors du processus de fusion. Il est recommandé d'envisager d'autres solutions si vous générez des filtres de jointure impliquant cinq tables ou plus :  
  
    -   Évitez de filtrer les tables qui sont essentiellement des tables de recherche, des tables de taille réduite et des tables qui ne font pas l'objet de modifications. Intégrez ces tables dans la publication dans leur globalité. Il est recommandé d'utiliser des filtres de jointure seulement entre des tables qui doivent être partitionnées entre des Abonnés. Pour plus d’informations, voir [Join Filters](../../../relational-databases/replication/merge/join-filters.md).  
  
    -   Envisagez la dénormalisation du design de la base de données ou l'utilisation d'une table de mappage s'il y a un grand nombre de tables dans une jointure. Par exemple, si un commercial a seulement besoin des données relatives à ses clients mais que six jointures sont nécessaires pour associer un client avec un commercial, envisagez d'ajouter une colonne à la table des clients pour identifier le commercial. Les données du commercial sont alors redondantes, mais les coûts liés à la dénormalisation des tables peuvent être compensés par les gains de performance pour le partitionnement de la réplication.  
  
    -   Pour améliorer les performances des partitions précalculées lorsque des traitements contiennent un grand nombre de données modifiées, concevez votre application avec soin. Assurez-vous que les modifications apportées aux données de la table parente dans un filtre de jointure ont lieu avant les modifications correspondantes dans les tables enfants.  
  
-   Définir le **join_unique_key** option **1** si logique le permet.  
  
     La définition de ce paramètre à **1** indique que la relation entre les tables enfants et parent dans un filtre de jointure est « un à un » ou « un à plusieurs ». Définissez ce paramètre à **1** seulement si vous avez une contrainte sur la colonne de jointure dans la table enfant qui garantit l'unicité. Si le paramètre est défini sur **1** incorrecte, une non-convergence des données peut se produire. Pour plus d’informations, voir [Join Filters](../../../relational-databases/replication/merge/join-filters.md).  
  
-   Évitez d'exécuter des traitements avec un grand nombre de modifications lorsque vous utilisez des partitions précalculées.  
  
     Lorsque vous exécutez l'Agent de fusion après avoir exécuté un traitement avec un grand nombre de données modifiées, l'agent tente de scinder le traitement en question en traitements plus petits. Au cours de cette opération, d'autres processus de l'Agent de fusion peuvent être bloqués. Si possible, réduisez le nombre de modifications dans un traitement et exécutez l'Agent de fusion entre les traitements. Si ce n’est pas possible, augmentez la valeur de **generation_leveling_threshold** pour la publication.  
  
## Considérations sur les abonnements  
  
-   Échelonnez les planifications de synchronisation des abonnements.  
  
     Si un grand nombre d'Abonnés se synchronisent avec un serveur de publication, envisagez d'échelonner les planifications de façon à ce que les Agents de fusion s'exécutent à des moments différents. Pour plus d'informations, voir [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md).  
  
## Paramètres de l'Agent de fusion  
 Pour plus d'informations sur l'Agent de fusion et sur ses paramètres, consultez [Replication Merge Agent](../../../relational-databases/replication/agents/replication-merge-agent.md).  
  
-   Mettez à niveau tous les Abonnés pour les abonnements par extraction vers [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure.  
  
     La mise à niveau de l'Abonné vers [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure met à niveau l'Agent de fusion utilisé par les abonnements sur cet Abonné. Pour tirer parti des nouvelles fonctionnalités et optimisations des performances, l'Agent de fusion [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure est obligatoire.  
  
-   Si un abonnement est synchronisé par le biais d’une connexion rapide et si des modifications sont envoyées à partir du serveur de publication et à partir de l’Abonné, utilisez le paramètre **–ParallelUploadDownload** pour l’Agent de fusion.  
  
     [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] a introduit un nouveau paramètre pour l’Agent de fusion : **–ParallelUploadDownload**. La définition de ce paramètre permet à l'Agent de fusion de traiter en parallèle les modifications chargées vers le serveur de publication et celles qui sont téléchargées vers l'Abonné. Ceci est utile dans les environnements où les volumes sont élevés, avec une bande passante réseau élevée. Les paramètres des agents peuvent être spécifiés dans des profils d'agent et sur la ligne de commande. Pour plus d'informations, consultez :  
  
    -   [Work with Replication Agent Profiles](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Afficher et modifier les paramètres d’invite de l’Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concepts des exécutables de l'agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
-   Envisagez d’augmenter la valeur de la **- MakeGenerationInterval** paramètre, surtout si la synchronisation implique plus de téléchargements des abonnés que vers les abonnés.  
  
-   Lorsque vous synchroniser des lignes de données avec une grande quantité de données (par exemple, des lignes avec des colonnes LOB), la synchronisation Web peur exiger une allocation supplémentaire de mémoire et nuire aux performances. Cette situation se produit lorsque l'Agent de fusion génère un message XML qui contient trop de lignes de données avec de gros volumes de données. Si l'Agent de fusion consomme trop de ressources lors de la synchronisation Web, réduisez le nombre de lignes transmises dans un seul message de l'une des manières suivantes :  
  
    -   Utilisez le profil de liaison lente de l'Agent de fusion. Pour plus d’informations, voir [Replication Agent Profiles](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
    -   Réduire le **- DownloadGenerationsPerBatch** et **- UploadGenerationsPerBatch** paramètres de l’Agent de fusion sur une valeur de 10 ou moins. La valeur par défaut de ces paramètres est 50.  
  
## Considérations sur les instantanés  
  
-   Créez une colonne ROWGUIDCOL sur les grandes tables avant la génération de l'instantané initial.  
  
     La réplication de fusion exige que chaque table publiée possède une colonne ROWGUIDCOL. Si aucune colonne ROWGUIDCOL n'existe dans la table avant que l'Agent d'instantané ne crée les premiers fichiers d'instantané, l'Agent doit tout d'abord ajouter et remplir la colonne ROWGUIDCOL. Pour bénéficier d'une amélioration des performances lors de la génération d'instantanés, créez la colonne ROWGUIDCOL sur chaque table avant de procéder à la publication. La colonne peut avoir n’importe quel nom (**rowguid** est utilisé par l’Agent de capture instantanée par défaut), mais doit avoir les données suivantes de caractéristiques de type :  
  
    -   Un type de données UNIQUEIDENTIFIER.  
  
    -   Une valeur par défaut NEWSEQUENTIALID() ou NEWID(). NEWSEQUENTIALID() est recommandée car elle peut améliorer les performances lorsque des modifications sont effectuées et suivies.  
  
    -   La propriété ROWGUIDCOL définie.  
  
    -   un index unique sur la colonne.  
  
-   Prégénérez des instantanés et/ou permettez aux Abonnés de demander la génération et l'application d'un instantané la première fois qu'ils se synchronisent.  
  
     Utilisez l'une ou l'autre de ces options ou les deux pour fournir des instantanés pour les publications qui utilisent des filtres paramétrés. Si vous ne spécifiez pas une de ces options, les abonnements sont initialisés à l'aide d'une série d'instructions SELECT et INSERT au lieu d'utiliser l'utilitaire **bcp** , ce processus étant beaucoup plus lent. Pour plus d’informations, voir [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
## Considérations sur la maintenance et sur l'analyse  
  
-   Réindexez occasionnellement les tables système d'une réplication de fusion  
  
     Dans le cadre de la gestion de la réplication de fusion, contrôlez la croissance des tables système associées à la réplication de fusion : **MSmerge_contents**, **MSmerge_genhistory**, et **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, et **MSmerge_past_partition_mappings**. Réindexez périodiquement ces tables. Pour plus d’informations, consultez [réorganisation et reconstruction des index](../../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Analysez les performances de la synchronisation à l'aide de l'onglet **Historique de synchronisation** dans le moniteur de réplication.  
  
     La réplication de fusion, le moniteur de réplication affiche des statistiques détaillées dans le **historique de synchronisation** onglet pour chaque article traité pendant la synchronisation, notamment la quantité de temps passé dans chaque phase de traitement (chargement des modifications, téléchargement modifications et ainsi de suite). Il peut être utile d'identifier les tables spécifiques qui provoquent les ralentissements ; il s'agit du meilleur observatoire pour résoudre les problèmes de performance avec les abonnements de fusion. Pour plus d’informations sur l’affichage des statistiques détaillées, consultez la page [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
  