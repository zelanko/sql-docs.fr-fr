---
title: Ajout d’une colonne à une Table SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bb1ffaf8f75f73ead1742f9a9284c06c81e83ef6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853257"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Ajout d'une colonne à une table SQL Server.
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ITableDefinition::AddColumn** (fonction). Cela permet aux consommateurs d’ajouter une colonne à une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Lorsque vous ajoutez une colonne à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client est contraint comme suit :  
  
-   Si DBPROP_COL_AUTOINCREMENT est VARIANT_TRUE, DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Si la colonne est définie en utilisant le type de données **timestamp** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Pour toute autre définition de colonne, DBPROP_COL_NULLABLE doit être VARIANT_TRUE.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Le nouveau nom de colonne est spécifié en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le membre *dbcid* du paramètre DBCOLUMNDESC *pColumnDesc*. Le membre *eKind* doit être DBKIND_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
