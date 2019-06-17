---
title: Mise en miroir de bases de données et catalogues de texte intégral (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- full-text catalogs [SQL Server], database mirroring
- catalogs [SQL Server], database mirroring
ms.assetid: e34072ae-fe8a-462d-bb03-02fa0987f793
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e90e2386fcd6c6d2f71e1cea31f253f8baac9195
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62807293"
---
# <a name="database-mirroring-and-full-text-catalogs-sql-server"></a>Mise en miroir de bases de données et catalogues de texte intégral (SQL Server)
  Pour créer un miroir d'une base de données dotée d'un catalogue de texte intégral, utilisez les fonctions habituelles de sauvegarde pour créer une sauvegarde complète de la base de données principale, puis restaurez la copie de celle-ci sur le serveur miroir. Pour plus d’informations, consultez [Préparer une base de données miroir pour la mise en miroir &#40;Transact-SQL&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
## <a name="full-text-catalog-and-indexes-before-failover"></a>Catalogue et index de texte intégral avant basculement  
 Dans une base de données miroir récemment créée, le catalogue de texte intégral est le même que lorsque la base de données a été sauvegardée. Une fois que la mise en miroir de la base de données a commencé, les modifications apportées au niveau du catalogue par les instructions DDL (CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG) sont enregistrées et envoyées au serveur miroir pour être relues sur la base de données miroir. Cependant, les modifications au niveau de l'index ne sont pas répercutées sur la base de données miroir dans la mesure où celle-ci n'est pas connectée au serveur principal. Par conséquent, les modifications affectant le contenu du catalogue de texte intégral sur la base de données principale ne sont pas synchronisées avec le contenu du catalogue de texte intégral sur la base de données miroir.  
  
## <a name="full-text-indexes-after-failover"></a>Index de texte intégral après basculement  
 À l'issue d'un basculement, une analyse complète d'un index de texte intégral sur le nouveau serveur principal peut être utile ou nécessaire dans les cas suivants :  
  
-   Si le suivi des modifications est désactivé sur un index de texte intégral, vous devez démarrer une analyse complète sur cet index à l'aide de l'instruction suivante :  
  
     ALTER FULLTEXT INDEX ON *nom_table* START FULL POPULATION  
  
-   Si un index de texte intégral est configuré pour le suivi des modifications automatique, cet index est synchronisé automatiquement. Toutefois, la synchronisation ralentit les performances du texte intégral dans une certaine mesure. Si les performances sont trop lentes, vous pouvez générer une analyse complète en désactivant le suivi des modifications et en le redéfinissant sur automatique :  
  
    -   Pour désactiver le suivi des modifications :  
  
         ALTER FULLTEXT INDEX ON *nom_table* SET CHANGE_TRACKING OFF  
  
    -   Pour définir le suivi des modifications sur automatique :  
  
         ALTER FULLTEXT INDEX ON *nom_table* SET CHANGE_TRACKING AUTO  
  
    > [!NOTE]  
    >  Pour savoir si le suivi automatique des modifications est activé, vous pouvez utiliser la fonction [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) pour interroger la propriété **TableFullTextBackgroundUpdateIndexOn** de la table.  
  
 Pour plus d’informations, consultez [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).  
  
> [!NOTE]  
>  Le démarrage d'une analyse après basculement fonctionne de la même manière que le démarrage d'une analyse après une restauration.  
  
## <a name="after-forcing-service"></a>Après avoir forcé le service  
 Une fois que le service a été forcé sur le serveur miroir (perte de données possible), commencez une analyse complète. La méthode à utiliser pour démarrer une analyse complète dépend si l'index de texte intégral fait l'objet d'un suivi des modifications. Pour plus d'informations, consultez « Index de texte intégral après basculement », plus haut dans cette rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Sauvegarder et restaurer des catalogues et des index de recherche en texte intégral](../../relational-databases/indexes/indexes.md)  
  
  
