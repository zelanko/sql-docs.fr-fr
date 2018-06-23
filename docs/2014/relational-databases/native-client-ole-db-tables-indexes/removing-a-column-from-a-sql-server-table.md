---
title: Supprimer une colonne d’une Table SQL Server | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9cecee484e16f2394e9bbef33ff5ed258a0f1752
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144503"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Suppression d'une colonne d'une table SQL Server
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ITableDefinition::DropColumn** (fonction). Cela permet aux consommateurs de supprimer une colonne d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.  
  
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
 [Tables et index](tables-and-indexes.md)  
  
  