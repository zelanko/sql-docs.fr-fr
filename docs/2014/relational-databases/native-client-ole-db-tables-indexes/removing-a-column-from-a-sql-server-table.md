---
title: Supprimer une colonne d’une Table SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 919bd28a82171068349e4019bb1bd5c190d08cd0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108349"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Suppression d'une colonne d'une table SQL Server
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ITableDefinition::DropColumn** (fonction). Cela permet aux consommateurs de supprimer une colonne d’une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Le consommateur indique un nom de colonne dans la *pwszName*membre de la *uName* union dans le *pColumnID* paramètre. Le nom de colonne est une chaîne de caractères Unicode. Le membre *eKind* de *pColumnID* doit être DBKIND_NAME.  
  
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
  
  
