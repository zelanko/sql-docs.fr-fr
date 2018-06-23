---
title: Les Conversions implicites de curseurs (ODBC) | Documents Microsoft
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
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b1f1880ea464949bd962bab002d1f1129261463c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044940"
---
# <a name="implicit-cursor-conversions-odbc"></a>Conversions de curseurs implicites (ODBC)
  Les applications peuvent demander un type de curseur via [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , puis exécutez une instruction SQL qui n’est pas pris en charge par les curseurs de serveur du type demandé. Un appel à **SQLExecute** ou **SQLExecDirect** retourne SQL_SUCCESS_WITH_INFO et **SQLGetDiagRec** retourne :  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 L’application peut déterminer quel type de curseur est maintenant utilisé en appelant **SQLGetStmtOption** la valeur SQL_CURSOR_TYPE. La conversion de type de curseur s'applique à une seule instruction. La prochaine **SQLExecDirect** ou **SQLExecute** est effectuée en utilisant les paramètres de curseur d’instruction d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de programmation de curseurs &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  