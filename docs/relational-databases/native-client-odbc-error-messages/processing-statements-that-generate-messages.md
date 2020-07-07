---
title: Traitement des instructions qui génèrent des messages | Microsoft Docs
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
ms.openlocfilehash: ebd3a371915f17f0a04165dd66ac0ca4394456e7
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009161"
---
# <a name="processing-statements-that-generate-messages"></a>Traitement des instructions qui génèrent des messages
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Les options STATISTICS TIME et STATISTICS IO de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] SET sont utilisées pour obtenir des informations qui aident au diagnostic des requêtes longues. Les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prennent aussi en charge l'option SHOWPLAN pour analyser les plans de requête. Une application ODBC peut définir ces options en exécutant les instructions suivantes :  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 Lorsque SET STATISTICs TIME ou SET SHOWPLAN sont ACTIVÉs, **SQLExecute** et **SQLExecDirect** retournent SQL_SUCCESS_WITH_INFO et, à ce stade, l’application peut récupérer la sortie Showplan ou Statistics Time en appelant **SQLGetDiagRec** jusqu’à ce qu’elle retourne SQL_NO_DATA. Chaque ligne des données SHOWPLAN est retournée au format suivant :  
  
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
  
 La sortie de SET STATISTICS IO n'est pas disponible jusqu'à la fin d'un jeu de résultats. Pour accéder à la sortie des statistiques d’e/s, l’application appelle **SQLGetDiagRec** au moment où **SQLFetch** ou [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) retourne SQL_NO_DATA. La sortie de STATISTICS IO est retournée au format suivant :  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a>Utilisation des instructions DBCC  
 Les instructions DBCC retournent leurs données comme messages, non comme jeux de résultats. **SQLExecDirect** ou **SQLExecute** retournent SQL_SUCCESS_WITH_INFO, et l’application récupère la sortie en appelant **SQLGetDiagRec** jusqu’à ce qu’elle retourne SQL_NO_DATA.  
  
 Par exemple, l'instruction suivante retourne SQL_SUCCESS_WITH_INFO :  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 Les appels à **SQLGetDiagRec** retournent :  
  
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
 [!INCLUDE[tsql](../../includes/tsql-md.md)]Les instructions PRINT et RAISERROR renvoient également des données en appelant **SQLGetDiagRec**. Les instructions PRINT forcent l’exécution de l’instruction SQL à retourner SQL_SUCCESS_WITH_INFO, et un appel ultérieur à **SQLGetDiagRec** retourne une valeur *SQLSTATE* de 01000. Une erreur RAISERROR avec une gravité égale ou inférieure à dix se comporte de la même façon que PRINT. Une instruction RAISERROR dont le niveau de gravité est supérieur ou égal à 11 provoque le retour de l’instruction EXECUTE SQL_ERROR et un appel ultérieur à **SQLGetDiagRec** retourne *SQLSTATE* 42000. Par exemple, l'instruction suivante retourne SQL_SUCCESS_WITH_INFO :  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 L’appel de **SQLGetDiagRec** retourne :  
  
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
  
 L’appel de **SQLGetDiagRec** retourne :  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 L'instruction suivante retourne SQL_ERROR :  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 L’appel de **SQLGetDiagRec** retourne :  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 Le minutage de l’appel de **SQLGetDiagRec** est essentiel lorsque la sortie des instructions Print ou RAISERROR est incluse dans un jeu de résultats. L’appel de **SQLGetDiagRec** pour récupérer la sortie Print ou RAISERROR doit être effectué immédiatement après l’instruction qui reçoit SQL_ERROR ou SQL_SUCCESS_WITH_INFO. Cela est simple lorsqu'une seule instruction SQL est exécutée, comme dans les exemples ci-dessus. Dans ce cas, l’appel à **SQLExecDirect** ou **SQLExecute** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO et **SQLGetDiagRec** peut ensuite être appelé. La situation est moins simple lors du codage de boucles pour gérer la sortie d'un lot d'instructions SQL ou lors de l'exécution de procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un jeu de résultats pour chaque instruction SELECT exécutée dans un lot ou une procédure stockée. Si le lot ou la procédure contient les instructions PRINT ou RAISERROR, leur sortie est entrelacée avec les jeux de résultats des instructions SELECT. Si la première instruction du traitement ou de la procédure est PRINT ou RAISERROR, **SQLExecute** ou **SQLExecDirect** retourne SQL_SUCCESS_WITH_INFO ou SQL_ERROR, et l’application doit appeler **SQLGetDiagRec** jusqu’à ce qu’elle retourne SQL_NO_DATA pour récupérer les informations Print ou RAISERROR.  
  
 Si l’instruction PRINT ou RAISERROR vient après une instruction SQL (telle qu’une instruction SELECT), les informations PRINT ou RAISERROR sont retournées lorsque [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)positionne sur le jeu de résultats contenant l’erreur. **SQLMoreResults** retourne SQL_SUCCESS_WITH_INFO ou SQL_ERROR selon la gravité du message. Les messages sont récupérés en appelant **SQLGetDiagRec** jusqu’à ce qu’il retourne SQL_NO_DATA.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
