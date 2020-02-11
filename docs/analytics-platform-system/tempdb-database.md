---
title: Base de données tempdb
description: Base de données tempdb en parallèle Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 3772e2b4cabac84c00854eba85f7a0c2a33d48bc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400142"
---
# <a name="tempdb-database-in-parallel-data-warehouse"></a>base de données tempdb en parallèle Data Warehouse
**tempdb** est une base de données système SQL Server PDW qui stocke des tables temporaires locales pour les bases de données utilisateur. Les tables temporaires sont souvent utilisées pour améliorer les performances des requêtes. Par exemple, vous pouvez utiliser une table temporaire pour modulariser un script et réutiliser des données calculées.  
  
Pour plus d’informations sur les bases de données système, voir [bases de données système](system-databases.md).  
  
## <a name="Basics"></a>Termes et concepts clés  
*table temporaire locale*  
Une *table temporaire locale* utilise le préfixe # avant le nom de la table et est une table temporaire créée par une session utilisateur locale. Chaque session peut uniquement accéder aux données des tables temporaires locales pour sa propre session.  
  
Chaque session peut afficher les métadonnées des tables temporaires locales dans toutes les sessions. Par exemple, toutes les sessions peuvent afficher les métadonnées de toutes les tables temporaires `SELECT * FROM tempdb.sys.tables` locales avec la requête.  
  
table temporaire globale  
Les *tables temporaires globales*, prises en charge dans SQL Server avec la syntaxe # #, ne sont pas prises en charge dans cette version de SQL Server PDW.  
  
pdwtempdb  
**pdwtempdb** est la base de données qui stocke les tables temporaires locales.  
  
PDW n’implémente pas les tables temporaires à l’aide de la base de données SQL Server**tempdb** . Au lieu de cela, PDW les stocke dans une base de données appelée pdwtempdb. Cette base de données existe sur chaque nœud de calcul et est invisible pour l’utilisateur via les interfaces PDW. Dans la console d’administration, dans la page stockage, vous verrez qu’ils sont comptabilisés dans une base de données système PDW nommée **tempdb-SQL**.  
  
tempdb  
**tempdb** est le SQL Server base de données tempdb. Il utilise la journalisation minimale. SQL Server utilise tempdb sur les nœuds de calcul pour stocker les tables temporaires dont il a besoin dans le cadre de l’exécution d’opérations de SQL Server.  
  
SQL Server PDW supprime les tables de **tempdb** dans les cas suivants :  
  
-   L’instruction DROP TABLE est exécutée.  
  
-   Une session est déconnectée. Seules les tables temporaires de la session sont supprimées.  
  
-   L’appliance est arrêtée.  
  
-   Le nœud de contrôle a un basculement de cluster.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
SQL Server PDW effectue les mêmes opérations sur les tables temporaires et les tables permanentes, sauf indication contraire. Par exemple, les données des tables temporaires locales, tout comme les tables permanentes, sont distribuées ou répliquées sur les nœuds de calcul.  
  
## <a name="LimitationsRestrictions"></a>Limitations et restrictions  
Limitations et restrictions relatives à la base de données**tempdb** SQL Server PDW. Vous *ne pouvez pas :*  
  
-   Créez une table temporaire globale qui commence par # #.  
  
-   Effectuez une sauvegarde ou une restauration de **tempdb**.  
  
-   Modifiez les autorisations sur **tempdb** avec les instructions **Grant**, **Deny**ou **Revoke** .  
  
-   Exécutez **DBCC SHRINKLOG** pour **tempdb tempdb.**  
  
-   Effectuer des opérations DDL sur **tempdb**. Il existe deux exceptions à cela. Pour plus d’informations, consultez la liste suivante des limitations et restrictions sur les tables temporaires locales.  
  
Limitations et restrictions sur les tables temporaires locales. Vous *ne pouvez pas :*  
  
-   Renommer une table temporaire  
  
-   Créer des partitions, des vues ou des index non-cluster sur une table temporaire. **ALTER index** peut être utilisé pour reconstruire un index cluster d’une table créée à l’aide d’un.  
  
-   Modifiez les autorisations sur les tables temporaires avec les instructions GRANT, DENY ou REVOKE.  
  
-   Exécutez les commandes de la console de base de données sur les tables temporaires.  
  
-   Utilisez le même nom pour deux tables temporaires ou plus dans le même lot. Si plusieurs tables temporaires locales sont utilisées dans un traitement, chacune doit avoir un nom unique. Si plusieurs sessions exécutent le même lot et créent la même table temporaire locale, SQL Server PDW ajoute en interne un suffixe numérique au nom de la table temporaire locale afin de conserver un nom unique pour chaque table temporaire locale.  
  
> [!NOTE]  
> Vous *pouvez* créer et mettre à jour des statistiques sur une table temporaire. **ALTER index** peut être utilisé pour reconstruire un index cluster.  
  
## <a name="permissions"></a>Autorisations  
Tous les utilisateurs peuvent créer des objets temporaires dans tempdb. Les utilisateurs n'ont accès qu'aux objets qu'ils possèdent, sauf s'ils ont reçu des autorisations supplémentaires. Il est possible de révoquer l’autorisation de connexion à tempdb pour empêcher un utilisateur d’utiliser tempdb. Cependant, cela n’est pas recommandé, car certaines opérations courantes nécessitent l’utilisation de tempdb.  
  
## <a name="RelatedTasks"></a>Tâches associées  
  
|Tâches|Description|  
|---------|---------------|  
|Créer une table dans **tempdb**.|Vous pouvez créer une table temporaire utilisateur avec les CREATE TABLE et CREATE TABLE en tant qu’instructions SELECT. Pour plus d’informations, consultez [Create table](../t-sql/statements/create-table-azure-sql-data-warehouse.md) et [Create table comme SELECT](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md).|  
|Affichez la liste des tables existantes dans **tempdb**.|`SELECT * FROM tempdb.sys.tables;`|  
|Affichez la liste des colonnes existantes dans **tempdb**.|`SELECT * FROM tempdb.sys.columns;`|  
|Affichez la liste des objets existants dans **tempdb**.|`SELECT * FROM tempdb.sys.objects;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
