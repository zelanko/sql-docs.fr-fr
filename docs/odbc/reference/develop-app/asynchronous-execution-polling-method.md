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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3200f4c83511f176c4d23af34f398a76047fe9a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701082"
---
# <a name="asynchronous-execution-polling-method"></a>Exécution asynchrone (méthode d’interrogation)
Avant d’ODBC 3.8 et le Kit de développement logiciel de Windows 7, les opérations asynchrones étaient autorisées uniquement sur les fonctions de l’instruction. Pour plus d’informations, consultez le **l’exécution des opérations déclaration de façon asynchrone**, plus loin dans cette rubrique.  
  
 ODBC 3.8 dans le Kit de développement logiciel de Windows 7 a introduit une exécution asynchrone sur les opérations liées à la connexion. Pour plus d’informations, consultez le **l’exécution d’opérations de connexion façon asynchrone** section, plus loin dans cette rubrique.  
  
 Dans le Kit de développement Windows 7 pour les opérations de connexion, ou l’instruction asynchrone, une application déterminé que l’opération asynchrone a été terminée à l’aide de la méthode d’interrogation. À compter dans le Kit de développement logiciel Windows 8, vous pouvez déterminer qu’une opération asynchrone est terminée à l’aide de la méthode de notification. Pour plus d’informations, consultez [exécution asynchrone (méthode de Notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 Par défaut, les pilotes s’exécutent les fonctions ODBC de manière synchrone ; Autrement dit, l’application appelle une fonction et le pilote ne retourne pas de contrôle à l’application jusqu'à ce qu’il a terminé l’exécution de la fonction. Toutefois, certaines fonctions peuvent être exécutées de façon asynchrone ; Autrement dit, l’application appelle la fonction, et le pilote, après un traitement minimal, retourne le contrôle à l’application. L’application peut ensuite appeler les autres fonctions tandis que la première fonction est en cours d’exécution.  
  
 Exécution asynchrone est pris en charge pour la plupart des fonctions qui sont exécutées en grande partie sur la source de données, telles que les fonctions pour établir des connexions, préparer et exécuter des instructions SQL, récupérer des métadonnées, extraire des données et valider des transactions. Il est particulièrement utile lorsque la tâche en cours d’exécution sur la source de données prend beaucoup de temps, comme un processus de connexion ou d’une requête complexe sur une base de données volumineux.  
  
 Lorsque l’application exécute une fonction avec une instruction ou une connexion qui est activée pour le traitement asynchrone, le pilote exécute une quantité minimale de traitement (par exemple, vérifiez les arguments pour les erreurs), transmet le traitement à la source de données et retourne le contrôle à l’application avec le code de retour de SQL_STILL_EXECUTING. L’application puis effectue d’autres tâches. Pour déterminer quand la fonction asynchrone est terminée, l’application interroge le pilote à intervalles réguliers en appelant la fonction avec les mêmes arguments que celui utilisé à l’origine. Si la fonction est en cours d’exécution, elle retourne SQL_STILL_EXECUTING ; Si l’exécution est terminée, elle retourne le code qu'il aurait retourné avait il exécutée de façon synchrone, tels que SQL_SUCCESS ou SQL_ERROR SQL_NEED_DATA.  
  
 Si une fonction s’exécute en mode synchrone ou asynchrone est spécifiques aux pilotes. Par exemple, supposons que les métadonnées du jeu de résultats sont mis en cache dans le pilote. Dans ce cas, il prend très peu de temps à exécuter **SQLDescribeCol** et le pilote doit simplement exécuter la fonction plutôt qu’artificiellement retarder l’exécution. En revanche, si le pilote a besoin récupérer les métadonnées à partir de la source de données, elle doit retourner contrôle à l’application pendant qu’il fait cela. Par conséquent, l’application doit être en mesure de gérer un code de retour différent de SQL_STILL_EXECUTING lorsqu’il exécute tout d’abord une fonction de façon asynchrone.  
  
## <a name="executing-statement-operations-asynchronously"></a>L’exécution d’opérations de l’instruction en mode asynchrone  
 Les fonctions d’instruction suivantes fonctionnent sur une source de données et peuvent exécuter de façon asynchrone :  
  
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
  
 Exécution d’instruction asynchrone est contrôlée par instruction ou une fonction de la connexion, en fonction de la source de données. Autrement dit, l’application ne spécifie pas qu’une fonction particulière consiste à exécuter de façon asynchrone, mais que n’importe quelle fonction exécutée sur une instruction particulière doit être exécuté de façon asynchrone. Pour trouver celle qui est prise en charge de la sortie, une application appelle [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) avec une option de SQL_ASYNC_MODE. SQL_AM_CONNECTION est retourné si l’exécution asynchrone de niveau de la connexion (pour un descripteur d’instruction) est pris en charge ; SQL_AM_STATEMENT si l’exécution asynchrone au niveau de l’instruction est pris en charge.  
  
 Pour spécifier que les fonctions exécutées avec une instruction particulière doivent être exécutées de façon asynchrone, l’application appelle **SQLSetStmtAttr** le SQL_ATTR_ASYNC_ENABLE de l’attribut et lui affecte la valeur SQL_ASYNC_ENABLE_ON. Si le traitement asynchrone au niveau de la connexion est prise en charge, l’attribut d’instruction SQL_ATTR_ASYNC_ENABLE est en lecture seule et sa valeur est identique à l’attribut de connexion de la connexion sur laquelle l’instruction a été allouée. Il est spécifique au pilote, si la valeur de l’attribut d’instruction est définie au moment de l’allocation d’instruction ou une version ultérieure. Tentative de définition retourne SQL_ERROR et SQLSTATE HYC00 (fonctionnalité facultative non implémentée).  
  
 Pour spécifier que les fonctions exécutées avec une connexion particulière doivent être exécutées de façon asynchrone, l’application appelle **SQLSetConnectAttr** le SQL_ATTR_ASYNC_ENABLE de l’attribut et lui affecte la valeur SQL_ASYNC_ENABLE_ON. Tous les descripteurs d’instruction futures allouées sur la connexion seront activées pour une exécution asynchrone ; elle est définie par le pilote activation des descripteurs d’instruction existante par cette action. Si SQL_ATTR_ASYNC_ENABLE est défini sur SQL_ASYNC_ENABLE_OFF, toutes les instructions sur la connexion sont en mode synchrone. Une erreur est retournée si l’exécution asynchrone est activée, bien qu’il existe une instruction active sur la connexion.  
  
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
  
 Une est en cours d’exécution en mode asynchrone, l’application peut appeler des fonctions sur toutes les autres instructions. L’application peut également appeler des fonctions sur n’importe quelle connexion, à l’exception de celui associé à l’instruction asynchrone. Mais l’application peut uniquement appeler la fonction d’origine et les fonctions suivantes (avec le descripteur d’instruction ou de la connexion associée, le handle d’environnement), après une opération de l’instruction retourne SQL_STILL_EXECUTING :  
  
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
  
 Si l’application appelle une autre fonction avec l’instruction asynchrone ou avec la connexion associée à cette instruction, la fonction retourne SQLSTATE HY010 (fonction d’erreur de séquence), par exemple.  
  
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
  
 Lorsqu’une application appelle une fonction permettant de déterminer si elle est en cours d’exécution en mode asynchrone, il doit utiliser le descripteur d’instruction d’origine. Il s’agit, car l’exécution asynchrone est suivie sur une base par instruction. L’application doit également fournir des valeurs valides pour les autres arguments, les arguments d’origine fera — pour passer outre dans le Gestionnaire de pilotes de vérification des erreurs. Toutefois, une fois le pilote vérifie le descripteur d’instruction et détermine que l’instruction s’exécute de façon asynchrone, il ignore tous les autres arguments.  
  
 Pendant l’exécution de façon asynchrone une fonction, autrement dit, une fois que ce dernier a renvoyé SQL_STILL_EXECUTING et avant elle retourne un code différent, l’application peut l’annuler en appelant **SQLCancel** ou **SQLCancelHandle** avec le même descripteur d’instruction. Cela n’est pas garanti pour annuler l’exécution de fonction. Par exemple, la fonction peut avoir déjà été achevée. En outre, le code retourné par **SQLCancel** ou **SQLCancelHandle** indique uniquement si la tentative d’annulation de la fonction a réussi, pas si elle annulée en fait la fonction. Pour déterminer si la fonction a été annulée, l’application appelle la fonction à nouveau. Si la fonction a été annulée, elle retourne SQL_ERROR et SQLSTATE HY008 (opération annulée). Si la fonction n’a pas été annulée, elle retourne un autre code, tels que SQL_SUCCESS ou SQL_ERROR avec une valeur SQLSTATE sous différents SQL_STILL_EXECUTING.  
  
 Pour désactiver l’exécution asynchrone d’une instruction particulière lorsque le pilote prend en charge le traitement asynchrone au niveau instruction, l’application appelle **SQLSetStmtAttr** le SQL_ATTR_ASYNC_ENABLE de l’attribut et lui affecte la valeur SQL_ ASYNC_ENABLE_OFF. Si le pilote prend en charge le traitement asynchrone au niveau de la connexion, l’application appelle **SQLSetConnectAttr** pour définir SQL_ATTR_ASYNC_ENABLE to SQL_ASYNC_ENABLE_OFF, ce qui désactive l’exécution asynchrone de toutes les instructions sur la connexion.  
  
 L’application doit traiter les enregistrements de diagnostic dans la boucle récurrente de la fonction d’origine. Si **SQLGetDiagField** ou **SQLGetDiagRec** est appelée lorsqu’une fonction asynchrone s’exécute, elle retournera la liste actuelle des enregistrements de diagnostic. Chaque fois que l’appel de fonction d’origine est répété, il efface les enregistrements de diagnostic précédentes.  
  
## <a name="executing-connection-operations-asynchronously"></a>L’exécution d’opérations de connexion en mode asynchrone  
 Avant d’ODBC 3.8, exécution asynchrone a été autorisée pour la préparer comme des opérations liées à la déclaration de, exécuter et extraire, ainsi que pour les opérations de métadonnées de catalogue. À compter de ODBC 3.8, l’exécution asynchrone peut également rollback, commit et liées à la connexion des opérations telles que se connecter, déconnecter.  
  
 Pour plus d’informations sur ODBC 3.8, consultez [What ' s New in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 L’exécution d’opérations de connexion en mode asynchrone est utile dans les scénarios suivants :  
  
-   Quand un petit nombre de threads gère un grand nombre d’appareils avec des débits très élevés. Pour optimiser la réactivité et l’évolutivité, il est souhaitable pour toutes les opérations asynchrones.  
  
-   Lorsque vous souhaitez se chevaucher des opérations de base de données sur plusieurs connexions pour réduire le temps de transfert écoulé.  
  
-   Les appels ODBC asynchrones efficaces et la possibilité d’annuler des opérations de connexion permettent à une application autoriser l’utilisateur à annuler toute opération lente sans avoir à attendre des délais d’attente.  
  
 Les fonctions suivantes, qui fonctionnent sur les handles de connexion, peuvent désormais être exécutées en mode asynchrone :  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Pour déterminer si un pilote prend en charge les opérations asynchrones sur ces fonctions, une application appelle **SQLGetInfo** avec SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE est retournée si les opérations asynchrones sont prises en charge. SQL_ASYNC_DBC_NOT_CAPABLE est retournée si les opérations asynchrones ne sont pas pris en charge.  
  
 Pour spécifier que les fonctions exécutées avec une connexion particulière doivent être exécutées de façon asynchrone, l’application appelle **SQLSetConnectAttr** et affecte l’attribut sql_attr_async_dbc_functions_enable ne SQL_ASYNC_DBC_ENABLE ACTI_VÉ. Définition d’un attribut de connexion avant d’établir une connexion toujours exécute de façon synchrone. En outre, l’opération de définition de la connexion attribut sql_attr_async_dbc_functions_enable n’avec **SQLSetConnectAttr** toujours exécute de façon synchrone.  
  
 Une application peut activer une opération asynchrone avant d’établir une connexion. Étant donné que le Gestionnaire de pilotes ne peut pas déterminer le pilote à utiliser avant d’établir une connexion, le Gestionnaire de pilotes renvoie toujours success dans **SQLSetConnectAttr**. Toutefois, il peut échouer pour vous connecter si le pilote ODBC ne prend pas en charge les opérations asynchrones.  
  
 En règle générale, il peut avoir au plus un exécute de façon asynchrone (fonction) associé à un handle de connexion particulier ou d’un descripteur d’instruction. Toutefois, un handle de connexion peut avoir plus d’un handle d’instruction associée. S’il n’existe aucune opération asynchrone, l’exécution sur le handle de connexion, un handle d’instruction associée peut exécuter une opération asynchrone. De même, vous pouvez avoir une opération asynchrone sur un handle de connexion si aucune opération asynchrone en cours d’exécution sur n’importe quel handle d’instruction associé. Une tentative d’exécution d’une opération asynchrone à l’aide d’un handle qui exécute actuellement une opération asynchrone retourne HY010, « Erreur de séquence de fonction ».  
  
 Une opération de connexion retourne SQL_STILL_EXECUTING, une application peut uniquement appeler la fonction d’origine et les fonctions suivantes pour ce descripteur de connexion :  
  
-   **SQLCancelHandle** (sur le handle de connexion)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (allocation ENV/DBC)  
  
-   **SQLAllocHandleStd** (allocation ENV/DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 L’application doit traiter les enregistrements de diagnostic dans la boucle récurrente de la fonction d’origine. Si SQLGetDiagField ou SQLGetDiagRec est appelée lors de l’exécution d’une fonction asynchrone, elle retournera la liste actuelle des enregistrements de diagnostic. Chaque fois que l’appel de fonction d’origine est répété, il efface les enregistrements de diagnostic précédentes.  
  
 Si une connexion est ouvert ou fermé de façon asynchrone, l’opération est terminée lorsque l’application reçoit SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO dans l’appel de fonction d’origine.  
  
 Une nouvelle fonction a été ajoutée à ODBC 3.8, **SQLCancelHandle**. Cette fonction annule les fonctions de six connexion (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**, et **SQLSetConnectAttr**). Une application doit appeler **SQLGetFunctions** pour déterminer si le pilote prend en charge **SQLCancelHandle**. Comme avec **SQLCancel**si **SQLCancelHandle** retourne les cas de réussite, cela ne signifie pas l’opération a été annulée. Une application doit appeler la fonction d’origine pour déterminer si l’opération a été annulée. **SQLCancelHandle** vous permet d’annuler des opérations asynchrones sur les handles de connexion ou de descripteurs d’instruction. À l’aide de **SQLCancelHandle** pour annuler une opération sur une instruction handle est le même que si vous appelez **SQLCancel**.  
  
 Il n’est pas nécessaire prendre en charge les deux **SQLCancelHandle** et les opérations de connexion asynchrone en même temps. Un pilote peut prendre en charge les opérations de connexion asynchrone, mais pas **SQLCancelHandle**, ou vice versa.  
  
 Opérations de connexion asynchrone et **SQLCancelHandle** peut également être utilisé par ODBC 3.x et les applications ODBC 2.x avec un pilote d’ODBC 3.8 et un gestionnaire ODBC 3.8. Pour savoir comment activer une application plus ancienne à utiliser les nouvelles fonctionnalités dans la version plus récente ODBC, consultez [matrice de compatibilité](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Regroupement de connexions  
 Chaque fois que le regroupement de connexions est activé, les opérations asynchrones sont uniquement au minimum pris en charge pour l’établissement d’une connexion (avec **SQLConnect** et **SQLDriverConnect**) et de la fermeture d’une connexion avec **SQLDisconnect**. Mais une application doit toujours être en mesure de gérer la valeur de retour de SQL_STILL_EXECUTING **SQLConnect**, **SQLDriverConnect**, et **SQLDisconnect**.  
  
 Lorsque le regroupement de connexions est activé, **SQLEndTran** et **SQLSetConnectAttr** sont pris en charge pour les opérations asynchrones.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre comment utiliser **SQLSetConnectAttr** pour permettre une exécution asynchrone pour les fonctions liées à la connexion.  
  
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
 Cet exemple illustre les opérations de validation asynchrone. Opérations de restauration possible également de cette façon.  
  
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
 [Exécution d’instructions dans ODBC](../../../odbc/reference/develop-app/executing-statements-odbc.md)
