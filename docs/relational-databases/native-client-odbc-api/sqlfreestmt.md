---
title: SQLFreeStmt | Microsoft Docs
ms.custom: 
ms.date: 11/23/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a198bb508f07bd16278df4784d4c5705bbdf8f9e
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  En règle générale   
      **SQLFreeStmt** n'est pas recommandé dans ODBC 3.0 et les versions ultérieures. Toutefois si l’application doit réutiliser l’instruction vous devez toujours utiliser **SQLFreeStmt** avec la **SQL_RESET_PARAMS** et **SQL_UNBIND** options). Vous pouvez également utiliser [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), et [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) pour remplacer ou dupliquent la fonction de **SQLFreeStmt** et les utiliser à la place.  
  
 En règle générale, il est plus efficace de réutiliser des instructions à to les supprimer et d’allouer de nouveaux. Toutefois dans certaines situations, telles que la réutilisation des instructions, SQLFreeStmt toujours doit être utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFreeStmt, fonction](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [Détails d’implémentation API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
