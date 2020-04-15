---
title: Conversions implicites de curseur (ODBC) Microsoft Docs
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
ms.openlocfilehash: ced726893b0f287db6b1fec7c8d16c6b844eea2b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298379"
---
# <a name="implicit-cursor-conversions-odbc"></a>Conversions de curseurs implicites (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les applications peuvent demander un type curseur par [SQLSetStmtAttr,](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) puis exécuter une déclaration SQL qui n’est pas pris en charge par les curseurs serveur du type demandé. Un appel à **SQLExecute** ou **SQLExecDirect** renvoie SQL_SUCCESS_WITH_INFO et **SQLGetDiagRec** revient :  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 L’application peut déterminer quel type de curseur est maintenant utilisé en appelant **SQLGetStmtOption** réglé pour SQL_CURSOR_TYPE. La conversion de type de curseur s'applique à une seule instruction. La prochaine **SQLExecDirect** ou **SQLExecute** se fera à l’aide des paramètres de curseur d’instruction d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de la programmation de Cursesor &#40;&#41;oDBC](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
