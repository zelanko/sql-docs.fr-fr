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
manager: craigg
ms.openlocfilehash: 99395f9a8dbcb812f5a7764634d42489526875af
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705614"
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
  
  
