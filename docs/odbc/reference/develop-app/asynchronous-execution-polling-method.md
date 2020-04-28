---
title: Exécution asynchrone (méthode d’interrogation) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81293399"
---
# <a name="asynchronous-execution-polling-method"></a>Exécution asynchrone (méthode d’interrogation)
Avant ODBC 3,8 et le kit de développement logiciel (SDK) Windows 7, les opérations asynchrones étaient uniquement autorisées sur les fonctions d’instruction. Pour plus d’informations, consultez **exécution des opérations d’instruction de manière asynchrone**, plus loin dans cette rubrique.  
  
 ODBC 3,8 dans le kit de développement logiciel (SDK) Windows 7 a introduit une exécution asynchrone sur les opérations liées à la connexion. Pour plus d’informations, consultez la section **exécution d’opérations de connexion de manière asynchrone** , plus loin dans cette rubrique.  
  
 Dans le kit de développement logiciel (SDK) Windows 7, pour les opérations de connexion ou d’instruction asynchrones, une application a déterminé que l’opération asynchrone a été effectuée à l’aide de la méthode d’interrogation. À compter du kit de développement logiciel (SDK) Windows 8, vous pouvez déterminer qu’une opération asynchrone est terminée à l’aide de la méthode de notification. Pour plus d’informations, consultez [exécution asynchrone (méthode de notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 Par défaut, les pilotes exécutent des fonctions ODBC de façon synchrone. autrement dit, l’application appelle une fonction et le pilote ne retourne pas de contrôle à l’application tant qu’elle n’a pas terminé l’exécution de la fonction. Toutefois, certaines fonctions peuvent être exécutées de façon asynchrone ; autrement dit, l’application appelle la fonction et le pilote, après un traitement minimal, retourne le contrôle à l’application. L’application peut ensuite appeler d’autres fonctions pendant que la première fonction est toujours en cours d’exécution.  
  
 L’exécution asynchrone est prise en charge pour la plupart des fonctions exécutées en grande partie sur la source de données, telles que les fonctions permettant d’établir des connexions, de préparer et d’exécuter des instructions SQL, de récupérer des métadonnées, d’extraire des données et de valider des transactions. Elle est particulièrement utile lorsque la tâche en cours d’exécution sur la source de données prend beaucoup de temps, par exemple un processus de connexion ou une requête complexe sur une base de données volumineuse.  
  
 Lorsque l’application exécute une fonction avec une instruction ou une connexion qui est activée pour le traitement asynchrone, le pilote effectue une quantité minimale de traitement (par exemple, la vérification des arguments pour les erreurs), le traitement à la source de données et retourne le contrôle à l’application avec le code de retour SQL_STILL_EXECUTING. L’application effectue ensuite d’autres tâches. Pour déterminer à quel moment la fonction asynchrone est terminée, l’application interroge le pilote à intervalles réguliers en appelant la fonction avec les mêmes arguments que ceux utilisés à l’origine. Si la fonction est toujours en cours d’exécution, elle retourne SQL_STILL_EXECUTING ; s’il a fini de s’exécuter, il retourne le code qu’il aurait retourné en mode synchrone, par exemple SQL_SUCCESS, SQL_ERROR ou SQL_NEED_DATA.  
  
 Si une fonction s’exécute de façon synchrone ou asynchrone, elle est spécifique au pilote. Par exemple, supposons que les métadonnées du jeu de résultats sont mises en cache dans le pilote. Dans ce cas, il faut très peu de temps pour exécuter **SQLDescribeCol** et le pilote doit simplement exécuter la fonction plutôt que de retarder l’exécution de façon artificielle. En revanche, si le pilote doit récupérer les métadonnées à partir de la source de données, il doit retourner le contrôle à l’application pendant ce cas. Par conséquent, l’application doit être en mesure de gérer un code de retour autre que SQL_STILL_EXECUTING lorsqu’il exécute pour la première fois une fonction de manière asynchrone.  
  
## <a name="executing-statement-operations-asynchronously"></a>Exécution d’opérations d’instruction de manière asynchrone  
 Les fonctions d’instruction suivantes fonctionnent sur une source de données et peuvent s’exécuter de façon asynchrone :  
  
||||  
|-|-|-|  
|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 L’exécution d’une instruction asynchrone est contrôlée soit par instruction, soit par connexion, selon la source de données. Autrement dit, l’application ne spécifie pas qu’une fonction particulière doit être exécutée de façon asynchrone, mais que toute fonction exécutée sur une instruction particulière doit être exécutée de façon asynchrone. Pour déterminer lequel est pris en charge, une application appelle [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) avec l’option SQL_ASYNC_MODE. SQL_AM_CONNECTION est retourné si l’exécution asynchrone au niveau de la connexion (pour un handle d’instruction) est prise en charge ; SQL_AM_STATEMENT si l’exécution asynchrone au niveau de l’instruction est prise en charge.  
  
 Pour spécifier que les fonctions exécutées avec une instruction particulière doivent être exécutées de façon asynchrone, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ASYNC_ENABLE et lui affecte la valeur SQL_ASYNC_ENABLE_ON. Si le traitement asynchrone au niveau de la connexion est pris en charge, l’attribut d’instruction SQL_ATTR_ASYNC_ENABLE est en lecture seule et sa valeur est identique à l’attribut de connexion de la connexion sur laquelle l’instruction a été allouée. Il est propre au pilote, que la valeur de l’attribut d’instruction soit définie au moment de l’allocation de l’instruction ou ultérieurement. Toute tentative de définition de cette valeur retourne SQL_ERROR et SQLSTATE HYC00 (fonctionnalité facultative non implémentée).  
  
 Pour spécifier que les fonctions exécutées avec une connexion particulière doivent être exécutées de façon asynchrone, l’application appelle **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ASYNC_ENABLE et lui affecte la valeur SQL_ASYNC_ENABLE_ON. Tous les futurs descripteurs d’instruction alloués sur la connexion seront activés pour l’exécution asynchrone ; Il est défini par le pilote, que les descripteurs d’instructions existants soient activés ou non par cette action. Si SQL_ATTR_ASYNC_ENABLE est défini sur SQL_ASYNC_ENABLE_OFF, toutes les instructions sur la connexion sont en mode synchrone. Une erreur est retournée si l’exécution asynchrone est activée alors qu’il existe une instruction active sur la connexion.  
  
 Pour déterminer le nombre maximal d’instructions simultanées actives en mode asynchrone que le pilote peut prendre en charge sur une connexion donnée, l’application appelle **SQLGetInfo** avec l’option SQL_MAX_ASYNC_CONCURRENT_STATEMENTS.  
  
 Le code suivant illustre le fonctionnement du modèle d’interrogation :  
  
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
  
 Lorsqu’une fonction s’exécute de façon asynchrone, l’application peut appeler des fonctions sur toutes les autres instructions. L’application peut également appeler des fonctions sur n’importe quelle connexion, à l’exception de celle qui est associée à l’instruction asynchrone. Toutefois, l’application ne peut appeler que la fonction d’origine et les fonctions suivantes (avec le descripteur d’instruction ou la connexion associée, le descripteur d’environnement), une fois qu’une opération d’instruction retourne SQL_STILL_EXECUTING :  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (sur le descripteur d’instruction)  
  
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
  
 Si l’application appelle une autre fonction avec l’instruction asynchrone ou avec la connexion associée à cette instruction, la fonction retourne SQLSTATE HY010 (erreur de séquence de fonction), par exemple.  
  
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
  
 Lorsqu’une application appelle une fonction pour déterminer si elle s’exécute toujours de façon asynchrone, elle doit utiliser le descripteur d’instruction d’origine. Cela est dû au fait que l’exécution asynchrone est suivie par instruction. L’application doit également fournir des valeurs valides pour les autres arguments. les arguments d’origine vont vous aider à effectuer la vérification des erreurs passée dans le gestionnaire de pilotes. Toutefois, une fois que le pilote a vérifié le descripteur d’instruction et déterminé que l’instruction s’exécute de façon asynchrone, il ignore tous les autres arguments.  
  
 Pendant qu’une fonction s’exécute de façon asynchrone, autrement dit, une fois qu’elle a retourné SQL_STILL_EXECUTING et avant de retourner un code différent, l’application peut l’annuler en appelant **SQLCancel** ou **SQLCancelHandle** avec le même descripteur d’instruction. Il n’est pas garanti que l’exécution de la fonction soit annulée. Par exemple, la fonction peut être déjà terminée. En outre, le code retourné par **SQLCancel** ou **SQLCancelHandle** indique uniquement si la tentative d’annulation de la fonction a réussi, pas si elle a réellement annulé la fonction. Pour déterminer si la fonction a été annulée, l’application appelle à nouveau la fonction. Si la fonction a été annulée, elle retourne SQL_ERROR et SQLSTATE HY008 (opération annulée). Si la fonction n’a pas été annulée, elle retourne un autre code, tel que SQL_SUCCESS, SQL_STILL_EXECUTING ou SQL_ERROR avec une valeur SQLSTATE différente.  
  
 Pour désactiver l’exécution asynchrone d’une instruction particulière lorsque le pilote prend en charge le traitement asynchrone au niveau de l’instruction, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ASYNC_ENABLE et lui affecte la valeur SQL_ASYNC_ENABLE_OFF. Si le pilote prend en charge le traitement asynchrone au niveau de la connexion, l’application appelle **SQLSetConnectAttr** pour définir SQL_ATTR_ASYNC_ENABLE sur SQL_ASYNC_ENABLE_OFF, ce qui désactive l’exécution asynchrone de toutes les instructions sur la connexion.  
  
 L’application doit traiter les enregistrements de diagnostic dans la boucle répétée de la fonction d’origine. Si **SQLGetDiagField** ou **SQLGetDiagRec** est appelé lors de l’exécution d’une fonction asynchrone, elle retourne la liste actuelle des enregistrements de diagnostic. Chaque fois que l’appel de fonction d’origine est répété, il efface les enregistrements de diagnostic précédents.  
  
## <a name="executing-connection-operations-asynchronously"></a>Exécution d’opérations de connexion de manière asynchrone  
 Avant ODBC 3,8, l’exécution asynchrone était autorisée pour les opérations liées aux instructions, telles que prepare, Execute et FETCH, ainsi que pour les opérations de métadonnées de catalogue. À compter de ODBC 3,8, l’exécution asynchrone est également possible pour les opérations liées à la connexion, telles que la connexion, la déconnexion, la validation et la restauration.  
  
 Pour plus d’informations sur ODBC 3,8, voir [What’s New in odbc 3,8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 L’exécution d’opérations de connexion de manière asynchrone est utile dans les scénarios suivants :  
  
-   Lorsqu’un petit nombre de threads gère un grand nombre d’appareils avec des débits de données très élevés. Pour optimiser la réactivité et l’évolutivité, il est souhaitable que toutes les opérations soient asynchrones.  
  
-   Lorsque vous souhaitez superposer des opérations de base de données sur plusieurs connexions afin de réduire les temps de transfert écoulés.  
  
-   Des appels ODBC asynchrones efficaces et la possibilité d’annuler des opérations de connexion permettent à une application d’annuler une opération lente sans avoir à attendre des délais d’attente.  
  
 Les fonctions suivantes, qui opèrent sur des handles de connexion, peuvent maintenant être exécutées de façon asynchrone :  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Pour déterminer si un pilote prend en charge les opérations asynchrones sur ces fonctions, une application appelle **SQLGetInfo** avec SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE est retourné si les opérations asynchrones sont prises en charge. SQL_ASYNC_DBC_NOT_CAPABLE est retourné si les opérations asynchrones ne sont pas prises en charge.  
  
 Pour spécifier que les fonctions exécutées avec une connexion particulière doivent être exécutées de façon asynchrone, l’application appelle **SQLSetConnectAttr** et définit l’attribut SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE sur SQL_ASYNC_DBC_ENABLE_ON. La définition d’un attribut de connexion avant d’établir une connexion s’exécute toujours de façon synchrone. En outre, l’opération qui définit l’attribut de connexion SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE avec **SQLSetConnectAttr** s’exécute toujours de façon synchrone.  
  
 Une application peut activer l’opération asynchrone avant d’établir une connexion. Étant donné que le gestionnaire de pilotes ne peut pas déterminer le pilote à utiliser avant d’établir une connexion, le gestionnaire de pilotes renvoie toujours la valeur réussite dans **SQLSetConnectAttr**. Toutefois, la connexion peut échouer si le pilote ODBC ne prend pas en charge les opérations asynchrones.  
  
 En général, il peut y avoir au plus une fonction d’exécution asynchrone associée à un handle de connexion ou un handle d’instruction particulier. Toutefois, un descripteur de connexion peut avoir plusieurs descripteurs d’instruction associés. S’il n’y a pas d’opération asynchrone en cours d’exécution sur le handle de connexion, un descripteur d’instruction associé peut exécuter une opération asynchrone. De même, vous pouvez avoir une opération asynchrone sur un handle de connexion si aucune opération asynchrone n’est en cours sur un handle d’instruction associé. Une tentative d’exécution d’une opération asynchrone à l’aide d’un handle qui exécute actuellement une opération asynchrone retourne HY010, « erreur de séquence de fonction ».  
  
 Si une opération de connexion retourne SQL_STILL_EXECUTING, une application peut uniquement appeler la fonction d’origine et les fonctions suivantes pour ce handle de connexion :  
  
-   **SQLCancelHandle** (sur le handle de connexion)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (allocation de env/DBC)  
  
-   **SQLAllocHandleStd** (allocation de env/DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 L’application doit traiter les enregistrements de diagnostic dans la boucle répétée de la fonction d’origine. Si SQLGetDiagField ou SQLGetDiagRec est appelé lors de l’exécution d’une fonction asynchrone, elle retourne la liste actuelle des enregistrements de diagnostic. Chaque fois que l’appel de fonction d’origine est répété, il efface les enregistrements de diagnostic précédents.  
  
 Si une connexion est ouverte ou fermée de manière asynchrone, l’opération est terminée lorsque l’application reçoit SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO dans l’appel de fonction d’origine.  
  
 Une nouvelle fonction a été ajoutée à ODBC 3,8, **SQLCancelHandle**. Cette fonction annule les six fonctions de connexion (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**et **SQLSetConnectAttr**). Une application doit appeler **SQLGetFunctions** pour déterminer si le pilote prend en charge **SQLCancelHandle**. Comme avec **SQLCancel**, si **SQLCancelHandle** retourne Success, cela ne signifie pas que l’opération a été annulée. Une application doit rappeler la fonction d’origine pour déterminer si l’opération a été annulée. **SQLCancelHandle** vous permet d’annuler des opérations asynchrones sur des handles de connexion ou des handles d’instruction. L’utilisation de **SQLCancelHandle** pour annuler une opération sur un handle d’instruction est identique à l’appel de **SQLCancel**.  
  
 Il n’est pas nécessaire de prendre en charge à la fois les opérations de connexion **SQLCancelHandle** et asynchrones. Un pilote peut prendre en charge des opérations de connexion asynchrones, mais pas **SQLCancelHandle**, ou vice versa.  
  
 Les opérations de connexion asynchrone et **SQLCancelHandle** peuvent également être utilisées par les applications ODBC 3. x et ODBC 2. x avec un pilote ODBC 3,8 et le gestionnaire de pilotes ODBC 3,8. Pour plus d’informations sur la façon d’activer une ancienne application pour utiliser les nouvelles fonctionnalités de la version ODBC ultérieure, consultez [matrice de compatibilité](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Regroupement de connexions  
 Chaque fois que le regroupement de connexions est activé, les opérations asynchrones sont uniquement prises en charge au minimum pour établir une connexion (avec **SQLConnect** et **SQLDriverConnect**) et fermer une connexion avec **SQLDisconnect**. Toutefois, une application doit toujours être en mesure de gérer le SQL_STILL_EXECUTING valeur de retour de **SQLConnect**, **SQLDriverConnect**et **SQLDisconnect**.  
  
 Lorsque le regroupement de connexions est activé, **SQLEndTran** et **SQLSetConnectAttr** sont pris en charge pour les opérations asynchrones.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre comment utiliser **SQLSetConnectAttr** pour activer l’exécution asynchrone pour les fonctions liées à la connexion.  
  
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
 Cet exemple montre des opérations de validation asynchrones. Les opérations de restauration peuvent également être effectuées de cette manière.  
  
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
