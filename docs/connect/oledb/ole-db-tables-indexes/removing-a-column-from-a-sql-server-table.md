---
title: Supprimer une colonne d’une Table SQL Server | Documents Microsoft
description: Supprimer une colonne d’une table SQL Server à l’aide du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
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
ms.workload: Inactive
ms.openlocfilehash: 5c5a0d279c4d44ba11a6b87223afedc99183c488
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
 [Tables et des index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
