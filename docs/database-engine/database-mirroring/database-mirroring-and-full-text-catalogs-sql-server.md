---
title: "Mise en miroir de bases de donn&#233;es et catalogues de texte int&#233;gral (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mise en miroir de bases de données [SQL Server], interopérabilité"
  - "catalogues de texte intégral [SQL Server], mise en miroir de bases de données"
  - "catalogues [SQL Server], mise en miroir de bases de données"
ms.assetid: e34072ae-fe8a-462d-bb03-02fa0987f793
caps.latest.revision: 50
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 50
---
# Mise en miroir de bases de donn&#233;es et catalogues de texte int&#233;gral (SQL Server)
  Pour créer un miroir d'une base de données dotée d'un catalogue de texte intégral, utilisez les fonctions habituelles de sauvegarde pour créer une sauvegarde complète de la base de données principale, puis restaurez la copie de celle-ci sur le serveur miroir. Pour plus d’informations, consultez [Préparer une base de données miroir pour la mise en miroir &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
## Catalogue et index de texte intégral avant basculement  
 Dans une base de données miroir récemment créée, le catalogue de texte intégral est le même que lorsque la base de données a été sauvegardée. Une fois que la mise en miroir de la base de données a commencé, les modifications apportées au niveau du catalogue par les instructions DDL (CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG) sont enregistrées et envoyées au serveur miroir pour être relues sur la base de données miroir. Cependant, les modifications au niveau de l'index ne sont pas répercutées sur la base de données miroir dans la mesure où celle-ci n'est pas connectée au serveur principal. Par conséquent, les modifications affectant le contenu du catalogue de texte intégral sur la base de données principale ne sont pas synchronisées avec le contenu du catalogue de texte intégral sur la base de données miroir.  
  
## Index de texte intégral après basculement  
 À l'issue d'un basculement, une analyse complète d'un index de texte intégral sur le nouveau serveur principal peut être utile ou nécessaire dans les cas suivants :  
  
-   Si le suivi des modifications est désactivé sur un index de texte intégral, vous devez démarrer une analyse complète sur cet index à l'aide de l'instruction suivante :  
  
     ALTER FULLTEXT INDEX ON *nom_table* START FULL POPULATION  
  
-   Si un index de texte intégral est configuré pour le suivi des modifications automatique, cet index est synchronisé automatiquement. Toutefois, la synchronisation ralentit les performances du texte intégral dans une certaine mesure. Si les performances sont trop lentes, vous pouvez générer une analyse complète en désactivant le suivi des modifications et en le redéfinissant sur automatique :  
  
    -   Pour désactiver le suivi des modifications :  
  
         ALTER FULLTEXT INDEX ON *nom_table* SET CHANGE_TRACKING OFF  
  
    -   Pour définir le suivi des modifications sur automatique :  
  
         ALTER FULLTEXT INDEX ON *nom_table* SET CHANGE_TRACKING AUTO  
  
    > [!NOTE]  
    >  Pour savoir si le suivi automatique des modifications est activé, vous pouvez utiliser la fonction [OBJECTPROPERTYEX](../../t-sql/functions/objectpropertyex-transact-sql.md) pour interroger la propriété **TableFullTextBackgroundUpdateIndexOn** de la table.  
  
 Pour plus d’informations, consultez [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md).  
  
> [!NOTE]  
>  Le démarrage d'une analyse après basculement fonctionne de la même manière que le démarrage d'une analyse après une restauration.  
  
## Après avoir forcé le service  
 Une fois que le service a été forcé sur le serveur miroir (perte de données possible), commencez une analyse complète. La méthode à utiliser pour démarrer une analyse complète dépend si l'index de texte intégral fait l'objet d'un suivi des modifications. Pour plus d'informations, consultez « Index de texte intégral après basculement », plus haut dans cette rubrique.  
  
## Voir aussi  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Sauvegarder et restaurer des catalogues et des index de recherche en texte intégral](../../relational-databases/search/back-up-and-restore-full-text-catalogs-and-indexes.md)  
  
  