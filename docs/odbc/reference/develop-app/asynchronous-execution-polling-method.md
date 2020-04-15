---
title: Exécution asynchrone (méthode de vote) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- asynchronous execution [ODBC]
ms.assetid: 8cd21734-ef8e-4066-afd5-1f340e213f9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca7b3d5fa16be44bf4c2ef8f8df8953ae081235d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293399"
---
# <a name="asynchronous-execution-polling-method"></a>Exécution asynchrone (méthode d’interrogation)
Avant ODBC 3.8 et Windows 7 SDK, les opérations asynchrones n’étaient autorisées que sur les fonctions de déclaration. Pour plus d’informations, voir les **opérations d’exécution de déclaration Asynchronously**, plus tard dans ce sujet.  
  
 ODBC 3.8 dans windows 7 SDK introduit l’exécution asynchrone sur les opérations liées à la connexion. Pour plus d’informations, voir la section **Opérations de connexion d’exécution Asynchroneously,** plus tard dans ce sujet.  
  
 Dans le Windows 7 SDK, pour les opérations asynchrones de déclaration ou de connexion, une application a déterminé que l’opération asynchrone était complète en utilisant la méthode de vote. À partir de windows 8 SDK, vous pouvez déterminer qu’une opération asynchrone est terminée en utilisant la méthode de notification. Pour plus d’informations, voir [Asynchrone Execution (Méthode de notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 Par défaut, les pilotes exécutent les fonctions ODBC de façon synchrone; c’est-à-dire que l’application appelle une fonction et le conducteur ne retourne pas le contrôle à l’application jusqu’à ce qu’il ait fini d’exécuter la fonction. Cependant, certaines fonctions peuvent être exécutées asynchrone; c’est-à-dire que l’application appelle la fonction, et le conducteur, après un traitement minimal, renvoie le contrôle à l’application. L’application peut alors appeler d’autres fonctions pendant que la première fonction est toujours en exécution.  
  
 L’exécution asynchrone est prise en charge pour la plupart des fonctions qui sont largement exécutées sur la source de données, telles que les fonctions d’établir des connexions, de préparer et d’exécuter des relevés SQL, de récupérer des métadonnées, d’obtenir des données et de valider des transactions. Il est plus utile lorsque la tâche exécutée sur la source de données prend beaucoup de temps, comme un processus de connexion ou une requête complexe contre une grande base de données.  
  
 Lorsque l’application exécute une fonction avec une déclaration ou une connexion activée pour le traitement asynchrone, le conducteur effectue une quantité minimale de traitement (comme la vérification des arguments pour les erreurs), le traitement des mains à la source de données, et retourne le contrôle à l’application avec le code de retour SQL_STILL_EXECUTING. L’application effectue ensuite d’autres tâches. Pour déterminer quand la fonction asynchrone est terminée, l’application sonde le conducteur à intervalles réguliers en appelant la fonction avec les mêmes arguments qu’il a utilisé à l’origine. Si la fonction est toujours en cours d’exécution, elle renvoie SQL_STILL_EXECUTING; s’il a fini l’exécution, il renvoie le code qu’il aurait retourné s’il avait été exécuté de façon synchronisée, comme SQL_SUCCESS, SQL_ERROR ou SQL_NEED_DATA.  
  
 Si une fonction s’exécute de façon synchrone ou asynchrone est spécifique au conducteur. Supposons, par exemple, que les métadonnées définies de résultat soient mises en cache dans le conducteur. Dans ce cas, il faut très peu de temps pour exécuter **SQLDescribeCol** et le conducteur doit simplement exécuter la fonction plutôt que de retarder artificiellement l’exécution. D’autre part, si le conducteur a besoin de récupérer les métadonnées de la source de données, il doit retourner le contrôle à l’application pendant qu’il le fait. Par conséquent, l’application doit être en mesure de gérer un code de retour autre que SQL_STILL_EXECUTING lorsqu’elle exécute pour la première fois une fonction asynchrone.  
  
## <a name="executing-statement-operations-asynchronously"></a>Exécution des opérations de déclaration asynchrone  
 Les fonctions d’instruction suivantes fonctionnent sur une source de données et peuvent s’exécuter asynchrone :  
  
||||  
|-|-|-|  
|[SQLBulkOperations (SQLBulkOperations)](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 L’exécution des déclarations asynchrones est contrôlée soit selon un relevé ou une base par connexion, selon la source de données. Autrement dit, l’application précise non pas qu’une fonction particulière doit être exécutée asynchronement, mais que toute fonction exécutée sur une déclaration particulière doit être exécutée asynchronement. Pour savoir lequel est pris en charge, une application appelle [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) avec une option de SQL_ASYNC_MODE. SQL_AM_CONNECTION est retournée si l’exécution asynchrone au niveau de connexion (pour une poignée de déclaration) est prise en charge; SQL_AM_STATEMENT si l’exécution asynchrone au niveau de la déclaration est soutenue.  
  
 Pour spécifier que les fonctions exécutées avec une instruction particulière doivent être exécutées asynchronement, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ASYNC_ENABLE et le définit à SQL_ASYNC_ENABLE_ON. Si le traitement asynchrone au niveau de connexion est pris en charge, l’attribut SQL_ATTR_ASYNC_ENABLE déclaration est lu uniquement et sa valeur est la même que l’attribut de connexion de la connexion sur laquelle l’instruction a été attribuée. Il est spécifique au conducteur si la valeur de l’attribut de l’instruction est fixée au moment de l’attribution des relevés ou plus tard. Tenter de le définir sera de retour SQL_ERROR et SQLSTATE HYC00 (fonction facultative non implémentée).  
  
 Pour spécifier que les fonctions exécutées avec une connexion particulière doivent être exécutées asynchronement, l’application appelle **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ASYNC_ENABLE et le définit à SQL_ASYNC_ENABLE_ON. Toutes les poignées de déclaration futures allouées à la connexion seront activées pour l’exécution asynchrone; il est défini par le conducteur si les poignées de relevé existantes seront activées par cette action. Si SQL_ATTR_ASYNC_ENABLE est configuré pour SQL_ASYNC_ENABLE_OFF, toutes les déclarations sur la connexion sont en mode synchrone. Une erreur est retournée si l’exécution asynchrone est activée alors qu’il y a une déclaration active sur la connexion.  
  
 Pour déterminer le nombre maximal d’instructions simultanées actives en mode asynchrone que le conducteur peut prendre en charge sur une connexion donnée, l’application appelle **SQLGetInfo** avec l’option SQL_MAX_ASYNC_CONCURRENT_STATEMENTS.  
  
 Le code suivant montre comment fonctionne le modèle de sondage :  
  
```  
SQLHSTMT  hstmt1;  
SQLRETURN rc;  
  
// Specify that the statement is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute a SELECT statement asynchronously.  
while ((rc=SQLExecDirect(hstmt1,"SELECT * FROM Orders",SQL_NTS))==SQL_STILL_EXECUTING) {  
   // While the statement is still executing, do something else.  
   // Do not use hstmt1, because it is being used asynchronously.  
}  
  
// When the statement has finished executing, retrieve the results.  
```  
  
 Pendant qu’une fonction s’exécute asynchronement, l’application peut appeler des fonctions sur n’importe quelle autre déclaration. L’application peut également appeler des fonctions sur n’importe quelle connexion, sauf celle associée à l’instruction asynchrone. Mais l’application ne peut appeler que la fonction d’origine et les fonctions suivantes (avec la poignée de déclaration ou sa connexion associée, poignée de l’environnement), après une opération de déclaration retourne SQL_STILL_EXECUTING:  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (sur la poignée de déclaration)  
  
-   [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 Si l’application appelle toute autre fonction avec l’instruction asynchrone ou avec la connexion associée à cette déclaration, la fonction renvoie SQLSTATE HY010 (erreur de séquence de fonction), par exemple.  
  
```  
SQLHDBC       hdbc1, hdbc2;  
SQLHSTMT      hstmt1, hstmt2, hstmt3;  
SQLCHAR *     SQLStatement = "SELECT * FROM Orders";  
SQLUINTEGER   InfoValue;  
SQLRETURN     rc;  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt2);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &hstmt3);  
  
// Specify that hstmt1 is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute hstmt1 asynchronously.  
while ((rc = SQLExecDirect(hstmt1, SQLStatement, SQL_NTS)) == SQL_STILL_EXECUTING) {  
   // The following calls return HY010 because the previous call to  
   // SQLExecDirect is still executing asynchronously on hstmt1. The  
   // first call uses hstmt1 and the second call uses hdbc1, on which  
   // hstmt1 is allocated.  
   SQLExecDirect(hstmt1, SQLStatement, SQL_NTS);   // Error!  
   SQLGetInfo(hdbc1, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // Error!  
  
   // The following calls do not return errors. They use a statement  
   // handle other than hstmt1 or a connection handle other than hdbc1.  
   SQLExecDirect(hstmt2, SQLStatement, SQL_NTS);   // OK  
   SQLTables(hstmt3, NULL, 0, NULL, 0, NULL, 0, NULL, 0);   // OK  
   SQLGetInfo(hdbc2, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // OK  
}  
```  
  
 Lorsqu’une application appelle une fonction pour déterminer si elle est toujours en cours d’exécution asynchrone, elle doit utiliser la poignée de déclaration originale. C’est parce que l’exécution asynchrone est suivie sur une base par déclaration. La demande doit également fournir des valeurs valides pour les autres arguments - les arguments initiaux feront - pour obtenir passé la vérification des erreurs dans le gestionnaire de conducteur. Cependant, après que le conducteur vérifie la poignée de la déclaration et détermine que la déclaration s’exécute asynchronement, il ignore tous les autres arguments.  
  
 Alors qu’une fonction s’exécute asynchronement - c’est-à-dire, après qu’elle soit retournée SQL_STILL_EXECUTING et avant qu’elle ne retourne un code différent - l’application peut l’annuler en appelant **SQLCancel** ou **SQLCancelHandle** avec la même poignée de déclaration. Cela n’est pas garanti pour annuler l’exécution de la fonction. Par exemple, la fonction peut déjà avoir terminé. De plus, le code retourné par **SQLCancel** ou **SQLCancelHandle** indique seulement si la tentative d’annulation de la fonction a été couronnée de succès, et non pas si elle a effectivement annulé la fonction. Pour déterminer si la fonction a été annulée, l’application appelle à nouveau la fonction. Si la fonction a été annulée, elle revient SQL_ERROR et SQLSTATE HY008 (Opération annulée). Si la fonction n’a pas été annulée, elle renvoie un autre code, comme SQL_SUCCESS, SQL_STILL_EXECUTING ou SQL_ERROR avec un SQLSTATE différent.  
  
 Pour désactiver l’exécution asynchrone d’une déclaration particulière lorsque le conducteur prend en charge le traitement asynchrone au niveau des déclarations, la demande appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ASYNC_ENABLE et la définit à SQL_ASYNC_ENABLE_OFF. Si le conducteur prend en charge le traitement asynchrone au niveau de connexion, la demande appelle **SQLSetConnectAttr** pour régler SQL_ATTR_ASYNC_ENABLE à SQL_ASYNC_ENABLE_OFF, ce qui désactive l’exécution asynchrone de toutes les déclarations sur la connexion.  
  
 La demande doit traiter les dossiers diagnostiques dans la boucle de répétition de la fonction originale. Si **SQLGetDiagField** ou **SQLGetDiagRec** est appelé lorsqu’une fonction asynchrone est exécutée, il retournera la liste actuelle des dossiers diagnostiques. Chaque fois que l’appel de fonction d’origine est répété, il efface les dossiers diagnostiques précédents.  
  
## <a name="executing-connection-operations-asynchronously"></a>Exécution des opérations de connexion asynchrone  
 Avant ODBC 3.8, l’exécution asynchrone a été autorisée pour les opérations liées à la déclaration telles que la préparation, l’exécution et l’aller chercher, ainsi que pour les opérations de métadonnées de catalogue. À partir de L’ODBC 3.8, l’exécution asynchrone est également possible pour les opérations liées à la connexion telles que la connexion, la déconnexion, la validation et le recul.  
  
 Pour plus d’informations sur ODBC 3.8, voir [What’s New in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 L’exécution des opérations de connexion est utile dans les scénarios suivants :  
  
-   Quand un petit nombre de threads gère un grand nombre d’appareils avec des taux de données très élevés. Pour maximiser la réactivité et l’évolutivité, il est souhaitable que toutes les opérations soient asynchrones.  
  
-   Lorsque vous souhaitez chevaucher les opérations de base de données sur plusieurs connexions afin de réduire les temps de transfert écoulés.  
  
-   Des appels ODBC efficaces et la possibilité d’annuler les opérations de connexion permettent à une application de permettre à l’utilisateur d’annuler toute opération lente sans avoir à attendre les délais d’attente.  
  
 Les fonctions suivantes, qui fonctionnent sur des poignées de connexion, peuvent maintenant être exécutées asynchrone :  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Pour déterminer si un conducteur prend en charge les opérations asynchrones sur ces fonctions, une application appelle **SQLGetInfo** avec SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE est retournée si les opérations asynchrones sont soutenues. SQL_ASYNC_DBC_NOT_CAPABLE est retournée si les opérations asynchrones ne sont pas soutenues.  
  
 Pour spécifier que les fonctions exécutées avec une connexion particulière doivent être exécutées asynchronement, l’application appelle **SQLSetConnectAttr** et définit l’attribut SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE à SQL_ASYNC_DBC_ENABLE_ON. Définir un attribut de connexion avant d’établir une connexion s’exécute toujours de façon synchrone. En outre, l’opération définissant l’attribut de connexion SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE avec **SQLSetConnectAttr** exécute toujours de façon synchrone.  
  
 Une application peut activer une opération asynchrone avant de faire une connexion. Étant donné que le gestionnaire de pilote ne peut pas déterminer quel pilote utiliser avant de faire une connexion, le gestionnaire de pilote retournera toujours le succès dans **SQLSetConnectAttr**. Toutefois, il peut ne pas se connecter si le conducteur de l’ODBC ne prend pas en charge les opérations asynchrones.  
  
 En général, il peut y avoir tout au plus une fonction d’exécution asynchrone associée à une poignée de connexion ou une poignée de déclaration particulière. Cependant, une poignée de connexion peut avoir plus d’une poignée de déclaration associée. S’il n’y a pas d’opération asynchrone exécutant sur la poignée de connexion, une poignée de déclaration associée peut exécuter une opération asynchrone. De même, vous pouvez avoir une opération asynchrone sur une poignée de connexion s’il n’y a pas d’opérations asynchrones en cours sur n’importe quelle poignée de déclaration associée. Une tentative d’exécuter une opération asynchrone à l’aide d’une poignée qui exécute actuellement une opération asynchrone retournera HY010, "Erreur de séquence de fonction".  
  
 Si une opération de connexion renvoie SQL_STILL_EXECUTING, une application ne peut appeler que la fonction d’origine et les fonctions suivantes pour cette poignée de connexion :  
  
-   **SQLCancelHandle** (sur la poignée de connexion)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (allouant ENV/DBC)  
  
-   **SQLAllocHandleStd** (allouant ENV/DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 La demande doit traiter les dossiers diagnostiques dans la boucle de répétition de la fonction originale. Si SQLGetDiagField ou SQLGetDiagRec est appelé lorsqu’une fonction asynchrone est exécutée, il retournera la liste actuelle des dossiers diagnostiques. Chaque fois que l’appel de fonction d’origine est répété, il efface les dossiers diagnostiques précédents.  
  
 Si une connexion est ouverte ou fermée de manière asynchrone, l’opération est terminée lorsque l’application reçoit SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO dans l’appel de fonction d’origine.  
  
 Une nouvelle fonction a été ajoutée à ODBC 3.8, **SQLCancelHandle**. Cette fonction annule les six fonctions de connexion (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLDEndTran**, et **SQLSetConnectAttr**). Une demande devrait appeler **SQLGetFunctions** pour déterminer si le conducteur prend en charge **SQLCancelHandle**. Comme pour **SQLCancel**, si **SQLCancelHandle** revient au succès, cela ne signifie pas que l’opération a été annulée. Une application devrait rappeler la fonction d’origine pour déterminer si l’opération a été annulée. **SQLCancelHandle** vous permet d’annuler des opérations asynchrones sur les poignées de connexion ou les poignées de relevés. Utiliser **SQLCancelHandle** pour annuler une opération sur une poignée de déclaration est la même chose que d’appeler **SQLCancel**.  
  
 Il n’est pas nécessaire de soutenir à la fois **SQLCancelHandle** et les opérations de connexion asynchrones en même temps. Un conducteur peut supporter les opérations de connexion asynchrone, mais pas **SQLCancelHandle**, ou vice versa.  
  
 Les opérations de connexion asynchrones et **SQLCancelHandle** peuvent également être utilisées par les applications ODBC 3.x et ODBC 2.x avec un conducteur ODBC 3.8 et ODBC 3.8 Driver Manager. Pour plus d’informations sur la façon de permettre à une ancienne application d’utiliser de nouvelles fonctionnalités dans la version ultérieure ODBC, voir [Compatibilité Matrix](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Regroupement de connexions  
 Chaque fois que la mise en commun des connexions est activée, les opérations asynchrones ne sont que peu prises en charge pour établir une connexion (avec **SQLConnect** et **SQLDriverConnect**) et la fermeture d’une connexion avec **SQLDisconnect**. Mais une application devrait toujours être en mesure de gérer la valeur de retour SQL_STILL_EXECUTING de **SQLConnect**, **SQLDriverConnect**, et **SQLDisconnect**.  
  
 Lorsque la mise en commun des connexions est activée, **SQLEndTran** et **SQLSetConnectAttr** sont pris en charge pour des opérations asynchrones.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre comment utiliser **SQLSetConnectAttr** pour permettre l’exécution asynchrone pour les fonctions liées à la connexion.  
  
### <a name="code"></a>Code  
  
```  
BOOL AsyncConnect (SQLHANDLE hdbc)   
{  
   SQLRETURN r;  
   SQLHANDLE hdbc;  
  
   // Enable asynchronous execution of connection functions.  
   // This must be executed synchronously, that is r != SQL_STILL_EXECUTING  
   r = SQLSetConnectAttr(  
         hdbc,   
         SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE,  
         reinterpret_cast<SQLPOINTER> (SQL_ASYNC_DBC_ENABLE_ON),  
         0);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   TCHAR szConnStrIn[256] = _T("DSN=AsyncDemo");  
  
   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
  
   if (r == SQL_ERROR)   
   {  
      // Use SQLGetDiagRec to process the error.  
      // If SQLState is HY114, the driver does not support asynchronous execution.  
      return FALSE;  
   }  
  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion, with the same set of arguments.  
      r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   return TRUE;  
}  
  
```  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Cet exemple montre des opérations de validation asynchrones. Les opérations de restauration peuvent également être effectuées de cette façon.  
  
### <a name="code"></a>Code  
  
```  
BOOL AsyncCommit ()   
{  
   SQLRETURN r;   
  
   // Assume that SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE is SQL_ASYNC_DBC_ENABLE_ON.  
  
   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion with the same set of arguments.  
      r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’instructions (ODBC)](../../../odbc/reference/develop-app/executing-statements-odbc.md)
