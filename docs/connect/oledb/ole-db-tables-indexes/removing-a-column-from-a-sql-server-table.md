---
title: Supprimer une colonne d’une Table SQL Server | Microsoft Docs
description: Supprimer une colonne d’une table SQL Server à l’aide de OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 007f4a21096dfc2e933ed7777c5bd407a6d40eb1
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109740"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Suppression d'une colonne d'une table SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server expose la **ITableDefinition::DropColumn** (fonction). Cela permet aux consommateurs de supprimer une colonne d’une table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Le consommateur indique un nom de colonne dans la *pwszName*membre de la *uName* union dans le *pColumnID* paramètre. Le nom de colonne est une chaîne de caractères Unicode. Le membre *eKind* de *pColumnID* doit être DBKIND_NAME.  
  
## <a name="example"></a> Exemple  
  
### <a name="code"></a>Code  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Tables et index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
