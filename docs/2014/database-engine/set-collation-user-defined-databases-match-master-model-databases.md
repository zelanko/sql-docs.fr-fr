---
title: Définissez les bases de données défini par le classement de l’utilisateur correspondent à ceux du serveur principal et de bases de données model | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c686446f-dae1-4b05-a3df-837b3422988d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dfb00b1cc1a9930f7a374403b40e2c0d793eb090
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371081"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-those-of-the-master-and-model-databases"></a>Définir le même classement pour les bases de données définies par l'utilisateur que pour les bases de données MASTER ou model
  Cette règle vérifie si les bases de données définies par l'utilisateur sont définies en utilisant un classement de base de données identique à celui de la base de données MASTER ou model.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Nous recommandons d'utiliser pour les bases de données définies par l'utilisateur les même classements que ceux des bases de données MASTER ou model. Dans le cas contraire, des conflits de classement pouvant empêcher l'exécution du code risquent de se produire. Par exemple, lorsqu'une procédure stockée joint une table à une table temporaire, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut terminer le lot et retourner une erreur de conflit de classement si les classements de la base de données définie par l'utilisateur et de la base de données model sont différents. Cela se produit car les tables temporaires sont créées dans tempdb, dont le classement repose sur celui de la base de données model.  
  
 Si vous rencontrez des erreurs de conflit de classement, considérez l'une des solutions suivantes :  
  
-   Exportez les données de la base de données utilisateur et importez-les dans de nouvelles tables ayant le même classement que les bases de données MASTER et model.  
  
-   Reconstruisez les bases de données système pour utiliser un classement qui correspond à celui de la base de données utilisateur. Pour plus d’informations sur la façon de reconstruire les bases de données système, consultez [reconstruire bases de données système](../relational-databases/databases/system-databases.md).  
  
-   Modifiez toute procédure stockée qui joint des tables utilisateur à des tables de la base de données tempdb pour créer les tables dans tempdb en utilisant le classement de la base de données utilisateur. Pour ce faire, ajoutez la clause `COLLATE database_default` aux définitions de colonnes de la table temporaire, comme indiqué dans l'exemple suivant :  
  
    ```  
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )  
    ```  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Définir ou modifier le classement de la base de données](../relational-databases/collations/set-or-change-the-database-collation.md)  
  
 [Définir ou modifier le classement des colonnes](../relational-databases/collations/set-or-change-the-column-collation.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [Article 325335 de la Base de connaissances Microsoft](https://go.microsoft.com/fwlink/?linkid=117751)  
  
 [Comment : Installer SQL Server 2008 à partir de l’invite de commandes](https://go.microsoft.com/fwlink/?LinkId=81585)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
