---
description: SQLColumnPrivileges
title: SQLColumnPrivileges | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 01deae36632bcc0543f5df60082a557894d9f50e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428381"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **SQLColumnPrivileges** retourne SQL_SUCCESS si des valeurs existent pour les paramètres*nomcatalogue*, *SchemaName*, *TableName*ou *ColumnName* . **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLColumnPrivileges** peut être exécuté sur un curseur côté serveur statique. Une tentative d’exécution de **SQLColumnPrivileges** sur un curseur pouvant être mis à jour (dynamique ou de jeu de clés) retourne SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les informations de création de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le paramètre *CatalogName* : *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLColumnPrivileges fonction)](https://go.microsoft.com/fwlink/?LinkId=59335)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
