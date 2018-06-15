---
title: Ajout d’une colonne à une Table SQL Server | Documents Microsoft
description: Ajout d’une colonne à une table SQL Server à l’aide du pilote OLE DB pour SQL Server
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
- columns [OLE DB]
- AddColumn function
- OLE DB Driver for SQL Server, columns
- adding columns
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 116991307bfe1c9601354f0aa01e6face270f83c
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306858"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Ajout d'une colonne à une table SQL Server.
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour SQL Server expose la **ITableDefinition::AddColumn** (fonction). Cela permet aux consommateurs d’ajouter une colonne à une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.  
  
 Lorsque vous ajoutez une colonne à une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de table, le pilote OLE DB pour le consommateur SQL Server est contraint comme suit :  
  
-   Si DBPROP_COL_AUTOINCREMENT est VARIANT_TRUE, DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Si la colonne est définie à l’aide de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **timestamp** type de données, DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Pour toute autre définition de colonne, DBPROP_COL_NULLABLE doit être VARIANT_TRUE.  
  
 Les consommateurs spécifient le nom de la table en tant que chaîne de caractères Unicode dans le *pwszName* membre de la *uName* union dans la *pTableID* paramètre. Le *eKind* membre *pTableID* doit être DBKIND_NAME.  
  
 Le nouveau nom de colonne est spécifié en tant que chaîne de caractères Unicode dans le *pwszName* membre de la *uName* union dans la *dbcid* membres du paramètre DBCOLUMNDESC *pColumnDesc*. Le *eKind* membre doit être DBKIND_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et des index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)  
  
  
