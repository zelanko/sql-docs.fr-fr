---
title: "Sp&#233;cifier les types d&#39;articles (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
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
  - "publication [réplication SQL Server], exécution d’une procédure stockée"
  - "articles [réplication SQL Server], options de réplication transactionnelle"
  - "articles [réplication SQL Server], options de réplication de fusion"
  - "procédures stockées [réplication SQL Server], publication"
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Sp&#233;cifier les types d&#39;articles (programmation Transact-SQL de la r&#233;plication)
  Les types d'articles par défaut pour la réplication sont les articles de table, mais vous pouvez publier d'autres objets de base de données en tant qu'articles, y compris des vues, des procédures stockées, des fonctions définies par l'utilisateur et l'exécution des procédures stockées. Vous pouvez utiliser les procédures stockées de réplication pour spécifier par programme un type d'article lorsque vous définissez un article. Les procédures à utiliser dépendent du type de réplication et du type d'article.  
  
> [!NOTE]  
>  La désignation de schéma uniquement, lorsque vous définissez des articles de table, de vue et de procédures stockées, indique que seule la définition des objets est répliquée.  
  
### Pour publier un article de table dans une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez une des valeurs suivantes pour **@type** pour définir le type d’article :  
  
    -   **logbased** -un article de table basé sur journal, qui est la valeur par défaut pour la réplication transactionnelle et de capture instantanée. La réplication génère automatiquement la procédure stockée utilisée pour le filtrage horizontal et la vue qui définit un article filtré verticalement.  
  
    -   **logbased manualfilter** -un article basé sur journal, filtré horizontalement, où la procédure stockée utilisée pour le filtrage horizontal est manuellement créée et définie par l’utilisateur et spécifiée pour **@filter**. Pour plus d'informations, voir [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
    -   **logbased manualview** -un article basé sur journal, filtré verticalement où la vue qui définit l’article filtré verticalement est créée et définie par l’utilisateur et spécifiée pour **@sync_object**. Pour plus d’informations, consultez [définir et modifier un filtre de lignes statiques](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) et [définir et modifier un filtre de colonne](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
    -   **logbased manualboth** -basé sur journal, horizontalement et verticalement filtré article où la procédure stockée utilisée pour le filtrage horizontal et la vue qui définit l’article filtré verticalement sont créées et définies par l’utilisateur et spécifiée pour **@filter** et **@sync_object**, respectivement. Pour plus d’informations, consultez [définir et modifier un filtre de lignes statiques](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) et [définir et modifier un filtre de colonne](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
     Cela définit un nouvel article pour la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Pour **logbased manualboth** et **logbased manualfilter** articles, exécutez [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) pour générer la procédure stockée de filtrage pour un article filtré horizontalement. Pour plus d'informations, voir [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Pour **logbased manualboth**, **logbased manualview**, et **logbased manualfilter** articles, exécutez [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) pour générer la vue qui définit l’article filtré verticalement. Pour plus d’informations, voir [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
### Pour publier un article de vue ou de vue indexée dans une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez une des valeurs suivantes pour **@type** pour définir le type d’article :  
  
    -   **indexées view logbased** -un article de vue indexée basé sur un journal. La réplication génère automatiquement la procédure stockée utilisée pour le filtrage horizontal et la vue qui définit un article filtré verticalement.  
  
    -   **afficher uniquement le schéma** -un article de vue schéma uniquement. La table de base doit également être répliquée.  
  
    -   **schéma de la vue indexée uniquement** -un article de schéma exclusivement de vue indexée. La table de base doit également être répliquée.  
  
    -   **indexées view logbased manualfilter** -un article de vue indexée basé sur journal, filtré horizontalement dans lequel la procédure stockée utilisée pour le filtrage horizontal est manuellement créée et définie par l’utilisateur et spécifiée pour **@filter**. Pour plus d'informations, voir [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
    -   **indexées view logbased manualview** -un article de vue indexée basé sur journal, filtré où la vue qui définit un article filtré verticalement est créée et définie par l’utilisateur et spécifiée pour **@sync_object**. Pour plus d’informations, consultez [définir et modifier un filtre de lignes statiques](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) et [définir et modifier un filtre de colonne](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
    -   **indexées view logbased manualboth** -un article de vue indexée basé sur journal, filtré où la procédure stockée utilisée pour le filtrage horizontal et la vue qui définit un article filtré verticalement sont créés et définis par l’utilisateur et spécifiée pour **@filter** et **@sync_object**, respectivement. Pour plus d’informations, consultez [définir et modifier un filtre de lignes statiques](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) et [définir et modifier un filtre de colonne](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
     Cela définit un nouvel article pour la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Pour **logbased manualboth** et **logbased manualfilter** articles, exécutez [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) pour générer la procédure stockée de filtrage pour un article filtré horizontalement. Pour plus d'informations, voir [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Pour **logbased manualboth**, **logbased manualview**, et **logbased manualfilter** articles, exécutez [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) pour générer la vue qui définit l’article filtré verticalement. Pour plus d’informations, voir [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
### Pour publier un article de procédure stockée, d'exécution des procédures stockées ou de fonction définie par l'utilisateur dans une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez une des valeurs suivantes pour **@type** pour définir le type d’article :  
  
    -   **schéma proc uniquement** -un article de schéma exclusivement de procédure stockée.  
  
    -   **proc exec** -réplique l’exécution de la procédure stockée sur tous les abonnés de l’article. Pour plus d’informations, voir [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **serializable proc exec** -réplique l’exécution de la procédure stockée uniquement si elle est exécutée dans le contexte d’une transaction sérialisable. Pour plus d’informations, voir [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **schéma Func uniquement** -un article de schéma uniquement la fonction définie par l’utilisateur.  
  
     Cela définit un nouvel article pour la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
### Pour publier un article de table ou de vue dans une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Spécifiez une des valeurs suivantes pour **@type** pour définir le type d’article :  
  
    -   **table** -un article de table.  
  
    -   **schéma de la vue indexée uniquement** -un article de schéma exclusivement de vue indexée.  
  
    -   **afficher uniquement le schéma** -un article de vue schéma uniquement.  
  
     Cela définit un nouvel article pour la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
### Pour publier un article de procédure stockée ou de fonction définie par l'utilisateur dans une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Spécifiez une des valeurs suivantes pour **@type** pour définir le type d’article :  
  
    -   **schéma Func uniquement** -un article de schéma uniquement la fonction définie par l’utilisateur.  
  
    -   **schéma proc uniquement** -un article de schéma exclusivement de procédure stockée.  
  
     Cela définit un nouvel article pour la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## Voir aussi  
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  