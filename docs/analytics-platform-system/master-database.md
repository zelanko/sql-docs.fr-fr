---
title: Base de données Master
description: En savoir plus sur la base de données Master en parallèle Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 526f7c7bea8d7ed1e7499649d929f6c732ab07a3
ms.sourcegitcommit: 3bd188e652102f3703812af53ba877cce94b44a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97489679"
---
# <a name="master-database---parallel-data-warehouse"></a>Base de données Master-Data Warehouse parallèles
La base de données Master SQL Server PDW stocke les informations de connexion au niveau de l’appareil et le catalogue de la base de données. Il s’agit d’une base de données Master SQL Server qui réside sur le nœud de contrôle. En tant que tel, il offre des fonctionnalités similaires SQL Server PDW à celles que le maître fournit pour SQL Server.  
  
Pour plus d’informations sur les bases de données système, voir [bases de données système](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
La liste suivante décrit les opérations que vous ne pouvez pas effectuer sur la base de données Master SQL Server PDW.  
  
Vous *ne pouvez pas :*  
  
-   Effectuez une sauvegarde différentielle de Master.  
  
-   Créer des objets utilisateur dans Master.  
  
-   Modifiez le classement de Master.  
  
-   Modifiez le propriétaire de la base de référence Master.  
  
-   Supprimez ou renommez Master.  
  
-   Modifiez les autorisations sur Master.  
  
-   Exécutez **DBCC SHRINKLOG**.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Tâche|Description|  
|--------|---------------|  
|Créez une sauvegarde complète de Master.|Exemple :<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Pour plus d’informations, consultez [Backup database](../t-sql/statements/backup-transact-sql.md?view=aps-pdw-2016&preserve-view=true).|  
|Restaurer la base de données MASTER|Pour restaurer la base de données Master, utilisez la page [restaurer la base de données Master](restore-the-master-database.md) dans l’outil Configuration Manager.|  
|Affichez les informations du catalogue de la base de données.|`SELECT * FROM master.sys.databases;`|  
|Affichez les informations de connexion et d’autorisation à l’ensemble du système.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
