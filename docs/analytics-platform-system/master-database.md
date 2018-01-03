---
title: "base de données master (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c71617c0-6689-4f52-81c6-58f4cf7c7377
caps.latest.revision: "8"
ms.workload: not set
ms.openlocfilehash: 1fde1a329703ed833a9fdeb6686b1a63c04aea79
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="master-database"></a>Base de données master
La base de données master de SQL Server PDW stocke les informations de connexion au niveau du matériel et le catalogue de base de données. Il s’agit d’une base de données master SQL Server qui réside sur le nœud de contrôle. Par conséquent, il fournit des fonctionnalités similaires à SQL Server PDW master fournit à SQL Server.  
  
Pour plus d’informations sur les bases de données système, consultez [bases de données système](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
La liste suivante décrit les opérations que vous ne pouvez effectuer sur la base de données master de SQL Server PDW.  
  
Vous *ne peut pas :*  
  
-   Effectuer une sauvegarde différentielle de master.  
  
-   Créer des objets utilisateur dans master.  
  
-   Modifier le classement de master.  
  
-   Modifier le propriétaire du maître.  
  
-   Supprimer ou renommer.  
  
-   Modifier les autorisations au masque.  
  
-   Exécutez **DBCC SHRINKLOG**.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Tâche|Description|  
|--------|---------------|  
|Créer une sauvegarde complète de master.|Exemple :<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Pour plus d’informations, consultez [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md).|  
|Restaurer la base de données master|Pour restaurer la base de données master, utilisez la [restaurer la base de données Master](restore-the-master-database.md) page dans l’outil de Configuration Manager.|  
|Afficher les informations de catalogue de base de données.|`SELECT * FROM master.sys.databases;`|  
|Afficher les informations de connexion et d’autorisation à l’échelle du système.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
