---
description: Lots d'instructions
title: Lots d’instructions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 77ca9dc51b0c4529b54e6107adfcf19fb4f8bab8
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438392"
---
# <a name="batches-of-statements"></a>Lots d'instructions
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Un lot d' [!INCLUDE[tsql](../../../includes/tsql-md.md)] instructions contient plusieurs instructions, séparées par un point-virgule (;), créé dans une chaîne unique transmise à la [fonction](../../../odbc/reference/syntax/sqlprepare-function.md) **SQLExecDirect** ou SQLPrepare. Par exemple :  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 Les lots peuvent se révéler plus efficaces que la soumission des instructions séparément car le trafic réseau est souvent réduit. Utilisez [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) pour être positionné sur le jeu de résultats suivant lorsque vous avez terminé avec le jeu de résultats actuel.  
  
 Les lots peuvent toujours être utilisés lorsque les attributs de curseur ODBC sont définis sur les valeurs par défaut d'un curseur avant uniquement en lecture seule avec une taille d'ensemble de lignes de 1.  
  
 Si un lot est exécuté lors de l'utilisation de curseurs côté serveur contre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le curseur côté serveur est converti implicitement en un jeu de résultats par défaut. **SQLExecDirect** ou **SQLExecute** retournent SQL_SUCCESS_WITH_INFO, et un appel à **SQLGetDiagRec** retourne :  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’instructions &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
