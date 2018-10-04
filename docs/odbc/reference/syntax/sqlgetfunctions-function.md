---
title: SQLGetFunctions, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetFunctions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetFunctions
helpviewer_keywords:
- SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98fb29265c17970fbcef0f21778d7a9130e52771
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644517"
---
# <a name="sqlgetfunctions-function"></a>Fonction SQLGetFunctions
**Conformité**  
 Version introduite : La mise en conformité des normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLGetFunctions** retourne les informations si un pilote prend en charge une fonction ODBC spécifique. Cette fonction est implémentée dans le Gestionnaire de pilotes ; elle peut également être implémentée dans les pilotes. Si un pilote implémente **SQLGetFunctions**, le Gestionnaire de pilotes appelle la fonction dans le pilote. Sinon, il exécute la fonction elle-même.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *Handle de connexion*  
 [Entrée] Handle de connexion.  
  
 *FunctionId*  
 [Entrée] Un **#define** valeur qui identifie la fonction ODBC d’intérêt ; **SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** est utilisé par un ODBC 3 *.x* application afin de déterminer la prise en charge d’ODBC 3 *.x* et fonctions antérieures. **SQL_API_ALL_FUNCTIONS** est utilisé par un 2 ODBC *.x* application afin de déterminer la prise en charge d’ODBC 2 *.x* et fonctions antérieures.  
  
 Pour obtenir la liste de **#define** valeurs qui identifient les fonctions ODBC, consultez les tableaux dans « Commentaires ».  
  
 *SupportedPtr*  
 [Sortie]  Si *FunctionId* identifie une seule fonction ODBC, *SupportedPtr* pointe vers un seul SQLUSMALLINT valeur SQL_TRUE si la fonction spécifiée est prise en charge par le pilote et SQL_FALSE si elle n’est pas prise en charge.  
  
 Si *FunctionId* est SQL_API_ODBC3_ALL_FUNCTIONS, *SupportedPtr* pointe vers un tableau SQLSMALLINT avec un nombre d’éléments égales à SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. Ce tableau est traité par le Gestionnaire de pilotes sous forme de bitmap 4 000 bits qui peut être utilisé pour déterminer si un ODBC 3 *.x* ou fonction earlier est pris en charge. La macro SQL_FUNC_EXISTS est appelée pour déterminer la prise en charge de la fonction. (Voir « Commentaires ».) Un ODBC 3 *.x* application peut appeler **SQLGetFunctions** avec SQL_API_ODBC3_ALL_FUNCTIONS contre un 3 ODBC *.x* ou ODBC 2 *.x* pilote.  
  
 Si *FunctionId* est SQL_API_ALL_FUNCTIONS, *SupportedPtr* pointe vers un tableau SQLUSMALLINT de 100 éléments. Le tableau est indexé par **#define** valeurs utilisées par *FunctionId* pour identifier chaque fonction ODBC ; certains éléments du tableau sont inutilisées et réservée pour une utilisation ultérieure. Un élément est SQL_TRUE si elle identifie un ODBC 2 *.x* ou fonction earlier pris en charge par le pilote. Il est SQL_FALSE si elle identifie une fonction ODBC non pris en charge par le pilote ou n’identifie pas une fonction ODBC.  
  
 Les tableaux retournés dans **SupportedPtr* utiliser l’indexation de base zéro.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetFunctions** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et un *gérer* de *ConnectionHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLGetFunctions** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------|-----|-----------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLGetFunctions** a été appelé avant **SQLConnect**, **SQLBrowseConnect**, ou **SQLDriverConnect**.<br /><br /> (DM) **SQLBrowseConnect** a été appelé pour le *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant **SQLBrowseConnect** a retourné SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *ConnectionHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY095|Type de fonction hors limites|(DM) non valide *FunctionId* valeur a été spécifiée.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
  
## <a name="comments"></a>Commentaires  
 **SQLGetFunctions** qui retourne toujours **SQLGetFunctions**, **SQLDataSources**, et **SQLDrivers** sont pris en charge. Pour cela, car ces fonctions sont implémentées dans le Gestionnaire de pilotes. Si la fonction Unicode existe et qu’il mappera une fonction Unicode à la fonction ANSI correspondante si la fonction ANSI existe, le Gestionnaire de pilotes mappera une fonction ANSI à la fonction Unicode correspondante. Pour plus d’informations sur l’utilisation des applications **SQLGetFunctions**, consultez [les niveaux de conformité Interface](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 Voici une liste des valeurs valides pour *FunctionId* pour les fonctions qui sont conformes au niveau – la conformité aux normes ISO 92 :  
  
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
  
 Voici une liste des valeurs valides pour *FunctionId* pour les fonctions conforme au niveau de la conformité aux normes – Open Group :  
  
|Valeur FunctionId|Valeur FunctionId|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 Voici une liste des valeurs valides pour *FunctionId* pour les fonctions conforme au niveau de la conformité aux normes – ODBC.  
  
|Valeur FunctionId|Valeur FunctionId|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS [1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1] lorsque vous travaillez avec un ODBC 2 *.x* pilote, **SQLBulkOperations** s’affichera comme pris en charge uniquement si les deux des options suivantes sont vraies : ODBC 2 *.x* pilote prend en charge  **SQLSetPos**, et le type d’information SQL_POS_OPERATIONS retourne le bit SQL_POS_ADD en tant que jeu.  
  
 Voici une liste des valeurs valides pour *FunctionId* pour les fonctions introduites dans ODBC 3.8 ou version ultérieure :  
  
|Valeur FunctionId|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle** s’affichera comme pris en charge uniquement si le pilote prend en charge les deux **SQLCancel** et **SQLCancelHandle**. Si **SQLCancel** est pris en charge mais **SQLCancelHandle** n’est pas le cas, l’application peut toujours appeler **SQLCancelHandle** sur un descripteur d’instruction, car il sera mappé à  **SQLCancel**.  
  
## <a name="sqlfuncexists-macro"></a>SQL_FUNC_EXISTS Macro  
 Le SQL_FUNC_EXISTS (*SupportedPtr*, *FunctionID*) macro est utilisée pour déterminer la prise en charge d’ODBC 3 *.x* ou fonctions antérieures après **SQLGetFunctions**  a été appelé avec un *FunctionId* argument de SQL_API_ODBC3_ALL_FUNCTIONS. L’application appelle SQL_FUNC_EXISTS avec la *SupportedPtr* affectée à l’argument le *SupportedPtr* transmis *SQLGetFunctions*et avec le  *FunctionID* affectée à l’argument le **#define** pour la fonction. SQL_FUNC_EXISTS retourne SQL_TRUE si la fonction est prise en charge et SQL_FALSE dans le cas contraire.  
  
> [!NOTE]  
>  Lorsque vous travaillez avec un ODBC 2 *.x* pilote, le 3 ODBC *.x* Gestionnaire de pilotes retourne SQL_TRUE pour **SQLAllocHandle** et **SQLFreeHandle**car **SQLAllocHandle** est mappé à **SQLAllocEnv**, **SQLAllocConnect**, ou **SQLAllocStmt**, et Étant donné que **SQLFreeHandle** est mappé à **SQLFreeEnv**, **SQLFreeConnect**, ou **SQLFreeStmt**. **SQLAllocHandle** ou **SQLFreeHandle** avec un *HandleType* argument de SQL_HANDLE_DESC n'est pas pris en charge, toutefois, même si SQL_TRUE est retourné pour les fonctions, car il n’est pas ODBC 2 *.x* fonction permettant de mapper vers dans ce cas.  
  
## <a name="code-example"></a>Exemple de code  
 Les trois exemples suivants montrent comment une application utilise **SQLGetFunctions** pour déterminer si un pilote prend en charge **SQLTables**, **SQLColumns**, et  **SQLStatistics**. Si le pilote ne prend pas en charge ces fonctions, l’application déconnecte le pilote. Le premier exemple appelle **SQLGetFunctions** une fois pour chaque fonction.  
  
```  
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
  
 Dans le deuxième exemple, une application de 3.x ODBC appelle **SQLGetFunctions** et transmet un tableau dans lequel **SQLGetFunctions** retourne des informations sur tous les ODBC 3.x et les fonctions antérieures.  
  
```  
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
  
 Le troisième exemple est une application ODBC 2.x appelle **SQLGetFunctions** et il passe un tableau de 100 éléments dans lequel **SQLGetFunctions** retourne des informations sur tous les ODBC 2.x et fonctions antérieures.  
  
```  
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
|Retourner le paramètre d’un attribut de connexion|[SQLGetConnectAttr, fonction](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Retour d’informations sur un pilote ou d’une source de données|[SQLGetInfo, fonction](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Retourner le paramètre d’un attribut d’instruction|[SQLGetStmtAttr, fonction](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
