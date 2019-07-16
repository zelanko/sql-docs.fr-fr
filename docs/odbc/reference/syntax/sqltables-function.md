---
title: Fonction SQLTables | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTables
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTables
helpviewer_keywords:
- SQLTables function [ODBC]
ms.assetid: 60d5068a-7d7c-447c-acc6-f3f2cf73440c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e99dd2f5cf3186120297d7679f87e973d5164a57
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039531"
---
# <a name="sqltables-function"></a>Fonction SQLTables
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : Ouvrir le groupe  
  
 **Résumé**  
 **SQLTables** renvoie la liste des noms de table, de catalogue ou de schéma et les types de tables, stockées dans une source de données spécifique. Le pilote retourne les informations comme jeu de résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLTables(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      TableType,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction pour récupérer les résultats.  
  
 *CatalogName*  
 [Entrée] Nom du catalogue. Le *CatalogName* argument accepte les modèles de recherche si l’attribut d’environnement SQL_ODBC_VERSION SQL_OV_ODBC3 ; il n’accepte pas les modèles de recherche si SQL_OV_ODBC2 est défini. Si un pilote prend en charge les catalogues pour certaines tables, mais pas pour d’autres, telles que lorsqu’un pilote récupère les données à partir de différents SGBD, une chaîne vide (« ») indique les tables qui n’ont pas de catalogues.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *CatalogName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *CatalogName* est un argument de valeur de modèle ; il est traité littéralement, et sa casse est significatif. Pour plus d’informations, consultez [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur en caractères de **CatalogName*.  
  
 *SchemaName*  
 [Entrée] Modèle de recherche de chaîne pour les noms de schéma. Si un pilote prend en charge les schémas pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, une chaîne vide (« ») indique les tables qui n’ont pas de schémas.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *SchemaName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *SchemaName* est un argument de valeur de modèle ; il est traité littéralement, et sa casse est significatif.  
  
 *NameLength2*  
 [Entrée] Longueur en caractères de **SchemaName*.  
  
 *TableName*  
 [Entrée] Modèle de recherche de chaîne pour les noms de table.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *TableName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *TableName* est un argument de valeur de modèle ; il est traité littéralement, et sa casse est significatif.  
  
 *NameLength3*  
 [Entrée] Longueur en caractères de **TableName*.  
  
 *TableType*  
 [Entrée] Liste des types de tables pour faire correspondre.  
  
 Notez que l’attribut d’instruction SQL_ATTR_METADATA_ID n’a aucun effet lors de la *TableType* argument. *TableType* est un argument de liste de valeur, quel que soit le paramètre de SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 [Entrée] Longueur en caractères de **TableType*.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLTables** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLTables** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|24000|État de curseur non valide|Un curseur a été ouvert sur le *au paramètre StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avait été appelée. Cette erreur est retournée par le Gestionnaire de pilotes si **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_NO_DATA et est retourné par le pilote si **SQLFetch** ou **SQLFetchScroll** a retourné SQL_NO_DATA.<br /><br /> Un curseur a été ouvert sur le *au paramètre StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelée.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer de la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*. La fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY009|Utilisation non valide de pointeur null|L’attribut d’instruction SQL_ATTR_METADATA_ID a été défini avec SQL_TRUE, le *CatalogName* argument était un pointeur null et le SQL_CATALOG_NAME *InfoType* retourne les noms de catalogue est pris en charge.<br /><br /> (DM) l’attribut d’instruction SQL_ATTR_METADATA_ID a été défini avec SQL_TRUE et le *SchemaName* ou *TableName* argument était un pointeur null.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution quand SQLTables a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur d’un des arguments de longueur était inférieure à 0 mais pas égale à SQL_NTS.<br /><br /> La valeur d’un des arguments de longueur de nom a dépassé la valeur de longueur maximale pour le nom correspondant.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|Un catalogue a été spécifié, et le pilote ou une source de données ne prend pas en charge les catalogues.<br /><br /> Un schéma a été spécifié, et le pilote ou une source de données ne prend pas en charge les schémas.<br /><br /> Un modèle de recherche de chaîne a été spécifié pour le nom du catalogue, le schéma de table ou le nom de table, et la source de données ne prend pas en charge les modèles de recherche pour un ou plusieurs de ces arguments.<br /><br /> La combinaison des paramètres actuels des attributs d’instruction SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE n’était pas pris en charge par la pilote ou source de données.<br /><br /> L’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a été défini sur SQL_UB_VARIABLE, et l’attribut d’instruction SQL_ATTR_CURSOR_TYPE a été défini pour un type de curseur pour lequel le pilote ne prend pas en charge les signets.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant la source de données a retourné le jeu de résultat demandé. Le délai d’expiration est défini via **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLTables** répertorie toutes les tables dans la plage demandée. Un utilisateur peut ou ne peut pas avoir des privilèges SELECT à une de ces tables. Pour vérifier l’accessibilité, une application peut :  
  
-   Appelez **SQLGetInfo** et vérifiez le type d’information SQL_ACCESSIBLE_TABLES.  
  
-   Appelez **SQLTablePrivileges** pour vérifier les privilèges pour chaque table.  
  
 Sinon, l’application doit être en mesure de gérer une situation où l’utilisateur sélectionne une table pour laquelle **sélectionnez** privilèges ne sont pas accordées.  
  
 Le *SchemaName* et *TableName* arguments acceptent des modèles de recherche. Le *CatalogName* argument accepte les modèles de recherche si l’attribut d’environnement SQL_ODBC_VERSION SQL_OV_ODBC3 ; il n’accepte pas les modèles de recherche si SQL_OV_ODBC2 est défini. Si SQL_OV_ODBC3 est définie, un 3 de ODBC *.x* pilote nécessitera que les caractères génériques caractères dans le *CatalogName* argument échappement pour être considérées littéralement. Pour plus d’informations sur les modèles de recherche valides, consultez [Arguments de valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, consultez [fonctions de catalogue](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Pour prendre en charge l’énumération des catalogues, schémas et types de tables, la sémantique spéciale suivante est définie pour le *CatalogName*, *SchemaName*, *TableName*et  *TableType* arguments de **SQLTables**:  
  
-   Si *CatalogName* est SQL_ALL_CATALOGS et *SchemaName* et *TableName* sont des chaînes vides, le jeu de résultats contient une liste des catalogues valides pour la source de données. (Toutes les colonnes à l’exception de la colonne TABLE_CAT contient les valeurs NULL.)  
  
-   Si *SchemaName* est SQL_ALL_SCHEMAS et *CatalogName* et *TableName* sont des chaînes vides, le jeu de résultats contient une liste de schémas valides pour la source de données. (Toutes les colonnes sauf la colonne TABLE_SCHEM contient de valeurs NULL.)  
  
-   Si *TableType* est SQL_ALL_TABLE_TYPES et *CatalogName*, *SchemaName*, et *TableName* sont des chaînes vides, le jeu de résultats contient une liste des types de table valide pour la source de données. (Toutes les colonnes sauf la colonne TABLE_TYPE contient de valeurs NULL.)  
  
 Si *TableType* n’est pas une chaîne vide, il doit contenir une liste de séparées par des virgules des valeurs pour les types d’intérêt ; chaque valeur peut être placé entre guillemets simples (') ou guillemets, par exemple, « TABLE », « VIEW » ou TABLE, afficher. Une application doit toujours spécifier le type de table en majuscules. le pilote doit convertir le type de table à la casse est requis par la source de données. Si la source de données ne prend pas en charge un type de table spécifié **SQLTables** ne retourne pas de résultats pour ce type.  
  
 **SQLTables** retourne les résultats sous la forme d’un jeu de résultats standard, classé par TABLE_TYPE, TABLE_CAT, TABLE_SCHEM et TABLE_NAME. Pour plus d’informations sur la façon dont ces informations peuvent être utilisées, consultez [utilise des données de catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Pour déterminer les longueurs réelles des colonnes TABLE_CAT, TABLE_SCHEM et TABLE_NAME, une application peut appeler **SQLGetInfo** avec les informations SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN et SQL_MAX_TABLE_NAME_LEN types.  
  
 Les colonnes suivantes ont été renommées pour ODBC 3 *.x*. Les modifications de nom de colonne n’affectent pas la compatibilité descendante, car les applications lier par numéro de colonne.  
  
|Colonne de ODBC 2.0|ODBC 3 *.x* colonne|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Le tableau suivant répertorie les colonnes du jeu de résultats. Les colonnes supplémentaires au-delà de la colonne 5 (Remarques) peuvent être définies par le pilote. Une application doit accéder à des colonnes spécifiques aux pilotes à rebours à partir de la fin de l’ensemble au lieu de spécifier une position ordinale explicite de résultats. Pour plus d’informations, consultez [les données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de la colonne|Numéro de colonne|Type de données|Commentaires|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Nom de catalogue ; NULL si non applicable à la source de données. Si un pilote prend en charge les catalogues pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, elle retourne une chaîne vide (" ») pour les tables qui n’ont pas de catalogues.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Nom du schéma ; NULL si non applicable à la source de données. Si un pilote prend en charge les schémas pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, elle retourne une chaîne vide (" ») pour les tables qui n’ont pas de schémas.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar|Nom de la table.|  
|TABLE_TYPE (ODBC 1.0)|4|Varchar|Nom du type de table ; les valeurs suivantes : « TABLE », « Vue », « TABLE système », « GLOBAL temporaire », « Temporaire LOCAL », « ALIAS », « SYNONYME » ou un nom de type spécifique à la source de données.<br /><br /> La signification de « ALIAS » et « SYNONYME » est spécifiques au pilote.|  
|REMARQUES (ODBC 1.0)|5\.|Varchar|Une description de la table.|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant ne libère pas les connexions et descripteurs. Consultez [SQLFreeHandle, fonction](../../../odbc/reference/syntax/sqlfreehandle-function.md) et [SQLFreeStmt, fonction](../../../odbc/reference/syntax/sqlfreestmt-function.md) pour obtenir des exemples de code libérer les handles et des instructions.  
  
```cpp  
// SQLTables.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
// simple helper functions  
int MySQLSuccess(SQLRETURN rc) {  
   return (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO);  
}  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printCatalog(const struct DataBinding* catalogResult) {  
   if (catalogResult[0].StrLen_or_Ind != SQL_NULL_DATA)   
      printf("Catalog Name = %s\n", (char *)catalogResult[0].TargetValuePtr);  
}  
  
// remember to disconnect and free memory, and free statements and handles  
int main() {  
   int bufferSize = 1024, i, numCols = 5;  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   wchar_t* dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   wchar_t* userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR*)"Driver={SQL Server}", SQL_NTS, (SQLCHAR*)connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
  
   bufferSize = 1024;  
  
   // allocate memory for the binding  
   // free this memory when done  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // setup the binding (can be used even if the statement is closed by closeStatementHandle)  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   // all catalogs query  
   printf( "A list of names of all catalogs\n" );  
   retCode = SQLTables( hstmt, (SQLCHAR*)SQL_ALL_CATALOGS, SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS );  
   for ( retCode = SQLFetch(hstmt) ;  MySQLSuccess(retCode) ; retCode = SQLFetch(hstmt) )  
      printCatalog( catalogResult );  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à une colonne dans un jeu de résultats|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Retour des privilèges pour une ou plusieurs colonnes|[SQLColumnPrivileges, fonction](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Retourner les colonnes dans une table ou des tables|[SQLColumns, fonction](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|L’extraction d’une seule ligne ou un bloc de données dans une direction avant uniquement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll, fonction](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Retourner l’index et les statistiques de table|[SQLStatistics, fonction](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Retour de privilèges pour une table ou de tables|[SQLTablePrivileges, fonction](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
