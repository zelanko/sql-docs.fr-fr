---
title: Conversions de curseurs implicites (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: rothja
ms.author: jroth
ms.openlocfilehash: ff8350c71a853e39ff1d35a1f3fba6e8e1944934
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85020659"
---
# <a name="implicit-cursor-conversions-odbc"></a>Conversions de curseurs implicites (ODBC)
  Les applications peuvent demander un type de curseur à l’aide de [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , puis exécuter une instruction SQL qui n’est pas prise en charge par les curseurs côté serveur du type demandé. Un appel à **SQLExecute** ou à **SQLExecDirect** retourne SQL_SUCCESS_WITH_INFO et **SQLGetDiagRec** retourne :  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 L’application peut déterminer le type de curseur qui est maintenant utilisé en appelant **SQLGetStmtOption** défini sur SQL_CURSOR_TYPE. La conversion de type de curseur s'applique à une seule instruction. **SQLExecDirect** ou **SQLExecute** suivant seront effectués à l’aide des paramètres de curseur d’instruction d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de programmation de curseur &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  
