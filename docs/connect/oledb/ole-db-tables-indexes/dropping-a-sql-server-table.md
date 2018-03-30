---
title: Suppression d’une Table SQL Server | Documents Microsoft
description: Suppression d’une table SQL Server à l’aide du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- OLE DB Driver for SQL Server, tables
- removing tables
- dropping tables
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62ff10b72d209dce89a4995542d40b4f3e262a34
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="dropping-a-sql-server-table"></a>Suppression d'une table SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour SQL Server expose la **ITableDefinition::DropTable** (fonction) pour supprimer un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table à partir d’une base de données.  
  
 Spécifiez le nom de la table en tant que chaîne de caractères Unicode dans le *pwszName* membre de la *uName* union dans la *pTableID* paramètre. Le *eKind* membre *pTableID* doit être DBKIND_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et des index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
