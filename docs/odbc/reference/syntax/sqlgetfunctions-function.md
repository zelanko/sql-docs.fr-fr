---
title: Fonction SQLGetFunctions (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetFunctions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLGetFunctions
helpviewer_keywords:
- SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15537b28ff2bae8a4fcd3e7be82426eb53aa83a8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285329"
---
# <a name="sqlgetfunctions-function"></a>Fonction SQLGetFunctions
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetFunctions** renvoie des renseignements sur la question de savoir si un conducteur prend en charge une fonction spécifique de l’ODBC. Cette fonction est mise en œuvre dans le Driver Manager; il peut également être mis en œuvre chez les conducteurs. Si un conducteur met en œuvre **SQLGetFunctions**, le Driver Manager appelle la fonction dans le conducteur. Sinon, il exécute la fonction elle-même.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
 *FonctionId*  
 [Entrée] Une valeur **#define** qui identifie la fonction d’intérêt de l’ODBC; **SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** est utilisé par une application ODBC 3 *.x* pour déterminer le soutien d’ODBC 3 *.x* et les fonctions antérieures. **SQL_API_ALL_FUNCTIONS** est utilisé par une application ODBC 2 *.x* pour déterminer le soutien de ODBC 2 *.x* et les fonctions antérieures.  
  
 Pour une liste de **valeurs #define** qui identifient les fonctions ODBC, voir les tableaux dans "Commentaires".  
  
 *SupportedPtr (en)*  
 [Sortie]  Si *FunctionId* identifie une seule fonction ODBC, *SupportedPtr* indique une seule valeur SQLUSMALLINT qui est SQL_TRUE si la fonction spécifiée est prise en charge par le conducteur, et SQL_FALSE si elle n’est pas prise en charge.  
  
 Si *FunctionId* est SQL_API_ODBC3_ALL_FUNCTIONS, *SupportedPtr* pointe vers un tableau SQLSMALLINT avec un certain nombre d’éléments égaux à SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. Ce tableau est traité par le Driver Manager comme un bitmap de 4 000 bits qui peut être utilisé pour déterminer si une fonction ODBC 3 *.x* ou antérieure est prise en charge. La macro SQL_FUNC_EXISTS est appelée pour déterminer le support de la fonction. (Voir "Commentaires.") Une application ODBC 3 *.x* peut appeler **SQLGetFunctions** avec SQL_API_ODBC3_ALL_FUNCTIONS contre un pilote ODBC 3 *.x* ou ODBC 2 *.x.*  
  
 Si *FunctionId* est SQL_API_ALL_FUNCTIONS, *SupportedPtr* indique une gamme SQLUSMALLINT de 100 éléments. Le tableau est indexé par **#define** valeurs utilisées par *FunctionId* pour identifier chaque fonction ODBC; certains éléments du tableau sont inutilisés et réservés à une utilisation future. Un élément est SQL_TRUE s’il identifie une fonction ODBC 2 *.x* ou antérieure soutenue par le conducteur. Il est SQL_FALSE s’il identifie une fonction ODBC non prise en charge par le conducteur ou n’identifie pas une fonction ODBC.  
  
 Les tableaux retournés dans l’indexation à base de zéro *- supportedPtr.*  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetFunctions** revient SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et une *poignée* de *ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLGetFunctions** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------|-----|-----------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLGetFunctions** a été appelé avant **SQLConnect**, **SQLBrowseConnect**, ou **SQLDriverConnect**.<br /><br /> (DM) **SQLBrowseConnect** a été appelé pour le *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant **que SQLBrowseConnect** ne revienne SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *ConnectionHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY095 HY095|Type de fonction hors de portée|(DM) Une valeur *FunctionId* invalide a été spécifiée.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
  
## <a name="comments"></a>Commentaires  
 **SQLGetFunctions** revient toujours que **SQLGetFunctions**, **SQLDataSources**, et **SQLDrivers** sont pris en charge. Il le fait parce que ces fonctions sont mises en œuvre dans le Gestionnaire de conducteur. Le Driver Manager cartographiera une fonction ANSI à la fonction Unicode correspondante si la fonction Unicode existe et cartographiera une fonction Unicode à la fonction ANSI correspondante si la fonction ANSI existe. Pour plus d’informations sur la façon dont les applications utilisent **SQLGetFunctions**, voir [Interface Conformance Levels](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 Ce qui suit est une liste de valeurs valides pour *FunctionId* pour les fonctions qui se conforment au niveau de conformité aux normes ISO 92 :  
  
|Valeur FunctionId|Valeur FunctionId|  
|----------|----------|  
|SQL_API_SQLALLOCHANDLE|SQL_API_SQLGETDESCFIELD|  
|SQL_API_SQLBINDCOL|SQL_API_SQLGETDESCREC|  
|SQL_API_SQLCANCEL|SQL_API_SQLGETDIAGFIELD|  
|SQL_API_SQLCLOSECURSOR|SQL_API_SQLGETDIAGREC|  
|SQL_API_SQLCOLATTRIBUTE|SQL_API_SQLGETENVATTR|  
|SQL_API_SQLCONNECT|SQL_API_SQLGETFUNCTIONS|  
|SQL_API_SQLCOPYDESC|SQL_API_SQLGETINFO|  
|SQL_API_SQLDATASOURCES|SQL_API_SQLGETSTMTATTR|  
|SQL_API_SQLDESCRIBECOL|SQL_API_SQLGETTYPEINFO|  
|SQL_API_SQLDISCONNECT|SQL_API_SQLNUMRESULTCOLS|  
|SQL_API_SQLDRIVERS|SQL_API_SQLPARAMDATA|  
|SQL_API_SQLENDTRAN|SQL_API_SQLPREPARE|  
|SQL_API_SQLEXECDIRECT|SQL_API_SQLPUTDATA|  
|SQL_API_SQLEXECUTE|SQL_API_SQLROWCOUNT|  
|SQL_API_SQLFETCH|SQL_API_SQLSETCONNECTATTR|  
|SQL_API_SQLFETCHSCROLL|SQL_API_SQLSETCURSORNAME|  
|SQL_API_SQLFREEHANDLE|SQL_API_SQLSETDESCFIELD|  
|SQL_API_SQLFREESTMT|SQL_API_SQLSETDESCREC|  
|SQL_API_SQLGETCONNECTATTR|SQL_API_SQLSETENVATTR|  
|SQL_API_SQLGETCURSORNAME|SQL_API_SQLSETSTMTATTR|  
|SQL_API_SQLGETDATA| |  
  
 Ce qui suit est une liste de valeurs valides pour *FunctionId* pour les fonctions conformes au niveau de conformité aux normes Open Group :  
  
|Valeur FunctionId|Valeur FunctionId|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 Ce qui suit est une liste de valeurs valides pour *FunctionId* pour les fonctions conformes au niveau de conformité aux normes ODBC.  
  
|Valeur FunctionId|Valeur FunctionId|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS[1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1] Lorsque vous travaillez avec un conducteur ODBC 2 *.x,* **SQLBulkOperations** sera retourné comme pris en charge que si les deux de ce qui suit sont vrais: l’ODBC 2 *.x* pilote prend en charge **SQLSetPos**, et le type d’information SQL_POS_OPERATIONS retourne le SQL_POS_ADD peu comme ensemble.  
  
 Ce qui suit est une liste de valeurs valides pour *FunctionId* pour les fonctions introduites dans ODBC 3.8 ou plus tard:  
  
|Valeur FunctionId|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle** sera retourné comme support seulement si le conducteur prend en charge à la fois **SQLCancel** et **SQLCancelHandle**. Si **SQLCancel** est pris en charge, mais **SQLCancelHandle** n’est pas, l’application peut toujours appeler **SQLCancelHandle** sur une poignée de déclaration, car il sera cartographié à **SQLCancel**.  
  
## <a name="sql_func_exists-macro"></a>SQL_FUNC_EXISTS Macro  
 Le SQL_FUNC_EXISTS *(SupportedPtr*, *FunctionID*) macro est utilisé pour déterminer le soutien de ODBC 3 *.x* ou des fonctions antérieures après **SQLGetFunctions** a été appelé avec un argument *FunctionId* de SQL_API_ODBC3_ALL_FUNCTIONS. La demande appelle SQL_FUNC_EXISTS avec *l’argument supportedPtr* fixé au *SupportPtr* passé dans *SQLGetFunctions*, et avec *l’argument FunctionID* réglé à la **#define** pour la fonction. SQL_FUNC_EXISTS renvoie SQL_TRUE si la fonction est prise en charge, et SQL_FALSE autrement.  
  
> [!NOTE]
>  Lorsque vous travaillez avec un pilote ODBC 2 *.x,* l’ODBC 3 *.x* Driver Manager sera de retour SQL_TRUE pour **SQLAllocHandle** et **SQLFreeHandle** parce que **SQLAllocHandle** est cartographié à **SQLAllocEnv**, **SQLAllocConnect**, ou **SQLAllocStmt**, et parce que **SQLFreeHandle** est cartographié à **SQLFreeEnv**, **SQLFreeConnect**, ou **SQLFreeStmt**. **SQLAllocHandle** ou **SQLFreeHandle** avec un argument *HandleType* de SQL_HANDLE_DESC n’est pas pris en charge, cependant, même si SQL_TRUE est retourné pour les fonctions, parce qu’il n’y a pas de fonction ODBC 2 *.x* à cartographier dans ce cas.  
  
## <a name="code-example"></a>Exemple de code  
 Les trois exemples suivants montrent comment une application utilise **SQLGetFunctions** pour déterminer si un conducteur prend en charge **SQLTables**, **SQLColumns**, et **SQLStatistics**. Si le conducteur ne prend pas en charge ces fonctions, l’application se déconnecte du conducteur. Le premier exemple appelle **SQLGetFunctions** une fois pour chaque fonction.  
  
```cpp  
SQLUSMALLINT TablesExists, ColumnsExists, StatisticsExists;  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
  
retcodeTables = SQLGetFunctions(hdbc, SQL_API_SQLTABLES, &TablesExists);  
retcodeColumns = SQLGetFunctions(hdbc, SQL_API_SQLCOLUMNS, &ColumnsExists);  
retcodeStatistics = SQLGetFunctions(hdbc, SQL_API_SQLSTATISTICS, &StatisticsExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (retcodeTables == SQL_SUCCESS && TablesExists == SQL_TRUE &&   
retcodeColumns == SQL_SUCCESS && ColumnsExists == SQL_TRUE &&   
retcodeStatistics == SQL_SUCCESS && StatisticsExists == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 Dans le deuxième exemple, une application ODBC 3.x appelle **SQLGetFunctions** et lui passe un tableau dans lequel **SQLGetFunctions** renvoie des informations sur toutes les fonctions ODBC 3.x et antérieures.  
  
```cpp  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[SQL_API_ODBC3_ALL_FUNCTIONS_SIZE];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ODBC3_ALL_FUNCTIONS, fExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (reccode == SQL_SUCCESS &&   
SQL_FUNC_EXISTS(fExists, SQL_API_SQLTABLES) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLCOLUMNS) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLSTATISTICS) == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 Le troisième exemple est une application ODBC 2.x appelle **SQLGetFunctions** et lui passe un tableau de 100 éléments dans **lesquels SQLGetFunctions** retourne des informations sur toutes les fonctions ODBC 2.x et antérieures.  
  
```cpp  
#define FUNCTIONS 100  
  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[FUNCTIONS];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ALL_FUNCTIONS, fExists);  
  
/* SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver. */  
if (retcode == SQL_SUCCESS &&   
fExists[SQL_API_SQLTABLES] == SQL_TRUE &&  
   fExists[SQL_API_SQLCOLUMNS] == SQL_TRUE &&  
   fExists[SQL_API_SQLSTATISTICS] == SQL_TRUE)   
{  
  
   /* Continue with application */  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Retour du paramètre d’un attribut de connexion|[Fonction SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Retour d’informations sur un conducteur ou une source de données|[Fonction SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Retour du paramètre d’un attribut de déclaration|[Fonction SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
