---
title: Suppression d’une Table SQL Server | Documents Microsoft
description: Suppression d’une table SQL Server à l’aide du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
manager: craigg
ms.openlocfilehash: 9c73e3be64145d2f3c3f1007b1132fd880c1e4be
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306558"
---
# <a name="dropping-a-sql-server-table"></a>Suppression d'une table SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour SQL Server expose la **ITableDefinition::DropTable** (fonction) pour supprimer un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table à partir d’une base de données.  
  
 Spécifiez le nom de la table en tant que chaîne de caractères Unicode dans le *pwszName* membre de la *uName* union dans la *pTableID* paramètre. Le *eKind* membre *pTableID* doit être DBKIND_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
