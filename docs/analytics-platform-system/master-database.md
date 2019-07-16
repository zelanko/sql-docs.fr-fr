---
title: Base de données master - Parallel Data Warehouse | Microsoft Docs
description: En savoir plus sur la base de données master dans Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9f37c7a85baea3b41f6016a57e4f57579b427719
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960651"
---
# <a name="master-database---parallel-data-warehouse"></a>Base de données master - Parallel Data Warehouse
La base de données master de SQL Server PDW stocke les informations de connexion au niveau du matériel et le catalogue de base de données. Il est une base de données master SQL Server qui réside sur le nœud de contrôle. Par conséquent, il fournit des fonctionnalités similaires à SQL Server PDW comme principal fournit à SQL Server.  
  
Pour plus d’informations sur les bases de données système, consultez [bases de données système](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
La liste suivante décrit les opérations que vous ne pouvez effectuer sur la base de données master de SQL Server PDW.  
  
Vous *ne peut pas :*  
  
-   Effectuer une sauvegarde différentielle de master.  
  
-   Créer des objets utilisateur dans master.  
  
-   Modifier le classement du serveur principal.  
  
-   Changer le propriétaire du maître.  
  
-   Supprimez ou renommez master.  
  
-   Autorisations de modification sur master.  
  
-   Exécutez **DBCC SHRINKLOG**.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Tâche|Description|  
|--------|---------------|  
|Créer une sauvegarde complète du serveur principal.|Exemple :<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Pour plus d’informations, consultez [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md).|  
|Restaurer la base de données MASTER|Pour restaurer la base de données master, utilisez la [restaurer la base de données Master](restore-the-master-database.md) page dans l’outil de Configuration Manager.|  
|Afficher les informations de catalogue de base de données.|`SELECT * FROM master.sys.databases;`|  
|Afficher les informations de connexion et l’autorisation de l’échelle du système.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
