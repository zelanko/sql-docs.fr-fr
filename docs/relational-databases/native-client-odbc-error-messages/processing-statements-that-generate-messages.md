---
title: Traitement des déclarations qui génèrent des messages . Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- PRINT statement
- messages [ODBC], statements generating messages
- statements [ODBC], message generation
- errors [ODBC], statements generating messages
- SQL Server Native Client ODBC driver, errors
- STATISTICS IO option
- STATISTICS TIME option
- DBCC statements
- SQLExecute function
- RAISERROR statement
- SQLGetDiagRec function
- ODBC error handling, statements generating messages
- SQLExecDirect function
ms.assetid: 672ebdc5-7fa1-4ceb-8d52-fd25ef646654
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9820e202f5032423292c4306aa63b175bce550b6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304690"
---
# <a name="processing-statements-that-generate-messages"></a>Traitement des instructions qui génèrent des messages
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les options STATISTICS TIME et STATISTICS IO de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] SET sont utilisées pour obtenir des informations qui aident au diagnostic des requêtes longues. Les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prennent aussi en charge l'option SHOWPLAN pour analyser les plans de requête. Une application ODBC peut définir ces options en exécutant les instructions suivantes :  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 Lorsque SET STATISTICS TIME ou SET SHOWPLAN sont SUR, **SQLExecute** et **SQLExecDirect** retournent SQL_SUCCESS_WITH_INFO, et, à ce moment-là, l’application peut récupérer la sortie SHOWPLAN ou STATISTICS TIME en appelant **SQLGetDiagRec** jusqu’à ce qu’elle revienne SQL_NO_DATA. Chaque ligne des données SHOWPLAN est retournée au format suivant :  
  
```  
szSqlState="01000", *pfNativeError=6223,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]   
              Table Scan"  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 a remplacé l'option SHOWPLAN par SHOWPLAN_ALL et SHOWPLAN_TEXT, qui retournent l'une et l'autre la sortie comme jeu de résultats, et non comme ensemble de messages.  
  
 Chaque ligne de STATISTICS TIME est retournée au format suivant :  
  
```  
szSqlState="01000", *pfNativeError= 3613,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
   SQL Server Parse and Compile Time: cpu time = 0 ms."  
```  
  
 La sortie de SET STATISTICS IO n'est pas disponible jusqu'à la fin d'un jeu de résultats. Pour obtenir la sortie DE STATISTICS IO, l’application appelle **SQLGetDiagRec** au moment **où SQLFetch** ou [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) retourne SQL_NO_DATA. La sortie de STATISTICS IO est retournée au format suivant :  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a>Utilisation des instructions DBCC  
 Les instructions DBCC retournent leurs données comme messages, non comme jeux de résultats. **SQLExecDirect** ou **SQLExecute** retournent SQL_SUCCESS_WITH_INFO, et l’application récupère la sortie en appelant **SQLGetDiagRec** jusqu’à ce qu’elle revienne SQL_NO_DATA.  
  
 Par exemple, l'instruction suivante retourne SQL_SUCCESS_WITH_INFO :  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 Appels vers **SQLGetDiagRec** retour:  
  
```  
szSqlState = "01000", *pfNativeError = 2536,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Checking authors"  
szSqlState = "01000", *pfNativeError = 2579,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   The total number of data pages in this table is 1."  
szSqlState = "01000", *pfNativeError = 7929,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table has 23 data rows."  
szSqlState = "01000", *pfNativeError = 2528  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   DBCC execution completed. If DBCC printed error messages,  
   see your System Administrator."  
```  
  
## <a name="using-print-and-raiserror-statements"></a>Utilisation des instructions PRINT et RAISERROR  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]LES déclarations PRINT et RAISERROR renvoient également les données en appelant **SQLGetDiagRec**. Les déclarations DE PRINT font renvoyer l’exécution de la déclaration SQL SQL_SUCCESS_WITH_INFO, et un appel subséquent à **SQLGetDiagRec** renvoie un *SQLState* de 01000. Une erreur RAISERROR avec une gravité égale ou inférieure à dix se comporte de la même façon que PRINT. Un RAISERROR avec une gravité de 11 ou plus provoque l’exécution de retourner SQL_ERROR, et un appel ultérieur à **SQLGetDiagRec** retourne *SQLState* 42000. Par exemple, l'instruction suivante retourne SQL_SUCCESS_WITH_INFO :  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 Appel **SQLGetDiagRec** revient:  
  
```  
szSQLState = "01000", *pfNative Error = 0,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Some message"  
```  
  
 L'instruction suivante retourne SQL_SUCCESS_WITH_INFO :  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 1.', 10, -1)",  
   SQL_NTS)  
```  
  
 Appel **SQLGetDiagRec** revient:  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 L'instruction suivante retourne SQL_ERROR :  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 Appel **SQLGetDiagRec** revient:  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 Le moment d’appeler **SQLGetDiagRec** est crucial lorsque la sortie des relevés PRINT ou RAISERROR est incluse dans un ensemble de résultats. L’appel à **SQLGetDiagRec** pour récupérer la sortie PRINT ou RAISERROR doit être fait immédiatement après la déclaration qui reçoit SQL_ERROR ou SQL_SUCCESS_WITH_INFO. Cela est simple lorsqu'une seule instruction SQL est exécutée, comme dans les exemples ci-dessus. Dans ces cas, l’appel à **SQLExecDirect** ou **SQLExecute** renvoie SQL_ERROR ou SQL_SUCCESS_WITH_INFO et **SQLGetDiagRec** peut alors être appelé. La situation est moins simple lors du codage de boucles pour gérer la sortie d'un lot d'instructions SQL ou lors de l'exécution de procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un jeu de résultats pour chaque instruction SELECT exécutée dans un lot ou une procédure stockée. Si le lot ou la procédure contient les instructions PRINT ou RAISERROR, leur sortie est entrelacée avec les jeux de résultats des instructions SELECT. Si la première déclaration dans le lot ou la procédure est un PRINT ou RAISERROR, le **SQLExecute** ou **SQLExecDirect** renvoie SQL_SUCCESS_WITH_INFO ou SQL_ERROR, et l’application doit appeler **SQLGetDiagRec** jusqu’à ce qu’il retourne SQL_NO_DATA pour récupérer les informations PRINT ou RAISERROR.  
  
 Si la déclaration PRINT ou RAISERROR vient après une déclaration SQL (comme une déclaration SELECT), alors les informations PRINT ou RAISERROR sont retournées lorsque [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)positions sur l’ensemble de résultat contenant l’erreur. **SQLMoreResults** retourne SQL_SUCCESS_WITH_INFO ou SQL_ERROR selon la gravité du message. Les messages sont récupérés en appelant **SQLGetDiagRec** jusqu’à ce qu’il revienne SQL_NO_DATA.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
