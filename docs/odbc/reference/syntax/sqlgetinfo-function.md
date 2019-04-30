---
title: SQLGetInfo, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0878b7c0d6e7cea6f1dcdc90fa7e78a2680546b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63132707"
---
# <a name="sqlgetinfo-function"></a>Fonction SQLGetInfo
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLGetInfo** retourne des informations générales sur la source de pilote et de données associée à une connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLGetInfo(  
     SQLHDBC         ConnectionHandle,  
     SQLUSMALLINT    InfoType,  
     SQLPOINTER      InfoValuePtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnectionHandle*  
 [Entrée] Handle de connexion.  
  
 *InfoType*  
 [Entrée] Type d’informations.  
  
 *InfoValuePtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner les informations. Selon le *InfoType* demandée, les informations retournées aura l’une des opérations suivantes : une chaîne de caractères se terminant par null, une valeur SQLUSMALLINT, un masque de bits SQLUINTEGER, un indicateur SQLUINTEGER, une valeur binaire SQLUINTEGER, ou un Valeur SQLULEN.  
  
 Si le *InfoType* argument est SQL_DRIVER_HDESC ou SQL_DRIVER_HSTMT, le *InfoValuePtr* argument est à la fois d’entrée et de sortie. (Voir les descripteurs SQL_DRIVER_HDESC ou SQL_DRIVER_HSTMT plus loin dans cette description de fonction pour plus d’informations.)  
  
 Si *InfoValuePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers laquelle pointée *InfoValuePtr*.  
  
 *BufferLength*  
 [Entrée] Longueur de la \* *InfoValuePtr* mémoire tampon. Si la valeur dans  *\*InfoValuePtr* n’est pas une chaîne de caractères ou si *InfoValuePtr* est un pointeur null, le *BufferLength* argument est ignoré. Le pilote part du principe que la taille de  *\*InfoValuePtr* est SQLUSMALLINT ou SQLUINTEGER, selon le *InfoType*. Si  *\*InfoValuePtr* est une chaîne Unicode (lors de l’appel **SQLGetInfoW**), la *BufferLength* argument doit être un nombre pair ; si non, SQLSTATE HY090 () Longueur de chaîne ou une mémoire tampon non valide) est retournée.  
  
 *StringLengthPtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total d’octets (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans **InfoValuePtr*.  
  
 Pour les données de caractères, si le nombre d’octets à retourner est supérieur ou égal à *BufferLength*, les informations contenues dans \* *InfoValuePtr* est tronqué à  *BufferLength* octets moins la longueur d’un caractère nul de terminaison de caractères et se termine par null par le pilote.  
  
 Pour tous les autres types de données, la valeur de *BufferLength* est ignoré et le pilote part du principe que la taille de \* *InfoValuePtr* est SQLUSMALLINT ou SQLUINTEGER, selon le  *InfoType*.  
  
## <a name="return-value"></a>Valeur de retour  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetInfo** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et un *gérer* de *ConnectionHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLGetInfo** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|La mémoire tampon \* *InfoValuePtr* n’est pas suffisamment grande pour retourner toutes les informations demandées. Par conséquent, les informations ont été tronquées. La longueur des informations demandées dans sa forme non tronqué est retournée dans **StringLengthPtr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) le type d’informations demandées dans *InfoType* nécessite une connexion ouverte. Les types d’informations réservés par ODBC, SQL_ODBC_VER uniquement peut être retournée sans une connexion ouverte.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer de la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY024|Valeur d’attribut non valide|(DM) le *InfoType* SQL_DRIVER_HSTMT a été l’argument et la valeur vers laquelle pointe *InfoValuePtr* n’était pas un descripteur d’instruction valide.<br /><br /> (DM) le *InfoType* SQL_DRIVER_HDESC a été l’argument et la valeur vers laquelle pointe *InfoValuePtr* n’était pas un handle de descripteur valide.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.<br /><br /> (DM) la valeur spécifiée pour *BufferLength* a un nombre impair, et  *\*InfoValuePtr* était d’un type de données Unicode.|  
|HY096|Type d’information hors limites|La valeur spécifiée pour l’argument *InfoType* n’était pas valide pour la version d’ODBC pris en charge par le pilote.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Champ facultatif non implémenté|La valeur spécifiée pour l’argument *InfoType* était une valeur spécifique au pilote qui n’est pas pris en charge par le pilote.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le pilote qui correspond à la *ConnectionHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Les types d’informations actuellement définies sont affichés dans les « Types d’informations » plus loin dans cette section. Il est probable que plusieurs seront définis pour tirer parti de différentes sources de données. Une plage de types d’informations est réservée par ODBC ; les développeurs de pilotes doivent réserver des valeurs pour leur propre usage spécifiques au pilote à partir d’Open Group. **SQLGetInfo** n’exécute aucune conversion Unicode ou *thunking* (consultez [annexe a : Codes d’erreur ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) de la *de référence du programmeur ODBC*) pour définis par le pilote *InfoTypes*. Pour plus d’informations, consultez [les Types de données spécifiques au pilote, Types de descripteurs, Types d’informations, Types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Le format des informations retournées dans \* *InfoValuePtr* varie selon le *InfoType* demandé. **SQLGetInfo** retournera les informations dans un des cinq formats différents :  
  
-   Une chaîne de caractères se terminant par null  
  
-   Une valeur SQLUSMALLINT  
  
-   Un masque de bits SQLUINTEGER  
  
-   Une valeur SQLUINTEGER  
  
-   Une valeur binaire SQLUINTEGER  
  
 Le format de chacun des types d’informations suivants est indiqué dans la description du type. L’application doit convertir la valeur renvoyée dans **InfoValuePtr* en conséquence. Pour obtenir un exemple de la façon dont une application peut récupérer des données à partir d’un masque de bits SQLUINTEGER, consultez « Exemple de Code ».  
  
 Un pilote doit retourner une valeur pour chaque type d’information qui est défini dans les tableaux suivants. Si un type d’information ne s’applique pas à la source de données ou le pilote, le pilote retourne une des valeurs répertoriées dans le tableau suivant.  
  
 Chaîne de caractères (« Y » ou « N »)  
 "N"  
  
 Chaîne de caractères (pas « Y » ou « N »)  
 Chaîne vide  
  
 SQLUSMALLINT  
 0  
  
 Masque de bits SQLUINTEGER ou valeur binaire SQLUINTEGER  
 0L  
  
 Par exemple, si une source de données ne prend pas en charge les procédures, **SQLGetInfo** retourne les valeurs répertoriées dans le tableau suivant pour les valeurs de *InfoType* qui sont liées à des procédures.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Chaîne vide  
  
 **SQLGetInfo** retourne SQLSTATE HY096 (valeur d’argument non valide) pour les valeurs de *InfoType* qui se trouvent dans la plage des types d’informations réservées pour une utilisation par ODBC, mais ne sont pas définis par la version d’ODBC pris en charge par le pilote. Pour déterminer quelle version d’ODBC un pilote est conforme à, une application appelle **SQLGetInfo** avec le type d’information SQL_DRIVER_ODBC_VER. **SQLGetInfo** retourne SQLSTATE HYC00 (fonctionnalité facultative non implémentée) pour les valeurs de *InfoType* qui se trouvent dans la plage des types d’informations réservées à une utilisation spécifique au pilote, mais ne sont pas pris en charge par le pilote.  
  
 Tous les appels à **SQLGetInfo** nécessitent une connexion ouverte, sauf quand le *InfoType* est SQL_ODBC_VER, qui retourne la version du Gestionnaire de pilotes.  
  
## <a name="information-types"></a>Types d’informations  
 Cette section répertorie les types d’informations pris en charge par **SQLGetInfo**. Types d’informations sont regroupées par catégories et par ordre alphabétique. Types d’informations qui ont été ajoutés ou renommés pour ODBC 3 *.x* sont également répertoriés.  
  
## <a name="driver-information"></a>Informations sur les pilotes  
 Les valeurs suivantes de la *InfoType* argument retourner des informations sur le pilote ODBC, telles que le nombre d’instructions actives, le nom de source de données et niveau de conformité aux normes de l’interface :  
  
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
>  Lors de l’implémentation **SQLGetInfo**, un pilote peut améliorer les performances en réduisant le nombre de fois où des informations sont envoyées ou demandées à partir du serveur.  
  
## <a name="dbms-product-information"></a>Informations sur les produits de SGBD  
 Les valeurs suivantes de la *InfoType* argument retourner des informations sur le produit du SGBD, telles que le nom du SGBD et la version :  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Informations de Source de données  
 Les valeurs suivantes de la *InfoType* argument retourner des informations sur la source de données, telles que des caractéristiques des curseurs et des fonctionnalités de transaction :  
  
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
  
## <a name="supported-sql"></a>SQL prises en charge  
 Les valeurs suivantes de la *InfoType* argument retourner des informations sur les instructions SQL pris en charge par la source de données. La syntaxe SQL de chaque fonctionnalité décrite par ces types d’informations est la syntaxe SQL-92. Ces types d’informations ne décrivent pas exhaustive de la totalité de la grammaire SQL-92. Au lieu de cela, ils décrivent les parties de la grammaire pour les données sources offrent généralement différents niveaux de prise en charge. Plus précisément, la plupart des instructions DDL dans SQL-92 couvertes.  
  
 Applications doivent déterminer le niveau général de grammaire pris en charge à partir du type d’informations SQL_SQL_CONFORMANCE et utiliser les autres types d’informations pour déterminer les variations à partir du niveau de conformité aux normes indiquées.  
  
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
  
## <a name="sql-limits"></a>Limites de SQL  
 Les valeurs suivantes de la *InfoType* argument retourner des informations sur les limites appliquées aux identificateurs et les clauses dans les instructions SQL, telles que les longueurs maximales des identificateurs d’et le nombre maximal de colonnes dans une liste de sélection. Limitations peuvent être imposées par le pilote ou la source de données.  
  
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
  
## <a name="scalar-function-information"></a>Informations sur les fonctions scalaires  
 Les valeurs suivantes de la *InfoType* argument retourner des informations sur les fonctions scalaires pris en charge par la source de données et le pilote. Pour plus d’informations sur les fonctions scalaires, consultez [annexe e : Fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Informations de conversion  
 Les valeurs suivantes de la *InfoType* argument retourner une liste des types de données SQL à laquelle la source de données peut convertir le type de données SQL spécifié avec le **convertir** fonction scalaire :  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>Types d’informations ajoutées pour ODBC 3.x  
 Les valeurs suivantes de la *InfoType* argument ont été ajoutés pour ODBC 3 *.x*:  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>Types d’informations renommés pour ODBC 3.x  
 Les valeurs suivantes de la *InfoType* argument ont été renommées pour ODBC 3 *.x*.  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Types d’informations déconseillées dans ODBC 3.x  
 Les valeurs suivantes de la *InfoType* argument ont été déconseillées dans ODBC 3 *.x*. ODBC 3 *.x* pilotes doivent continuer à prendre en charge ces types d’informations pour la compatibilité descendante avec ODBC 2 *.x* applications. (Pour plus d’informations sur ces types, consultez [prise en charge de SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md) dans g : annexe Pilote des instructions pour la compatibilité descendante.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Descriptions de types d’informations  
 Le tableau suivant répertorie par ordre alphabétique de chaque type d’information, la version d’ODBC dans lequel il a été introduit et sa description.  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 Une chaîne de caractères : « Y » si l’utilisateur peut exécuter toutes les procédures retournées par **SQLProcedures**; « N » s’il peut y avoir des procédures retournées que l’utilisateur ne peut pas exécuter.  
  
 SQL_ACCESSIBLE_TABLES(ODBC 1.0)  
 Une chaîne de caractères : « Y » si l’utilisateur est assuré **sélectionnez** des privilèges à toutes les tables retournées par **SQLTables**; « N » s’il peut y avoir des tables retournée que l’utilisateur ne peut pas accéder.  
  
 SQL_ACTIVE_ENVIRONMENTS(ODBC 3.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal d’environnements actifs que le pilote peut prendre en charge. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER l’énumération prise en charge des fonctions d’agrégation :  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Un pilote de conforme à niveau d’entrée SQL-92 toutes ces options retournera toujours pris en charge.  
  
 SQL_ALTER_DOMAIN(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **ALTER DOMAIN** instruction, comme défini dans SQL-92, pris en charge par la source de données. Un pilote de niveau compatible SQL-92 Full retournera toujours tous les masques de bits. Une valeur de retour de « 0 » signifie que le **ALTER DOMAIN** instruction n’est pas prise en charge.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = Ajout d’une contrainte de domaine est pris en charge (niveau total)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter domaine > \<ensemble domaine par défaut clause > est pris en charge (niveau total)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<clause de définition de contrainte name > est prise en charge pour la dénomination de contrainte de domaine (niveau intermédiaire)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<clause de contrainte de domaine drop > est pris en charge (niveau total)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter domaine > \<clause de suppression domaine par défaut > est pris en charge (niveau total)  
  
 Les bits suivantes spécifient la prise en charge \<les attributs de contrainte > Si \<ajouter une contrainte de domaine > est pris en charge (le bit SQL_AD_ADD_DOMAIN_CONSTRAINT est défini) :  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet)  
  
 SQL_ALTER_TABLE(ODBC 2.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **ALTER TABLE** instruction pris en charge par la source de données.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<AddColumn > clause est prise en charge, avec la fonctionnalité qui permet de spécifier le classement de colonne (niveau complet) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<AddColumn > clause est prise en charge, avec la fonctionnalité qui permet de spécifier les valeurs par défaut de la colonne (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<AddColumn > est pris en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<AddColumn > clause est prise en charge, avec la fonctionnalité qui permet de spécifier des contraintes de colonne (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<ajouter une contrainte de table > clause est prise en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<définition de nom de contrainte > est prise en charge pour la dénomination des contraintes de colonne et de table (niveau intermédiaire) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<supprimer la colonne > CASCADE est pris en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<de modifier la colonne > \<clause par défaut de column drop > est pris en charge (niveau intermédiaire) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<supprimer la colonne > RESTRICT est pris en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<supprimer la colonne > RESTRICT est pris en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<de modifier la colonne > \<jeu de colonnes par défaut clause > est pris en charge (niveau intermédiaire) (ODBC 3.0)  
  
 Les bits suivantes spécifient la prise en charge \<les attributs de contrainte > Si la spécification de contraintes de colonne ou une table est pris en charge (le bit SQL_AT_ADD_CONSTRAINT est défini) :  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (niveau complet) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 Une valeur SQLUINTEGER qui indique si le pilote peut exécuter des fonctions en mode asynchrone sur le handle de connexion.  
  
 SQL_ASYNC_DBC_CAPABLE = le pilote peut exécuter des fonctions de connexion de façon asynchrone.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = le pilote ne peut pas exécuter les fonctions de connexion de façon asynchrone.  
  
 SQL_ASYNC_MODE(ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le niveau de prise en charge asynchrone dans le pilote :  
  
 SQL_AM_CONNECTION = connexion d’exécution asynchrone au niveau est pris en charge. Tous les descripteurs d’instruction associées à un handle de connexion donné sont en mode asynchrone ou toutes sont en mode synchrone. Un descripteur d’instruction sur une connexion ne peut pas être en mode asynchrone alors que le handle d’une autre instruction sur la même connexion est en mode synchrone et vice versa.  
  
 SQL_AM_STATEMENT = l’instruction d’exécution asynchrone au niveau est pris en charge. Certains descripteurs d’instruction associées à un handle de connexion peuvent être en mode asynchrone, tandis que les autres descripteurs d’instruction sur la même connexion sont en mode synchrone.  
  
 SQL_AM_NONE = asynchrone mode n’est pas pris en charge.  
  
 SQL_ASYNC_NOTIFICATION  
 Une valeur SQLUINTEGER qui indique si le pilote prend en charge la notification asynchrone :  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** notification d’exécution asynchrone est prise en charge par le pilote.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** notification d’exécution asynchrone n’est pas pris en charge par le pilote.  
  
 Il existe deux catégories d’opérations asynchrones ODBC : les opérations asynchrones au niveau de connexion et d’instruction le niveau d’opérations asynchrones.  Si un pilote retourne SQL_ASYNC_NOTIFICATION_CAPABLE, il doit prendre en charge des notifications pour toutes les API qu’elle peut exécuter de façon asynchrone.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Masque de bits SQLUINTEGER qui énumère le comportement du pilote en ce qui concerne la disponibilité de la ligne de compte. Les masques de bits suivantes utilisées en conjonction avec le type d’informations :  
  
 SQL_BRC_ROLLED_UP = nombre de lignes pour les instructions INSERT, DELETE ou UPDATE consécutifs sont reportées en une seule. Si ce bit n’est pas défini, le nombre de lignes est disponibles pour chaque instruction.  
  
 SQL_BRC_PROCEDURES = nombre de lignes, si elles, sont disponibles lorsqu’un lot est exécuté dans une procédure stockée. Si le nombre de lignes est disponibles, elles peuvent être restaurées vers le haut ou individuellement disponibles, selon le bit SQL_BRC_ROLLED_UP.  
  
 SQL_BRC_EXPLICIT = nombre de lignes, si elles, sont disponibles lorsqu’un lot est exécuté directement en appelant **SQLExecute** ou **SQLExecDirect**. Si le nombre de lignes est disponibles, elles peuvent être restaurées vers le haut ou individuellement disponibles, selon le bit SQL_BRC_ROLLED_UP.  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 Un masque de bits SQLUINTEGER l’énumération prise en charge du pilote pour les lots. Les masques de bits suivants sont utilisés pour déterminer le niveau auquel est pris en charge :  
  
 SQL_BS_SELECT_EXPLICIT = pilote prend en charge explicite répertoriant les lots peuvent avoir-jeu de résultats génèrent des instructions.  
  
 SQL_BS_SELECT_PROC = pilote prend en charge explicite répertoriant les lots peuvent avoir des instructions de génération de nombre de lignes.  
  
 SQL_BS_SELECT_PROC = les pilote prend en charge explicite des procédures qui peuvent avoir-jeu de résultats génèrent des instructions.  
  
 Sql_bs_select_explicit = les pilote prend en charge explicite des procédures qui peuvent avoir des instructions de génération de nombre de lignes.  
  
 SQL_BOOKMARK_PERSISTENCE(ODBC 2.0)  
 Un masque de bits SQLUINTEGER énumérant les opérations par le biais duquel les signets persistent.  
  
 Les masques de bits suivantes permettent de déterminer par le biais duquel les signets d’options persistent avec l’indicateur :  
  
 SQL_BP_CLOSE = les signets sont valides après une application appelle **SQLFreeStmt** avec l’option SQL_CLOSE, ou **SQLCloseCursor** pour fermer le curseur associé à une instruction.  
  
 SQL_BP_DELETE = le signet pour une ligne est valide après cette ligne a été supprimée.  
  
 SQL_BP_DROP = les signets sont valides après une application appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT pour une instruction drop.  
  
 SQL_BP_TRANSACTION = les signets sont valides après une application valide ou restaure une transaction.  
  
 SQL_BP_UPDATE = le signet pour une ligne est valide après n’importe quelle colonne de cette ligne a été mis à jour, y compris les colonnes clés.  
  
 SQL_BP_OTHER_HSTMT = un signet associé à une instruction peut être utilisée avec une autre instruction. À moins que SQL_BP_CLOSE ou SQL_BP_DROP est spécifié, le curseur sur la première instruction doit être ouvert.  
  
 SQL_CATALOG_LOCATION(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui indique la position du catalogue dans un nom de table qualifié :  
  
 SQL_CL_STARTSQL_CL_END  
  
 Par exemple, un pilote Xbase retourne SQL_CL_START, car le nom du répertoire (catalogue) est au début du nom de table, comme dans \EMPDATA\EMP. DBF. Un pilote ORACLE Server retourne SQL_CL_END, car le catalogue est à la fin du nom de table, comme dans ADMIN.EMP@EMPDATA.  
  
 Un pilote conforme à niveau complète de SQL-92 retournera toujours SQL_CL_START. Une valeur de 0 est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_CATALOG_NAME.  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_QUALIFIER_LOCATION.  
  
 SQL_CATALOG_NAME(ODBC 3.0)  
 Une chaîne de caractères : « Y » si le serveur prend en charge les noms de catalogues, ou « N » si elle n’est pas le cas.  
  
 Un pilote conforme à niveau complète de SQL-92 retourne toujours « Y ».  
  
 SQL_CATALOG_NAME_SEPARATOR(ODBC 1.0)  
 Une chaîne de caractères : l’ou les caractères qui définit de la source de données comme séparateur entre un nom de catalogue et de l’élément de nom qualifié qui suit ou précède.  
  
 Une chaîne vide est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_CATALOG_NAME. Retourne toujours un pilote conforme à niveau complète de SQL-92 «. ».  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_QUALIFIER_NAME_SEPARATOR.  
  
 SQL_CATALOG_TERM(ODBC 1.0)  
 Une chaîne de caractères avec le nom du fournisseur de source de données pour un catalogue ; par exemple, « database » ou « directory ». Cette chaîne peut être dans le coin supérieur, inférieur ou les casses mixtes.  
  
 Une chaîne vide est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_CATALOG_NAME. Retourne toujours un pilote conforme à niveau complète de SQL-92 « catalog ».  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_QUALIFIER_TERM.  
  
 SQL_CATALOG_USAGE(ODBC 2.0)  
 Un masque de bits SQLUINTEGER énumérant les instructions dans lesquels les catalogues peuvent être utilisés.  
  
 Les masques de bits suivants sont utilisés pour déterminer où les catalogues peuvent être utilisés :  
  
 SQL_CU_DML_STATEMENTS = les catalogues sont pris en charge dans toutes les instructions de langage de Manipulation de données : **Sélectionnez**, **insérer**, **mettre à jour**, **supprimer**et si la prise en charge, **Sélectionnez pour mettre à jour** et positionné update et delete instructions.  
  
 SQL_CU_PROCEDURE_INVOCATION = les catalogues sont pris en charge dans l’instruction d’appel de procédure ODBC.  
  
 SQL_CU_TABLE_DEFINITION = les catalogues sont pris en charge dans toutes les instructions de définition de table : **CRÉER la TABLE**, **CREATE VIEW**, **ALTER TABLE**, **DROP TABLE**, et **DROP VIEW**.  
  
 SQL_CU_INDEX_DEFINITION = les catalogues sont pris en charge dans toutes les instructions de définition d’index : **CRÉER INDEX** et **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = les catalogues sont pris en charge dans toutes les instructions de définition de privilèges : **GRANT** et **RÉVOQUER**.  
  
 Une valeur de 0 est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_CATALOG_NAME. Un pilote conforme à niveau complète de SQL-92 retournent toujours un masque de bits avec toutes ces bits défini.  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_QUALIFIER_USAGE.  
  
 SQL_COLLATION_SEQ(ODBC 3.0)  
 Le nom de la séquence de classement. Il s’agit d’une chaîne de caractères qui indique le nom du classement par défaut pour le caractère par défaut définie pour ce serveur (par exemple, « EBCDIC ou ISO 8859-1'). Si c’est inconnu, une chaîne vide est retournée. Un pilote conforme à niveau complète de SQL-92 retourne toujours une chaîne non vide.  
  
 SQL_COLUMN_ALIAS(ODBC 2.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge les alias de colonne ; Sinon, « N ».  
  
 Un alias de colonne est un autre nom qui peut être spécifié pour une colonne dans la liste de sélection à l’aide d’une clause AS. Un pilote de conforme à niveau d’entrée SQL-92 retourne toujours « Y ».  
  
 SQL_CONCAT_NULL_BEHAVIOR(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui indique la façon dont la source de données gère la concaténation de NULL à valeurs de colonnes de type de données de caractères avec des colonnes de type caractère à valeurs non NULL :  
  
 SQL_CB_NULL = résultat est la valeur NULL de la table.  
  
 SQL_CB_NON_NULL = résultat est la concaténation d’ou des colonnes à valeurs non NULL.  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_ DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 Un masque de bits SQLUINTEGER. Le masque de bits indique les conversions prises en charge par la source de données avec le **convertir** fonction scalaire pour les données de type nommé dans le *InfoType*. Si le masque de bits est égal à zéro, la source de données ne prend pas en charge les conversions à partir des données de type nommé, notamment la conversion vers le même type de données.  
  
 Par exemple, pour déterminer si une source de données prend en charge la conversion de données SQL_INTEGER SQL_BIGINT type de données, une application appelle **SQLGetInfo** avec la *InfoType* de SQL_CONVERT_INTEGER. L’application effectue une **AND** opération avec le masque de bits retourné et SQL_CVT_BIGINT. Si la valeur résultante est différente de zéro, la conversion est prise en charge.  
  
 Les masques de bits suivants sont utilisés pour déterminer quelles conversions sont prises en charge :  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL SQL_CVT_ DE SQL_CVT_TIME (ODBC 1.0) _CVT_INTERVAL_YEAR_MONTH (ODBC 3.0) SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0) SQL_CVT_LONGVARBINARY (ODBC 1.0) SQL_CVT_LONGVARCHAR (ODBC 1.0) SQL_CVT_NUMERIC (ODBC 1.0) SQL_CVT_REAL ODBC 1.0) SQL_CVT_SMALLINT (ODBC 1.0) HORODATAGE (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS(ODBC 1.0)  
 Un masque de bits SQLUINTEGER énumérant les fonctions de conversion scalaires pris en charge par le pilote et de la source de données associée.  
  
 Le masque de bits suivant est utilisé pour déterminer les fonctions de conversion sont prises en charge :  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui indique si les noms de corrélation de table sont pris en charge :  
  
 SQL_CN_NONE = la corrélation de noms ne sont pas pris en charge.  
  
 SQL_CN_DIFFERENT = corrélation noms sont pris en charge mais doivent différer les noms des tables qu’ils représentent.  
  
 SQL_CN_ANY = corrélation noms sont pris en charge et peuvent être n’importe quel nom défini par l’utilisateur valid.  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours SQL_CN_ANY.  
  
 SQL_CREATE_ASSERTION(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **ASSERTION créer** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_CA_CREATE_ASSERTION  
  
 Bits suivants spécifient l’attribut de contrainte pris en charge la possibilité de spécifier explicitement les attributs de contrainte est pris en charge (voir les types d’informations SQL_ALTER_TABLE et SQL_CREATE_TABLE) :  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Un pilote conforme à niveau complète de SQL-92 toutes ces options retournera toujours pris en charge. Une valeur de retour de « 0 » signifie que le **ASSERTION créer** instruction n’est pas prise en charge.  
  
 SQL_CREATE_CHARACTER_SET(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **créer un jeu de caractères** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Un pilote conforme à niveau complète de SQL-92 toutes ces options retournera toujours pris en charge. Une valeur de retour de « 0 » signifie que le **créer un jeu de caractères** instruction n’est pas prise en charge.  
  
 SQL_CREATE_COLLATION(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **créer un classement** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de bits suivant est utilisé pour déterminer les clauses sont prises en charge :  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Un pilote conforme à niveau complète de SQL-92 retournera toujours cette option comme pris en charge. Une valeur de retour de « 0 » signifie que le **créer un classement** instruction n’est pas prise en charge.  
  
 SQL_CREATE_DOMAIN(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **créer un domaine** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_CDO_CREATE_DOMAIN = domaine de créer l’instruction est prise en charge (niveau intermédiaire).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<définition de nom de contrainte > est prise en charge pour la dénomination des contraintes des domaines (niveau intermédiaire).  
  
 Les bits suivantes spécifient la capacité de créer des contraintes de colonne : SQL_CDO_DEFAULT = spécification de contraintes de domaine est pris en charge (niveau intermédiaire) SQL_CDO_CONSTRAINT = spécifiant les valeurs par défaut du domaine est pris en charge (niveau intermédiaire) SQL_CDO_COLLATION = Spécification de classement de domaine est pris en charge (niveau total)  
  
 Les bits suivants spécifient les attributs de contrainte pris en charge si la spécification de contraintes de domaine est pris en charge (SQL_CDO_DEFAULT est défini) :  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (Full level)SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (Full level)SQL_CDO_CONSTRAINT_DEFERRABLE (Full level)SQL_CDO_CONSTRAINT_NON_DEFERRABLE (Full level)  
  
 Une valeur de retour de « 0 » signifie que le **créer un domaine** instruction n’est pas prise en charge.  
  
 SQL_CREATE_SCHEMA(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **CREATE SCHEMA** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Un pilote conforme de niveau intermédiaire SQL-92 retournera toujours les options SQL_CS_CREATE_SCHEMA et SQL_CS_AUTHORIZATION pris en charge. Ils doivent également être pris en charge le niveau d’entrée de SQL-92, mais pas nécessairement en tant qu’instructions SQL. Un pilote conforme à niveau complète de SQL-92 toutes ces options retournera toujours pris en charge.  
  
 SQL_CREATE_TABLE(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **CREATE TABLE** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_CT_CREATE_TABLE = TABLE de créer l’instruction est prise en charge. (Niveau d’entrée)  
  
 SQL_CT_TABLE_CONSTRAINT = spécifiant les contraintes de table est pris en charge (niveau transitoire FIPS)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = le \<définition de nom de contrainte > clause est prise en charge pour la dénomination des contraintes de colonne et de table (niveau intermédiaire)  
  
 Les bits suivantes spécifient la possibilité de créer des tables temporaires :  
  
 SQL_CT_COMMIT_PRESERVE = Deleted lignes sont conservées lors de la validation. (Niveau complet) SQL_CT_COMMIT_DELETE = Deleted lignes sont supprimées lors de la validation. (Niveau complet) SQL_CT_GLOBAL_TEMPORARY = Global des tables temporaires peuvent être créés. (Niveau complet) SQL_CT_LOCAL_TEMPORARY = Local tables temporaires peuvent être créés. (Niveau complet)  
  
 Les bits suivantes spécifient la possibilité de créer des contraintes de colonne :  
  
 SQL_CT_COLUMN_CONSTRAINT = spécifiant les contraintes de colonne est pris en charge (niveau transitoire FIPS) SQL_CT_COLUMN_DEFAULT = spécifiant les valeurs par défaut de la colonne est pris en charge (niveau transitoire FIPS) SQL_CT_COLUMN_COLLATION = la spécification de classement de colonne est prise en charge (niveau complet)  
  
 Les bits suivants spécifient les attributs de contrainte pris en charge si la spécification de contraintes de colonne ou une table est pris en charge :  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) SQL_CT_CONSTRAINT_DEFERRABLE (niveau complet) SQL_CT_CONSTRAINT_NON_DEFERRABLE (niveau complet)  
  
 SQL_CREATE_TRANSLATION(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **créer une traduction** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de bits suivant est utilisé pour déterminer les clauses sont prises en charge :  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Un pilote conforme à niveau complète de SQL-92 retournera toujours ces options pris en charge. Une valeur de retour de « 0 » signifie que le **créer une traduction** instruction n’est pas prise en charge.  
  
 SQL_CREATE_VIEW(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **CREATE VIEW** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Une valeur de retour de « 0 » signifie que le **CREATE VIEW** instruction n’est pas prise en charge.  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours les options SQL_CV_CREATE_VIEW et SQL_CV_CHECK_OPTION pris en charge.  
  
 Un pilote conforme à niveau complète de SQL-92 toutes ces options retournera toujours pris en charge.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui indique comment un **validation** opération affecte les curseurs et des instructions préparées dans la source de données (le comportement de la source de données lorsque vous validez une transaction).  
  
 La valeur de cet attribut reflète l’état actuel du paramètre suivant : SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = curseurs fermer et supprimer des instructions préparées. Pour utiliser le curseur là encore, l’application doit reprepare et redéfinir l’instruction.  
  
 SQL_CB_CLOSE = curseurs fermer. Pour les instructions préparées, l’application peut appeler **SQLExecute** sur l’instruction sans appeler **SQLPrepare** à nouveau. La valeur par défaut pour le pilote ODBC SQL est SQL_CB_CLOSE. Cela signifie que le pilote ODBC SQL se ferme votre ou les curseurs lorsque vous validez une transaction.  
  
 SQL_CB_PRESERVE = conserver les curseurs dans la même position comme avant la **valider** opération. L’application peut continuer à extraire des données, ou il peut fermer le curseur et ré-exécutez l’instruction sans ré-préparation.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui indique comment un **ROLLBACK** opération affecte les curseurs et des instructions préparées dans la source de données :  
  
 SQL_CB_DELETE = curseurs fermer et supprimer des instructions préparées. Pour utiliser le curseur là encore, l’application doit reprepare et redéfinir l’instruction.  
  
 SQL_CB_CLOSE = curseurs fermer. Pour les instructions préparées, l’application peut appeler **SQLExecute** sur l’instruction sans appeler **SQLPrepare** à nouveau.  
  
 SQL_CB_PRESERVE = conserver les curseurs dans la même position comme avant la **ROLLBACK** opération. L’application peut continuer à extraire des données, ou il peut fermer le curseur et redéfinir l’instruction sans repreparing il.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique la prise en charge pour la sensibilité du curseur :  
  
 SQL_INSENSITIVE = tous les curseurs sur instruction handle afficher le jeu de résultats sans montrer toutes les modifications qui lui ont été apportées par n’importe quel autre curseur dans la même transaction.  
  
 SQL_UNSPECIFIED = il n’est pas spécifié si les curseurs sur le descripteur d’instruction rendre visibles les modifications qui ont été apportées à un jeu de résultats par un autre curseur dans la même transaction. Les curseurs sur le descripteur d’instruction peuvent rendre visible à none, tout ou partie de ces modifications.  
  
 SQL_SENSITIVE = curseurs sont sensibles aux modifications qui ont été apportées par les autres curseurs dans la même transaction.  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournent toujours l’option SQL_UNSPECIFIED pris en charge.  
  
 Un pilote conforme à niveau complète de SQL-92 retournent toujours l’option SQL_INSENSITIVE pris en charge.  
  
 SQL_DATA_SOURCE_NAME(ODBC 1.0)  
 Une chaîne de caractères avec le nom de source de données qui a été utilisé lors de la connexion. Si l’application a appelé **SQLConnect**, c’est la valeur de la *szDSN* argument. Si l’application a appelé **SQLDriverConnect** ou **SQLBrowseConnect**, c’est la valeur du mot clé DSN dans la chaîne de connexion transmise au pilote. Si la chaîne de connexion ne contenait pas la **DSN** mot clé (par exemple lorsqu’il ne contient le **pilote** mot clé), il s’agit d’une chaîne vide.  
  
 SQL_DATA_SOURCE_READ_ONLY(ODBC 1.0)  
 Une chaîne de caractères. « Y » si la source de données est définie en mode lecture seule, « N » s’il s’agit dans le cas contraire.  
  
 Cette caractéristique se rapporte uniquement à la source de données ; Il n’est pas une caractéristique du pilote qui permet d’accéder à la source de données. Un pilote qui est en lecture/écriture peut être utilisé avec une source de données est en lecture seule. Si un pilote est en lecture seule, toutes ses sources de données doivent être en lecture seule et doivent retourner SQL_DATA_SOURCE_READ_ONLY.  
  
 SQL_DATABASE_NAME(ODBC 1.0)  
 Un caractère de chaîne avec le nom de la base de données actuelle en cours d’utilisation, si la source de données définit un objet nommé appelé « database ».  
  
> [!NOTE]
>  Dans ODBC 3 *.x*, la valeur retournée pour ce *InfoType* peut également être retourné en appelant **SQLGetConnectAttr** avec un *attribut* argument de SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les littéraux de date/heure SQL-92 pris en charge par la source de données. Notez que ceux-ci sont les littéraux de date/heure répertoriés dans la spécification SQL-92 et sont séparés des clauses d’échappement de littéral de date/heure définis par ODBC. Pour plus d’informations sur les clauses d’échappement ODBC le littéral de date/heure, consultez [Date, Time et Timestamp littéraux](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Un pilote de niveau conforme FIPS transitoire retourne toujours la valeur « 1 » dans le masque de bits pour les bits contenus dans la liste suivante. Valeur « 0 » signifie que les littéraux de date/heure SQL-92 ne sont pas pris en charge.  
  
 Les masques de bits suivants sont utilisés pour déterminer les littéraux sont pris en charge :  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_ SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME(ODBC 1.0)  
 Une chaîne de caractères avec le nom du produit SGBD accédé par le pilote.  
  
 SQL_DBMS_VER(ODBC 1.0)  
 Une chaîne de caractères qui indique la version du produit SGBD accédé par le pilote. La version est au format ##. ##. ###, où les deux premiers chiffres sont la version principale, les deux chiffres suivants à la version secondaire, et les quatre derniers chiffres sont la version release. Le pilote doit rendre la version du produit SGBD dans cet écran, mais peut également ajouter la version de produit spécifique de SGBD. Par exemple, « 04.01.0000 Rdb 4.1 ».  
  
 SQL_DDL_INDEX(ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique la prise en charge pour la création et suppression d’index :  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION(ODBC 1.0)  
 Une valeur SQLUINTEGER qui indique le niveau d’isolation de transaction par défaut pris en charge par la pilote ou source de données, ou zéro si la source de données ne prend pas en charge les transactions. Les termes suivants sont utilisés pour définir des niveaux d’isolation de transaction :  
  
 **Lecture erronée** 1 de la Transaction modifie une ligne. La transaction 2 lit la ligne modifiée avant que la transaction 1 valide la modification. Si la transaction 1 annule la modification, la transaction 2 ont lit une ligne qui est considéré comme n’ayant jamais existé.  
  
 **Lecture non renouvelable** 1 de la Transaction lit une ligne. La transaction 2 met à jour ou supprime cette ligne et cette modification est validée. Si la transaction 1 tente de relire la ligne, il recevra les valeurs de ligne différents ou découvrir que la ligne a été supprimée.  
  
 **Fantômes** 1 de la Transaction lit un ensemble de lignes qui répondent à certains critères de recherche. La transaction 2 génère une ou plusieurs lignes (via les insertions ou mises à jour) qui correspondent aux critères de recherche. Si la transaction 1 reexecutes l’instruction qui lit les lignes, il reçoit un autre ensemble de lignes.  
  
 Si la source de données prend en charge les transactions, le pilote retourne un des masques suivants :  
  
 SQL_TXN_READ_UNCOMMITTED = Dirty lectures, les lectures non reproductibles et les fantômes sont possibles.  
  
 SQL_TXN_READ_COMMITTED = Dirty lectures ne sont pas possibles. Fantômes et des lectures non reproductibles sont possibles.  
  
 SQL_TXN_REPEATABLE_READ = Dirty lectures et des lectures non reproductibles ne sont pas possibles. Les fantômes sont possibles.  
  
 SQL_TXN_SERIALIZABLE = Transactions sont sérialisables. Les transactions Serializable n’autorisent pas les lectures incorrectes, des lectures non reproductibles ou des fantômes.  
  
 SQL_DESCRIBE_PARAMETER(ODBC 3.0)  
 Une chaîne de caractères : « Y » si les paramètres peuvent être décrits ; « N » dans le cas contraire.  
  
 Un pilote conforme à niveau complète de SQL-92 retourne généralement « Y », car il prendra en charge la **DÉCRIVENT une entrée** instruction. Étant donné que cela ne spécifie pas directement de la prise en charge SQL sous-jacent, toutefois, décrivant les paramètres ne peut pas être pris en charge, même dans un pilote conforme à niveau complète de SQL-92.  
  
 SQL_DM_VER(ODBC 3.0)  
 Une chaîne de caractères avec la version du Gestionnaire de pilotes. La version est au format ##. ##. ###. ###, où :  
  
 Le premier jeu de deux chiffres est la version majeure de ODBC, comme indiqué par la constante SQL_SPEC_MAJOR.  
  
 Le deuxième ensemble de deux chiffres est la version secondaire de ODBC, comme indiqué par la constante SQL_SPEC_MINOR.  
  
 Le troisième ensemble de quatre chiffres est le numéro de build majeure du Gestionnaire de pilotes.  
  
 Le dernier jeu de quatre chiffres est le numéro de build mineure du Gestionnaire de pilotes.  
  
 La version de Windows 7 pilote Manager est 03.80. La version de Windows 8 pilote Manager est 03.81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 Une valeur SQLUINTEGER qui indique si le pilote prend en charge le regroupement prenant en charge de pilote. (Pour plus d’informations, consultez [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE indique que le pilote peut prendre en charge le mécanisme de regroupement pilote prenant en charge.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE indique que le pilote ne peut pas prendre en charge de mécanisme de regroupement pilote prenant en charge.  
  
 Un pilote n’a pas besoin d’implémenter SQL_DRIVER_AWARE_POOLING_SUPPORTED et le Gestionnaire de pilotes ne respecteront pas à la valeur de retour du pilote.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV(ODBC 1.0)  
 Une valeur SQLULEN du pilote handle d’environnement et/ou handle de connexion, déterminée par l’argument *InfoType*.  
  
 Ces types d’informations sont implémentées par le Gestionnaire de pilote uniquement.  
  
 SQL_DRIVER_HDESC(ODBC 3.0)  
 Handle de descripteur du pilote déterminé par le handle du descripteur du Gestionnaire de pilotes, qui doit être passée en entrée dans un SQLULEN valeur \* *InfoValuePtr* à partir de l’application. Dans ce cas, *InfoValuePtr* est un argument d’entrée et de sortie. Le handle de descripteur d’entrée transmis \* *InfoValuePtr* doit avoir été implicitement ou explicitement alloué sur le *ConnectionHandle*.  
  
 L’application doit faire une copie du descripteur du Gestionnaire de pilotes de gérer avant d’appeler **SQLGetInfo** avec ce type d’information, pour vous assurer que le handle n’est pas remplacé lors de la sortie.  
  
 Ce type d’information est implémenté par le Gestionnaire de pilote uniquement.  
  
 SQL_DRIVER_HLIB(ODBC 2.0)  
 Une valeur SQLULEN, le *hinst* à partir de la bibliothèque charge retourné pour le Gestionnaire de pilotes lorsqu’il chargé la DLL du pilote sur un système d’exploitation de Microsoft Windows, ou son équivalent sur un autre système d’exploitation. Le handle est valide uniquement pour le handle de connexion spécifié dans l’appel à **SQLGetInfo**.  
  
 Ce type d’information est implémenté par le Gestionnaire de pilote uniquement.  
  
 SQL_DRIVER_HSTMT(ODBC 1.0)  
 Descripteur d’instruction du pilote déterminé par le descripteur d’instruction de gestionnaire de pilotes, qui doit être passé en entrée dans un SQLULEN valeur \* *InfoValuePtr* à partir de l’application. Dans ce cas, *InfoValuePtr* est une entrée et un argument de sortie. Le descripteur d’instruction d’entrée transmis \* *InfoValuePtr* doit avoir été alloué sur l’argument *ConnectionHandle*.  
  
 L’application doit faire une copie de l’instruction du Gestionnaire de pilotes gérer avant d’appeler **SQLGetInfo** avec ce type d’information, pour vous assurer que le handle n’est pas remplacé lors de la sortie.  
  
 Ce type d’information est implémenté par le Gestionnaire de pilote uniquement.  
  
 SQL_DRIVER_NAME(ODBC 1.0)  
 Une chaîne de caractères avec le nom de fichier du pilote utilisé pour accéder à la source de données.  
  
 SQL_DRIVER_ODBC_VER(ODBC 2.0)  
 Une chaîne de caractères avec la version d’ODBC qui prend en charge par le pilote. La version est au format ##. ##, où les deux premiers chiffres sont la version principale et les deux chiffres suivants à la version mineure. SQL_SPEC_MAJOR et SQL_SPEC_MINOR définissent les numéros de version majeure et mineure. Pour la version d’ODBC, décrit dans ce manuel, il s’agit de 0 et 3, et le pilote doit retourner « 03.00 ».  
  
 Le Gestionnaire de pilotes ODBC ne modifiera pas la valeur de retour de SQLGetInfo(SQL_DRIVER_ODBC_VER) pour assurer la compatibilité descendante pour les applications existantes. Le pilote spécifie quelle valeur à retourner. Toutefois, un pilote qui prend en charge l’extensibilité du type de données C doit retourner 3,8 (ou version ultérieure) lorsqu’une application appelle **SQLSetEnvAttr** à la valeur SQL_ATTR_ODBC_VERSION 3.8. Pour plus d’informations, consultez [des Types de données C dans ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER(ODBC 1.0)  
 Une chaîne de caractères avec la version du pilote et éventuellement une description du pilote. Au minimum, la version est au format ##. ##. ###, où les deux premiers chiffres sont la version principale, les deux chiffres suivants à la version secondaire, et les quatre derniers chiffres sont la version release.  
  
 SQL_DROP_ASSERTION(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **ASSERTION DROP** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de bits suivant est utilisé pour déterminer les clauses sont prises en charge :  
  
 SQL_DA_DROP_ASSERTION  
  
 Un pilote conforme à niveau complète de SQL-92 retournera toujours cette option comme pris en charge.  
  
 SQL_DROP_CHARACTER_SET(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **supprimer le jeu de caractères** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de bits suivant est utilisé pour déterminer les clauses sont prises en charge :  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Un pilote conforme à niveau complète de SQL-92 retournera toujours cette option comme pris en charge.  
  
 SQL_DROP_COLLATION(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **classement DROP** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de bits suivant est utilisé pour déterminer les clauses sont prises en charge :  
  
 SQL_DC_DROP_COLLATION  
  
 Un pilote conforme à niveau complète de SQL-92 retournera toujours cette option comme pris en charge.  
  
 SQL_DROP_DOMAIN(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **DROP DOMAIN** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Un pilote conforme de niveau intermédiaire SQL-92 toutes ces options retournera toujours pris en charge.  
  
 SQL_DROP_SCHEMA(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **DROP SCHEMA** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Un pilote conforme de niveau intermédiaire SQL-92 toutes ces options retournera toujours pris en charge.  
  
 SQL_DROP_TABLE(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **DROP TABLE** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Un pilote de niveau conforme FIPS transitoire retourne toujours toutes ces options de prise en charge.  
  
 SQL_DROP_TRANSLATION(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **supprimer la traduction** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de bits suivant est utilisé pour déterminer les clauses sont prises en charge :  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Un pilote conforme à niveau complète de SQL-92 retournera toujours cette option comme pris en charge.  
  
 SQL_DROP_VIEW(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **DROP VIEW** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Un pilote de niveau conforme FIPS transitoire retourne toujours toutes ces options de prise en charge.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui décrit les attributs d’un curseur dynamique sont pris en charge par le pilote. Ce masque de bits contient le premier sous-ensemble d’attributs ; pour le deuxième sous-ensemble, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Les masques de bits suivants sont utilisés pour déterminer quels attributs sont prises en charge :  
  
 SQL_CA1_NEXT = A *FetchOrientation* argument de SQL_FETCH_NEXT est pris en charge dans un appel à **SQLFetchScroll** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_ABSOLUTE = *FetchOrientation* arguments de SQL_FETCH_FIRST, SQL_FETCH_LAST et SQL_FETCH_ABSOLUTE sont pris en charge dans un appel à **SQLFetchScroll** quand le curseur est un curseur dynamique. (L’ensemble de lignes qui est extraites est indépendante de la position actuelle du curseur.)  
  
 SQL_CA1_RELATIVE = *FetchOrientation* arguments de SQL_FETCH_PRIOR et SQL_FETCH_RELATIVE sont pris en charge dans un appel à **SQLFetchScroll** quand le curseur est un curseur dynamique. (L’ensemble de lignes qui est extraites dépend de la position actuelle du curseur. Notez que cela est séparée de SQL_FETCH_NEXT, car un curseur avant uniquement, SQL_FETCH_NEXT uniquement est pris en charge.)  
  
 SQL_CA1_BOOKMARK = A *FetchOrientation* argument de SQL_FETCH_BOOKMARK est pris en charge dans un appel à **SQLFetchScroll** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_EXCLUSIVE = A *LockType* argument de SQL_LOCK_EXCLUSIVE est pris en charge dans un appel à **SQLSetPos** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_NO_CHANGE = A *LockType* argument de SQL_LOCK_NO_CHANGE est pris en charge dans un appel à **SQLSetPos** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_UNLOCK = A *LockType* argument de SQL_LOCK_UNLOCK est pris en charge dans un appel à **SQLSetPos** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_POSITION = un *opération* argument de SQL_POSITION est pris en charge dans un appel à **SQLSetPos** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_UPDATE = un *opération* argument de SQL_UPDATE est pris en charge dans un appel à **SQLSetPos** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_DELETE = un *opération* argument de SQL_DELETE est pris en charge dans un appel à **SQLSetPos** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_REFRESH = un *opération* argument de SQL_REFRESH est pris en charge dans un appel à **SQLSetPos** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_POSITIONED_UPDATE = une mise à jour où actuelle de SQL instruction est prise en charge lorsque le curseur se trouve un curseur dynamique. (Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours cette option comme pris en charge.)  
  
 SQL_CA1_POSITIONED_DELETE = un DELETE où actuelle de SQL instruction est prise en charge lorsque le curseur se trouve un curseur dynamique. (Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours cette option comme pris en charge.)  
  
 SQL_CA1_SELECT_FOR_UPDATE = une instruction SELECT pour l’instruction SQL de mise à jour est prise en charge lorsque le curseur se trouve un curseur dynamique. (Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours cette option comme pris en charge.)  
  
 SQL_CA1_BULK_ADD = un *opération* argument de SQL_ADD est pris en charge dans un appel à **SQLBulkOperations** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = un *opération* argument de SQL_UPDATE_BY_BOOKMARK est pris en charge dans un appel à **SQLBulkOperations** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = un *opération* argument de SQL_DELETE_BY_BOOKMARK est pris en charge dans un appel à **SQLBulkOperations** quand le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = un *opération* argument de SQL_FETCH_BY_BOOKMARK est pris en charge dans un appel à **SQLBulkOperations** quand le curseur est un curseur dynamique.  
  
 Un pilote conforme de niveau intermédiaire SQL-92 retourne généralement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE pris en charge, car il prend en charge des curseurs avec défilement via l’instruction SQL FETCH incorporée. Étant donné que cela ne détermine pas directement de la prise en charge SQL sous-jacent, toutefois, curseurs avec défilement ne peuvent pas être pris en charge, même pour un pilote conforme de niveau intermédiaire SQL-92.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui décrit les attributs d’un curseur dynamique sont pris en charge par le pilote. Ce masque de bits contient le deuxième sous-ensemble d’attributs ; pour le premier sous-ensemble, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Les masques de bits suivants sont utilisés pour déterminer quels attributs sont prises en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = lecture seule curseur dynamique, dans lequel aucune mise à jour n’est autorisées, est pris en charge. (L’attribut d’instruction SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_READ_ONLY pour un curseur dynamique).  
  
 SQL_CA2_LOCK_CONCURRENCY = un curseur dynamique qui utilise le plus bas niveau de verrouillage pour vous assurer que la ligne peut être mis à jour est prise en charge. (L’attribut d’instruction SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_LOCK pour un curseur dynamique). Ces verrous doivent être cohérentes avec le niveau d’isolement de transaction défini par l’attribut de connexion de SQL_ATTR_TXN_ISOLATION.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = un curseur dynamique qu’utilise les versions de ligne comparaison du contrôle de l’accès concurrentiel optimiste est pris en charge. (L’attribut d’instruction SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_ROWVER pour un curseur dynamique).  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = un curseur dynamique qu’utilise les valeurs de comparaison de contrôle d’accès concurrentiel optimiste est pris en charge. (L’attribut d’instruction SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_VALUES pour un curseur dynamique).  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = Added lignes sont visibles pour un curseur dynamique ; le curseur peut défiler aux lignes. (Où ces lignes sont ajoutées au curseur dépend du pilote.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = Deleted lignes ne sont plus disponibles pour un curseur dynamique et ne laissez pas un « trou » dans le jeu de résultats ; une fois que le curseur dynamique fait défiler d’une ligne supprimée, elle ne peut pas retourner à cette ligne.  
  
 SQL_CA2_SENSITIVITY_UPDATES = mises à jour de lignes sont visibles pour un curseur dynamique ; Si le curseur dynamique défile à partir d’et renvoie à une ligne mise à jour, les données retournées par le curseur sont les données mises à jour, pas les données d’origine.  
  
 SQL_CA2_MAX_ROWS_SELECT = SQL_ATTR_MAX_ROWS l’instruction attribut affecte **sélectionnez** instructions lorsque le curseur se trouve un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_INSERT = SQL_ATTR_MAX_ROWS l’instruction attribut affecte **insérer** instructions lorsque le curseur se trouve un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_DELETE = SQL_ATTR_MAX_ROWS l’instruction attribut affecte **supprimer** instructions lorsque le curseur se trouve un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_UPDATE = SQL_ATTR_MAX_ROWS l’instruction attribut affecte **mise à jour** instructions lorsque le curseur se trouve un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_CATALOG = SQL_ATTR_MAX_ROWS l’instruction attribut affecte **catalogue** jeux de résultats lorsque le curseur se trouve un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = SQL_ATTR_MAX_ROWS l’instruction attribut affecte **sélectionnez**, **insérer**, **supprimer**, et **mise à jour** instructions, et **catalogue** jeux de résultats, lorsque le curseur se trouve un curseur dynamique.  
  
 SQL_CA2_CRC_EXACT = exactement le nombre de lignes est disponible dans le champ de diagnostic SQL_DIAG_CURSOR_ROW_COUNT lorsque le curseur se trouve un curseur dynamique.  
  
 SQL_CA2_CRC_APPROXIMATE = un nombre approximatif nombre de lignes est disponible dans le champ de diagnostic SQL_DIAG_CURSOR_ROW_COUNT lorsque le curseur se trouve un curseur dynamique.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = le pilote ne garantit pas simulant positionné mise à jour ou des instructions de suppression affecteront qu’une seule ligne lorsque le curseur se trouve un curseur dynamique ; Il est responsable de l’application pour garantir cela. (Si une instruction concerne plusieurs lignes, **SQLExecute** ou **SQLExecDirect** retourne SQLSTATE 01001 [conflit d’opération de curseur].) Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec la SQL_ATTR_SIMULATE_CURSOR attribut SQL_SC_NON_UNIQUE.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = le pilote tente de garantir qu’une mise à jour positionnée simulé ou des instructions delete affectera qu’une seule ligne lorsque le curseur se trouve un curseur dynamique. Le pilote exécute toujours ces instructions, même si elles peuvent affecter plusieurs lignes, par exemple quand il n’existe aucune clé unique. (Si une instruction concerne plusieurs lignes, **SQLExecute** ou **SQLExecDirect** retourne SQLSTATE 01001 [conflit d’opération de curseur].) Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec la SQL_ATTR_SIMULATE_CURSOR attribut SQL_SC_TRY_UNIQUE.  
  
 SQL_CA2_SIMULATE_UNIQUE = le pilote garantit que simulated positionné mise à jour ou des instructions de suppression affecteront qu’une seule ligne lorsque le curseur se trouve un curseur dynamique. Si le pilote ne peut pas garantir cela pour une instruction donnée, **SQLExecDirect** ou **SQLPrepare** retourne SQLSTATE 01001 (conflit d’opération de curseur). Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec la SQL_ATTR_SIMULATE_CURSOR attribut SQL_SC_UNIQUE.  
  
 SQL_EXPRESSIONS_IN_ORDERBY(ODBC 1.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge les expressions dans le **ORDER BY** liste ; « N » dans le cas contraire.  
  
 SQL_FILE_USAGE(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui indique la manière dont un pilote de niveau unique traite directement les fichiers dans une source de données :  
  
 SQL_FILE_NOT_SUPPORTED = le pilote n’est pas un pilote de niveau unique. Par exemple, un pilote ORACLE est un pilote à deux niveaux.  
  
 SQL_FILE_TABLE = fichiers traite monocouches pilote dans une source de données en tant que tables. Par exemple, un pilote Xbase traite chaque fichier Xbase sous forme de table.  
  
 SQL_FILE_CATALOG = un seul niveau pilote traite les fichiers dans une source de données en tant que catalogue. Par exemple, un pilote Microsoft Access traite chaque fichier Microsoft Access comme une base de données complète.  
  
 Une application peut utiliser cela pour déterminer la façon dont les utilisateurs sélectionnera les données. Par exemple, Xbase utilisateurs pensent souvent des données stockées dans des fichiers, tandis que les utilisateurs ORACLE et Microsoft Access pensent généralement de données tel que stocké dans les tables.  
  
 Lorsqu’un utilisateur sélectionne une source de données Xbase, l’application peut afficher le Windows **ouvrir le fichier** boîte de dialogue commune ; lorsque l’utilisateur sélectionne une source de données Microsoft Access ou ORACLE, l’application peut afficher un personnalisé  **Sélectionnez la Table** boîte de dialogue.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui décrit les attributs d’un curseur avant uniquement qui sont pris en charge par le pilote. Ce masque de bits contient le premier sous-ensemble d’attributs ; pour le deuxième sous-ensemble, consultez SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Les masques de bits suivants sont utilisés pour déterminer quels attributs sont prises en charge :  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_ UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (puis remplacez « curseur avant uniquement » pour « curseur dynamique » dans les descriptions).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui décrit les attributs d’un curseur avant uniquement qui sont pris en charge par le pilote. Ce masque de bits contient le deuxième sous-ensemble d’attributs ; pour le premier sous-ensemble, consultez SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Les masques de bits suivants sont utilisés pour déterminer quels attributs sont prises en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (puis remplacez « curseur avant uniquement » pour « curseur dynamique » dans les descriptions).  
  
 SQL_GETDATA_EXTENSIONS(ODBC 2.0)  
 Un masque de bits SQLUINTEGER l’énumération des extensions à **SQLGetData**.  
  
 Les masques de bits suivants sont utilisés avec l’indicateur pour déterminer quelles extensions courantes, le pilote prend en charge pour **SQLGetData**:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** peut être appelée pour toute colonne indépendante, y compris celles avant la dernière colonne dépendante. Notez que les colonnes doivent être appelées dans l’ordre de l’ordre croissant de numéro de colonne, sauf si SQL_GD_ANY_ORDER est également retourné.  
  
 SQL_GD_ANY_ORDER = **SQLGetData** peut être appelée pour les colonnes indépendantes dans n’importe quel ordre. Notez que **SQLGetData** peut être appelée uniquement pour les colonnes après la dernière colonne de dépendante, sauf si SQL_GD_ANY_COLUMN est également retourné.  
  
 SQL_GD_BLOCK = **SQLGetData** peut être appelée pour une colonne indépendante dans n’importe quelle ligne dans un bloc (où la taille de l’ensemble de lignes est supérieure à 1) de données après la position en cette ligne avec **SQLSetPos**.  
  
 SQL_GD_BOUND = **SQLGetData** peut être appelée pour les colonnes liées en plus des colonnes indépendantes. Un pilote ne peut pas retourner cette valeur, sauf si elle retourne également SQL_GD_ANY_COLUMN.  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData** peut être appelée pour retourner des valeurs de paramètre de sortie. Pour plus d’informations, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** est nécessaire pour retourner uniquement les données des colonnes indépendantes qui se produisent après la dernière colonne, dépendante sont appelés dans l’ordre croissant des numéros de colonne et ne sont pas dans une ligne dans un bloc de lignes.  
  
 Si un pilote prend en charge des signets (soit de longueur fixe ou de longueur variable), il doit prendre en charge l’appel **SQLGetData** sur la colonne 0. Cette prise en charge est requis indépendamment de ce que le pilote retourne pour un appel à **SQLGetInfo** avec la SQL_GETDATA_EXTENSIONS *InfoType*.  
  
 SQL_GROUP_BY(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie la relation entre les colonnes de la **GROUP BY** clause et les colonnes non regroupées en agrégats dans la liste de sélection :  
  
 SQL_GB_COLLATE = A **COLLATE** clause peut être spécifiée à la fin de chaque colonne de regroupement. (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY** clauses ne sont pas prises en charge. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = le **GROUP BY** clause doit contenir toutes les colonnes non regroupées en agrégats dans la liste de sélection. Il ne peut pas contenir toutes les autres colonnes. Par exemple, **sélectionnez DEPT, MAX(SALARY) d’employé GROUP BY DEPT**. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = le **GROUP BY** clause doit contenir toutes les colonnes non regroupées en agrégats dans la liste de sélection. Il peut contenir des colonnes qui ne sont pas dans la liste de sélection. Par exemple, **sélectionnez DEPT, MAX(SALARY) d’employé GROUP BY DEPT, l’ancienneté**. (ODBC 2.0)  
  
 SQL_GB_NO_RELATION = les colonnes dans le **GROUP BY** clause et la liste de sélection ne sont pas liées. La signification des colonnes nongrouped, non regroupées en agrégats dans la liste de sélection est dépend de la source de données. Par exemple, **sélectionnez DEPT, salaire d’employé GROUP BY DEPT, l’ancienneté**. (ODBC 2.0)  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournent toujours l’option SQL_GB_GROUP_BY_EQUALS_SELECT pris en charge. Un pilote conforme à niveau complète de SQL-92 retournent toujours l’option SQL_GB_COLLATE pris en charge. Si aucune option ne sont prise en charge, le **GROUP BY** clause n’est pas pris en charge par la source de données.  
  
 SQL_IDENTIFIER_CASE(ODBC 1.0)  
 Un SQLUSMALLINT valeur comme suit :  
  
 SQL_IC_UPPER = identificateurs dans SQL ne respectent pas la casse et sont stockés en majuscules dans le catalogue système.  
  
 SQL_IC_LOWER = identificateurs dans SQL ne respectent pas la casse et sont stockés en minuscules dans le catalogue système.  
  
 Sql_ic_sensitive en = identificateurs dans SQL respectent la casse et sont stockées dans une casse mixte dans le catalogue système.  
  
 Sql_ic_mixed en = identificateurs dans SQL ne respectent pas la casse et sont stockées dans une casse mixte dans le catalogue système.  
  
 Identificateurs dans SQL-92 ne respectent jamais la casse, un pilote qui respecte strictement SQL-92 (n’importe quel niveau) ne retourne jamais l’option sql_ic_sensitive en pris en charge.  
  
 SQL_IDENTIFIER_QUOTE_CHAR(ODBC 1.0)  
 La chaîne de caractères qui est utilisée comme délimiteur de début et de fin d’une entre guillemets (délimité) identificateur dans les instructions SQL. (Les identificateurs passés comme arguments aux fonctions ODBC n’ont pas à être mis entre guillemets.) Si la source de données ne prend pas en charge les identificateurs entre guillemets, une valeur vide est retournée.  
  
 Cette chaîne de caractères peut également être utilisée pour les arguments de fonction de catalogue lorsque l’attribut de connexion SQL_ATTR_METADATA_ID a la valeur SQL_TRUE.  
  
 Étant donné que le caractère de guillemet d’identificateur dans SQL-92 est le double guillemet («), un pilote compatible strictement à SQL-92 retourne toujours le caractère guillemet double.  
  
 SQL_INDEX_KEYWORDS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui énumère les mots clés dans l’instruction CREATE INDEX qui sont pris en charge par le pilote :  
  
 SQL_IK_NONE = aucun des mots clés est pris en charge.  
  
 SQL_IK_ASC = ASC mot clé est prise en charge.  
  
 SQL_IK_DESC = DESC mot clé est prise en charge.  
  
 SQL_IK_ALL = tous les mots clés sont pris en charge.  
  
 Pour voir si l’instruction CREATE INDEX est pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_DLL_INDEX.  
  
 SQL_INFO_SCHEMA_VIEWS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérer les vues de INFORMATION_SCHEMA qui sont pris en charge par le pilote. Les vues dans et le contenu de, INFORMATION_SCHEMA sont tel que défini dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer les vues sont prises en charge :  
  
 SQL_ISV_ASSERTIONS = identifie les assertions du catalogue qui sont détenues par un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_CHARACTER_SETS = identifie les jeux de caractères du catalogue qui sont accessibles par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_CHECK_CONSTRAINTS = identifie la vérification des contraintes qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_COLLATIONS = identifie les classements de caractères pour le catalogue qui sont accessibles par un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = identifie les colonnes pour le catalogue qui dépendent de domaines définis dans le catalogue et sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_COLUMN_PRIVILEGES = identifie les privilèges sur les colonnes de tables persistantes qui sont disponibles à ou accordés par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_COLUMNS = identifie les colonnes des tables persistantes qui sont accessibles par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = similaire à CONSTRAINT_TABLE_USAGE (vue), les colonnes sont identifiés pour les différentes contraintes qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = identifie les tables qui sont utilisées par les contraintes (référentielle, unique et les assertions) et sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = identifie les contraintes de domaine (des domaines dans le catalogue) qui sont accessibles par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_DOMAINS = identifie les domaines définis dans un catalogue qui sont accessibles par l’utilisateur. (Niveau intermédiaire)  
  
 SQL_ISV_KEY_COLUMN_USAGE = identifie les colonnes définies dans le catalogue qui sont limitées en tant que clés par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = identifie les contraintes référentielles qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_SCHEMATA = identifie les schémas qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_SQL_LANGUAGES = identifie les niveaux de conformité SQL, les options et les dialectes pris en charge par l’implémentation SQL. (Niveau intermédiaire)  
  
 SQL_ISV_TABLE_CONSTRAINTS = identifie les contraintes de table qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_TABLE_PRIVILEGES = identifie les privilèges sur les tables persistantes qui sont disponibles à ou accordés par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_TABLES = identifie les tables persistantes définies dans un catalogue qui sont accessibles par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_TRANSLATIONS = identifie les traductions de caractères pour le catalogue qui sont accessibles par un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_USAGE_PRIVILEGES = identifie l’utilisation des privilèges sur les objets de catalogue qui sont disponibles pour ou détenu par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = identifie les colonnes sur lequel les d’affichages catalogue qui sont détenues par un utilisateur donné sont dépendantes. (Niveau intermédiaire)  
  
 SQL_ISV_VIEW_TABLE_USAGE = identifie les tables sur laquelle les d’affichages catalogue qui sont détenues par un utilisateur donné sont dépendantes. (Niveau intermédiaire)  
  
 SQL_ISV_VIEWS = identifie les tables affichées définies dans ce catalogue qui sont accessibles par un utilisateur donné. (Niveau transitoire FIPS)  
  
 SQL_INSERT_STATEMENT(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui indique la prise en charge de **insérer** instructions :  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Un pilote de conforme à niveau d’entrée SQL-92 toutes ces options retournera toujours pris en charge.  
  
 SQL_INTEGRITY(ODBC 1.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge le Integrity Enhancement Facility ; « N » dans le cas contraire.  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_ODBC_SQL_OPT_IEF.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui décrit les attributs d’un curseur de jeu de clés qui sont prises en charge par le pilote. Ce masque de bits contient le premier sous-ensemble d’attributs ; pour le deuxième sous-ensemble, consultez SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Les masques de bits suivants sont utilisés pour déterminer quels attributs sont prises en charge :  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (puis remplacez « curseur » pour « curseur dynamique » dans les descriptions).  
  
 Un pilote conforme de niveau intermédiaire SQL-92 retourne généralement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE pris en charge, car le pilote prend en charge des curseurs avec défilement via l’instruction SQL FETCH incorporée. Étant donné que cela ne détermine pas directement de la prise en charge SQL sous-jacent, toutefois, curseurs avec défilement ne peuvent pas être pris en charge, même pour un pilote conforme de niveau intermédiaire SQL-92.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui décrit les attributs d’un curseur de jeu de clés qui sont prises en charge par le pilote. Ce masque de bits contient le deuxième sous-ensemble d’attributs ; pour le premier sous-ensemble, consultez SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Les masques de bits suivants sont utilisés pour déterminer quels attributs sont prises en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (puis remplacez « curseur » pour « curseur dynamique » dans les descriptions).  
  
 SQL_KEYWORDS(ODBC 2.0)  
 Une chaîne de caractères qui contient une liste séparée par des virgules de tous les mots clés spécifiques à la source de données. Cette liste ne contient pas de mots clés spécifiques à ODBC ou les mots clés utilisés par la source de données et ODBC. Cette liste représente tous les mots clés réservés ; applications interopérables ne devraient pas utiliser ces mots dans les noms d’objet.  
  
 Pour obtenir la liste de mots clés ODBC, consultez [mots clés réservés](../../../odbc/reference/appendixes/reserved-keywords.md) dans [annexe c : Grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Le **#define** valeur SQL_ODBC_KEYWORDS contient une liste séparée par des virgules des mots clés ODBC.  
  
 Annexe C : Grammaire SQL  
  
 SQL_LIKE_ESCAPE_CLAUSE(ODBC 2.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge un caractère d’échappement pour le caractère de pourcentage (%) et un trait de soulignement (_) de caractères dans un **comme** prédicat et le pilote prend en charge la syntaxe ODBC permettant de définir un **comme** prédicat caractère d’échappement ; « N » dans le cas contraire.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS(ODBC 3.0)  
 Une valeur SQLUINTEGER qui spécifie le nombre maximal d’instructions simultanées actives en mode asynchrone que le pilote peut prendre en charge sur une connexion donnée. S’il n’existe aucune limite spécifique ou la limite est inconnue, cette valeur est zéro.  
  
 SQL_MAX_BINARY_LITERAL_LEN(ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères hexadécimaux, en excluant le préfixe et le suffixe retourné par **SQLGetTypeInfo**) d’un littéral binaire dans une instruction SQL. Par exemple, le fichier binaire 0xFFAA littéral a une longueur de 4. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_CATALOG_NAME_LEN(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de catalogue dans la source de données. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS complète renvoie au moins 128.  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_MAX_QUALIFIER_NAME_LEN.  
  
 SQL_MAX_CHAR_LITERAL_LEN(ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères, ni le préfixe et le suffixe retourné par **SQLGetTypeInfo**) d’un caractère littéral dans une instruction SQL. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_COLUMN_NAME_LEN(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de colonne dans la source de données. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins égale à 18. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans un **GROUP BY** clause. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins 6. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 15.  
  
 SQL_MAX_COLUMNS_IN_INDEX(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans un index. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans un **ORDER BY** clause. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins 6. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 15.  
  
 SQL_MAX_COLUMNS_IN_SELECT(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisé dans une liste de sélection. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins 100. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 250.  
  
 SQL_MAX_COLUMNS_IN_TABLE(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisé dans une table. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins 100. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 250.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal d’instructions actives qui le pilote peut prendre en charge pour une connexion. Une instruction est définie comme actif s’il a des résultats en attente, avec les lignes de signification terme « résultats » à partir d’un **sélectionnez** opération ou lignes affectées par une **insérer**, **mise à jour**, ou **Supprimer** opération (par exemple, un nombre de lignes), ou si elle est dans un état NEED_DATA. Cette valeur peut refléter une limitation imposée par le pilote ou la source de données. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_ACTIVE_STATEMENTS.  
  
 SQL_MAX_CURSOR_NAME_LEN(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de curseur dans la source de données. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins égale à 18. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 128.  
  
 SQL_MAX_DRIVER_CONNECTIONS(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de connexions actives qui le pilote peut prendre en charge pour un environnement. Cette valeur peut refléter une limitation imposée par le pilote ou la source de données. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_ACTIVE_CONNECTIONS.  
  
 SQL_MAX_IDENTIFIER_LEN(ODBC 3.0)  
 SQLUSMALLINT qui indique la taille maximale en caractères qui prend en charge de la source de données pour les noms définis par l’utilisateur.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins égale à 18. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 128.  
  
 SQL_MAX_INDEX_SIZE(ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie le nombre maximal d’octets autorisés dans les champs combinés d’un index. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_PROCEDURE_NAME_LEN(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de procédure dans la source de données. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_ROW_SIZE(ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie la longueur maximale d’une ligne unique dans une table. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins de 2 000. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 8 000.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG(ODBC 3.0)  
 Une chaîne de caractères : « Y » si la taille maximale des lignes retournées pour le type d’information SQL_MAX_ROW_SIZE inclut la longueur des colonnes de toutes les SQL_LONGVARCHAR et SQL_LONGVARBINARY dans la ligne ; « N » dans le cas contraire.  
  
 SQL_MAX_SCHEMA_NAME_LEN(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de schéma dans la source de données. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins égale à 18. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 128.  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_MAX_OWNER_NAME_LEN.  
  
 SQL_MAX_STATEMENT_LEN(ODBC 2.0)  
 Une valeur SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères, y compris un espace blanc) d’une instruction SQL. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_TABLE_NAME_LEN(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de table dans la source de données. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins égale à 18. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 128.  
  
 SQL_MAX_TABLES_IN_SELECT(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal de tables autorisées dans le **FROM** clause d’une **sélectionnez** instruction. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote de niveau-conforme FIPS entrée retourne au moins 15. Un pilote de niveau-conforme FIPS intermédiaire renvoie au moins 50.  
  
 SQL_MAX_USER_NAME_LEN(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom d’utilisateur dans la source de données. S’il n’existe aucune longueur maximale ou la longueur est inconnue, cette valeur est définie à zéro.  
  
 SQL_MULT_RESULT_SETS(ODBC 1.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge plusieurs jeux de résultats, « N » si elle n’est pas le cas.  
  
 Pour plus d’informations sur plusieurs jeux de résultats, consultez [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN(ODBC 1.0)  
 Une chaîne de caractères : « Y » si le pilote ne prend en charge plus de transactions actives en même temps, « N » si une seule transaction peut être active à tout moment.  
  
 Les informations retournées pour ce type d’information ne s’applique pas dans le cas des transactions distribuées.  
  
 SQL_NEED_LONG_DATA_LEN(ODBC 2.0)  
 Une chaîne de caractères : Si elle n’est pas le cas, « Y » si la source de données a besoin de la longueur d’une valeur de données de type long (le type de données est SQL_LONGVARCHAR, SQL_LONGVARBINARY ou un type de données spécifiques à la source de données de type long) avant cette valeur est envoyée à la source de données, « N ». Pour plus d’informations, consultez [SQLBindParameter, fonction](../../../odbc/reference/syntax/sqlbindparameter-function.md) et [SQLSetPos, fonction](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS(ODBC 1.0)  
 Une valeur SQLUSMALLINT qui spécifie si la source de données prend en charge pas de valeur NULL dans les colonnes :  
  
 SQL_NNC_NULL = toutes les colonnes doivent être nullables.  
  
 SQL_NNC_NON_NULL = colonnes ne peut pas être nullables. (La source de données prend en charge la **pas NULL** contrainte de colonne dans **CREATE TABLE** instructions.)  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournera SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION(ODBC 2.0)  
 Une valeur SQLUSMALLINT qui spécifie où les valeurs NULL sont triées dans un jeu de résultats :  
  
 SQL_NC_END = les valeurs NULL sont triées à la fin du jeu de résultats, quel que soit les mots clés ASC ou DESC.  
  
 SQL_NC_HIGH = les valeurs NULL sont triées dans la partie supérieure du jeu de résultats, selon les mots clés ASC ou DESC.  
  
 SQL_NC_LOW = les valeurs NULL sont triées dans la partie inférieure du jeu de résultats, selon les mots clés ASC ou DESC.  
  
 SQL_NC_START = les valeurs NULL sont triées au début du jeu de résultats, quel que soit les mots clés ASC ou DESC.  
  
 SQL_NUMERIC_FUNCTIONS(ODBC 1.0)  
 Remarque : Le type d’informations a été introduit dans ODBC 1.0 ; chaque masque de bits est étiquetée avec la version dans laquelle il a été introduite.  
  
 Un masque de bits SQLUINTEGER énumérant les fonctions numériques scalaires pris en charge par le pilote et de la source de données associée.  
  
 Les masques de bits suivants sont utilisés pour déterminer les fonctions numériques sont prises en charge :  
  
 SQL_FN_NUM_ABS (ODBC 1.0) SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 SQL_ SQL_FN_NUM_DEGREES (ODBC 2.0) DE (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COT (ODBC 1.0) FN_NUM_EXP (ODBC 1.0) SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (ODBC 1.0) SQL_FN_NUM_LOG10 SQL_FN_ SQL_FN_NUM_RAND (ODBC 1.0) DE (ODBC 2.0) SQL_FN_NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) NUM_ROUND (ODBC 2.0) SQL_FN_NUM_SIGN (ODBC 1.0) SQL_FN_NUM_SIN (ODBC 1.0) SQL_FN_NUM_SQRT (ODBC 1.0) SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE(ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le niveau de 3 ODBC *.x* interface le pilote est conforme à.  
  
 SQL_OIC_CORE: Le niveau minimal qui sont tous les pilotes ODBC doit se conformer. Ce niveau comprend les éléments d’interface de base telles que les fonctions de connexion, fonctions pour la préparation et l’exécution d’une instruction SQL, fonctions de métadonnées de jeu de résultats de base, les fonctions de catalogue de base et ainsi de suite.  
  
 SQL_OIC_LEVEL1 : Un niveau, y compris les principales fonctionnalités de niveau de conformité aux normes, ainsi que des curseurs avec défilement, signets, positionnés met à jour et supprime et ainsi de suite.  
  
 SQL_OIC_LEVEL2 EN : Un niveau de fonctionnalités au niveau de conformité de normes niveau 1, ainsi que des fonctionnalités avancées telles que les curseurs sensibles ; mettre à jour, supprimer et actualiser les signets. prise en charge de la procédure stockée ; fonctions de catalogue pour les clés primaires et étrangères ; prise en charge du catalogue multi ; et ainsi de suite.  
  
 Pour plus d’informations, consultez [les niveaux de conformité Interface](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 SQL_ODBC_VER(ODBC 1.0)  
 Une chaîne de caractères avec la version d’ODBC à laquelle le Gestionnaire de pilotes se conforme. La version est au format ##. ##. 0000, où les deux premiers chiffres sont la version principale et les deux chiffres suivants à la version mineure. Cela est implémentée uniquement dans le Gestionnaire de pilotes.  
  
 SQL_OJ_CAPABILITIES(ODBC 2.01)  
 Un masque de bits SQLUINTEGER énumérer les types de jointures externes pris en charge par la source de données et de pilote. Les masques de bits suivants sont utilisés pour déterminer quels types sont pris en charge :  
  
 SQL_OJ_LEFT = gauche jointures externes sont pris en charge.  
  
 SQL_OJ_RIGHT = Right jointures externes sont pris en charge.  
  
 SQL_OJ_FULL = Full jointures externes sont pris en charge.  
  
 SQL_OJ_NESTED = Nested jointures externes sont pris en charge.  
  
 SQL_OJ_NOT_ORDERED = la colonne de noms dans la clause ON de la jointure externe n’ont pas à se trouver dans le même ordre que leurs noms de table concernée dans le **jointure externe** clause.  
  
 SQL_OJ_INNER = interne table (la table de droite dans une jointure externe gauche) ou de la table de gauche dans une jointure externe droite peut également être utilisée dans une jointure interne. Cela ne concerne pas les jointures externes entières, ce qui n’ont pas d’une table interne.  
  
 SQL_OJ_ALL_COMPARISON_OPS = la comparaison opérateur dans la clause ON peut être un des opérateurs de comparaison ODBC. Si ce bit n’est pas défini, seul l’opérateur de comparaison égal à (=) peut être utilisé dans les jointures externes.  
  
 Si aucune de ces options n’est retournée comme pris en charge, aucune clause de jointure externe n’est prise en charge.  
  
 Pour plus d’informations sur la prise en charge des opérateurs de jointure relationnelle dans une instruction SELECT, comme défini par SQL-92, consultez SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT(ODBC 2.0)  
 Une chaîne de caractères : « Y » si les colonnes dans le **ORDER BY** clause doit être dans la liste de sélection ; sinon, « N ».  
  
 SQL_PARAM_ARRAY_ROW_COUNTS(ODBC 3.0)  
 Une énumération des propriétés du pilote concernant la disponibilité de la ligne SQLUINTEGER compte dans une exécution paramétrable. A les valeurs suivantes :  
  
 SQL_PARC_BATCH = individuel des nombres de lignes sont disponibles pour chaque jeu de paramètres. Conceptuellement, cela équivaut à la génération d’un lot d’instructions SQL, une pour chaque paramètre défini dans le tableau de pilote. Informations d’erreur étendues peuvent être récupérées en utilisant le champ de descripteur SQL_PARAM_STATUS_PTR.  
  
 SQL_PARC_NO_BATCH ne = qu’une seule ligne le nombre est disponible, c'est-à-dire le nombre de lignes cumulative résultant de l’exécution de l’instruction pour l’intégralité du tableau de paramètres. Conceptuellement, cela équivaut à traiter l’instruction avec le tableau de paramètres complet en tant qu’unité atomique unique. Les erreurs sont gérés comme si une instruction ont été exécutée.  
  
 SQL_PARAM_ARRAY_SELECTS(ODBC 3.0)  
 Une énumération des propriétés du pilote concernant la disponibilité du résultat SQLUINTEGER définit dans une exécution paramétrable. A les valeurs suivantes :  
  
 SQL_PAS_BATCH = il existe un jeu de résultats disponible par le jeu de paramètres. Conceptuellement, cela équivaut à la génération d’un lot d’instructions SQL, une pour chaque paramètre défini dans le tableau de pilote.  
  
 SQL_PAS_NO_BATCH = il n'est qu’un seul jeu de résultats disponible, ce qui représente le résultat cumulé jeu résultant de l’exécution de l’instruction pour le tableau complet des paramètres. Conceptuellement, cela équivaut à traiter l’instruction avec le tableau de paramètres complet en tant qu’unité atomique unique.  
  
 SQL_PAS_NO_SELECT = un pilote n’autorise pas une instruction de génération de jeu de résultats doit être exécuté avec un tableau de paramètres.  
  
 SQL_PROCEDURE_TERM(ODBC 1.0)  
 Une chaîne de caractères avec le nom du fournisseur de source de données d’une procédure ; par exemple, « procédure de base de données », « procédure stockée », « procédure », « package » ou « requête stockée ».  
  
 SQL_PROCEDURES(ODBC 1.0)  
 Une chaîne de caractères : « Y » si la source de données prend en charge les procédures et le pilote prend en charge la syntaxe d’appel de procédure ODBC ; « N » dans le cas contraire.  
  
 SQL_POS_OPERATIONS(ODBC 2.0)  
 Un masque de bits SQLINTEGER énumérant les opérations de prise en charge dans **SQLSetPos**.  
  
 Les masques de bits suivantes sont utilisées avec l’indicateur pour déterminer quelles options sont prises en charge.  
  
 SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE(ODBC 2.0)  
 Un SQLUSMALLINT valeur comme suit :  
  
 SQL_IC_UPPER = entre guillemets les identificateurs dans SQL ne respectent pas la casse et sont stockés dans majuscules dans le catalogue système.  
  
 SQL_IC_LOWER = entre guillemets les identificateurs dans SQL ne respectent pas la casse et sont stockés en minuscules dans le catalogue système.  
  
 Sql_ic_sensitive en = entre guillemets les identificateurs dans SQL respectent la casse et sont stockées dans une casse mixte dans le catalogue système. (Dans une base de données compatibles avec SQL-92, les identificateurs entre guillemets sont toujours la casse.)  
  
 Sql_ic_mixed en = entre guillemets les identificateurs dans SQL ne respectent pas la casse et sont stockées dans une casse mixte dans le catalogue système.  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours sql_ic_sensitive en.  
  
 SQL_ROW_UPDATES(ODBC 1.0)  
 Une chaîne de caractères : « Y » si un curseur commandé par keyset ou mixte gère les versions de ligne ou de valeurs pour toutes les extraire des lignes et par conséquent peut détecter les mises à jour qui ont été apportées à une ligne par n’importe quel utilisateur depuis la dernière extraction de la ligne. (S’applique uniquement aux mises à jour, pas suppressions ou insertions). Le pilote peut retourner l’indicateur SQL_ROW_UPDATED à l’état de la ligne de tableau quand **SQLFetchScroll** est appelée. Sinon, « N ».  
  
 SQL_SCHEMA_TERM(ODBC 1.0)  
 Une chaîne de caractères avec le nom du fournisseur de source de données pour un schéma ; par exemple, « propriétaire », « ID d’autorisation » ou « Schema ».  
  
 La chaîne de caractères peut être retournée dans supérieure, inférieure ou les casses mixtes.  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retourne toujours « schema ».  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_OWNER_TERM.  
  
 SQL_SCHEMA_USAGE(ODBC 2.0)  
 Un masque de bits SQLUINTEGER énumérant les instructions dans lequel les schémas peuvent être utilisés :  
  
 SQL_SU_DML_STATEMENTS = schémas sont pris en charge dans toutes les instructions de langage de Manipulation de données : **Sélectionnez**, **insérer**, **mettre à jour**, **supprimer**et si la prise en charge, **Sélectionnez pour mettre à jour** et positionné update et delete instructions.  
  
 SQL_SU_PROCEDURE_INVOCATION = schémas sont pris en charge dans l’instruction d’appel de procédure ODBC.  
  
 SQL_SU_TABLE_DEFINITION = schémas sont pris en charge dans toutes les instructions de définition de table : **CRÉER la TABLE**, **CREATE VIEW**, **ALTER TABLE**, **DROP TABLE**, et **DROP VIEW**.  
  
 SQL_SU_INDEX_DEFINITION = schémas sont pris en charge dans toutes les instructions de définition d’index : **CRÉER INDEX** et **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = schémas sont pris en charge dans toutes les instructions de définition de privilèges : **GRANT** et **RÉVOQUER**.  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours les options SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION et SQL_SU_PRIVILEGE_DEFINITION, pris en charge.  
  
 Cela *InfoType* a été renommé pour ODBC 3.0 à partir de l’interface ODBC 2.0 *InfoType* SQL_OWNER_USAGE.  
  
 SQL_SCROLL_OPTIONS(ODBC 1.0)  
 Remarque : Le type d’informations a été introduit dans ODBC 1.0 ; chaque masque de bits est étiquetée avec la version dans laquelle il a été introduite.  
  
 Un masque de bits SQLUINTEGER énumérant les options de défilement pris en charge pour les curseurs avec défilement.  
  
 Les masques de bits suivants sont utilisés pour déterminer quelles options sont prises en charge :  
  
 SQL_SO_FORWARD_ONLY = le curseur uniquement fait défiler vers l’avant. (ODBC 1.0)  
  
 SQL_SO_STATIC = les données dans le résultat de l’ensemble est statique. (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN = le pilote enregistre et utilise les clés pour chaque ligne du jeu de résultats. (ODBC 1.0)  
  
 SQL_SO_DYNAMIC = le pilote conserve les clés pour chaque ligne dans l’ensemble de lignes (la taille du jeu de clés est identique à la taille de l’ensemble de lignes). (ODBC 1.0)  
  
 SQL_SO_MIXED = le pilote de conserve les clés pour chaque ligne dans le jeu de clés et la taille de jeu de clés est supérieure à la taille de l’ensemble de lignes. Le curseur est dynamique en dehors du jeu de clés et curseurs pilotés par dans le jeu de clés. (ODBC 1.0)  
  
 Pour plus d’informations sur les curseurs avec défilement, consultez [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE(ODBC 1.0)  
 Une chaîne de caractères spécifiant que le pilote prend en charge comme caractère d’échappement qui autorise l’utilisation du modèle correspondance métacaractères un trait de soulignement (_) et le signe de pourcentage (%) comme les caractères valides dans les modèles de recherche. Ce caractère d’échappement s’applique uniquement à ces arguments de fonction de catalogue qui prennent en charge les chaînes de recherche. Si cette chaîne est vide, le pilote ne prend pas en charge un caractère d’échappement de modèle de recherche.  
  
 Étant donné que ce type d’information n’indique pas de prise en charge générale du caractère d’échappement dans le **comme** prédicat, SQL-92 n’inclure pas les exigences pour cette chaîne de caractères.  
  
 Cela *InfoType* est limité aux fonctions de catalogue. Pour obtenir une description de l’utilisation du caractère d’échappement dans les chaînes de modèle de recherche, consultez [Arguments de valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME(ODBC 1.0)  
 Une chaîne de caractères avec le nom de serveur de spécifique à la source de données réelles ; utile lorsqu’un nom de source de données est utilisé au cours de **SQLConnect**, **SQLDriverConnect**, et **SQLBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS(ODBC 2.0)  
 Une chaîne de caractères qui contient tous les caractères spéciaux (autrement dit, tous les caractères à l’exception d’a à z, A à Z, 0 à 9 et trait de soulignement) qui peuvent être utilisés dans un nom d’identificateur, par exemple un nom de la table, le nom de colonne ou le nom de l’index sur la source de données. Par exemple, « #$^ ». Si un identificateur contient un ou plusieurs de ces caractères, l’identificateur doit être un identificateur délimité.  
  
 SQL_SQL_CONFORMANCE(ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le niveau de prise en charge par le pilote SQL-92 :  
  
 SQL_SC_SQL92_ENTRY = entrée niveau SQL-92 conforme.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = FIPS 127-2 transitoire niveau conforme.  
  
 SQL_SC_SQL92_FULL = niveau complet conformes SQL-92.  
  
 SQL_SC_ SQL92_INTERMEDIATE = intermédiaire au niveau SQL-92 conforme.  
  
 SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les fonctions scalaires datetime sont pris en charge par le pilote et de la source de données associé, tel que défini dans SQL-92.  
  
 Les masques de bits suivants sont utilisés pour déterminer les fonctions de date/heure sont pris en charge :  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les règles pris en charge pour une clé étrangère dans une **supprimer** instruction, comme défini dans SQL-92.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont pris en charge par la source de données :  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Un pilote de niveau conforme FIPS transitoire retourne toujours toutes ces options de prise en charge.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les règles pris en charge pour une clé étrangère dans une **mise à jour** instruction, comme défini dans SQL-92.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont pris en charge par la source de données :  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Un pilote conforme à niveau complète de SQL-92 toutes ces options retournera toujours pris en charge.  
  
 SQL_SQL92_GRANT(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses prises en charge dans les **GRANT** instruction, comme défini dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont pris en charge par la source de données :  
  
 () SQL_SG_INSERT_COLUMN (niveau intermédiaire) SQL_SG_INSERT_TABLE (niveau d’entrée) SQL_SG_REFERENCES_TABLE (niveau d’entrée) SQL_SG_REFERENCES_COLUMN (niveau d’entrée) SQL_SG_SELECT_TABLE (niveau d’entrée) SQL_SG_UPDATE_COLUMN SQL_SG_DELETE_TABLE (niveau d’entrée) Niveau d’entrée) SQL_SG_UPDATE_TABLE (niveau d’entrée) SQL_SG_USAGE_ON_DOMAIN (niveau transitoire FIPS) SQL_SG_USAGE_ON_CHARACTER_SET (niveau transitoire FIPS) SQL_SG_USAGE_ON_COLLATION (niveau transitoire FIPS) SQL_SG_USAGE_ON_TRANSLATION (FIPS Niveau transitoire) SQL_SG_WITH_GRANT_OPTION (niveau d’entrée)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les fonctions scalaires de valeur numérique qui sont pris en charge par le pilote et de la source de données associé, tel que défini dans SQL-92.  
  
 Les masques de bits suivants sont utilisés pour déterminer les fonctions numériques sont prises en charge :  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les prédicats pris en charge dans un **sélectionnez** instruction, comme défini dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer quelles options sont prises en charge par la source de données :  
  
 SQL_SP_BETWEEN (niveau d’entrée) SQL_SP_COMPARISON (niveau d’entrée) sql_sp_like (niveau d’entrée) SQL_SP_IN (niveau d’entrée) SQL_SP_ISNOTNULL (niveau d’entrée) sql_sp_isnotnull (niveau d’entrée) sql_sp_exists (niveau d’entrée) SQL_SP_MATCH_FULL (niveau complet) SQL_SP_MATCH_PARTIAL (Niveau complet) SQL_SP_MATCH_UNIQUE_FULL (niveau complet) SQL_SP_MATCH_UNIQUE_PARTIAL (niveau complet) SQL_SP_OVERLAPS (niveau transitoire FIPS) SQL_SP_QUANTIFIED_COMPARISON (niveau d’entrée) SQL_SP_UNIQUE (niveau d’entrée)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les opérateurs de jointure relationnelle pris en charge dans un **sélectionnez** instruction, comme défini dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer quelles options sont prises en charge par la source de données :  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (niveau intermédiaire) SQL_SRJO_CROSS_JOIN (niveau complet) SQL_SRJO_EXCEPT_JOIN (niveau intermédiaire) SQL_SRJO_FULL_OUTER_JOIN (niveau intermédiaire) SQL_SRJO_INNER_JOIN (niveau transitoire FIPS) SQL_SRJO_INTERSECT_JOIN (Niveau intermédiaire) SQL_SRJO_LEFT_OUTER_JOIN (niveau transitoire FIPS) SQL_SRJO_NATURAL_JOIN (niveau transitoire FIPS) SQL_SRJO_RIGHT_OUTER_JOIN (niveau transitoire FIPS) SQL_SRJO_UNION_JOIN (niveau complet)  
  
 SQL_SRJO_INNER_JOIN indique la prise en charge pour le **INNER JOIN** syntaxe, pas pour que la fonctionnalité de jointure interne. Prise en charge pour le **INNER JOIN** syntaxe est transitoire FIPS, tandis que prise en charge la fonctionnalité de jointure interne est **entrée**.  
  
 SQL_SQL92_REVOKE(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses prises en charge dans les **RÉVOQUER** instruction, comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont pris en charge par la source de données :  
  
 SQL_SR_CASCADE (niveau transitoire FIPS) SQL_SR_DELETE_TABLE (niveau d’entrée) SQL_SR_GRANT_OPTION_FOR (niveau intermédiaire) SQL_SR_INSERT_COLUMN (niveau intermédiaire) SQL_SR_INSERT_TABLE (niveau d’entrée) SQL_SR_REFERENCES_COLUMN (niveau d’entrée) SQL_SR_ REFERENCES_TABLE (niveau d’entrée) SQL_SR_RESTRICT (niveau transitoire FIPS) SQL_SR_SELECT_TABLE (niveau d’entrée) SQL_SR_UPDATE_COLUMN (niveau d’entrée) SQL_SR_UPDATE_TABLE (niveau d’entrée) SQL_SR_USAGE_ON_DOMAIN (niveau transitoire FIPS) SQL_SR_USAGE_ON_ SQL_SR_USAGE_ON_TRANSLATION de SQL_SR_USAGE_ON_COLLATION (niveau transitoire FIPS) CHARACTER_SET (niveau transitoire FIPS) (niveau transitoire FIPS)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les expressions de constructeur de valeurs de ligne pris en charge dans un **sélectionnez** instruction, comme défini dans SQL-92. Les masques de bits suivants sont utilisés pour déterminer quelles options sont prises en charge par la source de données :  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les fonctions scalaires de chaîne qui sont pris en charge par le pilote et de la source de données associé, tel que défini dans SQL-92.  
  
 Les masques de bits suivants sont utilisés pour déterminer les fonctions de chaîne sont prises en charge :  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les expressions de valeur pris en charge, tel que défini dans SQL-92.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer quelles options sont prises en charge par la source de données :  
  
 SQL_SVE_CASE (niveau intermédiaire) SQL_SVE_CAST (niveau transitoire FIPS) SQL_SVE_COALESCE (niveau intermédiaire) SQL_SVE_NULLIF (niveau intermédiaire)  
  
 SQL_STANDARD_CLI_CONFORMANCE(ODBC 3.0)  
 Un masque de bits SQLUINTEGER l’énumération de l’interface CLI ou les normes à laquelle le pilote se conforme. Les masques de bits suivants sont utilisés pour déterminer les niveaux qui le pilote est conforme à :  
  
 SQL_SCC_XOPEN_CLI_VERSION1: Le pilote est conforme à l’interface CLI ouverte de groupe version 1.  
  
 SQL_SCC_ISO92_CLI : Le pilote est conforme à ISO 92 CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui décrit les attributs d’un curseur statique qui sont pris en charge par le pilote. Ce masque de bits contient le premier sous-ensemble d’attributs ; pour le deuxième sous-ensemble, consultez SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Les masques de bits suivants sont utilisés pour déterminer quels attributs sont prises en charge :  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (puis remplacez « curseur statique » pour « curseur dynamique » dans les descriptions).  
  
 Un pilote conforme de niveau intermédiaire SQL-92 retourne généralement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE pris en charge, car le pilote prend en charge des curseurs avec défilement via l’instruction SQL FETCH incorporée. Étant donné que cela ne détermine pas directement de la prise en charge SQL sous-jacent, toutefois, curseurs avec défilement ne peuvent pas être pris en charge, même pour un pilote conforme de niveau intermédiaire SQL-92.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Un masque de bits SQLUINTEGER qui décrit les attributs d’un curseur statique qui sont pris en charge par le pilote. Ce masque de bits contient le deuxième sous-ensemble d’attributs ; pour le premier sous-ensemble, consultez SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Les masques de bits suivants sont utilisés pour déterminer quels attributs sont prises en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (puis remplacez « curseur statique » pour « curseur dynamique » dans les descriptions).  
  
 SQL_STRING_FUNCTIONS(ODBC 1.0)  
 Remarque : Le type d’informations a été introduit dans ODBC 1.0 ; chaque masque de bits est étiquetée avec la version dans laquelle il a été introduite.  
  
 Un masque de bits SQLUINTEGER énumérant les fonctions de chaîne scalaire pris en charge par le pilote et de la source de données associée.  
  
 Les masques de bits suivants sont utilisés pour déterminer les fonctions de chaîne sont prises en charge :  
  
 SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 2.0) SQL_FN_STR_INSERT (ODBC SQL_FN_STR_ASCII (ODBC 1.0) SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) 1.0) SQL_FN_STR_LCASE (ODBC 1.0) SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_ SQL_FN_STR_REPEAT (ODBC 1.0) STR_REPLACE (ODBC 1.0) SQL_FN_STR_RIGHT (ODBC 1.0) SQL_FN_STR_RTRIM (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) SQL_FN_STR_SPACE (ODBC 2.0) SQL_FN_STR_SUBSTRING (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1.0)  
  
 Si une application peut appeler le **localiser** fonction scalaire avec la *string_exp1*, *string_exp2*, et *Démarrer* arguments, le pilote Retourne le masque de bits SQL_FN_STR_LOCATE. Si une application peut appeler la fonction scalaire localiser avec uniquement le *string_exp1* et *string_exp2* arguments, le pilote retourne le masque de bits SQL_FN_STR_LOCATE_2. Les pilotes qui prennent en charge la **localiser** les deux masques de bits de retour de fonction scalaire.  
  
 (Pour plus d’informations, consultez [fonctions de chaîne](../../../odbc/reference/appendixes/string-functions.md) dans l’annexe E, « fonctions scalaires. »)  
  
 SQL_SUBQUERIES(ODBC 2.0)  
 Un masque de bits SQLUINTEGER énumérant les prédicats qui prennent en charge les sous-requêtes :  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Le masque de bits SQL_SQ_CORRELATED_SUBQUERIES indique que tous les prédicats qui prennent en charge les sous-requêtes prennent en charge les sous-requêtes corrélées.  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournent toujours un masque de bits dans laquelle tous ces bits sont définies.  
  
 SQL_SYSTEM_FUNCTIONS(ODBC 1.0)  
 Un masque de bits SQLUINTEGER énumérant les fonctions système scalaires pris en charge par le pilote et de la source de données associée.  
  
 Les masques de bits suivants sont utilisés pour déterminer les fonctions système sont prises en charge :  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM(ODBC 1.0)  
 Une chaîne de caractères avec le nom du fournisseur de source de données pour une table ; par exemple, « table » ou « fichier ».  
  
 Cette chaîne de caractères peut être dans le coin supérieur, inférieur ou les casses mixtes.  
  
 Retourne toujours un pilote de conforme à niveau d’entrée SQL-92 « table ».  
  
 SQL_TIMEDATE_ADD_INTERVALS(ODBC 2.0)  
 Un masque de bits SQLUINTEGER énumérant les intervalles d’horodatage pris en charge par le pilote et de la source de données associée pour la fonction scalaire TIMESTAMPADD.  
  
 Les masques de bits suivants sont utilisés pour déterminer les intervalles sont pris en charge :  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Un pilote de niveau conforme FIPS transitoire retourne toujours un masque de bits dans laquelle tous ces bits sont définies.  
  
 SQL_TIMEDATE_DIFF_INTERVALS(ODBC 2.0)  
 Un masque de bits SQLUINTEGER énumérant les intervalles d’horodatage pris en charge par le pilote et de la source de données associée pour la fonction scalaire TIMESTAMPDIFF.  
  
 Les masques de bits suivants sont utilisés pour déterminer les intervalles sont pris en charge :  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Un pilote de niveau conforme FIPS transitoire retourne toujours un masque de bits dans laquelle tous ces bits sont définies.  
  
 SQL_TIMEDATE_FUNCTIONS(ODBC 1.0)  
 Remarque : Le type d’informations a été introduit dans ODBC 1.0 ; chaque masque de bits est étiquetée avec la version dans laquelle il a été introduite.  
  
 Un masque de bits SQLUINTEGER énumérant les scalaire fonctions date et heure prises en charge par le pilote et de la source de données associée.  
  
 Les masques de bits suivants sont utilisés pour déterminer les fonctions de date et d’heure sont pris en charge :  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK () ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 3.0) SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_ DEUXIÈME (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0) SQL_FN_TD_WEEK (ODBC 1.0) SQL_FN_TD_YEAR (ODBC 1.0)  
  
 SQL_TXN_CAPABLE(ODBC 1.0)  
 Remarque : Le type d’informations a été introduit dans ODBC 1.0 ; chaque valeur de retour est étiquetée avec la version dans laquelle il a été introduite.  
  
 Une valeur SQLUSMALLINT qui décrit la prise en charge de transaction dans la source de données ou de pilote :  
  
 SQL_TC_NONE = non pris en charge des Transactions. (ODBC 1.0)  
  
 SQL_TC_DML = Transactions peuvent contenir uniquement des instructions de langage de Manipulation de données (DML) (**sélectionnez**, **insérer**, **mise à jour**, **supprimer** ). Instructions de langage de définition (DDL) de données dans une cause de la transaction une erreur. (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT = Transactions peuvent contenir uniquement des instructions DML. Instructions DDL (**CREATE TABLE**, **DROP INDEX**, et ainsi de suite) a rencontré dans une cause de la transaction de la transaction est validée. (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE = Transactions peuvent contenir uniquement des instructions DML. Instructions DDL a rencontré dans une transaction sont ignorées. (ODBC 2.0)  
  
 SQL_TC_ALL = Transactions peuvent contenir des instructions DDL et des instructions DML de n’importe quel ordre. (ODBC 1.0)  
  
 (Étant donné que la prise en charge des transactions est obligatoire dans SQL-92, un pilote de conforme SQL-92 [n’importe quel niveau] ne retourne jamais SQL_TC_NONE.)  
  
 SQL_TXN_ISOLATION_OPTION(ODBC 1.0)  
 Un masque de bits SQLUINTEGER énumérant les niveaux d’isolation de transaction disponibles à partir de la source de données ou de pilote.  
  
 Les masques de bits suivants sont utilisés avec l’indicateur pour déterminer quelles options sont prises en charge :  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Pour obtenir une description de ces niveaux d’isolement, consultez la description de SQL_DEFAULT_TXN_ISOLATION.  
  
 Pour définir le niveau d’isolation de transaction, une application appelle **SQLSetConnectAttr** pour définir l’attribut SQL_ATTR_TXN_ISOLATION. Pour plus d’informations, consultez [fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Un pilote de conforme à niveau d’entrée SQL-92 retournera toujours SQL_TXN_SERIALIZABLE pris en charge. Un pilote de niveau conforme FIPS transitoire retourne toujours toutes ces options de prise en charge.  
  
 SQL_UNION(ODBC 2.0)  
 Un masque de bits SQLUINTEGER l’énumération de la prise en charge pour le **UNION** clause :  
  
 SQL_U_UNION = la source de données prend en charge la **UNION** clause.  
  
 SQL_U_UNION_ALL = la source de données prend en charge la **tous les** mot clé dans le **UNION** clause. (**SQLGetInfo** retourne SQL_U_UNION et SQL_U_UNION_ALL dans ce cas.)  
  
 Un pilote de conforme à niveau d’entrée SQL-92 renvoie toujours ces deux options pris en charge.  
  
 SQL_USER_NAME(ODBC 1.0)  
 Une chaîne de caractères avec le nom utilisé dans une base de données, qui peut être différent du nom de connexion.  
  
 SQL_XOPEN_CLI_YEAR(ODBC 3.0)  
 Une chaîne de caractères qui indique l’année de publication de la spécification Open Group avec lequel la version du Gestionnaire de pilotes ODBC est entièrement conforme.  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 Une chaîne de caractères : « Y » si l’utilisateur peut exécuter toutes les procédures retournées par **SQLProcedures**; « N » s’il peut y avoir des procédures retournées que l’utilisateur ne peut pas exécuter.  
  
 SQL_ACCESSIBLE_TABLES(ODBC 1.0)  
 Une chaîne de caractères : « Y » si l’utilisateur est assuré **sélectionnez** des privilèges à toutes les tables retournées par **SQLTables**; « N » s’il peut y avoir des tables retournée que l’utilisateur ne peut pas accéder.  
  
 SQL_ACTIVE_ENVIRONMENTS(ODBC 3.0)  
 Une valeur SQLUSMALLINT qui spécifie le nombre maximal d’environnements actifs que le pilote peut prendre en charge. Si aucune limite n’est spécifié ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 Un masque de bits SQLUINTEGER l’énumération prise en charge des fonctions d’agrégation :  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Un pilote de conforme à niveau d’entrée SQL-92 toutes ces options retournera toujours pris en charge.  
  
 SQL_ALTER_DOMAIN(ODBC 3.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **ALTER DOMAIN** instruction, comme défini dans SQL-92, pris en charge par la source de données. Un pilote de niveau compatible SQL-92 Full retournera toujours tous les masques de bits. Une valeur de retour de « 0 » signifie que le **ALTER DOMAIN** instruction n’est pas prise en charge.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = Ajout d’une contrainte de domaine est pris en charge (niveau total)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter domaine > \<ensemble domaine par défaut clause > est pris en charge (niveau total)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<clause de définition de contrainte name > est prise en charge pour la dénomination de contrainte de domaine (niveau intermédiaire)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<clause de contrainte de domaine drop > est pris en charge (niveau total)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter domaine > \<clause de suppression domaine par défaut > est pris en charge (niveau total)  
  
 Les bits suivantes spécifient la prise en charge \<les attributs de contrainte > Si \<ajouter une contrainte de domaine > est pris en charge (le bit SQL_AD_ADD_DOMAIN_CONSTRAINT est défini) :  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet)  
  
 SQL_ALTER_TABLE(ODBC 2.0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans le **ALTER TABLE** instruction pris en charge par la source de données.  
  
 Le niveau de conformité SQL-92 ou FIPS à laquelle cette fonctionnalité doit être pris en charge est affiché entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<AddColumn > clause est prise en charge, avec la fonctionnalité qui permet de spécifier le classement de colonne (niveau complet) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<AddColumn > clause est prise en charge, avec la fonctionnalité qui permet de spécifier les valeurs par défaut de la colonne (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<AddColumn > est pris en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<AddColumn > clause est prise en charge, avec la fonctionnalité qui permet de spécifier des contraintes de colonne (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<ajouter une contrainte de table > clause est prise en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<définition de nom de contrainte > est prise en charge pour la dénomination des contraintes de colonne et de table (niveau intermédiaire) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<supprimer la colonne > CASCADE est pris en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<de modifier la colonne > \<clause par défaut de column drop > est pris en charge (niveau intermédiaire) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<supprimer la colonne > RESTRICT est pris en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<supprimer la colonne > RESTRICT est pris en charge (niveau transitoire FIPS) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<de modifier la colonne > \<jeu de colonnes par défaut clause > est pris en charge (niveau intermédiaire) (ODBC 3.0)  
  
 Les bits suivantes spécifient la prise en charge \<les attributs de contrainte > Si la spécification de contraintes de colonne ou une table est pris en charge (le bit SQL_AT_ADD_CONSTRAINT est défini) :  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (niveau complet) (ODBC 3.0)  
  
 SQL_ASYNC_MODE(ODBC 3.0)  
 Une valeur SQLUINTEGER qui indique le niveau de prise en charge asynchrone dans le pilote :  
  
 SQL_AM_CONNECTION = connexion d’exécution asynchrone au niveau est pris en charge. Tous les descripteurs d’instruction associées à un handle de connexion donné sont en mode asynchrone ou toutes sont en mode synchrone. Un descripteur d’instruction sur une connexion ne peut pas être en mode asynchrone alors que le handle d’une autre instruction sur la même connexion est en mode synchrone et vice versa.  
  
 SQL_AM_STATEMENT = l’instruction d’exécution asynchrone au niveau est pris en charge. Certains descripteurs d’instruction associées à un handle de connexion peuvent être en mode asynchrone, tandis que les autres descripteurs d’instruction sur la même connexion sont en mode synchrone.  
  
 SQL_AM_NONE = asynchrone mode n’est pas pris en charge.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Un masque de bits SQLUINTEGER le comportement du pilote en ce qui concerne la disponibilité de la ligne de l’énumération des nombres. Les masques de bits suivantes utilisées en conjonction avec le type d’informations :  
  
 SQL_BRC_ROLLED_UP = nombre de lignes pour les instructions INSERT, DELETE ou UPDATE consécutifs sont reportées en une seule. Si ce bit n’est pas défini, le nombre de lignes est disponibles pour chaque instruction.  
  
 SQL_BRC_PROCEDURES = nombre de lignes, si elles, sont disponibles lorsqu’un lot est exécuté dans une procédure stockée. Si le nombre de lignes est disponibles, elles peuvent être restaurées vers le haut ou individuellement disponibles, selon le bit SQL_BRC_ROLLED_UP.  
  
 SQL_BRC_EXPLICIT = nombre de lignes, si elles, sont disponibles lorsqu’un lot est exécuté directement en appelant **SQLExecute** ou **SQLExecDirect**. Si le nombre de lignes est disponibles, elles peuvent être restaurées vers le haut ou individuellement disponibles, selon le bit SQL_BRC_ROLLED_UP.  
  
## <a name="example"></a>Exemple  
 **SQLGetInfo** retourne la liste des options prises en charge comme un masque de bits SQLUINTEGER dans **InfoValuePtr*. Le masque de bits pour chaque option est utilisée avec l’indicateur pour déterminer si l’option est prise en charge.  
  
 Par exemple, une application peut utiliser le code suivant pour déterminer si la fonction scalaire sous-chaîne est pris en charge par le pilote associé à la connexion.  
  
 Pour un autre exemple d’utilisation **SQLGetInfo**, consultez [fonction SQLTables](../../../odbc/reference/syntax/sqltables-function.md).  
  
```  
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
 Retourner le paramètre d’un attribut de connexion  
 [SQLGetConnectAttr, fonction](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Déterminer si un pilote prend en charge une fonction  
 [SQLGetFunctions, fonction](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Retourner le paramètre d’un attribut d’instruction  
 [SQLGetStmtAttr, fonction](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Retour d’informations sur les types de données d’une source de données  
 [SQLGetTypeInfo, fonction](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
