---
title: Ajout d'une colonne à une table SQL Server | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b848875ba70c0b31e29de6cb54852c403bd109a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283049"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Ajout d'une colonne à une table SQL Server.
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native De DB OLE de client expose la **fonction ITableDefinition ::AddColumn** fonction. Cela permet aux consommateurs d’ajouter une colonne à une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Lorsque vous ajoutez une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à une table, le consommateur fournisseur de services OLE DB de native Client est limité comme suit :  
  
-   Si DBPROP_COL_AUTOINCREMENT est VARIANT_TRUE, DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Si la colonne est définie en utilisant le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**, DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Pour toute autre définition de colonne, DBPROP_COL_NULLABLE doit être VARIANT_TRUE.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Le nouveau nom de colonne est spécifié en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le membre *dbcid* du paramètre DBCOLUMNDESC *pColumnDesc*. Le membre *eKind* doit être DBKIND_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux et indices](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
