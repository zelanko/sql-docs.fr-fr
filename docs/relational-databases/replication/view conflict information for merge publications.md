---
title: "Afficher les informations relatives aux conflits pour les publications de fusion (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "résolution des conflits de réplication de fusion [réplication SQL Server], affichage des conflits"
  - "sp_helpmergeconflictrows"
  - "affichage des informations sur les conflits"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
  - "sp_helpmergearticleconflicts"
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Afficher les informations relatives aux conflits pour les publications de fusion (programmation Transact-SQL de la r&#233;plication)
  Lorsqu'un conflit est résolu dans une réplication de fusion, les données de la ligne perdante sont écrites dans une table de conflits. Ces données peuvent être affichées par programme en utilisant des procédures stockées de réplication. Pour plus d’informations, consultez [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### Pour afficher les informations relatives au conflit et les données de ligne perdante pour tous les types de conflits  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Notez les valeurs des colonnes suivantes dans le jeu de résultats :  
  
    -   **centralized_conflicts** -1 indique que les lignes en conflit sont stockés sur le serveur de publication, et 0 indique que les lignes en conflit ne sont pas stockés sur le serveur de publication.  
  
    -   **decentralized_conflicts** -1 indique que les lignes en conflit sont stockés sur l’abonné, et 0 indique que les lignes en conflit ne sont pas stockés sur l’abonné.  
  
        > [!NOTE]  
        >  Le comportement de journalisation des conflits d’une publication de fusion est défini à l’aide de la **@conflict_logging** paramètre de [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Utilisation de la **@centralized_conflicts** paramètre a été déconseillé.  
  
     Le tableau suivant décrit les valeurs de ces colonnes en fonction de la valeur spécifiée pour **@conflict_logging**.  
  
    |Valeur de @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher**|1|0|  
    |**subscriber**|0|1|  
    |**both**|1|1|  
  
2.  Serveur de la base de données de publication ou sur l’abonné sur la base de données d’abonnement, exécutez [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Spécifiez une valeur pour **@publication** pour retourner uniquement les informations de conflit pour les articles qui appartiennent à une publication spécifique. Des informations sur les tables de conflits sont alors retournées pour les articles présentant des conflits. Notez la valeur de **conflict_table** pour tout article qui vous intéresse. Si la valeur de **conflict_table** pour un article est NULL, uniquement les conflits de suppression se sont produites dans cet article.  
  
3.  (Facultatif) Examinez les lignes présentant des conflits pour les articles qui vous intéressent. En fonction des valeurs de **centralized_conflicts** et **decentralized_conflicts** à l’étape 1, effectuez l’une des opérations suivantes :  
  
    -   Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Spécifiez une table de conflits pour l’article (de l’étape 1) pour **@conflict_table**. (Facultatif) Spécifiez la valeur **@publication** pour limiter les informations de conflit retourné pour une publication spécifique. Des données de ligne et autres informations sur la ligne perdante sont alors retournées.  
  
    -   Sur la base de données d’abonnement de l’abonné, exécutez [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Spécifiez une table de conflits pour l’article (de l’étape 1) pour **@conflict_table**. Des données de ligne et autres informations sur la ligne perdante sont alors retournées.  
  
### Pour afficher des informations uniquement sur les conflits avec échec de suppression  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Notez les valeurs des colonnes suivantes dans le jeu de résultats :  
  
    -   **centralized_conflicts** -1 indique que les lignes en conflit sont stockés sur le serveur de publication, et 0 indique que les lignes en conflit ne sont pas stockés sur le serveur de publication.  
  
    -   **decentralized_conflicts** -1 indique que les lignes en conflit sont stockés sur l’abonné, et 0 indique que les lignes en conflit ne sont pas stockés sur l’abonné.  
  
        > [!NOTE]  
        >  Le comportement de journalisation des conflits d’une publication de fusion est défini à l’aide de la **@conflict_logging** paramètre de [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Utilisation de la **@centralized_conflicts** paramètre a été déconseillé.  
  
2.  Serveur de la base de données de publication ou sur l’abonné sur la base de données d’abonnement, exécutez [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Spécifiez une valeur pour **@publication** pour retourner uniquement les informations de table de conflits pour les articles qui appartiennent à une publication spécifique. Des informations sur les tables de conflits sont alors retournées pour les articles présentant des conflits. Notez la valeur de **source_object** pour tout article qui vous intéresse. Si la valeur de **conflict_table** pour un article est NULL, uniquement les conflits de suppression se sont produites dans cet article.  
  
3.  (Facultatif) Examinez les informations sur les conflits pour les conflits de suppression. En fonction des valeurs de **centralized_conflicts** et **decentralized_conflicts** à l’étape 1, effectuez l’une des opérations suivantes :  
  
    -   Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Spécifiez le nom de la table source (à l’étape 1) sur lequel le conflit s’est produite pour **@source_object**. (Facultatif) Spécifiez la valeur **@publication** pour limiter les informations de conflit retourné pour une publication spécifique. Les informations sur les conflits de suppression stockées sur le serveur de publication sont alors retournées.  
  
    -   Sur la base de données d’abonnement de l’abonné, exécutez [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Spécifiez le nom de la table source (à l’étape 1) sur lequel le conflit s’est produite pour **@source_object**. (Facultatif) Spécifiez la valeur **@publication** pour limiter les informations de conflit retourné pour une publication spécifique. Les informations sur les conflits de suppression stockées sur l'Abonné sont alors retournées.  
  
## Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  