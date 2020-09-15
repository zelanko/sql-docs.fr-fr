---
title: Définir le même classement pour les bases de données définies par l’utilisateur que pour les bases de données MASTER ou model
description: Découvrez comment activer une stratégie pour vérifier si les classements des bases de données système et définies par l’utilisateur sont identiques.
ms.custom: seo-lt-2019
ms.date: 08/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 905accc62afdc12152110d44a18e61d4c8a9bcef
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284990"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-master-and-model-databases"></a>Définir le même classement pour les bases de données définies par l’utilisateur que pour les bases de données MASTER ou model
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle vérifie si les bases de données définies par l'utilisateur sont définies en utilisant un classement de base de données identique à celui de la base de données MASTER ou model.
  
## <a name="best-practices-recommendations"></a>Bonnes pratiques recommandées  
 Nous recommandons d'utiliser pour les bases de données définies par l'utilisateur les même classements que ceux des bases de données MASTER ou model. Dans le cas contraire, des conflits de classement pouvant empêcher l'exécution du code risquent de se produire. Par exemple, lorsqu’une procédure stockée joint une table à une table temporaire, SQL Server peut terminer le lot et retourner une erreur de conflit de classement si les classements de la base de données définie par l’utilisateur et de la base de données model sont différents. Cela se produit car les tables temporaires sont créées dans tempdb, dont le classement repose sur celui de la base de données model.

  Si vous rencontrez des erreurs de conflit de classement, considérez l'une des solutions suivantes :

  - Exportez les données de la base de données utilisateur et importez-les dans de nouvelles tables ayant le même classement que les bases de données MASTER et model.

  - Reconstruisez les bases de données système pour utiliser un classement qui correspond à celui de la base de données utilisateur. Pour plus d’informations sur la reconstruction des bases de données système, consultez [Reconstruire des bases de données système](../databases/rebuild-system-databases.md).

  - Modifiez toute procédure stockée qui joint des tables utilisateur à des tables de la base de données tempdb pour créer les tables dans tempdb en utilisant le classement de la base de données utilisateur. Pour ce faire, ajoutez la clause COLLATE database_default aux définitions de colonnes de la table temporaire, comme indiqué dans l’exemple suivant :
  
    ```
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )
    ```

## <a name="see-also"></a>Voir aussi
  
 [Définir ou modifier le classement du serveur](../collations/set-or-change-the-server-collation.md)  

 [Définir ou modifier le classement de la base de données](../collations/set-or-change-the-database-collation.md)

 [Définir ou modifier le classement des colonnes](../collations/set-or-change-the-column-collation.md)
 
 [Afficher des informations de classement](../collations/view-collation-information.md)    
  
  
