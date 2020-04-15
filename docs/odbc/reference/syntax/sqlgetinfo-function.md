---
title: Fonction SQLGetInfo (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInfo
helpviewer_keywords:
- SQLGetInfo function [ODBC]
ms.assetid: 49dceccc-d816-4ada-808c-4c6138dccb64
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 514922fd085cfd2ba19eb5c07dd844db82d55202
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303341"
---
# <a name="sqlgetinfo-function"></a>Fonction SQLGetInfo
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetInfo** renvoie des informations générales sur le conducteur et la source de données associées à une connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetInfo(  
     SQLHDBC         ConnectionHandle,  
     SQLUSMALLINT    InfoType,  
     SQLPOINTER      InfoValuePtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
 *InfoType InfoType*  
 [Entrée] Type d’information.  
  
 *InfoValuePtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner l’information. Selon *infoType* demandée, l’information retournée sera l’une des suivantes : une chaîne de caractères non terminée, une valeur SQLUSMALLINT, un bitmask SQLUINTEGER, un drapeau SQLUINTEGER, une valeur binaire SQLUINTEGER ou une valeur SQLULEN.  
  
 Si l’argument *d’InfoType* est SQL_DRIVER_HDESC ou SQL_DRIVER_HSTMT, l’argument *d’InfoValuePtr* est à la fois l’entrée et la sortie. (Voir les SQL_DRIVER_HDESC ou SQL_DRIVER_HSTMT descripteurs plus tard dans cette description de fonction pour plus d’informations.)  
  
 Si *InfoValuePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (à l’exclusion du caractère de non-termination pour les données de caractère) disponible pour revenir dans le tampon indiqué par *InfoValuePtr*.  
  
 *BufferLength*  
 [Entrée] Longueur du \*tampon *InfoValuePtr.* Si la valeur * \*d’InfoValuePtr* n’est pas une chaîne de caractères ou si *InfoValuePtr* est un pointeur nul, l’argument *de BufferLength* est ignoré. Le conducteur suppose que la taille * \*d’InfoValuePtr* est SQLUSMALLINT ou SQLUINTEGER, d’après *l’InfoType*. Si * \*InfoValuePtr* est une chaîne Unicode (lorsqu’il appelle **SQLGetInfoW**), l’argument *BufferLength* doit être un nombre pair; sinon, SQLSTATE HY090 (longueur de ficelle ou tampon invalide) est retournée.  
  
 *StringLengthPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total d’octets (à l’exclusion du caractère de non-termination pour les données de caractère) disponible pour revenir dans *'InfoValuePtr*.  
  
 Pour les données de caractère, si le nombre d’octets disponibles pour \*revenir est supérieur ou égal à *BufferLength*, les informations dans *InfoValuePtr* sont tronquées aux octets *BufferLength* moins la longueur d’un caractère de non-termination et est annulée par le conducteur.  
  
 Pour tous les autres types de données, la valeur de *BufferLength* est ignorée et le conducteur suppose que la taille \* *d’InfoValuePtr* est SQLUSMALLINT ou SQLUINTEGER, selon *infoType*.  
  
## <a name="return-value"></a>Valeur de retour  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetInfo** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et une *poignée* de *ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLGetInfo** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \*tampon *InfoValuePtr* n’était pas assez grand pour retourner toutes les informations demandées. Par conséquent, l’information a été tronquée. La longueur des informations demandées sous sa forme fausse est retournée dans*le stringLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) Le type d’information demandée dans *InfoType* nécessite une connexion ouverte. Parmi les types d’information réservés par ODBC, seuls SQL_ODBC_VER peuvent être retournés sans connexion ouverte.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY024|Valeur d’attribut invalide|(DM) *L’argument d’InfoType* était SQL_DRIVER_HSTMT, et la valeur soulignée par *InfoValuePtr* n’était pas une poignée de déclaration valide.<br /><br /> (DM) *L’argument d’InfoType* était SQL_DRIVER_HDESC, et la valeur soulignée par *InfoValuePtr* n’était pas une poignée valide descripteur.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.<br /><br /> (DM) La valeur spécifiée pour *BufferLength* était un nombre impair, et * \*InfoValuePtr* était d’un type de données Unicode.|  
|HY096 HY096|Type d’information hors de portée|La valeur spécifiée pour l’argument *InfoType* n’était pas valable pour la version d’ODBC prise en charge par le conducteur.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Champ optionnel non mis en œuvre|La valeur spécifiée pour l’argument *InfoType* était une valeur spécifique au conducteur qui n’est pas prise en charge par le conducteur.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur qui correspond à la *ConnectionHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Les types d’information actuellement définis sont indiqués dans les « types d’information », plus tard dans cette section; on s’attend à ce que d’autres sources de données soient définies pour tirer parti de différentes sources de données. Une gamme de types d’informations est réservée par ODBC; les développeurs de pilotes doivent réserver des valeurs pour leur propre utilisation spécifique au conducteur de Open Group. **SQLGetInfo** n’effectue aucune conversion Unicode ou *thunking* (voir [Annexe A: ODBC Error Codes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) of the *ODBC Programmer’s Reference*) pour *InfoTypes*défini par le conducteur . Pour plus d’informations, consultez [les types de données spécifiques au conducteur, les types descripteurs, les types d’information, les types de diagnostic et les attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Le format des informations \*retournées dans *InfoValuePtr* dépend de *l’InfoType* demandée. **SQLGetInfo** retournera l’information dans l’un des cinq formats différents :  
  
-   Une chaîne de caractères non terminée  
  
-   Une valeur SQLUSMALLINT  
  
-   Un bitmask SQLUINTEGER  
  
-   Une valeur SQLUINTEGER  
  
-   Une valeur binaire SQLUINTEGER  
  
 Le format de chacun des types d’information suivants est noté dans la description du type. L’application doit jeter la valeur retournée dans*InfoValuePtr* en conséquence. Par exemple, comment une application pourrait récupérer des données à partir d’un bitmask SQLUINTEGER, voir « Exemple de code ».  
  
 Un conducteur doit retourner une valeur pour chaque type d’information qui est défini dans les tableaux suivants. Si un type d’information ne s’applique pas au conducteur ou à la source de données, le conducteur renvoie l’une des valeurs énumérées dans le tableau suivant.  
  
 Chaîne de caractères (« Y » ou « N »)  
 "N"  
  
 Chaîne de caractère (pas "Y" ou "N")  
 Chaîne vide  
  
 SQLUSMALLINT  
 0  
  
 SQLUINTEGER bitmask ou SQLUINTEGER valeur binaire  
 0L  
  
 Par exemple, si une source de données ne prend pas en charge les procédures, **SQLGetInfo** renvoie les valeurs énumérées dans le tableau suivant pour les valeurs *d’InfoType* qui sont liées aux procédures.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Chaîne vide  
  
 **SQLGetInfo** retourne SQLSTATE HY096 (valeur d’argument invalide) pour les valeurs *d’InfoType* qui sont dans la gamme de types d’information réservés à l’utilisation par ODBC, mais ne sont pas définies par la version de oDBC pris en charge par le conducteur. Pour déterminer quelle version d’ODBC un conducteur se conforme, une application appelle **SQLGetInfo** avec le type d’information SQL_DRIVER_ODBC_VER. **SQLGetInfo** retourne SQLSTATE HYC00 (fonction facultative non mise en œuvre) pour les valeurs *d’InfoType* qui sont dans la gamme de types d’information réservés à une utilisation spécifique au conducteur, mais ne sont pas pris en charge par le conducteur.  
  
 Tous les appels vers **SQLGetInfo** nécessitent une connexion ouverte, sauf lorsque *l’InfoType* est SQL_ODBC_VER, qui renvoie la version du Driver Manager.  
  
## <a name="information-types"></a>Types d’information  
 Cette section répertorie les types d’information pris en charge par **SQLGetInfo**. Les types d’information sont regroupés catégoriquement et classés par ordre alphabétique. Les types d’information qui ont été ajoutés ou renommés pour ODBC 3 *.x* sont également répertoriés.  
  
## <a name="driver-information"></a>Informations sur le conducteur  
 Les valeurs suivantes de l’argument *InfoType* renvoient des informations sur le pilote ODBC, telles que le nombre d’instructions actives, le nom de source de données et le niveau de conformité des normes d’interface :  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_FILE_USAGE|  
|SQL_ASYNC_MODE|SQL_GETDATA_EXTENSIONS|  
|SQL_ASYNC_NOTIFICATION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_BATCH_ROW_COUNT|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_BATCH_SUPPORT|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_DATA_SOURCE_NAME|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_DRIVER_AWARE_POOLING_SUPPORTED|SQL_MAX_CONCURRENT_ACTIVITIES|  
|SQL_DRIVER_HDBC|SQL_MAX_DRIVER_CONNECTIONS|  
|SQL_DRIVER_HDESC|SQL_ODBC_INTERFACE_CONFORMANCE|  
|SQL_DRIVER_HENV|SQL_ODBC_STANDARD_CLI_CONFORMANCE|  
|SQL_DRIVER_HLIB|SQL_ODBC_VER|  
|SQL_DRIVER_HSTMT|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_DRIVER_NAME|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DRIVER_ODBC_VER|SQL_ROW_UPDATES|  
|SQL_DRIVER_VER|SQL_SEARCH_PATTERN_ESCAPE|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|SQL_SERVER_NAME|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_STATIC_CURSOR_ATTRIBUTES2|  
  
> [!NOTE]  
>  Lors de la mise en œuvre **de SQLGetInfo**, un pilote peut améliorer les performances en minimisant le nombre de fois que les informations sont envoyées ou demandées sur le serveur.  
  
## <a name="dbms-product-information"></a>Informations sur les produits DBMS  
 Les valeurs suivantes de l’argument *InfoType* renvoient des informations sur le produit DBMS, telles que le nom et la version DBMS :  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Informations sur la source de données  
 Les valeurs suivantes de l’argument *InfoType* renvoient des informations sur la source de données, telles que les caractéristiques du curseur et les capacités de transaction :  
  
|||  
|-|-|  
|SQL_ACCESSIBLE_PROCEDURES|SQL_MULT_RESULT_SETS|  
|SQL_ACCESSIBLE_TABLES|SQL_MULTIPLE_ACTIVE_TXN|  
|SQL_BOOKMARK_PERSISTENCE|SQL_NEED_LONG_DATA_LEN|  
|SQL_CATALOG_TERM|SQL_NULL_COLLATION|  
|SQL_COLLATION_SEQ|SQL_PROCEDURE_TERM|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_SCHEMA_TERM|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_SCROLL_OPTIONS|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_TABLE_TERM|  
|SQL_CURSOR_SENSITIVITY|SQL_TXN_CAPABLE|  
|SQL_DATA_SOURCE_READ_ONLY|SQL_TXN_ISOLATION_OPTION|  
|SQL_DEFAULT_TXN_ISOLATION|SQL_USER_NAME|  
|SQL_DESCRIBE_PARAMETER||  
  
## <a name="supported-sql"></a>SQL soutenu  
 Les valeurs suivantes de l’argument *d’InfoType* renvoient des informations sur les déclarations SQL étayées par la source de données. La syntaxe SQL de chaque entité décrite par ces types d’information est la syntaxe SQL-92. Ces types d’information ne décrivent pas de façon exhaustive l’ensemble de la grammaire SQL-92. Au lieu de cela, ils décrivent les parties de la grammaire pour lesquelles les sources de données offrent généralement différents niveaux de soutien. Plus précisément, la plupart des déclarations DDL dans SQL-92 sont couvertes.  
  
 Les demandes devraient déterminer le niveau général de grammaire supportée à partir du type d’information SQL_SQL_CONFORMANCE et utiliser les autres types d’information pour déterminer les variations par rapport au niveau de conformité des normes énoncés.  
  
|||  
|-|-|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DROP_TABLE|  
|SQL_ALTER_DOMAIN|SQL_DROP_TRANSLATION|  
|SQL_ALTER_SCHEMA|SQL_DROP_VIEW|  
|SQL_ALTER_TABLE|SQL_EXPRESSIONS_IN_ORDERBY|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_GROUP_BY|  
|SQL_CATALOG_LOCATION|SQL_IDENTIFIER_CASE|  
|SQL_CATALOG_NAME|SQL_IDENTIFIER_QUOTE_CHAR|  
|SQL_CATALOG_NAME_SEPARATOR|SQL_INDEX_KEYWORDS|  
|SQL_CATALOG_USAGE|SQL_INSERT_STATEMENT|  
|SQL_COLUMN_ALIAS|SQL_INTEGRITY|  
|SQL_CORRELATION_NAME|SQL_KEYWORDS|  
|SQL_CREATE_ASSERTION|SQL_LIKE_ESCAPE_CLAUSE|  
|SQL_CREATE_CHARACTER_SET|SQL_NON_NULLABLE_COLUMNS|  
|SQL_CREATE_COLLATION|SQL_SQL_CONFORMANCE|  
|SQL_CREATE_DOMAIN|SQL_OJ_CAPABILITIES|  
|SQL_CREATE_SCHEMA|SQL_ORDER_BY_COLUMNS_IN_SELECT|  
|SQL_CREATE_TABLE|SQL_OUTER_JOINS|  
|SQL_CREATE_TRANSLATION|SQL_PROCEDURES|  
|SQL_DDL_INDEX|SQL_QUOTED_IDENTIFIER_CASE|  
|SQL_DROP_ASSERTION|SQL_SCHEMA_USAGE|  
|SQL_DROP_CHARACTER_SET|SQL_SPECIAL_CHARACTERS|  
|SQL_DROP_COLLATION|SQL_SUBQUERIES|  
|SQL_DROP_DOMAIN|SQL_UNION|  
|SQL_DROP_SCHEMA||  
  
## <a name="sql-limits"></a>Limites SQL  
 Les valeurs suivantes de l’argument *InfoType* renvoient des informations sur les limites appliquées aux identifiants et aux clauses dans les déclarations SQL, telles que les longueurs maximales des identifiants et le nombre maximum de colonnes dans une liste sélectionnée. Les limitations peuvent être imposées par le conducteur ou la source de données.  
  
|||  
|-|-|  
|SQL_MAX_BINARY_LITERAL_LEN|SQL_MAX_IDENTIFIER_LEN|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAX_INDEX_SIZE|  
|SQL_MAX_CHAR_LITERAL_LEN|SQL_MAX_PROCEDURE_NAME_LEN|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAX_ROW_SIZE|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAX_ROW_SIZE_INCLUDES_LONG|  
|SQL_MAX_COLUMNS_IN_INDEX|SQL_MAX_SCHEMA_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAX_STATEMENT_LEN|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAX_TABLE_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAX_TABLES_IN_SELECT|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAX_USER_NAME_LEN|  
  
## <a name="scalar-function-information"></a>Informations sur la fonction Scalar  
 Les valeurs suivantes de l’argument *InfoType* renvoient des informations sur les fonctions scalaires prises en charge par la source de données et le conducteur. Pour plus d’informations sur les fonctions scalaires, voir [Annexe E: Scalar Functions](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Informations de conversion  
 Les valeurs suivantes de l’argument *InfoType* renvoient une liste des types de données SQL auxquels la source de données peut convertir le type de données SQL spécifié avec la fonction scalaire **CONVERT** :  
  
|||  
|-|-|  
|SQL_CONVERT_BIGINT|SQL_CONVERT_LONGVARBINARY|  
|SQL_CONVERT_BINARY|SQL_CONVERT_LONGVARCHAR|  
|SQL_CONVERT_BIT|SQL_CONVERT_NUMERIC|  
|SQL_CONVERT_CHAR|SQL_CONVERT_REAL|  
|SQL_CONVERT_DATE|SQL_CONVERT_SMALLINT|  
|SQL_CONVERT_DECIMAL|SQL_CONVERT_TIME|  
|SQL_CONVERT_DOUBLE|SQL_CONVERT_TIMESTAMP|  
|SQL_CONVERT_FLOAT|SQL_CONVERT_TINYINT|  
|SQL_CONVERT_INTEGER|SQL_CONVERT_VARBINARY|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_CONVERT_VARCHAR|  
|SQL_CONVERT_INTERVAL_DAY_TIME||  
  
## <a name="information-types-added-for-odbc-3x"></a>Types d’informations ajoutés pour ODBC 3.x  
 Les valeurs suivantes de l’argument *InfoType* ont été ajoutées pour ODBC 3 *.x*:  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_DRIVER_AWARE_POOLING_SUPPORTED|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DRIVER_HDESC|  
|SQL_ALTER_DOMAIN|SQL_DROP_ASSERTION|  
|SQL_ALTER_SCHEMA|SQL_DROP_CHARACTER_SET|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_DROP_COLLATION|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_DROP_DOMAIN|  
|SQL_ASYNC_MODE|SQL_DROP_SCHEMA|  
|SQL_ASYNC_NOTIFICATION|SQL_DROP_TABLE|  
|SQL_BATCH_ROW_COUNT|SQL_DROP_TRANSLATION|  
|SQL_BATCH_SUPPORT|SQL_DROP_VIEW|  
|SQL_CATALOG_NAME|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|  
|SQL_COLLATION_SEQ|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|  
|SQL_CONVERT_INTERVAL_DAY_TIME|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_ASSERTION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_CREATE_CHARACTER_SET|SQL_INSERT_STATEMENT|  
|SQL_CREATE_COLLATION|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_CREATE_DOMAIN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_SCHEMA|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_CREATE_TABLE|SQL_MAX_IDENTIFIER_LEN|  
|SQL_CREATE_TRANSLATION|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_CURSOR_SENSITIVITY|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DDL_INDEX|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_DESCRIBE_PARAMETER|SQL_STATIC_CURSOR_ATTRIBUTES2|  
|SQL_DM_VER|SQL_XOPEN_CLI_YEAR|  
  
## <a name="information-types-renamed-for-odbc-3x"></a>Types d’information renommés pour ODBC 3.x  
 Les valeurs suivantes de l’argument *InfoType* ont été rebaptisées pour ODBC 3 *.x*.  
  
 SQL_ACTIVE_CONNECTIONS  
 SQL_MAX_DRIVER_CONNECTIONS  
  
 SQL_ACTIVE_STATEMENTS  
 SQL_MAX_CONCURRENT_ACTIVITIES  
  
 SQL_MAX_OWNER_NAME_LEN  
 SQL_MAX_SCHEMA_NAME_LEN  
  
 SQL_MAX_QUALIFIER_NAME_LEN  
 SQL_MAX_CATALOG_NAME_LEN  
  
 SQL_ODBC_SQL_OPT_IEF  
 SQL_INTEGRITY  
  
 SQL_OWNER_TERM  
 SQL_SCHEMA_TERM  
  
 SQL_OWNER_USAGE  
 SQL_SCHEMA_USAGE  
  
 SQL_QUALIFIER_LOCATION  
 SQL_CATALOG_LOCATION  
  
 SQL_QUALIFIER_NAME_SEPARATOR  
 SQL_CATALOG_NAME_SEPARATOR  
  
 SQL_QUALIFIER_TERM  
 SQL_CATALOG_TERM  
  
 SQL_QUALIFIER_USAGE  
 SQL_CATALOG_USAGE  
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Types d’information dépréciés dans ODBC 3.x  
 Les valeurs suivantes de l’argument *InfoType* ont été dépréciées dans ODBC 3 *.x*. Les conducteurs D’ODBC 3 *.x* doivent continuer à prendre en charge ces types d’informations pour la compatibilité vers l’arrière avec les applications ODBC 2 *.x.* (Pour plus d’informations sur ces types, voir [SQLGetInfo Support](../../../odbc/reference/appendixes/sqlgetinfo-support.md) in Annexe G: Driver Guidelines for Backward Compatibility.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Descriptions de type d’information  
 Le tableau suivant répertorie par ordre alphabétique chaque type d’information, la version de l’ODBC dans laquelle il a été introduit, et sa description.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 Une chaîne de caractères: "Y" si l’utilisateur peut exécuter toutes les procédures retournées par **SQLProcedures**; "N" s’il peut y avoir des procédures retournées que l’utilisateur ne peut pas exécuter.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Une chaîne de caractères : « Y » si l’utilisateur est garanti **privilèges SELECT** à toutes les tables retournées par **SQLTables**; "N" s’il peut y avoir des tables retournées que l’utilisateur ne peut pas accéder.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal d’environnements actifs que le conducteur peut supporter. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant le support pour les fonctions d’agrégation :  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Un conducteur SQL-92 d’entrée conforme retournera toujours toutes ces options en cas de support.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **ALTER DOMAIN,** tel que défini dans SQL-92, étayé par la source de données. Un pilote SQL-92 Entièrement conforme au niveau retournera toujours tous les bitmasks. Une valeur de retour de « 0 » signifie que la déclaration **ALTER DOMAIN** n’est pas prise en charge.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT - L’ajout d’une contrainte de domaine est pris en charge (niveau complet)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT - \<modifier la clause de \<défaut de domaine> définie> est prise en charge (niveau complet)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION clause de \<définition de nom de contrainte> est pris en charge pour la contrainte de nommage de domaine (niveau intermédiaire)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT clause de \<contrainte de domaine de chute> est pris en charge (niveau complet)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT - \<modifier la clause \<de défaut de domaine> de laisser tomber> est pris en charge (niveau complet)  
  
 Les bits suivants \<spécifient les \<attributs de contrainte pris en charge> si ajouter la contrainte de domaine> est pris en charge (le bit SQL_AD_ADD_DOMAIN_CONSTRAINT est réglé):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **ALTER TABLE** appuyée par la source de données.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_AT_ADD_COLUMN_COLLATION - \<ajouter la clause de> de colonne est prise en charge, avec la facilité de spécifier la collation de colonne (niveau complet) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT - \<ajouter la clause de> de colonne est prise en charge, avec la possibilité de spécifier les défauts de colonne (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE - \<ajouter la colonne> est pris en charge (niveau de transition FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT - \<ajouter la clause de> de colonne est prise en charge, avec la facilité de spécifier les contraintes de colonne (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT - \<ajouter la clause de contrainte de table> est soutenue (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION définition de \<nom de contrainte> est pris en charge pour nommer les contraintes de colonne et de table (niveau intermédiaire) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE - \<colonne de baisse> CASCADE est pris en charge (niveau de transition FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT - \<modifier la colonne \<> la clause par défaut de colonne de baisse> est pris en charge (niveau intermédiaire) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT - \<colonne de baisse> RESTRICT est pris en charge (niveau de transition FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT - \<colonne de baisse> RESTRICT est pris en charge (niveau de transition FIPS) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT - \<modifier la colonne \<> la clause par défaut de colonne définie> est prise en charge (niveau intermédiaire) (ODBC 3.0)  
  
 Les bits suivants \<spécifient les attributs de contrainte de support> si la spécification des contraintes de colonne ou de table est prise en charge (le SQL_AT_ADD_CONSTRAINT bit est réglé) :  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) (ODBC 3.0)SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (niveau complet) (ODBC 3.0)SQL_AT_CONSTRAINT_NON_DEFERRABLE (niveau complet) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 Une valeur SQLUINTEGER qui indique si le conducteur peut exécuter des fonctions asynchrone sur la poignée de connexion.  
  
 SQL_ASYNC_DBC_CAPABLE le conducteur peut exécuter les fonctions de connexion asynchrone.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE - Le conducteur ne peut pas exécuter les fonctions de connexion asynchrone.  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le niveau de soutien asynchrone chez le conducteur :  
  
 SQL_AM_CONNECTION - L’exécution asynchrone de niveau de connexion est soutenue. Soit toutes les poignées de déclaration associées à une poignée de connexion donnée sont en mode asynchrone ou tous sont en mode synchrone. Une poignée de déclaration sur une connexion ne peut pas être en mode asynchrone tandis qu’une autre poignée de déclaration sur la même connexion est en mode synchrone, et vice versa.  
  
 SQL_AM_STATEMENT - L’exécution asynchrone de niveau d’instruction est soutenue. Certaines poignées de déclaration associées à une poignée de connexion peuvent être en mode asynchrone, tandis que d’autres poignées de déclaration sur la même connexion sont en mode synchrone.  
  
 SQL_AM_NONE - Mode Asynchrone n’est pas pris en charge.  
  
 SQL_ASYNC_NOTIFICATION  
 Une valeur SQLUINTEGER qui indique si le conducteur prend en charge la notification asynchrone :  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** La notification d’exécution asynchrone est prise en charge par le conducteur.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** La notification d’exécution asynchrone n’est pas prise en charge par le conducteur.  
  
 Il existe deux catégories d’opérations asynchrones de l’ODBC : les opérations asynchrones au niveau de connexion et les opérations asynchrones au niveau de déclaration.  Si un pilote retourne SQL_ASYNC_NOTIFICATION_CAPABLE, il doit prendre en charge la notification pour toutes les API qu’il peut exécuter asynchrone.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui énumère le comportement du conducteur par rapport à la disponibilité des dénombrements de rangées. Les bitmasks suivants sont utilisés avec le type d’information :  
  
 SQL_BRC_ROLLED_UP - Les comptes de ligne pour les relevés INSERT, DELETE ou UPDATE consécutifs sont regroupés en un seul. Si ce bit n’est pas réglé, les nombres de lignes sont disponibles pour chaque instruction.  
  
 SQL_BRC_PROCEDURES - Le nombre de rangées, le cas échéant, est disponible lorsqu’un lot est exécuté dans une procédure stockée. Si des nombres de rangées sont disponibles, ils peuvent être enroulés ou disponibles individuellement, selon le SQL_BRC_ROLLED_UP bit.  
  
 SQL_BRC_EXPLICIT - Le nombre de rangées, le cas échéant, est disponible lorsqu’un lot est exécuté directement en appelant **SQLExecute** ou **SQLExecDirect**. Si des nombres de rangées sont disponibles, ils peuvent être enroulés ou disponibles individuellement, selon le SQL_BRC_ROLLED_UP bit.  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant le soutien du conducteur pour les lots. Les bitmasks suivants sont utilisés pour déterminer quel niveau est pris en charge :  
  
 SQL_BS_SELECT_EXPLICIT - Le conducteur prend en charge les lots explicites qui peuvent avoir des instructions génératrices de résultats.  
  
 SQL_BS_ROW_COUNT_EXPLICIT - Le conducteur prend en charge les lots explicites qui peuvent avoir des déclarations génératrices de nombres de rangées.  
  
 SQL_BS_SELECT_PROC - Le conducteur prend en charge les procédures explicites qui peuvent avoir des instructions génératrices de résultats.  
  
 SQL_BS_ROW_COUNT_PROC - Le conducteur prend en charge les procédures explicites qui peuvent avoir des énoncés générateurs de nombres de rangées.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les opérations par lesquelles les signets persistent.  
  
 Les bitmasks suivants sont utilisés avec le drapeau pour déterminer quelles options les signets persistent :  
  
 SQL_BP_CLOSE - Les signets sont valides après qu’une demande a appelé **SQLFreeStmt** avec l’option SQL_CLOSE, ou **SQLCloseCursor** pour fermer le curseur associé à une déclaration.  
  
 SQL_BP_DELETE - Le signet d’une ligne est valide après que cette ligne a été supprimée.  
  
 SQL_BP_DROP - Les signets sont valides après qu’une demande appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT pour déposer une déclaration.  
  
 SQL_BP_TRANSACTION - Les signets sont valides après qu’une demande a commis ou réversé une transaction.  
  
 SQL_BP_UPDATE - Le signet d’une ligne est valide après que n’importe quelle colonne de cette rangée a été mise à jour, y compris les colonnes clés.  
  
 SQL_BP_OTHER_HSTMT un signet associé à une instruction peut être utilisé avec une autre déclaration. À moins que SQL_BP_CLOSE ou SQL_BP_DROP ne soit spécifié, le curseur de la première déclaration doit être ouvert.  
  
 SQL_CATALOG_LOCATION (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui indique la position du catalogue dans un nom de tableau qualifié :  
  
 SQL_CL_STARTSQL_CL_END  
  
 Par exemple, un pilote Xbase retourne SQL_CL_START parce que le nom de l’annuaire (catalogue) est au début du nom de table, comme dans 'EMPDATA’EMP. Dbf. Un pilote ORACLE Server retourne SQL_CL_END parce que le catalogue est à ADMIN.EMP@EMPDATAla fin du nom de la table, comme dans .  
  
 Un pilote SQL-92 De niveau complet sera toujours de retour SQL_CL_START. Une valeur de 0 est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_CATALOG_NAME.  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_QUALIFIER_LOCATION.  
  
 SQL_CATALOG_NAME (ODBC 3.0)  
 Une chaîne de caractères: "Y" si le serveur prend en charge les noms de catalogue, ou "N" si elle ne le fait pas.  
  
 Un pilote SQL-92 De niveau complet sera toujours de retour "Y".  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1.0)  
 Une chaîne de caractères : le personnage ou les caractères que la source de données définit comme séparateur entre un nom de catalogue et l’élément nom qualifié qui le suit ou le précède.  
  
 Une chaîne vide est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_CATALOG_NAME. Un pilote SQL-92 De niveau complet sera toujours de retour ".".  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_QUALIFIER_NAME_SEPARATOR.  
  
 SQL_CATALOG_TERM (ODBC 1.0)  
 Une chaîne de caractères avec le nom du fournisseur de source de données pour un catalogue; par exemple, "base de données" ou "annuaire". Cette chaîne peut être dans le cas supérieur, inférieur ou mixte.  
  
 Une chaîne vide est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_CATALOG_NAME. Un pilote SQL-92 Full level-conformant retournera toujours «catalogue».  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_QUALIFIER_TERM.  
  
 SQL_CATALOG_USAGE (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les déclarations dans lesquelles les catalogues peuvent être utilisés.  
  
 Les bitmasks suivants sont utilisés pour déterminer où les catalogues peuvent être utilisés :  
  
 SQL_CU_DML_STATEMENTS catalogues sont pris en charge dans toutes les déclarations de langage de manipulation de données : **SELECT**, **INSERT**, **UPDATE**, **DELETE**, et si pris en charge, **SELECT FOR UPDATE** et positionné mise à jour et supprimer les déclarations.  
  
 SQL_CU_PROCEDURE_INVOCATION - Les catalogues sont pris en charge dans l’énoncé d’invocation de la procédure ODBC.  
  
 SQL_CU_TABLE_DEFINITION - Les catalogues sont pris en charge dans toutes les déclarations de définition de tableau: **CREATE TABLE**, **CREATE VIEW**, ALTER **TABLE**, **DROP TABLE**, et DROP **VIEW**.  
  
 SQL_CU_INDEX_DEFINITION catalogues sont pris en charge dans tous les énoncés de définition d’index : **CREATE INDEX** et **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION - Les catalogues sont pris en charge dans toutes les déclarations de définition du privilège : **GRANT** et **REVOKE**.  
  
 Une valeur de 0 est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_CATALOG_NAME. Un pilote SQL-92 Full level-conformant retournera toujours un peu de masse avec tous ces bits ensemble.  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_QUALIFIER_USAGE.  
  
 SQL_COLLATION_SEQ (ODBC 3.0)  
 Le nom de la séquence de collation. Il s’agit d’une chaîne de caractères qui indique le nom de la collation par défaut pour le caractère par défaut défini pour ce serveur (par exemple, 'ISO 8859-1' ou EBCDIC). Si cela est inconnu, une corde vide sera retournée. Un conducteur SQL-92 Entièrement conforme au niveau retournera toujours une corde non vide.  
  
 SQL_COLUMN_ALIAS (ODBC 2.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge les alias de colonne ; sinon, "N".  
  
 Un alias de colonne est un nom alternatif qui peut être spécifié pour une colonne dans la liste sélectionnée en utilisant une clause AS. Un pilote SQL-92 d’entrée conforme à l’entrée retournera toujours « Y ».  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui indique comment la source de données gère la concatenation des colonnes de type de données de caractères évaluées PAR NULL avec des colonnes de type de données de caractère non valorisées NULL :  
  
 SQL_CB_NULL - Le résultat est VALORisé.  
  
 SQL_CB_NON_NULL - Le résultat est la concatenation de colonnes ou de colonnes non valorisées.  
  
 Un pilote SQL-92 d’entrée conforme à l’entrée sera toujours de retour SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 Un bitmask SQLUINTEGER. Le bitmask indique les conversions prises en charge par la source de données avec la fonction scalaire **CONVERT** pour les données du type nommé dans *l’InfoType*. Si le bitmask est égal à zéro, la source de données ne prend en charge aucune conversion à partir des données du type nommé, y compris la conversion au même type de données.  
  
 Par exemple, pour déterminer si une source de données prend en charge la conversion des données SQL_INTEGER au type de données SQL_BIGINT, une application appelle **SQLGetInfo** avec *l’InfoType* de SQL_CONVERT_INTEGER. L’application effectue une opération **ET** avec le bitmask retourné et SQL_CVT_BIGINT. Si la valeur résultante n’est pas zéro, la conversion est prise en charge.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles conversions sont prises en charge :  
  
 SQL_CVT_BIGINT (ODBC 1.0)SQL_CVT_BINARY (ODBC 1.0)SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5)SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0)SQL_CVT_DOUBLEBC (ODBC (ODBC 1.0) (ODBC 1.0)SQL_CVT_DOUBLEBC (ODBC1.0) SQL_CVT_FLOAT (ODBC 1.0)SQL_CVT_INTEGER (ODBC 1.0)SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 3.0)SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARCHAR (ODBC 1.0)SQL_CVT_NUMERIC (ODBC 1.0)SQL_ CVT_REAL ODBC 1.0)SQL_CVT_SMALLINT (ODBC 1.0)SQL_CVT_TIME (ODBC 1.0)SQL_CVT_TIMESTAMP (ODBC 1.0)SQL_CVT_TINYINT (ODBC 1.0)SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1.0)  
 Un bitmask SQLUINTEGER énumérant les fonctions de conversion scalaires supportées par le conducteur et la source de données associée.  
  
 Le bitmask suivant est utilisé pour déterminer quelles fonctions de conversion sont prises en charge :  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui indique si les noms de corrélation de tableau sont pris en charge :  
  
 SQL_CN_NONE les noms de corrélation ne sont pas pris en charge.  
  
 SQL_CN_DIFFERENT les noms de corrélation sont pris en charge, mais doivent différer des noms des tableaux qu’ils représentent.  
  
 SQL_CN_ANY les noms de corrélation sont pris en charge et peuvent être n’importe quel nom valide défini par l’utilisateur.  
  
 Un pilote SQL-92 d’entrée conforme à l’entrée sera toujours de retour SQL_CN_ANY.  
  
 SQL_CREATE_ASSERTION (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses contenues dans la déclaration **CREATE ASSERTION,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CA_CREATE_ASSERTION  
  
 Les bits suivants spécifient l’attribut de contrainte pris en charge si la capacité de spécifier explicitement les attributs de contrainte est prise en charge (voir les types d’informations SQL_ALTER_TABLE et SQL_CREATE_TABLE) :  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Un conducteur SQL-92 Full level-conformant retournera toujours toutes ces options en cas de support. Une valeur de retour de « 0 » signifie que l’énoncé **CREATE ASSERTION** n’est pas pris en charge.  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de l’énoncé **CREATE CHARACTER SET,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Un conducteur SQL-92 Full level-conformant retournera toujours toutes ces options en cas de support. Une valeur de retour de «0» signifie que l’énoncé **CREATE CHARACTER SET** n’est pas pris en charge.  
  
 SQL_CREATE_COLLATION(ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **CREATE COLLATION,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Le bitmask suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Un pilote SQL-92 De niveau complet sera toujours retourner cette option comme pris en charge. Une valeur de retour de « 0 » signifie que l’énoncé **CREATE COLLATION** n’est pas pris en charge.  
  
 SQL_CREATE_DOMAIN (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **CREATE DOMAIN,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CDO_CREATE_DOMAIN - L’énoncé CREATE DOMAIN est pris en charge (niveau intermédiaire).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION définition de \<nom de contrainte> est pris en charge pour la désignation des contraintes de domaine (niveau intermédiaire).  
  
 Les bits suivants spécifient la possibilité de créer des contraintes de colonne : SQL_CDO_DEFAULT - Spécifier les contraintes de domaine est pris en charge (niveau intermédiaire) SQL_CDO_CONSTRAINT - Spécifier les défauts de domaine est pris en charge (niveau intermédiaire) SQL_CDO_COLLATION - La collation de domaine de spécifier est prise en charge (niveau complet)  
  
 Les bits suivants spécifient les attributs de contrainte pris en charge si la spécifier les contraintes de domaine est prise en charge (SQL_CDO_DEFAULT est définie) :  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) SQL_CDO_CONSTRAINT_DEFERRABLE (niveau complet) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (niveau complet)  
  
 Une valeur de retour de « 0 » signifie que l’énoncé **CREATE DOMAIN** n’est pas pris en charge.  
  
 SQL_CREATE_SCHEMA (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **CREATE SCHEMA,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Un conducteur sqL-92 Intermediate level-conformant retournera toujours les options SQL_CS_CREATE_SCHEMA et SQL_CS_AUTHORIZATION comme support. Ceux-ci doivent également être pris en charge au niveau SQL-92 Entrée, mais pas nécessairement comme déclarations SQL. Un conducteur SQL-92 Full level-conformant retournera toujours toutes ces options en cas de support.  
  
 SQL_CREATE_TABLE (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de l’énoncé **CREATE TABLE,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CT_CREATE_TABLE - L’énoncé CREATE TABLE est pris en charge. (Niveau d’entrée)  
  
 SQL_CT_TABLE_CONSTRAINT - Spécifier les contraintes de table est soutenu (niveau transitoire FIPS)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION - La \<définition de nom de contrainte> clause est prise en charge pour les contraintes de colonne et de table de nommage (niveau intermédiaire)  
  
 Les bits suivants spécifient la possibilité de créer des tables temporaires :  
  
 SQL_CT_COMMIT_PRESERVE - Les lignes supprimées sont conservées sur commit. (Niveau complet) SQL_CT_COMMIT_DELETE - Les lignes supprimées sont supprimées sur la validation. (Niveau complet) SQL_CT_GLOBAL_TEMPORARY - Des tables temporaires globales peuvent être créées. (Niveau complet) SQL_CT_LOCAL_TEMPORARY - Des tables temporaires locales peuvent être créées. (Niveau complet)  
  
 Les bits suivants spécifient la possibilité de créer des contraintes de colonne :  
  
 SQL_CT_COLUMN_CONSTRAINT - Spécifier les contraintes de colonne est pris en charge (niveau transitoire FIPS) SQL_CT_COLUMN_DEFAULT - Spécifier les défauts de la colonne est pris en charge (niveau transitoire FIPS) SQL_CT_COLUMN_COLLATION - La collation de la colonne de spécifier est prise en charge (niveau complet)  
  
 Les bits suivants spécifient les attributs de contrainte pris en charge si la spécification des contraintes de colonne ou de table est prise en charge :  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) SQL_CT_CONSTRAINT_DEFERRABLE (niveau complet) SQL_CT_CONSTRAINT_NON_DEFERRABLE (niveau complet)  
  
 SQL_CREATE_TRANSLATION (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **CREATE TRANSLATION,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Le bitmask suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Un pilote SQL-92 Full level-conformant retournera toujours ces options en charge. Une valeur de retour de « 0 » signifie que l’énoncé **CREATE TRANSLATION** n’est pas pris en charge.  
  
 SQL_CREATE_VIEW (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **CREATE VIEW,** tel que défini dans SQL-92, étayé par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Une valeur de retour de « 0 » signifie que l’énoncé **CREATE VIEW** n’est pas pris en charge.  
  
 Un conducteur SQL-92 De niveau d’entrée retournera toujours les options SQL_CV_CREATE_VIEW et SQL_CV_CHECK_OPTION comme pris en charge.  
  
 Un conducteur SQL-92 Full level-conformant retournera toujours toutes ces options en cas de support.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui indique comment une opération **COMMIT** affecte les curseurs et les instructions préparées dans la source de données (le comportement de la source de données lorsque vous commettez une transaction).  
  
 La valeur de cet attribut reflétera l’état actuel du prochain paramètre : SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE - Fermer les curseurs et supprimer les instructions préparées. Pour utiliser à nouveau le curseur, l’application doit se reprédérer et réexécuter la déclaration.  
  
 SQL_CB_CLOSE - Fermer les curseurs. Pour les déclarations préparées, la demande peut appeler **SQLExecute** sur la déclaration sans appeler **SQLPrepare** nouveau. La valeur par défaut du conducteur SQL ODBC est SQL_CB_CLOSE. Cela signifie que le conducteur SQL ODBC fermera votre curseur lorsque vous commettez une transaction.  
  
 SQL_CB_PRESERVE - Préserver les curseurs dans la même position qu’avant l’opération **COMMIT.** L’application peut continuer à chercher des données, ou elle peut fermer le curseur et ré-exécuter l’instruction sans le re-préparer.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui indique comment une opération **ROLLBACK** affecte les curseurs et les énoncés préparés dans la source de données :  
  
 SQL_CB_DELETE - Fermer les curseurs et supprimer les instructions préparées. Pour utiliser à nouveau le curseur, l’application doit se reprédérer et réexécuter la déclaration.  
  
 SQL_CB_CLOSE - Fermer les curseurs. Pour les déclarations préparées, la demande peut appeler **SQLExecute** sur la déclaration sans appeler **SQLPrepare** nouveau.  
  
 SQL_CB_PRESERVE - Préserver les curseurs dans la même position qu’avant l’opération **ROLLBACK.** L’application peut continuer à chercher des données, ou elle peut fermer le curseur et réexécuter l’instruction sans les repreparer.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le support de la sensibilité des curseurs :  
  
 SQL_INSENSITIVE - Tous les curseurs sur la poignée de déclaration montrent le résultat défini sans refléter les modifications qui lui ont été apportées par tout autre curseur dans la même transaction.  
  
 SQL_UNSPECIFIED - Il n’est pas précisé si les curseurs sur la poignée de déclaration rendent visibles les modifications qui ont été apportées à un résultat défini par un autre curseur dans la même transaction. Les curseurs sur la poignée de déclaration peuvent rendre visibles aucun, certains ou tous ces changements.  
  
 SQL_SENSITIVE - Les curseurs sont sensibles aux modifications apportées par d’autres curseurs au cours de la même transaction.  
  
 Un conducteur SQL-92 D’entrée conforme retournera toujours l’option SQL_UNSPECIFIED tel que pris en charge.  
  
 Un conducteur SQL-92 De niveau complet remettra toujours l’option SQL_INSENSITIVE tel que pris en charge.  
  
 SQL_DATA_SOURCE_NAME (ODBC 1.0)  
 Une chaîne de caractères avec le nom de source de données qui a été utilisé lors de la connexion. Si l’application appelée **SQLConnect**, c’est la valeur de *l’argument szDSN.* Si l’application appelée **SQLDriverConnect** ou **SQLBrowseConnect**, c’est la valeur du mot clé DSN dans la chaîne de connexion passé au conducteur. Si la chaîne de connexion ne contenait pas le mot clé **DSN** (par exemple lorsqu’il contient le mot clé **DRIVER),** il s’agit d’une chaîne vide.  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1.0)  
 Chaîne caractère. "Y" si la source de données est définie en mode READ ONLY, "N" si elle est autrement.  
  
 Cette caractéristique ne concerne que la source de données elle-même; ce n’est pas une caractéristique du conducteur qui permet l’accès à la source de données. Un conducteur qui est lu/écriture peut être utilisé avec une source de données qui est lue uniquement. Si un conducteur est lu uniquement, toutes ses sources de données doivent être lues uniquement et doivent retourner SQL_DATA_SOURCE_READ_ONLY.  
  
 SQL_DATABASE_NAME (ODBC 1.0)  
 Une chaîne de caractères avec le nom de la base de données actuelle en cours d’utilisation, si la source de données définit un objet nommé appelé "base de données".  
  
> [!NOTE]
>  Dans ODBC 3 *.x*, la valeur retournée pour cette *InfoType* peut également être retournée en appelant **SQLGetConnectAttr** avec un argument *d’attribut* de SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les litres de date SQL-92 soutenus par la source de données. Notez qu’il s’agit des littérals de date énumérés dans les spécifications SQL-92 et sont distincts des clauses d’évasion littérales de date définies par ODBC. Pour plus d’informations sur les clauses d’évasion littérales ODBC datetime, voir [Date, Time, et Timestamp Literals](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Un pilote FIPS Transitional Level-conformant retournera toujours la valeur "1" dans le bitmask pour les bits dans la liste suivante. Une valeur de «0» signifie que SQL-92 littérates datetime ne sont pas pris en charge.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels littérals sont pris en charge :  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1.0)  
 Une chaîne de caractères avec le nom du produit DBMS accessible par le conducteur.  
  
 SQL_DBMS_VER (ODBC 1.0)  
 Une chaîne de caractères qui indique la version du produit DBMS accessible par le conducteur. La version est du formulaire ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' Le conducteur doit rendre la version produit DBMS sous cette forme, mais peut également ajouter la version spécifique au produit DBMS. Par exemple, "04.01.0000 Rdb 4.1".  
  
 SQL_DDL_INDEX (ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le soutien à la création et à la baisse des indices :  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1.0)  
 Une valeur SQLUINTEGER qui indique le niveau d’isolement des transactions par défaut pris en charge par le conducteur ou la source de données, ou zéro si la source de données ne prend pas en charge les transactions. Les termes suivants sont utilisés pour définir les niveaux d’isolement des transactions :  
  
 **Sale Lire** La transaction 1 change d’affilée. La transaction 2 lit la ligne modifiée avant que la transaction 1 commette la modification. Si la transaction 1 annule le changement, la transaction 2 aura lu une ligne qui est considérée comme n’ayant jamais existé.  
  
 **Lire non-repeatable** La transaction 1 lit une ligne. Transaction 2 met à jour ou supprime cette ligne et commet cette modification. Si la transaction 1 tente de relire la ligne, elle recevra différentes valeurs de ligne ou découvrira que la ligne a été supprimée.  
  
 **Fantôme** La transaction 1 lit un ensemble de lignes qui répondent à certains critères de recherche. La transaction 2 génère une ou plusieurs lignes (par des encarts ou des mises à jour) qui correspondent aux critères de recherche. Si la transaction 1 réexamine l’instruction qui lit les lignes, elle reçoit un ensemble différent de lignes.  
  
 Si la source de données prend en charge les transactions, le conducteur retourne l’un des bitmasks suivants :  
  
 SQL_TXN_READ_UNCOMMITTED - Lectures sales, lectures nonrepeatables, et les fantômes sont possibles.  
  
 SQL_TXN_READ_COMMITTED - Les lectures sales ne sont pas possibles. Des lectures nonrepeatables et des fantômes sont possibles.  
  
 SQL_TXN_REPEATABLE_READ - Lectures sales et lectures nonrepeatables ne sont pas possibles. Les fantômes sont possibles.  
  
 SQL_TXN_SERIALIZABLE - Les transactions sont sérialisables. Les transactions sérialisables ne permettent pas de lectures sales, de lectures non fiables ou de fantômes.  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3.0)  
 Une chaîne de caractères : « Y » si des paramètres peuvent être décrits ; "N", si ce n’est pas le cas.  
  
 Un conducteur SQL-92 Full level-conformant retournera habituellement « Y » parce qu’il appuiera l’énoncé **DESCRIBE INPUT.** Toutefois, parce que cela ne précise pas directement le support SQL sous-jacent, la description des paramètres pourrait ne pas être prise en charge, même dans un conducteur conforme au niveau complet SQL-92.  
  
 SQL_DM_VER (ODBC 3.0)  
 Une chaîne de caractères avec la version du Driver Manager. La version est du formulaire ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '  
  
 La première série de deux chiffres est la version principale ODBC, comme le donne la constante SQL_SPEC_MAJOR.  
  
 La deuxième série de deux chiffres est la version mineure ODBC, comme le donne la constante SQL_SPEC_MINOR.  
  
 La troisième série de quatre chiffres est le numéro de construction majeur Driver Manager.  
  
 La dernière série de quatre chiffres est le numéro de construction mineur Driver Manager.  
  
 La version Windows 7 Driver Manager est 03.80. La version Windows 8 Driver Manager est 03.81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 Une valeur SQLUINTEGER qui indique si le conducteur prend en charge la mise en commun consciente du conducteur. (Pour plus d’informations, voir [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE indique que le conducteur peut prendre en charge le mécanisme de mise en commun conscient du conducteur.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE indique que le conducteur ne peut pas prendre en charge le mécanisme de mise en commun conscient du conducteur.  
  
 Un conducteur n’a pas besoin de mettre en œuvre SQL_DRIVER_AWARE_POOLING_SUPPORTED et le gestionnaire de conducteur ne sera pas honorer la valeur de retour du conducteur.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1.0)  
 Une valeur SQLULEN, la poignée de l’environnement du conducteur ou la poignée de connexion, déterminée par l’argument *InfoType*.  
  
 Ces types d’information sont mis en œuvre par le gestionnaire de conducteur seul.  
  
 SQL_DRIVER_HDESC (ODBC 3.0)  
 Une valeur SQLULEN, la poignée descripteur du conducteur déterminée par la poignée descripteur \*du gestionnaire de conducteur, qui doit être transmise sur l’entrée dans *InfoValuePtr* de la demande. Dans ce cas, *InfoValuePtr* est à la fois un argument d’entrée et de sortie. La poignée descripteur \*d’entrée passée dans *InfoValuePtr* doit avoir été explicitement ou implicitement allouée sur le *ConnectionHandle*.  
  
 L’application doit faire une copie de la poignée descripteur du gestionnaire de conducteur avant d’appeler **SQLGetInfo** avec ce type d’information, pour s’assurer que la poignée n’est pas écrasée sur la sortie.  
  
 Ce type d’information est mis en œuvre par le gestionnaire de conducteur seul.  
  
 SQL_DRIVER_HLIB (ODBC 2.0)  
 Valeur SQLULEN, le *hinst* de la bibliothèque de chargement est retourné au Driver Manager lorsqu’il a chargé le pilote DLL sur un système d’exploitation Microsoft Windows, ou son équivalent sur un autre système d’exploitation. La poignée n’est valable que pour la poignée de connexion spécifiée dans l’appel à **SQLGetInfo**.  
  
 Ce type d’information est mis en œuvre par le gestionnaire de conducteur seul.  
  
 SQL_DRIVER_HSTMT (ODBC 1.0)  
 Une valeur SQLULEN, la poignée de déclaration du conducteur déterminée par la \*poignée de relevé du gestionnaire de conducteur, qui doit être transmise sur l’entrée dans *InfoValuePtr* de la demande. Dans ce cas, *InfoValuePtr* est à la fois un argument d’entrée et de sortie. La poignée de \*déclaration d’entrée adoptée dans *InfoValuePtr* doit avoir été allouée sur l’argument *ConnectionHandle*.  
  
 La demande doit faire une copie de la poignée de déclaration du gestionnaire de conducteur avant d’appeler **SQLGetInfo** avec ce type d’information, afin de s’assurer que la poignée n’est pas écrasée sur la sortie.  
  
 Ce type d’information est mis en œuvre par le gestionnaire de conducteur seul.  
  
 SQL_DRIVER_NAME(ODBC 1.0)  
 Une chaîne de caractères avec le nom de fichier du pilote utilisé pour accéder à la source de données.  
  
 SQL_DRIVER_ODBC_VER (ODBC 2.0)  
 Une chaîne de caractères avec la version d’ODBC que le conducteur prend en charge. La version est du formulaire ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' SQL_SPEC_MAJOR et SQL_SPEC_MINOR définir les numéros de versions majeures et mineures. Pour la version de l’ODBC décrite dans ce manuel, il s’agit de 3 et 0, et le conducteur doit retourner "03.00".  
  
 Le gestionnaire de conducteur ODBC ne modifiera pas la valeur de retour de SQLGetInfo (SQL_DRIVER_ODBC_VER) pour maintenir la compatibilité rétrograde pour les applications existantes. Le conducteur précise quelle valeur sera retournée. Toutefois, un conducteur qui prend en charge l’extéabilité de type de données C doit retourner 3,8 (ou plus) lorsqu’une application appelle **SQLSetEnvAttr** pour définir SQL_ATTR_ODBC_VERSION à 3,8. Pour plus d’informations, voir [C Data Types in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER (ODBC 1.0)  
 Une chaîne de caractère avec la version du conducteur et optionnellement, une description du conducteur. À tout le moins, la version est du formulaire ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '  
  
 SQL_DROP_ASSERTION (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **DROP ASSERTION,** telle que définie dans SQL-92, appuyée par la source de données.  
  
 Le bitmask suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DA_DROP_ASSERTION  
  
 Un pilote SQL-92 De niveau complet sera toujours retourner cette option comme pris en charge.  
  
 SQL_DROP_CHARACTER_SET (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de l’énoncé **DROP CHARACTER SET,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Le bitmask suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Un pilote SQL-92 De niveau complet sera toujours retourner cette option comme pris en charge.  
  
 SQL_DROP_COLLATION (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **DROP COLLATION,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Le bitmask suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DC_DROP_COLLATION  
  
 Un pilote SQL-92 De niveau complet sera toujours retourner cette option comme pris en charge.  
  
 SQL_DROP_DOMAIN (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **DROP DOMAIN,** telle que définie dans SQL-92, appuyée par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Un conducteur SQL-92 Intermediate level-conformant retournera toujours toutes ces options en cas de support.  
  
 SQL_DROP_SCHEMA (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **DROP SCHEMA,** tel que défini dans SQL-92, appuyé par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Un conducteur SQL-92 Intermediate level-conformant retournera toujours toutes ces options en cas de support.  
  
 SQL_DROP_TABLE(ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **DROP TABLE,** telle que définie dans SQL-92, appuyée par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Un pilote conforme au niveau de transition FIPS retournera toujours toutes ces options en cas de soutien.  
  
 SQL_DROP_TRANSLATION (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **DROP TRANSLATION,** telle que définie dans SQL-92, appuyée par la source de données.  
  
 Le bitmask suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Un pilote SQL-92 De niveau complet sera toujours retourner cette option comme pris en charge.  
  
 SQL_DROP_VIEW (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **DROP VIEW,** telle que définie dans SQL-92, appuyée par la source de données.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Un pilote conforme au niveau de transition FIPS retournera toujours toutes ces options en cas de soutien.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui décrit les attributs d’un curseur dynamique qui sont soutenus par le conducteur. Ce bitmask contient le premier sous-ensemble d’attributs; pour le deuxième sous-ensemble, voir SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels attributs sont pris en charge :  
  
 SQL_CA1_NEXT - Un argument *d’orientation de* SQL_FETCH_NEXT est soutenu dans un appel à **SQLFetchScroll** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_ABSOLUTE - Les arguments *d’orientation* de SQL_FETCH_FIRST, SQL_FETCH_LAST et SQL_FETCH_ABSOLUTE sont soutenus dans un appel à **SQLFetchScroll** lorsque le curseur est un curseur dynamique. (Le ramset qui sera récupéré est indépendant de la position actuelle du curseur.)  
  
 SQL_CA1_RELATIVE - Les arguments *d’orientation* de SQL_FETCH_PRIOR et SQL_FETCH_RELATIVE sont soutenus dans un appel à **SQLFetchScroll** lorsque le curseur est un curseur dynamique. (Le ramset qui sera récupéré dépend de la position actuelle du curseur. Notez que cela est séparé de SQL_FETCH_NEXT parce que dans un curseur avant seulement, seulement SQL_FETCH_NEXT est pris en charge.)  
  
 SQL_CA1_BOOKMARK - Un argument *d’orientation de* SQL_FETCH_BOOKMARK est soutenu dans un appel à **SQLFetchScroll** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_EXCLUSIVE - Un argument *LockType* de SQL_LOCK_EXCLUSIVE est soutenu dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_NO_CHANGE - Un argument *LockType* de SQL_LOCK_NO_CHANGE est soutenu dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_UNLOCK un argument *LockType* de SQL_LOCK_UNLOCK est soutenu dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_POSITION - Un argument *d’opération* de SQL_POSITION est soutenu dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_UPDATE - Un argument *d’opération* de SQL_UPDATE est soutenu dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_DELETE - Un argument *d’opération* de SQL_DELETE est soutenu dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_REFRESH - Un argument *d’opération* de SQL_REFRESH est soutenu dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POSITIONED_UPDATE - Une MISE À JOUR Où LA déclaration DE SQL EST prise en charge lorsque le curseur est un curseur dynamique. (Un pilote SQL-92 d’entrée conforme à ce niveau retournera toujours cette option en tant que support.)  
  
 SQL_CA1_POSITIONED_DELETE - A DELETE WHERE CURRENT OF SQL déclaration est pris en charge lorsque le curseur est un curseur dynamique. (Un pilote SQL-92 d’entrée conforme à ce niveau retournera toujours cette option en tant que support.)  
  
 SQL_CA1_SELECT_FOR_UPDATE - Une déclaration SÉLECT POUR UPDATE SQL est prise en charge lorsque le curseur est un curseur dynamique. (Un pilote SQL-92 d’entrée conforme à ce niveau retournera toujours cette option en tant que support.)  
  
 SQL_CA1_BULK_ADD - Un argument *d’opération* de SQL_ADD est soutenu dans un appel à **SQLBulkOperations** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK - Un argument *d’opération* de SQL_UPDATE_BY_BOOKMARK est soutenu dans un appel à **SQLBulkOperations** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK - Un argument *d’opération* de SQL_DELETE_BY_BOOKMARK est soutenu dans un appel à **SQLBulkOperations** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK - Un argument *d’opération* de SQL_FETCH_BY_BOOKMARK est soutenu dans un appel à **SQLBulkOperations** lorsque le curseur est un curseur dynamique.  
  
 Un conducteur sqL-92 Intermediate level-conformant retournera habituellement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE comme pris en charge, parce qu’il prend en charge les curseurs défilants par le biais de la déclaration SQL FETCH intégrée. Toutefois, comme cela ne détermine pas directement le support SQL sous-jacent, les curseurs défilementables peuvent ne pas être pris en charge, même pour un conducteur conforme au niveau intermédiaire SQL-92.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui décrit les attributs d’un curseur dynamique qui sont soutenus par le conducteur. Ce bitmask contient le deuxième sous-ensemble d’attributs; pour le premier sous-ensemble, voir SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels attributs sont pris en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCY un curseur dynamique de lecture seulement, dans lequel aucune mise à jour n’est autorisée, est pris en charge. (L’attribut de l’SQL_ATTR_CONCURRENCY déclaration peut être SQL_CONCUR_READ_ONLY pour un curseur dynamique).  
  
 SQL_CA2_LOCK_CONCURRENCY - Un curseur dynamique qui utilise le niveau le plus bas de verrouillage suffisant pour s’assurer que la ligne peut être mise à jour est pris en charge. (L’attribut de l’SQL_ATTR_CONCURRENCY déclaration peut être SQL_CONCUR_LOCK pour un curseur dynamique.) Ces verrous doivent être compatibles avec le niveau d’isolement des transactions fixé par l’attribut de connexion SQL_ATTR_TXN_ISOLATION.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY un curseur dynamique qui utilise le contrôle de concurrence optimiste comparant les versions de la ligne est pris en charge. (L’attribut de l’SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_ROWVER pour un curseur dynamique.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY un curseur dynamique qui utilise le contrôle de la concurrence optimiste comparant les valeurs est pris en charge. (L’attribut de l’SQL_ATTR_CONCURRENCY déclaration peut être SQL_CONCUR_VALUES pour un curseur dynamique.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS - Les lignes ajoutées sont visibles à un curseur dynamique; le curseur peut faire défiler ces lignes. (Lorsque ces lignes sont ajoutées au curseur dépend du conducteur.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS - Les lignes supprimées ne sont plus accessibles à un curseur dynamique et ne laissent pas de « trou » dans l’ensemble de résultats ; après que le curseur dynamique défile d’une ligne supprimée, il ne peut pas revenir à cette ligne.  
  
 SQL_CA2_SENSITIVITY_UPDATES - Les mises à jour des rangées sont visibles par un curseur dynamique; si le curseur dynamique fait défiler et retourne à une ligne mise à jour, les données retournées par le curseur sont les données mises à jour, et non les données d’origine.  
  
 SQL_CA2_MAX_ROWS_SELECT l’attribut de l’instruction SQL_ATTR_MAX_ROWS affecte les instructions **SELECT** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_INSERT l’attribut de l’instruction SQL_ATTR_MAX_ROWS affecte les instructions **INSERT** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_DELETE l’attribut de l’SQL_ATTR_MAX_ROWS indique que les instructions **SUPPRIMER** sont modifiées lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_UPDATE l’attribut de l’SQL_ATTR_MAX_ROWS indique que les instructions **UPDATE** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_CATALOG l’attribut de l’instruction SQL_ATTR_MAX_ROWS affecte les ensembles de résultats **CATALOG** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL l’attribut de l’instruction SQL_ATTR_MAX_ROWS affecte **SELECT**, **INSERT**, **DELETE**, et **les** ensembles de résultats **CATALOG,** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_CRC_EXACT - Le nombre exact de rangées est disponible dans le domaine du diagnostic SQL_DIAG_CURSOR_ROW_COUNT lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_CRC_APPROXIMATE - Un nombre de rangées approximative est disponible dans le domaine du diagnostic SQL_DIAG_CURSOR_ROW_COUNT lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE - Le conducteur ne garantit pas que la mise à jour ou la suppression simulée des instructions de mise à jour ou de suppression n’affecteront qu’une seule ligne lorsque le curseur est un curseur dynamique; il incombe à l’application de garantir cela. (Si une déclaration touche plus d’une rangée, **SQLExecute** ou **SQLExecDirect** renvoie SQLSTATE 01001 [conflit d’opération Cursor].) Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_SIMULATE_CURSOR défini à SQL_SC_NON_UNIQUE.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE - Le conducteur tente de garantir que la mise à jour ou la suppression simulée des instructions positionnées n’affectera qu’une seule ligne lorsque le curseur est un curseur dynamique. Le conducteur exécute toujours de telles déclarations, même si elles peuvent affecter plus d’une rangée, par exemple lorsqu’il n’y a pas de clé unique. (Si une déclaration touche plus d’une rangée, **SQLExecute** ou **SQLExecDirect** renvoie SQLSTATE 01001 [conflit d’opération Cursor].) Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_SIMULATE_CURSOR défini à SQL_SC_TRY_UNIQUE.  
  
 SQL_CA2_SIMULATE_UNIQUE - Le conducteur garantit que les instructions de mise à jour ou de suppression positionnées simulées n’affecteront qu’une seule ligne lorsque le curseur est un curseur dynamique. Si le conducteur ne peut pas le garantir pour une déclaration donnée, **SQLExecDirect** ou **SQLPrepare** retournent SQLSTATE 01001 (conflit d’exploitation cursor). Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_SIMULATE_CURSOR défini à SQL_SC_UNIQUE.  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge les expressions de la liste **ORDER BY** ; "N" si ce n’est pas le cas.  
  
 SQL_FILE_USAGE (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui indique comment un conducteur à un seul niveau traite directement les fichiers dans une source de données :  
  
 SQL_FILE_NOT_SUPPORTED le conducteur n’est pas un conducteur à un seul niveau. Par exemple, un pilote ORACLE est un pilote à deux vitesses.  
  
 SQL_FILE_TABLE un pilote à un seul niveau traite les fichiers dans une source de données comme des tableaux. Par exemple, un pilote Xbase traite chaque fichier Xbase comme une table.  
  
 SQL_FILE_CATALOG un pilote à un seul niveau traite les fichiers d’une source de données comme un catalogue. Par exemple, un pilote Microsoft Access traite chaque fichier Microsoft Access comme une base de données complète.  
  
 Une application peut l’utiliser pour déterminer comment les utilisateurs sélectionneront les données. Par exemple, les utilisateurs de Xbase pensent souvent que les données sont stockées dans des fichiers, tandis que les utilisateurs d’ORACLE et de Microsoft Access pensent généralement que les données sont stockées dans les tables.  
  
 Lorsqu’un utilisateur sélectionne une source de données Xbase, l’application peut afficher la boîte de dialogue commune De Windows **File Open** ; lorsque l’utilisateur sélectionne une source de données Microsoft Access ou ORACLE, l’application peut afficher une boîte de dialogue **Select Table** personnalisée.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui décrit les attributs d’un curseur avant seulement qui sont soutenus par le conducteur. Ce bitmask contient le premier sous-ensemble d’attributs; pour le deuxième sous-ensemble, voir SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels attributs sont pris en charge :  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour les descriptions de ces bitmasks, voir SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (et remplacer le « curseur avant-seulement » par le « curseur dynamique » dans les descriptions).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui décrit les attributs d’un curseur avant seulement qui sont soutenus par le conducteur. Ce bitmask contient le deuxième sous-ensemble d’attributs; pour le premier sous-ensemble, voir SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels attributs sont pris en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Pour les descriptions de ces bitmasks, voir SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (et remplacer le « curseur avant-seulement » par le « curseur dynamique » dans les descriptions).  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les extensions à **SQLGetData**.  
  
 Les bitmasks suivants sont utilisés avec le drapeau pour déterminer quelles extensions communes le conducteur prend en charge pour **SQLGetData**:  
  
 SQL_GD_ANY_COLUMN - **SQLGetData** peut être appelé pour n’importe quelle colonne non liée, y compris celles avant la dernière colonne liée. Notez que les colonnes doivent être appelées dans l’ordre du numéro de colonne ascendante à moins que SQL_GD_ANY_ORDER ne soit également retournée.  
  
 SQL_GD_ANY_ORDER - **SQLGetData** peut être appelé pour des colonnes non liées dans n’importe quel ordre. Notez que **SQLGetData** ne peut être appelé que pour les colonnes après la dernière colonne liée à moins que SQL_GD_ANY_COLUMN ne soit également retourné.  
  
 SQL_GD_BLOCK **- SQLGetData** peut être appelé pour une colonne non liée dans n’importe quelle rangée dans un bloc (où la taille de rowset est supérieure à 1) des données après le positionnement à cette rangée avec **SQLSetPos**.  
  
 SQL_GD_BOUND - **SQLGetData** peut être appelé pour les colonnes liées en plus de colonnes non liées. Un conducteur ne peut pas retourner cette valeur à moins qu’il ne retourne également SQL_GD_ANY_COLUMN.  
  
 SQL_GD_OUTPUT_PARAMS - **SQLGetData** peut être appelé à retourner les valeurs de paramètres de sortie. Pour plus d’informations, voir [Paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** est tenu de retourner les données uniquement à partir de colonnes non liées qui se produisent après la dernière colonne liée, sont appelés par ordre de numéro de colonne croissante, et ne sont pas dans une rangée dans un bloc de rangées.  
  
 Si un conducteur prend en charge les signets (à longueur fixe ou à longueur variable), il doit prendre en charge l’appel **SQLGetData** sur la colonne 0. Ce support est nécessaire indépendamment de ce que le conducteur retourne pour un appel à **SQLGetInfo** avec le SQL_GETDATA_EXTENSIONS *InfoType*.  
  
 SQL_GROUP_BY (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui précise la relation entre les colonnes de la clause **GROUPE BY** et les colonnes non agrégées dans la liste sélectionnée :  
  
 SQL_GB_COLLATE une clause **COLLATE** peut être spécifiée à la fin de chaque colonne de groupement. (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED clauses **GROUPE BY** ne sont pas prises en charge. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT - La clause **GROUPE BY** doit contenir toutes les colonnes non agrégatées dans la liste de sélection. Il ne peut contenir aucune autre colonne. Par exemple, **SELECT DEPT, MAX (SALARY) FROM EMPLOYEE GROUP BY DEPT**. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT - La clause **GROUPE BY** doit contenir toutes les colonnes non ventilées dans la liste de sélection. Il peut contenir des colonnes qui ne sont pas dans la liste de sélection. Par exemple, **SELECT DEPT, MAX (SALARY) FROM EMPLOYEE GROUP BY DEPT, AGE**. (ODBC 2.0)  
  
 SQL_GB_NO_RELATION - Les colonnes de la clause **GROUPE BY** et de la liste sélectionnée ne sont pas liées. La signification des colonnes non groupées et non regroupées dans la liste sélectionnée est dépendante des données. Par exemple, **SELECT DEPT, SALARY FROM EMPLOYEE GROUP BY DEPT, AGE**. (ODBC 2.0)  
  
 Un conducteur SQL-92 D’entrée conforme retournera toujours l’option SQL_GB_GROUP_BY_EQUALS_SELECT tel que pris en charge. Un conducteur SQL-92 De niveau complet remettra toujours l’option SQL_GB_COLLATE tel que pris en charge. Si aucune des options n’est prise en charge, la clause **GROUPE BY** n’est pas prise en charge par la source de données.  
  
 SQL_IDENTIFIER_CASE (ODBC 1.0)  
 Une valeur SQLUSMALLINT comme suit :  
  
 SQL_IC_UPPER - Les identifiants dans SQL ne sont pas sensibles aux cas et sont stockés dans la majuscule dans le catalogue du système.  
  
 SQL_IC_LOWER - Les identifiants dans SQL ne sont pas sensibles aux cas et sont stockés dans une chambre inférieure dans le catalogue du système.  
  
 SQL_IC_SENSITIVE - Les identifiants de SQL sont sensibles aux cas et sont stockés dans des cas mixtes dans le catalogue du système.  
  
 SQL_IC_MIXED - Les identifiants dans SQL ne sont pas sensibles aux cas et sont stockés dans des cas mixtes dans le catalogue du système.  
  
 Étant donné que les identificateurs de SQL-92 ne sont jamais sensibles aux cas, un conducteur qui se conforme strictement à SQL-92 (n’importe quel niveau) ne retournera jamais l’option SQL_IC_SENSITIVE tel que pris en charge.  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1.0)  
 La chaîne de caractère qui est utilisée comme délimiter de départ et de fin d’un identifiant cité (délimité) dans les déclarations SQL. (Les identifications passées comme arguments aux fonctions de l’ODBC n’ont pas à être citées.) Si la source de données ne prend pas en charge les identifiants cités, un blanc est retourné.  
  
 Cette chaîne de caractère peut également être utilisée pour citer des arguments de fonction de catalogue lorsque l’attribut de connexion SQL_ATTR_METADATA_ID est réglé pour SQL_TRUE.  
  
 Parce que le caractère de citation d’identification dans SQL-92 est la double marque de citation ("), un conducteur qui se conforme strictement à SQL-92 sera toujours retourner le caractère double marque de citation.  
  
 SQL_INDEX_KEYWORDS (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui énumère les mots clés dans la déclaration CREATE INDEX qui sont pris en charge par le conducteur :  
  
 SQL_IK_NONE aucun des mots clés n’est pris en charge.  
  
 SQL_IK_ASC mot-clé de nCP est pris en charge.  
  
 SQL_IK_DESC mot-clé de LAC est pris en charge.  
  
 SQL_IK_ALL - Tous les mots clés sont pris en charge.  
  
 Pour voir si la déclaration CREATE INDEX est prise en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_DLL_INDEX.  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les points de vue dans le INFORMATION_SCHEMA qui sont soutenus par le conducteur. Les vues et le contenu de la INFORMATION_SCHEMA sont définis dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles vues sont prises en charge :  
  
 SQL_ISV_ASSERTIONS identifie les affirmations du catalogue qui appartiennent à un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_CHARACTER_SETS identifie les ensembles de caractères du catalogue qui peuvent être consultés par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_CHECK_CONSTRAINTS identifie les contraintes CHECK qui appartiennent à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_COLLATIONS identifie les collations de caractère pour le catalogue qui peuvent être consultées par un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE identifie les colonnes pour le catalogue qui dépendent des domaines définis dans le catalogue et qui appartiennent à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_COLUMN_PRIVILEGES identifie les privilèges sur les colonnes de tableaux persistants qui sont disponibles ou accordés par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_COLUMNS identifie les colonnes de tables persistantes auxquelles un utilisateur donné peut accéder. (Niveau transitoire FIPS)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE - Semblable à CONSTRAINT_TABLE_USAGE vue, les colonnes sont identifiées pour les diverses contraintes qui appartiennent à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE identifie les tableaux qui sont utilisés par des contraintes (référentiels, uniques et affirmations), et qui appartiennent à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS identifie les contraintes de domaine (des domaines du catalogue) auxquelles un utilisateur donné peut accéder. (Niveau intermédiaire)  
  
 SQL_ISV_DOMAINS identifie les domaines définis dans un catalogue accessible par l’utilisateur. (Niveau intermédiaire)  
  
 SQL_ISV_KEY_COLUMN_USAGE identifie les colonnes définies dans le catalogue qui sont limitées comme clés par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS identifie les contraintes référentielles qui appartiennent à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_SCHEMATA identifie les schémas qui appartiennent à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_SQL_LANGUAGES identifie les niveaux de conformité SQL, les options et les dialectes soutenus par la mise en œuvre SQL. (Niveau intermédiaire)  
  
 SQL_ISV_TABLE_CONSTRAINTS identifie les contraintes de table qui appartiennent à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_TABLE_PRIVILEGES identifie les privilèges sur les tables persistantes qui sont disponibles ou accordées par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_TABLES identifie les tableaux persistants définis dans un catalogue accessible par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_TRANSLATIONS identifie les traductions de caractères pour le catalogue qui peuvent être consultées par un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_USAGE_PRIVILEGES identifie les privilèges USE sur les objets de catalogue qui sont disponibles ou appartenant à un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_VIEW_COLUMN_USAGE identifie les colonnes sur lesquelles dépendent les vues du catalogue qui appartiennent à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_VIEW_TABLE_USAGE identifie les tableaux sur lesquels les vues du catalogue qui appartiennent à un utilisateur donné sont dépendantes. (Niveau intermédiaire)  
  
 SQL_ISV_VIEWS identifie les tableaux visualisés définis dans ce catalogue qui peuvent être consultés par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_INSERT_STATEMENT (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui indique le soutien aux déclarations **INSERT** :  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Un conducteur SQL-92 d’entrée conforme retournera toujours toutes ces options en cas de support.  
  
 SQL_INTEGRITY (ODBC 1.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge l’installation d’amélioration de l’intégrité; "N" si ce n’est pas le cas.  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_ODBC_SQL_OPT_IEF.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui décrit les attributs d’un curseur de clé qui sont soutenus par le conducteur. Ce bitmask contient le premier sous-ensemble d’attributs; pour le deuxième sous-ensemble, voir SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels attributs sont pris en charge :  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour les descriptions de ces bitmasks, voir SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (et remplacer le curseur « keyset- piloté » par « curseur dynamique » dans les descriptions).  
  
 Un conducteur sqL-92 Intermediate level-conformant retournera habituellement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE comme pris en charge, parce que le conducteur prend en charge les curseurs défilants par l’intermédiaire de la déclaration SQL FETCH intégrée. Toutefois, comme cela ne détermine pas directement le support SQL sous-jacent, les curseurs défilementables peuvent ne pas être pris en charge, même pour un conducteur conforme au niveau intermédiaire SQL-92.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui décrit les attributs d’un curseur de clé qui sont soutenus par le conducteur. Ce bitmask contient le deuxième sous-ensemble d’attributs; pour le premier sous-ensemble, voir SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels attributs sont pris en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Pour les descriptions de ces bitmasks, voir SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (et remplacer le curseur « keyset- piloté » par « curseur dynamique » dans les descriptions).  
  
 SQL_KEYWORDS (ODBC 2.0)  
 Une chaîne de caractères qui contient une liste séparée par virgule de tous les mots clés spécifiques à la source de données. Cette liste ne contient pas de mots clés spécifiques à ODBC ou de mots clés utilisés à la fois par la source de données et oDBC. Cette liste représente tous les mots clés réservés; les applications interopérables ne doivent pas utiliser ces mots dans les noms d’objets.  
  
 Pour une liste de mots clés ODBC, voir [Mots clés réservés](../../../odbc/reference/appendixes/reserved-keywords.md) à [l’annexe C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). La **valeur #define** SQL_ODBC_KEYWORDS contient une liste de mots clés ODBC séparée par la virgule.  
  
 Annexe C : Grammaire SQL  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge un caractère d’évasion pour le pourcentage de caractère (%) et souligner le caractère () dans un **predicate LIKE** et le conducteur prend en charge la syntaxe ODBC pour définir un caractère d’évasion PRÉdicate **LIKE;** "N" autrement.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3.0)  
 Une valeur SQLUINTEGER qui spécifie le nombre maximal d’instructions simultanées actives en mode asynchrone que le conducteur peut prendre en charge sur une connexion donnée. S’il n’y a pas de limite spécifique ou si la limite est inconnue, cette valeur est nulle.  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères hexadecimal, à l’exclusion du préfixe et du suffixe littéral retourné par **SQLGetTypeInfo**) d’un littératal binaire dans une déclaration SQL. Par exemple, le binaire littéral 0xFFAA a une longueur de 4. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de catalogue dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote FIPS Full level-conformant retournera au moins 128.  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_MAX_QUALIFIER_NAME_LEN.  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères, à l’exclusion du préfixe et du suffixe littéral retourné par **SQLGetTypeInfo**) d’un personnage littéral dans un communiqué SQL. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de colonne dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 18. Un pilote fiPS Intermediate niveau conforme reviendra au moins 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui précise le nombre maximal de colonnes autorisées dans une clause **GROUPE BY.** S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 6. Un pilote fiPS Intermediate niveau conforme reviendra au moins 15.  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans un indice. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui précise le nombre maximal de colonnes autorisées dans une clause **ORDER BY.** S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 6. Un pilote fiPS Intermediate niveau conforme reviendra au moins 15.  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximum de colonnes autorisées dans une liste sélectionnée. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 100. Un pilote fiPS Intermediate niveau conforme reviendra au moins 250.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximum de colonnes autorisées dans un tableau. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 100. Un pilote fiPS Intermediate niveau conforme reviendra au moins 250.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal d’instructions actives que le conducteur peut prendre en charge pour une connexion. Une déclaration est définie comme active si elle a des résultats en attente, avec le terme "résultats" signifiant lignes d’une opération **SELECT** ou des lignes affectées par un **INSERT**, **UPDATE**, ou **l’opération DELETE** (comme un nombre de lignes), ou si elle est dans un état NEED_DATA. Cette valeur peut refléter une limitation imposée par le conducteur ou la source de données. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_ACTIVE_STATEMENTS.  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de curseur dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 18. Un pilote fiPS Intermediate niveau conforme reviendra au moins 128.  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de connexions actives que le conducteur peut supporter pour un environnement. Cette valeur peut refléter une limitation imposée par le conducteur ou la source de données. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_ACTIVE_CONNECTIONS.  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3.0)  
 Un SQLUSMALLINT qui indique la taille maximale des caractères que la source de données prend en charge pour les noms définis par l’utilisateur.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 18. Un pilote fiPS Intermediate niveau conforme reviendra au moins 128.  
  
 SQL_MAX_INDEX_SIZE (ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie le nombre maximal d’octets autorisés dans les champs combinés d’un indice. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la durée maximale d’un nom de procédure dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_ROW_SIZE (ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie la longueur maximale d’une seule rangée dans une table. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 2 000 personnes. Un pilote fiPS Intermediate level-conformant retournera au moins 8 000.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3.0)  
 Une chaîne de caractère: "Y" si la taille maximale de la rangée retournée pour le type d’information SQL_MAX_ROW_SIZE comprend la longueur de toutes les colonnes SQL_LONGVARCHAR et SQL_LONGVARBINARY dans la rangée; "N" autrement.  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de schéma dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 18. Un pilote fiPS Intermediate niveau conforme reviendra au moins 128.  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_MAX_OWNER_NAME_LEN.  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères, y compris l’espace blanc) d’une déclaration SQL. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de table dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 18. Un pilote fiPS Intermediate niveau conforme reviendra au moins 128.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui précise le nombre maximal de tableaux autorisés dans la clause **FROM** d’un relevé **SELECT.** S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau FIPS Entry reviendra au moins 15. Un pilote fiPS Intermediate niveau conforme reviendra au moins 50.  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie la durée maximale d’un nom d’utilisateur dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MULT_RESULT_SETS (ODBC 1.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge plusieurs ensembles de résultats, « N » si ce n’est pas le cas.  
  
 Pour plus d’informations sur les ensembles de résultats multiples, voir [résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1.0)  
 Une chaîne de caractères : « Y » si le conducteur prend en charge plus d’une transaction active en même temps, « N » si une seule transaction peut être active à tout moment.  
  
 Les renseignements retournés pour ce type d’information ne s’appliquent pas dans le cas des transactions distribuées.  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2.0)  
 Une chaîne de caractères : « Y » si la source de données a besoin de la durée d’une longue valeur de données (le type de données est SQL_LONGVARCHAR, SQL_LONGVARBINARY ou un type de données spécifique à une source de données) avant que cette valeur ne soit envoyée à la source de données, « N » si ce n’est pas le cas. Pour plus d’informations, voir [SQLBindParameter Function](../../../odbc/reference/syntax/sqlbindparameter-function.md) et [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1.0)  
 Une valeur SQLUSMALLINT qui précise si la source de données ne prend PAS en charge NULL dans les colonnes :  
  
 SQL_NNC_NULL - Toutes les colonnes doivent être annulées.  
  
 SQL_NNC_NON_NULL - Les colonnes ne peuvent pas être annulées. (La source de données prend en charge la contrainte de la colonne **NOT NULL** dans les énoncés **CREATE TABLE.)**  
  
 Un conducteur SQL-92 d’entrée de niveau-conformant retournera SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION (ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie où les NULL sont triés dans un ensemble de résultats :  
  
 SQL_NC_END - NULLs sont triés à la fin de l’ensemble de résultats, indépendamment des mots clés ASC ou DESC.  
  
 SQL_NC_HIGH - NULLs sont triés à l’extrémité supérieure de l’ensemble de résultats, en fonction des mots clés ASC ou DESC.  
  
 SQL_NC_LOW - NULLs sont triés à l’extrémité basse de l’ensemble de résultats, en fonction des mots clés ASC ou DESC.  
  
 SQL_NC_START ' NULLs sont triés au début de l’ensemble de résultats, indépendamment des mots clés ASC ou DESC.  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1.0)  
 Remarque : Le type d’information a été introduit dans ODBC 1.0; chaque bitmask est étiqueté avec la version dans laquelle il a été introduit.  
  
 Un bitmask SQLUINTEGER énumérant les fonctions numériques scalaires supportées par le conducteur et la source de données associée.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles fonctions numériques sont prises en charge :  
  
 SQL_FN_NUM_ABS (ODBC 1.0)SQL_FN_NUM_ACOS (ODBC 1.0)SQL_FN_NUM_ASIN (ODBC 1.0)SQL_FN_NUM_ATAN (ODBC 1.0)SQL_FN_NUM_ATAN2 (ODBC 1.0)SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC) SQL_FN_NUM_COS (ODBC) SQL_FN_NUM_COS (ODBC 1.0)SQL_FN_NUM_COT (ODBC 1.0)SQL_FN_NUM_DEGREES (ODBC 2.0)SQL_FN_NUM_EXP (ODBC 1.0)SQL_FN_NUM_FLOOR (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 2.0)SQL_FN_ NUM_MOD (ODBC 1.0)SQL_FN_NUM_PI (ODBC 1.0)SQL_FN_NUM_POWER (ODBC 2.0)SQL_FN_NUM_RADIANS (ODBC 2.0)SQL_FN_NUM_RAND (ODBC 1.0)SQL_FN_NUM_ROUND (ODBC) SQL_FN_NUM_ROUND (ODBC) 2.0) SQL_FN_NUM_SIGN (ODBC 1.0)SQL_FN_NUM_SIN (ODBC 1.0)SQL_FN_NUM_SQRT (ODBC 1.0)SQL_FN_NUM_TAN (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le niveau de l’interface ODBC 3 *.x* que le conducteur se conforme.  
  
 SQL_OIC_CORE : Le niveau minimum auquel tous les conducteurs d’ODBC sont censés se conformer. Ce niveau comprend des éléments d’interface de base tels que des fonctions de connexion, des fonctions pour la préparation et l’exécution d’une déclaration SQL, des fonctions de métadonnées de base définies de résultat, des fonctions de catalogue de base, et ainsi de suite.  
  
 SQL_OIC_LEVEL1 : Un niveau comprenant la fonctionnalité de niveau de conformité des normes de base, ainsi que des curseurs défilementables, des signets, des mises à jour et des suppressions positionnées, et ainsi de suite.  
  
 SQL_OIC_LEVEL2 : Un niveau comprenant la fonctionnalité de niveau 1 de niveau de conformité des normes, ainsi que des fonctionnalités avancées telles que les curseurs sensibles ; mettre à jour, supprimer et rafraîchir par des signets; support de procédure stocké; fonctions de catalogue pour les clés primaires et étrangères; support multi-catalogue; et ainsi de suite.  
  
 Pour plus d’informations, voir [Interface Conformance Levels](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 SQL_ODBC_VER (ODBC 1.0)  
 Une chaîne de caractères avec la version d’ODBC à laquelle le Driver Manager se conforme. La version est du formulaire de 10 000 euros, où les deux premiers chiffres sont la version principale et les deux prochains chiffres sont la version mineure. Ceci n’est mis en œuvre que dans le Driver Manager.  
  
 SQL_OJ_CAPABILITIES(ODBC 2.01)  
 Un bitmask SQLUINTEGER énumérant les types de jointures extérieures supportées par le conducteur et la source de données. Les bitmasks suivants sont utilisés pour déterminer quels types sont pris en charge :  
  
 SQL_OJ_LEFT - Les jointures extérieures de gauche sont soutenues.  
  
 SQL_OJ_RIGHT - Les jointures extérieures droites sont prises en charge.  
  
 SQL_OJ_FULL - Les jointures extérieures complètes sont prises en charge.  
  
 SQL_OJ_NESTED - Les jointures extérieures imbriquées sont soutenues.  
  
 SQL_OJ_NOT_ORDERED - Les noms de colonne dans la clause ON de l’adhésion extérieure n’ont pas à être dans le même ordre que leurs noms de table respectifs dans la clause **OUTER JOIN.**  
  
 SQL_OJ_INNER la table intérieure (la table droite dans une jointure extérieure gauche ou la table gauche dans une jointure extérieure droite) peut également être utilisée dans une jointure intérieure. Cela ne s’applique pas aux jointures extérieures complètes, qui n’ont pas de table intérieure.  
  
 SQL_OJ_ALL_COMPARISON_OPS - L’opérateur de comparaison de la clause ON peut être l’un des opérateurs de comparaison ODBC. Si ce bit n’est pas réglé, seul l’opérateur de comparaison égal peut être utilisé dans les jointures extérieures.  
  
 Si aucune de ces options n’est retournée comme pris en charge, aucune clause de jointure extérieure n’est prise en charge.  
  
 Pour obtenir de l’information sur le soutien des opérateurs de jointure relationnel dans un communiqué SELECT, tel que défini par SQL-92, voir SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2.0)  
 Une chaîne de caractères: "Y" si les colonnes de la clause **ORDER BY** doivent être dans la liste sélectionnée; sinon, "N".  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3.0)  
 Un SQLUINTEGER énumérant les propriétés du conducteur concernant la disponibilité des dénombrements de rangées dans une exécution paramétrée. A les valeurs suivantes:  
  
 SQL_PARC_BATCH - Des nombres de lignes individuels sont disponibles pour chaque ensemble de paramètres. Ceci est conceptuellement équivalent au conducteur générant un lot de déclarations SQL, un pour chaque paramètre défini dans le tableau. Les informations d’erreur étendues peuvent être récupérées en utilisant le champ descripteur SQL_PARAM_STATUS_PTR.  
  
 SQL_PARC_NO_BATCH - Il n’y a qu’un seul nombre de lignes disponibles, c’est-à-propos du nombre cumulatif de rangées résultant de l’exécution de l’énoncé pour l’ensemble des paramètres. Ceci est conceptuellement équivalent à traiter l’instruction avec le tableau complet des paramètres comme une unité atomique. Les erreurs sont traitées de la même façon que si une instruction avait été exécutée.  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3.0)  
 Un SQLUINTEGER énumérant les propriétés du conducteur concernant la disponibilité des résultats s’installe dans une exécution paramétrée. A les valeurs suivantes:  
  
 SQL_PAS_BATCH - Il y a un ensemble de résultats disponible par ensemble de paramètres. Ceci est conceptuellement équivalent au conducteur générant un lot de déclarations SQL, un pour chaque paramètre défini dans le tableau.  
  
 SQL_PAS_NO_BATCH - Il n’y a qu’un seul ensemble de résultats disponibles, ce qui représente l’ensemble de résultats cumulatif résultant de l’exécution de l’énoncé pour la gamme complète de paramètres. Ceci est conceptuellement équivalent à traiter l’instruction avec le tableau complet des paramètres comme une unité atomique.  
  
 SQL_PAS_NO_SELECT un pilote ne permet pas l’exécution d’une déclaration génératrice de résultats avec un éventail de paramètres.  
  
 SQL_PROCEDURE_TERM (ODBC 1.0)  
 Une chaîne de caractères avec le nom du fournisseur de source de données pour une procédure; par exemple, "procédure de base de données", "procédure stockée", "procédure", "paquet" ou "requête stockée".  
  
 SQL_PROCEDURES (ODBC 1.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge les procédures et le conducteur prend en charge la syntaxe d’invocation de la procédure ODBC; "N" autrement.  
  
 SQL_POS_OPERATIONS (ODBC 2.0)  
 Un bitmask SQLINTEGER énumérant les opérations de soutien dans **SQLSetPos**.  
  
 Les bitmasks suivants sont utilisés avec le drapeau pour déterminer quelles options sont prises en charge.  
  
 SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2.0)  
 Une valeur SQLUSMALLINT comme suit :  
  
 SQL_IC_UPPER - Les identifiants cités dans SQL ne sont pas sensibles aux cas et sont stockés dans la majuscule dans le catalogue du système.  
  
 SQL_IC_LOWER - Les identifiants cités dans SQL ne sont pas sensibles aux cas et sont stockés dans la chambre inférieure dans le catalogue du système.  
  
 SQL_IC_SENSITIVE - Les identifiants cités dans SQL sont sensibles aux cas et sont stockés en cas mixte dans le catalogue du système. (Dans une base de données conforme à la SQL-92, les identifiants cités sont toujours sensibles au cas.)  
  
 SQL_IC_MIXED - Les identifiants cités dans SQL ne sont pas sensibles aux cas et sont stockés en cas mixte dans le catalogue du système.  
  
 Un pilote SQL-92 d’entrée conforme à l’entrée sera toujours de retour SQL_IC_SENSITIVE.  
  
 SQL_ROW_UPDATES(ODBC 1.0)  
 Une chaîne de caractères : « Y » si un curseur à clé ou mixte conserve des versions de ligne ou des valeurs pour toutes les rangées récupérées et peut donc détecter toutes les mises à jour qui ont été faites à une ligne par n’importe quel utilisateur depuis que la dernière ligne a été récupérée. (Cela ne s’applique qu’aux mises à jour, et non aux suppressions ou aux insertions.) Le conducteur peut retourner le drapeau SQL_ROW_UPDATED au tableau d’état de la rangée lorsque **SQLFetchScroll** est appelé. Sinon, "N".  
  
 SQL_SCHEMA_TERM (ODBC 1.0)  
 Une chaîne de caractères avec le nom du fournisseur de source de données pour un schéma; par exemple, "propriétaire", "identification d’autorisation" ou "Schema".  
  
 La chaîne de caractère peut être retournée dans le cas supérieur, inférieur ou mixte.  
  
 Un pilote SQL-92 d’entrée conforme à l’entrée retournera toujours « schéma ».  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_OWNER_TERM.  
  
 SQL_SCHEMA_USAGE (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les énoncés dans lesquels les schémas peuvent être utilisés :  
  
 SQL_SU_DML_STATEMENTS - Schemas sont pris en charge dans toutes les déclarations de langage de manipulation de données: **SELECT**, **INSERT**, **UPDATE**, **SUPPRIMER**, et si pris en charge, **SELECT FOR UPDATE** et positionné mise à jour et supprimer les déclarations.  
  
 SQL_SU_PROCEDURE_INVOCATION - Schemas sont pris en charge dans la déclaration d’invocation de la procédure ODBC.  
  
 SQL_SU_TABLE_DEFINITION - Schemas sont pris en charge dans toutes les déclarations de définition de tableau: **CREATE TABLE**, **CREATE VIEW**, ALTER **TABLE**, **DROP TABLE**, et DROP **VIEW**.  
  
 SQL_SU_INDEX_DEFINITION schemas sont pris en charge dans tous les énoncés de définition des indices : **CREATE INDEX** et **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION - Schemas sont soutenus dans toutes les déclarations de définition du privilège : **GRANT** et **REVOKE**.  
  
 Un conducteur sqL-92 De niveau d’entrée retournera toujours les options SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION et SQL_SU_PRIVILEGE_DEFINITION, comme pris en charge.  
  
 Cette *InfoType* a été rebaptisée pour ODBC 3.0 de l’ODBC 2.0 *InfoType* SQL_OWNER_USAGE.  
  
 SQL_SCROLL_OPTIONS (ODBC 1.0)  
 Remarque : Le type d’information a été introduit dans ODBC 1.0; chaque bitmask est étiqueté avec la version dans laquelle il a été introduit.  
  
 Un bitmask SQLUINTEGER énumérant les options de défilement prises en charge pour les curseurs défilementables.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles options sont prises en charge :  
  
 SQL_SO_FORWARD_ONLY - Le curseur ne fait que défiler vers l’avant. (ODBC 1.0)  
  
 SQL_SO_STATIC - Les données de l’ensemble de résultats sont statiques. (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN le pilote enregistre et utilise les clés pour chaque ligne dans l’ensemble de résultat. (ODBC 1.0)  
  
 SQL_SO_DYNAMIC - Le conducteur conserve les clés pour chaque rangée dans le jeu de ligne (la taille de l’ensemble de clés est la même que la taille de l’aviron). (ODBC 1.0)  
  
 SQL_SO_MIXED - Le conducteur conserve les clés pour chaque rangée dans le jeu de clés, et la taille de l’ensemble de clés est supérieure à la taille de l’ensemble de rangées. Le curseur est piloté à l’intérieur du jeu de clés et dynamique à l’extérieur du jeu de clés. (ODBC 1.0)  
  
 Pour plus d’informations sur les curseurs défilementables, voir [Cursesors défilants](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE(ODBC 1.0)  
 Une chaîne de caractères spécifiant ce que le conducteur prend en charge comme un personnage d’évasion qui permet l’utilisation des métacharacteurs de correspondance de modèle soulignent () et signe de pourcentage (%) en tant que caractères valides dans les modèles de recherche. Ce caractère d’évasion ne s’applique que pour les arguments de fonction de catalogue qui prennent en charge les chaînes de recherche. Si cette chaîne est vide, le conducteur ne prend pas en charge un caractère d’évasion de type d’évasion de type de recherche.  
  
 Étant donné que ce type d’information n’indique pas le soutien général du caractère d’évasion dans le **predicate LIKE,** SQL-92 n’inclut pas les exigences pour cette chaîne de caractère.  
  
 Cette *InfoType* se limite aux fonctions de catalogue. Pour une description de l’utilisation du caractère d’évasion dans les chaînes de modèle de recherche, voir [Arguments de valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME (ODBC 1.0)  
 Une chaîne de caractères avec le nom de serveur spécifique à la source de données réelle; utile lorsqu’un nom source de données est utilisé lors **de SQLConnect**, **SQLDriverConnect**, et **SQLBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2.0)  
 Une chaîne de caractères qui contient tous les caractères spéciaux (c’est-à-dire tous les caractères sauf un z, A à Z, 0 à 9, et souligner) qui peut être utilisé dans un nom d’identifiant, comme un nom de table, nom de colonne, ou un nom d’index, sur la source de données. Par exemple, « $ ». Si un identifiant contient un ou plusieurs de ces caractères, l’identifiant doit être un identifiant délimité.  
  
 SQL_SQL_CONFORMANCE (ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le niveau de SQL-92 supporté par le conducteur :  
  
 SQL_SC_SQL92_ENTRY - Niveau d’entrée SQL-92 conforme.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL - FIPS 127-2 niveau de transition conforme.  
  
 SQL_SC_SQL92_FULL - Niveau complet SQL-92 conforme.  
  
 SQL_SC_ SQL92_INTERMEDIATE - Niveau intermédiaire SQL-92 conforme.  
  
 SQL_SQL92_DATETIME_FUNCTIONS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les fonctions scalaires de date qui sont prises en charge par le conducteur et la source de données associée, tel que défini dans SQL-92.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles fonctions d’heure de date sont prises en charge :  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les règles prises en charge pour une clé étrangère dans une déclaration **DELETE,** telle que définie dans SQL-92.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge par la source de données :  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Un pilote conforme au niveau de transition FIPS retournera toujours toutes ces options en cas de soutien.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les règles prises en charge pour une clé étrangère dans une déclaration **UPDATE,** telle que définie dans SQL-92.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge par la source de données :  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Un conducteur SQL-92 Full level-conformant retournera toujours toutes ces options en cas de support.  
  
 SQL_SQL92_GRANT (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses appuyées dans la déclaration **GRANT,** telle que définie dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge par la source de données :  
  
 SQL_SG_DELETE_TABLE (niveau d’entrée) SQL_SG_INSERT_COLUMN (niveau intermédiaire) SQL_SG_INSERT_TABLE (niveau d’entrée) SQL_SG_REFERENCES_TABLE (niveau d’entrée) SQL_SG_REFERENCES_COLUMN (niveau d’entrée) SQL_SG_SELECT_TABLE (niveau d’entrée) SQL_SG_UPDATE_COLUMN (niveau d’entrée) SQL_SG_UPDATE_TABLE (niveau d’entrée) SQL_SG_USAGE_ON_DOMAIN (niveau transitoire FIPS) SQL_SG_USAGE_ON_CHARACTER_SET (niveau transitoire FIPS) SQL_SG_USAGE_ON_COLLATION (niveau de transition FIPS) SQL_SG_USAGE_ON_TRANSLATION SQL_SG_USAGE_ON_COLLATION (FIPS(niveau transitoire FIPS) SQL_SG_USAGE_ON_COLLATION (FIPS(niveau transitoire FIPS) SQL_SG_USAGE_ON_COLLATION (FIPS niveau) SQL_SG_WITH_GRANT_OPTION (niveau d’entrée)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les fonctions scalaires de valeur numérique qui sont prises en charge par le conducteur et la source de données associée, tel que défini dans SQL-92.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles fonctions numériques sont prises en charge :  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les prédicats pris en charge dans une déclaration **SELECT,** tel que défini dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles options sont prises en charge par la source de données :  
  
 SQL_SP_BETWEEN (niveau d’entrée) SQL_SP_COMPARISON (niveau d’entrée) SQL_SP_EXISTS (niveau d’entrée) SQL_SP_IN (niveau d’entrée) SQL_SP_ISNOTNULL (niveau d’entrée) SQL_SP_ISNULL (niveau d’entrée) SQL_SP_LIKE (niveau d’entrée) SQL_SP_MATCH_FULL (niveau complet) SQL_SP_MATCH_PARTIAL (niveau complet) SQL_SP_MATCH_UNIQUE_FULL (niveau complet) SQL_SP_MATCH_UNIQUE_PARTIAL (niveau complet) SQL_SP_OVERLAPS (niveau transitoire FIPS) SQL_SP_QUANTIFIED_COMPARISON (niveau d’entrée) SQL_SP_UNIQUE (niveau d’entrée)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les opérateurs relationnels de jointure soutenus dans une déclaration **DE SELECT,** tel que défini dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles options sont prises en charge par la source de données :  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (niveau intermédiaire) SQL_SRJO_CROSS_JOIN (niveau plein) SQL_SRJO_EXCEPT_JOIN (niveau intermédiaire) SQL_SRJO_FULL_OUTER_JOIN (niveau intermédiaire) SQL_SRJO_INNER_JOIN (niveau transitoire FIPS) SQL_SRJO_INTERSECT_JOIN (niveau intermédiaire) SQL_SRJO_LEFT_OUTER_JOIN (niveau transitoire FIPS) SQL_SRJO_NATURAL_JOIN (niveau transitoire FIPS) SQL_SRJO_RIGHT_OUTER_JOIN (niveau transitoire FIPS) SQL_SRJO_UNION_JOIN (niveau complet) (niveau de transition fiPS) SQL_SRJO_UNION_JOIN (niveau complet)  
  
 SQL_SRJO_INNER_JOIN indique le soutien à la syntaxe **INNER JOIN,** et non à la capacité de jointure intérieure. Le soutien à la syntaxe **INNER JOIN** est FIPS TRANSITIONAL, tandis que le soutien à la capacité de jointure interne est **ENTRY**.  
  
 SQL_SQL92_REVOKE (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses appuyées dans la déclaration **REVOKE,** telle que définie dans SQL-92, appuyée par la source de données.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge par la source de données :  
  
 SQL_SR_CASCADE (niveau transitoire FIPS) SQL_SR_DELETE_TABLE (niveau d’entrée) SQL_SR_GRANT_OPTION_FOR (niveau intermédiaire) SQL_SR_INSERT_COLUMN (niveau intermédiaire) SQL_SR_INSERT_TABLE (niveau d’entrée) SQL_SR_REFERENCES_COLUMN (niveau d’entrée) SQL_SR_REFERENCES_TABLE (niveau d’entrée) SQL_SR_RESTRICT (niveau transitoire FIPS) SQL_SR_SELECT_TABLE (niveau d’entrée) SQL_SR_UPDATE_COLUMN (niveau d’entrée) SQL_SR_UPDATE_TABLE (niveau d’entrée) SQL_SR_USAGE_ON_DOMAIN (niveau de transition FIPS) SQL_SR_USAGE_ON_CHARACTER_ SQL_SR_USAGE_ON_CHARACTER_ SET (niveau transitoire FIPS)SQL_SR_USAGE_ON_COLLATION (niveau transitoire FIPS) SQL_SR_USAGE_ON_TRANSLATION (niveau transitoire FIPS)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les expressions de constructeur de valeur de ligne prises en charge dans une déclaration **SELECT,** telle que définie dans SQL-92. Les bitmasks suivants sont utilisés pour déterminer quelles options sont prises en charge par la source de données :  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les fonctions scalaires de chaîne qui sont prises en charge par le conducteur et la source de données associée, tel que défini dans SQL-92.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles fonctions de chaîne sont prises en charge :  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les expressions de valeur supportées, telles que définies dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles options sont prises en charge par la source de données :  
  
 SQL_SVE_CASE (niveau intermédiaire) SQL_SVE_CAST (niveau transitoire FIPS) SQL_SVE_COALESCE (niveau intermédiaire) SQL_SVE_NULLIF (niveau intermédiaire)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant la norme CLI ou les normes auxquelles le conducteur se conforme. Les bitmasks suivants sont utilisés pour déterminer les niveaux auxquels le conducteur est conforme :  
  
 SQL_SCC_XOPEN_CLI_VERSION1 : Le pilote est conforme à la version CLI Open Group 1.  
  
 SQL_SCC_ISO92_CLI: Le conducteur se conforme à l’ISO 92 CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui décrit les attributs d’un curseur statique qui sont pris en charge par le conducteur. Ce bitmask contient le premier sous-ensemble d’attributs; pour le deuxième sous-ensemble, voir SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels attributs sont pris en charge :  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour les descriptions de ces bitmasks, voir SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (et remplacer le « curseur statique » par « curseur dynamique » dans les descriptions).  
  
 Un conducteur sqL-92 Intermediate level-conformant retournera habituellement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE comme pris en charge, parce que le conducteur prend en charge les curseurs défilants par l’intermédiaire de la déclaration SQL FETCH intégrée. Toutefois, comme cela ne détermine pas directement le support SQL sous-jacent, les curseurs défilementables peuvent ne pas être pris en charge, même pour un conducteur conforme au niveau intermédiaire SQL-92.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 Un bitmask SQLUINTEGER qui décrit les attributs d’un curseur statique qui sont pris en charge par le conducteur. Ce bitmask contient le deuxième sous-ensemble d’attributs; pour le premier sous-ensemble, voir SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels attributs sont pris en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Pour les descriptions de ces bitmasks, voir SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (et remplacer le « curseur statique » par « curseur dynamique » dans les descriptions).  
  
 SQL_STRING_FUNCTIONS (ODBC 1.0)  
 Remarque : Le type d’information a été introduit dans ODBC 1.0; chaque bitmask est étiqueté avec la version dans laquelle il a été introduit.  
  
 Un bitmask SQLUINTEGER énumérant les fonctions de chaîne scalaire supportées par le conducteur et la source de données associée.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles fonctions de chaîne sont prises en charge :  
  
 SQL_FN_STR_ASCII (ODBC 1.0)SQL_FN_STR_BIT_LENGTH (ODBC 3.0)SQL_FN_STR_CHAR (ODBC 1.0)SQL_FN_STR_CHAR_LENGTH (ODBC 3.0)SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0)SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 2.0)SQL_FN_STR_INSERT (ODBC 1.0)SQL_FN_STR_LCASE (ODBC 1.0)SQL_FN_STR_LEFT (ODBC 1.0)SQL_FN_STR_LENGTH (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC) SQL_FN_STR_LTRIM (ODBC) SQL_FN_STR_LTRIM (ODBC) 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0)SQL_FN_STR_REPEAT (ODBC 1.0)SQL_FN_STR_REPLACE (ODBC 1.0)SQL_FN_STR_RIGHT (ODBC 1.. 0) SQL_FN_STR_RTRIM (ODBC 1.0)SQL_FN_STR_SOUNDEX (ODBC 2.0)SQL_FN_STR_SPACE (ODBC 2.0)SQL_FN_STR_SUBSTRING (ODBC 1.0)SQL_FN_STR_UCASE (ODBC 1.0)  
  
 Si une application peut appeler la fonction scalaire **LOCATE** avec le *string_exp1,* *string_exp2*, et *commencer* les arguments, le conducteur retourne le SQL_FN_STR_LOCATE bitmask. Si une application peut appeler la fonction scalaire LOCATE avec seulement les *arguments string_exp1* et *string_exp2,* le conducteur retourne le SQL_FN_STR_LOCATE_2 le bitmask. Les conducteurs qui prennent pleinement en charge la fonction scalaire **LOCATE** retournent les deux bitmasks.  
  
 (Pour plus d’informations, voir [Fonctions de chaîne](../../../odbc/reference/appendixes/string-functions.md) à l’annexe E, "Scalar Functions.")  
  
 SQL_SUBQUERIES (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les prédicats qui soutiennent les sous-ques :  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Le SQL_SQ_CORRELATED_SUBQUERIES le bitmask indique que tous les prédicats qui soutiennent les sous-familles supportent les sous-ques corrélées.  
  
 Un pilote SQL-92 d’entrée de niveau-conformant retournera toujours un peu de masse dans lequel tous ces morceaux sont réglés.  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1.0)  
 Un bitmask SQLUINTEGER énumérant les fonctions du système scalaire supportées par le conducteur et la source de données associée.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles fonctions système sont prises en charge :  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1.0)  
 Une chaîne de caractères avec le nom du fournisseur de source de données pour une table; par exemple, "table" ou "fichier".  
  
 Cette chaîne de caractère peut être dans le cas supérieur, inférieur ou mélangé.  
  
 Un conducteur SQL-92 d’entrée conforme à la « table ».  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les intervalles d’humidité de temps soutenus par le conducteur et la source de données associée pour la fonction scalaire TIMESTAMPADD.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels intervalles sont pris en charge :  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Un pilote FIPS Transitional Level-conformant retournera toujours un peu de masse dans lequel tous ces bits sont réglés.  
  
 SQL_TIMEDATE_DIFF_INTERVALS(ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les intervalles d’humidité de temps soutenus par le conducteur et la source de données associée pour la fonction scalaire TIMESTAMPDIFF.  
  
 Les bitmasks suivants sont utilisés pour déterminer quels intervalles sont pris en charge :  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Un pilote FIPS Transitional Level-conformant retournera toujours un peu de masse dans lequel tous ces bits sont réglés.  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1.0)  
 Remarque : Le type d’information a été introduit dans ODBC 1.0; chaque bitmask est étiqueté avec la version dans laquelle il a été introduit.  
  
 Un bitmask SQLUINTEGER énumérant les fonctions de date et d’heure échaudées prises en charge par le conducteur et la source de données associée.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles fonctions de date et d’heure sont prises en charge :  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0)SQL_FN_TD_CURRENT_TIME (ODBC 3.0)SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0)SQL_FN_TD_CURDATE (ODBC 1.0)SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0)SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK (ODBC 1.0)SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 3.0)SQL_FN_TD_HOUR (ODBC 1.0)SQL_FN_TD_MINUTE (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTHNAME (ODBC 2.0)SQL_FN_TD_NOW (ODBC 1.0)SQL_FN_TD_QUARTER (ODBC 1.0)SQL_FN_TD_SECOND (ODBC 1.. 0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0)SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0)SQL_FN_TD_WEEK (ODBC 1.0)SQL_FN_TD_YEAR (ODBC 1.0)  
  
 SQL_TXN_CAPABLE (ODBC 1.0)  
 Remarque : Le type d’information a été introduit dans ODBC 1.0; chaque valeur de retour est étiquetée avec la version dans laquelle elle a été introduite.  
  
 Une valeur SQLUSMALLINT décrivant le support transactionnel dans le conducteur ou la source de données :  
  
 SQL_TC_NONE - Transactions non prises en charge. (ODBC 1.0)  
  
 SQL_TC_DML - Les transactions ne peuvent contenir que des relevés de langage de manipulation de données (DML) (**SELECT**, **INSERT**, **UPDATE**, **DELETE**). Les relevés de langage de définition des données (DDL) rencontrés dans une transaction causent une erreur. (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT - Les transactions ne peuvent contenir que des relevés DML. Les relevés DDL (**CREATE TABLE**, **DROP INDEX**, etc.) rencontrés dans une transaction entraînent l’engagement de la transaction. (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE - Les transactions ne peuvent contenir que des relevés DML. Les déclarations DDL rencontrées dans le cours d’une transaction sont ignorées. (ODBC 2.0)  
  
 SQL_TC_ALL - Les transactions peuvent contenir des relevés DDL et des relevés DML dans n’importe quel ordre. (ODBC 1.0)  
  
 (Étant donné que le soutien des transactions est obligatoire dans SQL-92, un conducteur conforme SQL-92 [n’importe quel niveau] ne reviendra jamais SQL_TC_NONE.)  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1.0)  
 Un bitmask SQLUINTEGER énumérant les niveaux d’isolement des transactions disponibles auprès du conducteur ou de la source de données.  
  
 Les bitmasks suivants sont utilisés avec le drapeau pour déterminer quelles options sont prises en charge :  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Pour les descriptions de ces niveaux d’isolement, voir la description de SQL_DEFAULT_TXN_ISOLATION.  
  
 Pour définir le niveau d’isolement des transactions, une application appelle **SQLSetConnectAttr** pour définir l’attribut SQL_ATTR_TXN_ISOLATION. Pour plus d’informations, voir [SQLSetConnectAttr Function](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Un conducteur SQL-92 d’entrée conforme à l’entrée retournera toujours SQL_TXN_SERIALIZABLE comme support. Un pilote conforme au niveau de transition FIPS retournera toujours toutes ces options en tant que prisées.  
  
 SQL_UNION (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant l’appui à la clause **UNION** :  
  
 SQL_U_UNION - La source de données prend en charge la clause **UNION.**  
  
 SQL_U_UNION_ALL - La source de données prend en charge **le MOT** clé TOUS dans la clause **UNION.** (**SQLGetInfo** renvoie à la fois SQL_U_UNION et SQL_U_UNION_ALL dans ce cas.)  
  
 Un pilote SQL-92 d’entrée conforme retournera toujours ces deux options en cas de support.  
  
 SQL_USER_NAME (ODBC 1.0)  
 Une chaîne de caractères avec le nom utilisé dans une base de données particulière, qui peut être différente du nom de connexion.  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3.0)  
 Une chaîne de caractères qui indique l’année de publication des spécifications Open Group avec lesquelles la version du Driver Manager ODBC se conforme pleinement.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 Une chaîne de caractères: "Y" si l’utilisateur peut exécuter toutes les procédures retournées par **SQLProcedures**; "N" s’il peut y avoir des procédures retournées que l’utilisateur ne peut pas exécuter.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Une chaîne de caractères : « Y » si l’utilisateur est garanti **privilèges SELECT** à toutes les tables retournées par **SQLTables**; "N" s’il peut y avoir des tables retournées que l’utilisateur ne peut pas accéder.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal d’environnements actifs que le conducteur peut supporter. S’il n’y a pas de limite spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant le support pour les fonctions d’agrégation :  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Un conducteur SQL-92 d’entrée conforme retournera toujours toutes ces options en cas de support.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **ALTER DOMAIN,** tel que défini dans SQL-92, étayé par la source de données. Un pilote SQL-92 Entièrement conforme au niveau retournera toujours tous les bitmasks. Une valeur de retour de « 0 » signifie que la déclaration **ALTER DOMAIN** n’est pas prise en charge.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT - L’ajout d’une contrainte de domaine est pris en charge (niveau complet)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT - \<modifier la clause de \<défaut de domaine> définie> est prise en charge (niveau complet)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION clause de \<définition de nom de contrainte> est pris en charge pour la contrainte de nommage de domaine (niveau intermédiaire)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT clause de \<contrainte de domaine de chute> est pris en charge (niveau complet)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT - \<modifier la clause \<de défaut de domaine> de laisser tomber> est pris en charge (niveau complet)  
  
 Les bits suivants \<spécifient les \<attributs de contrainte pris en charge> si ajouter la contrainte de domaine> est pris en charge (le bit SQL_AD_ADD_DOMAIN_CONSTRAINT est réglé):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 Un bitmask SQLUINTEGER énumérant les clauses de la déclaration **ALTER TABLE** appuyée par la source de données.  
  
 Le niveau de conformité SQL-92 ou FIPS auquel cette fonction doit être prise est indiqué entre parenthèses à côté de chaque bitmask.  
  
 Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_AT_ADD_COLUMN_COLLATION - \<ajouter la clause de> de colonne est prise en charge, avec la facilité de spécifier la collation de colonne (niveau complet) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT - \<ajouter la clause de> de colonne est prise en charge, avec la possibilité de spécifier les défauts de colonne (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE - \<ajouter la colonne> est pris en charge (niveau de transition FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT - \<ajouter la clause de> de colonne est prise en charge, avec la facilité de spécifier les contraintes de colonne (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT - \<ajouter la clause de contrainte de table> est soutenue (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION définition de \<nom de contrainte> est pris en charge pour nommer les contraintes de colonne et de table (niveau intermédiaire) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE - \<colonne de baisse> CASCADE est pris en charge (niveau de transition FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT - \<modifier la colonne \<> la clause par défaut de colonne de baisse> est pris en charge (niveau intermédiaire) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT - \<colonne de baisse> RESTRICT est pris en charge (niveau de transition FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT - \<colonne de baisse> RESTRICT est pris en charge (niveau de transition FIPS) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT - \<modifier la colonne \<> la clause par défaut de colonne définie> est prise en charge (niveau intermédiaire) (ODBC 3.0)  
  
 Les bits suivants \<spécifient les attributs de contrainte de support> si la spécification des contraintes de colonne ou de table est prise en charge (le SQL_AT_ADD_CONSTRAINT bit est réglé) :  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) (ODBC 3.0)SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (niveau complet) (ODBC 3.0)SQL_AT_CONSTRAINT_NON_DEFERRABLE (niveau complet) (ODBC 3.0)  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le niveau de soutien asynchrone chez le conducteur :  
  
 SQL_AM_CONNECTION - L’exécution asynchrone de niveau de connexion est soutenue. Soit toutes les poignées de déclaration associées à une poignée de connexion donnée sont en mode asynchrone ou tous sont en mode synchrone. Une poignée de déclaration sur une connexion ne peut pas être en mode asynchrone tandis qu’une autre poignée de déclaration sur la même connexion est en mode synchrone, et vice versa.  
  
 SQL_AM_STATEMENT - L’exécution asynchrone de niveau d’instruction est soutenue. Certaines poignées de déclaration associées à une poignée de connexion peuvent être en mode asynchrone, tandis que d’autres poignées de déclaration sur la même connexion sont en mode synchrone.  
  
 SQL_AM_NONE - Mode Asynchrone n’est pas pris en charge.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Un bitmask SQLUINTEGER énumérant le comportement du conducteur en ce qui concerne la disponibilité des dénombrements de rangées. Les bitmasks suivants sont utilisés avec le type d’information :  
  
 SQL_BRC_ROLLED_UP - Les comptes de ligne pour les relevés INSERT, DELETE ou UPDATE consécutifs sont regroupés en un seul. Si ce bit n’est pas réglé, les nombres de lignes sont disponibles pour chaque instruction.  
  
 SQL_BRC_PROCEDURES - Le nombre de rangées, le cas échéant, est disponible lorsqu’un lot est exécuté dans une procédure stockée. Si des nombres de rangées sont disponibles, ils peuvent être enroulés ou disponibles individuellement, selon le SQL_BRC_ROLLED_UP bit.  
  
 SQL_BRC_EXPLICIT - Le nombre de rangées, le cas échéant, est disponible lorsqu’un lot est exécuté directement en appelant **SQLExecute** ou **SQLExecDirect**. Si des nombres de rangées sont disponibles, ils peuvent être enroulés ou disponibles individuellement, selon le SQL_BRC_ROLLED_UP bit.  
  
## <a name="example"></a>Exemple  
 **SQLGetInfo** retourne des listes d’options prises en charge en tant que bitmask SQLUINTEGER dans*InfoValuePtr*. Le bitmask pour chaque option est utilisé avec le drapeau pour déterminer si l’option est prise en charge.  
  
 Par exemple, une application peut utiliser le code suivant pour déterminer si la fonction scalaire SUBSTRING est prise en charge par le conducteur associé à la connexion.  
  
 Pour un autre exemple d’utilisation **de SQLGetInfo**, voir [SQLTables Function](../../../odbc/reference/syntax/sqltables-function.md).  
  
```cpp  
SQLUINTEGER fFuncs;  
  
SQLGetInfo(hdbc,   
           SQL_STRING_FUNCTIONS,  
           (SQLPOINTER)&fFuncs,  
           sizeof(fFuncs),  
           NULL);  
  
// SUBSTRING supported  
if (fFuncs & SQL_FN_STR_SUBSTRING)   
   ;   // do something  
  
// SUBSTRING not supported  
else  
   ;   // do something else  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
 Retour du paramètre d’un attribut de connexion  
 [Fonction SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Déterminer si un conducteur prend en charge une fonction  
 [Fonction SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Retour du paramètre d’un attribut de déclaration  
 [Fonction SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Retour d’informations sur les types de données d’une source de données  
 [Fonction SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
