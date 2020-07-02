---
title: Conversions de curseurs implicites (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c10777a2d1142df0c49b7a5e9cd6ac9ab4e7da05
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715292"
---
# <a name="implicit-cursor-conversions-odbc"></a>Conversions de curseurs implicites (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Les applications peuvent demander un type de curseur à l’aide de [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , puis exécuter une instruction SQL qui n’est pas prise en charge par les curseurs côté serveur du type demandé. Un appel à **SQLExecute** ou à **SQLExecDirect** retourne SQL_SUCCESS_WITH_INFO et **SQLGetDiagRec** retourne :  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 L’application peut déterminer le type de curseur qui est maintenant utilisé en appelant **SQLGetStmtOption** défini sur SQL_CURSOR_TYPE. La conversion de type de curseur s'applique à une seule instruction. **SQLExecDirect** ou **SQLExecute** suivant seront effectués à l’aide des paramètres de curseur d’instruction d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de programmation de curseur &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
