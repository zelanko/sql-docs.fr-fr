---
title: Spécifier les types d’articles (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- stored procedures [SQL Server replication], publishing
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7864825891203530bf30015471ca22a1daccf9b9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060334"
---
# <a name="specify-article-types-replication-transact-sql-programming"></a>Spécifier les types d'articles (programmation Transact-SQL de la réplication)
  Les types d'articles par défaut pour la réplication sont les articles de table, mais vous pouvez publier d'autres objets de base de données en tant qu'articles, y compris des vues, des procédures stockées, des fonctions définies par l'utilisateur et l'exécution des procédures stockées. Vous pouvez utiliser les procédures stockées de réplication pour spécifier par programme un type d'article lorsque vous définissez un article. Les procédures à utiliser dépendent du type de réplication et du type d'article.  
  
> [!NOTE]  
>  La désignation de schéma uniquement, lorsque vous définissez des articles de table, de vue et de procédures stockées, indique que seule la définition des objets est répliquée.  
  
### <a name="to-publish-a-table-article-in-a-transactional-or-snapshot-publication"></a>Pour publier un article de table dans une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez l’une des valeurs suivantes pour ** \@ type** pour définir le type d’article :  
  
    -   **logbased** – article de table basé sur le journal, utilisé par défaut pour la réplication transactionnelle et d'instantané. La réplication génère automatiquement la procédure stockée utilisée pour le filtrage horizontal et la vue qui définit un article filtré verticalement.  
  
    -   **logbased manualfilter** – article basé sur un journal, filtré horizontalement, dans lequel la procédure stockée utilisée pour le filtrage horizontal est créée et définie manuellement par l’utilisateur et spécifiée pour le ** \@ filtre**. Pour plus d'informations, voir [Définir et modifier un filtre de lignes statiques](define-and-modify-a-static-row-filter.md).  
  
    -   **logbased manualview** – article basé sur un journal, filtré verticalement pour lequel la vue qui définit l’article filtré verticalement est créée et définie par l’utilisateur et spécifiée pour ** \@ sync_object**. Pour plus d'informations, consultez [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) et [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
    -   **logbased manualboth** : article basé sur un journal, filtré horizontalement et verticalement, dans lequel la procédure stockée utilisée pour le filtrage horizontal et la vue qui définit l’article filtré verticalement sont créées et définies par l’utilisateur et spécifiées pour ** \@ filtre** et ** \@ sync_object**, respectivement. Pour plus d'informations, consultez [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) et [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
     Cela définit un nouvel article pour la publication. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
2.  Pour les articles **logbased manualboth** et **logbased manualfilter** , exécutez [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) pour générer la procédure stockée de filtrage pour un article filtré horizontalement. Pour plus d'informations, voir [Définir et modifier un filtre de lignes statiques](define-and-modify-a-static-row-filter.md).  
  
3.  Pour les articles **logbased manualboth**, **logbased manualview**et **logbased manualfilter** , exécutez [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) pour générer la vue qui définit l'article filtré verticalement. Pour plus d'informations, voir [Définir et modifier un filtre de colonne](define-and-modify-a-column-filter.md).  
  
### <a name="to-publish-a-view-or-indexed-view-article-in-a-transactional-or-snapshot-publication"></a>Pour publier un article de vue ou de vue indexée dans une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez l’une des valeurs suivantes pour ** \@ type** pour définir le type d’article :  
  
    -   **indexed view logbased** – article de vue indexée basé sur un journal. La réplication génère automatiquement la procédure stockée utilisée pour le filtrage horizontal et la vue qui définit un article filtré verticalement.  
  
    -   **view schema only** – article de vue de schéma uniquement. La table de base doit également être répliquée.  
  
    -   **indexed view schema only** – article de vue indexée de schéma uniquement. La table de base doit également être répliquée.  
  
    -   **indexed view logbased manualfilter** – article de vue indexée basé sur un journal et filtré horizontalement pour lequel la procédure stockée utilisée pour le filtrage horizontal est créée et définie manuellement par l’utilisateur et spécifiée pour le ** \@ filtre**. Pour plus d'informations, voir [Définir et modifier un filtre de lignes statiques](define-and-modify-a-static-row-filter.md).  
  
    -   **indexed view logbased manualview** – article de vue indexée basé sur un journal et filtré pour lequel la vue qui définit un article filtré verticalement est créée et définie par l’utilisateur et spécifiée pour ** \@ sync_object**. Pour plus d'informations, consultez [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) et [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
    -   **indexed view logbased manualboth** – article de vue indexée basé sur un journal et filtré pour lequel la procédure stockée utilisée pour le filtrage horizontal et la vue qui définit un article filtré verticalement sont créées et définies par l’utilisateur et spécifiées pour ** \@ Filter** et ** \@ sync_object**, respectivement. Pour plus d'informations, consultez [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) et [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
     Cela définit un nouvel article pour la publication. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
2.  Pour les articles **logbased manualboth** et **logbased manualfilter** , exécutez [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) pour générer la procédure stockée de filtrage pour un article filtré horizontalement. Pour plus d'informations, voir [Définir et modifier un filtre de lignes statiques](define-and-modify-a-static-row-filter.md).  
  
3.  Pour les articles **logbased manualboth**, **logbased manualview**et **logbased manualfilter** , exécutez [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) pour générer la vue qui définit l'article filtré verticalement. Pour plus d'informations, voir [Définir et modifier un filtre de colonne](define-and-modify-a-column-filter.md).  
  
### <a name="to-publish-a-stored-procedure-stored-procedure-execution-or-user-defined-function-article-in-a-transactional-or-snapshot-publication"></a>Pour publier un article de procédure stockée, d'exécution des procédures stockées ou de fonction définie par l'utilisateur dans une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez l’une des valeurs suivantes pour ** \@ type** pour définir le type d’article :  
  
    -   **proc schema only** – article de procédure stockée de schéma uniquement.  
  
    -   **proc exec** – réplique l'exécution de la procédure stockée sur tous les Abonnés de l'article. Pour plus d’informations, consultez [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **serializable proc exec** – réplique l'exécution de la procédure stockée uniquement si l'exécution s'effectue dans le contexte d'une transaction sérialisable. Pour plus d’informations, consultez [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **func schema only** – article de fonction définie par l'utilisateur de schéma uniquement.  
  
     Cela définit un nouvel article pour la publication. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
### <a name="to-publish-a-table-or-view-article-in-a-merge-publication"></a>Pour publier un article de table ou de vue dans une publication de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez l’une des valeurs suivantes pour ** \@ type** pour définir le type d’article :  
  
    -   **table** – article de table.  
  
    -   **indexed view schema only** – article de vue indexée de schéma uniquement.  
  
    -   **view schema only** – article de vue de schéma uniquement.  
  
     Cela définit un nouvel article pour la publication. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
### <a name="to-publish-a-stored-procedure-or-user-defined-function-article-in-a-merge-publication"></a>Pour publier un article de procédure stockée ou de fonction définie par l'utilisateur dans une publication de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez l’une des valeurs suivantes pour ** \@ type** pour définir le type d’article :  
  
    -   **func schema only** – article de fonction définie par l'utilisateur de schéma uniquement.  
  
    -   **proc schema only** – article de procédure stockée de schéma uniquement.  
  
     Cela définit un nouvel article pour la publication. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts des procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md)   
 [Publier des données et des objets de base de données](publish-data-and-database-objects.md)  
  
  
