---
title: Supprimer une colonne d’une Table SQL Server | Documents Microsoft
description: Supprimer une colonne d’une table SQL Server à l’aide du pilote OLE DB pour SQL Server
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
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 7cc11e60ae29f71b539550f7ffe06a26dc2904a8
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306788"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Suppression d'une colonne d'une table SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour SQL Server expose la **ITableDefinition::DropColumn** (fonction). Cela permet aux consommateurs de supprimer une colonne d’une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.  
  
 Les consommateurs spécifient le nom de la table en tant que chaîne de caractères Unicode dans le *pwszName*membre de la *uName* union dans la *pTableID* paramètre. Le *eKind*membre *pTableID* doit être DBKIND_NAME.  
  
 Le consommateur indique un nom de colonne dans la *pwszName*membre de la *uName* union dans la *pColumnID* paramètre. Le nom de colonne est une chaîne de caractères Unicode. Le *eKind* membre *pColumnID* doit être DBKIND_NAME.  
  
## <a name="example"></a>Exemple  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
