---
title: Ajout d’une colonne à une Table SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 32e78feae791788e0aad87079546ea8c7d49e734
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046494"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Ajout d'une colonne à une table SQL Server.
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ITableDefinition::AddColumn** (fonction). Cela permet aux consommateurs d’ajouter une colonne à une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Lorsque vous ajoutez une colonne à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client est contraint comme suit :  
  
-   Si DBPROP_COL_AUTOINCREMENT est VARIANT_TRUE, DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Si la colonne est définie en utilisant le type de données **timestamp** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Pour toute autre définition de colonne, DBPROP_COL_NULLABLE doit être VARIANT_TRUE.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Le nouveau nom de colonne est spécifié en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le membre *dbcid* du paramètre DBCOLUMNDESC *pColumnDesc*. Le membre *eKind* doit être DBKIND_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
