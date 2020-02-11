---
title: Fonction SQLGetInfo | Microsoft Docs
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
ms.openlocfilehash: b0e62e7aaba276643a2874a22e74a08214cfe51e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030659"
---
# <a name="sqlgetinfo-function"></a>Fonction SQLGetInfo
**Conformité**  
 Version introduite : ODBC 1,0 conformité aux normes : ISO 92  
  
 **Résumé**  
 **SQLGetInfo** retourne des informations générales sur le pilote et la source de données associés à une connexion.  
  
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
 *ConnectionHandle*  
 [Entrée] Handle de connexion.  
  
 *TypeInfo*  
 Entrée Type d’informations.  
  
 *InfoValuePtr*  
 Sortie Pointeur vers une mémoire tampon dans laquelle retourner les informations. Selon l' *infotype* demandé, les informations retournées sont l’une des suivantes : une chaîne de caractères terminée par le caractère null, une valeur SQLUSMALLINT, un masque de bits SQLUINTEGER, un indicateur SQLUINTEGER, une valeur binaire SQLUINTEGER ou une valeur SQLULEN.  
  
 Si l’argument *infotype* est SQL_DRIVER_HDESC ou SQL_DRIVER_HSTMT, l’argument *InfoValuePtr* est à la fois l’entrée et la sortie. (Pour plus d’informations, consultez les descripteurs SQL_DRIVER_HDESC ou SQL_DRIVER_HSTMT plus loin dans cette description de fonction.)  
  
 Si *InfoValuePtr* a la valeur null, *StringLengthPtr* retourne toujours le nombre total d’octets (à l’exception du caractère de fin null pour les données de type caractère) disponibles pour retourner dans la mémoire tampon vers laquelle pointe *InfoValuePtr*.  
  
 *BufferLength*  
 Entrée Longueur de la \*mémoire tampon *InfoValuePtr* . Si la valeur de * \*InfoValuePtr* n’est pas une chaîne de caractères ou si *InfoValuePtr* est un pointeur null, l’argument *BufferLength* est ignoré. Le pilote suppose que la taille de * \*InfoValuePtr* est SQLUSMALLINT ou SQLUINTEGER, en fonction de l' *infotype*. Si * \*InfoValuePtr* est une chaîne Unicode (lors de l’appel de **SQLGetInfoW**), l’argument *BufferLength* doit être un nombre pair ; Si ce n’est pas le cas, SQLSTATE HY090 (longueur de chaîne ou de mémoire tampon non valide) est retourné.  
  
 *StringLengthPtr*  
 Sortie Pointeur vers une mémoire tampon dans laquelle retourner le nombre total d’octets (à l’exception du caractère de fin null pour les données de type caractère) disponibles pour le retour de **InfoValuePtr*.  
  
 Pour les données de type caractère, si le nombre d’octets disponibles à retourner est supérieur ou égal à *BufferLength*, les \*informations dans *InfoValuePtr* sont tronquées à *BufferLength* octets moins la longueur d’un caractère de fin null et le pilote se termine par un caractère null.  
  
 Pour tous les autres types de données, la valeur de *BufferLength* est ignorée et le pilote suppose que la \*taille de *InfoValuePtr* est SQLUSMALLINT ou SQLUINTEGER, en fonction de l' *infotype*.  
  
## <a name="return-value"></a>Valeur de retour  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Quand **SQLGetInfo** retourne soit SQL_ERROR, soit SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *comme HandleType* de SQL_HANDLE_DBC et un *handle* de *ConnectionHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLGetInfo** et explique chacune d’elles dans le contexte de cette fonction. la notation « (DM) » précède les descriptions des SQLSTATEs retournées par le gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, tronquées à droite|Le \* *InfoValuePtr* de mémoire tampon n’est pas assez grand pour retourner toutes les informations demandées. Par conséquent, les informations ont été tronquées. La longueur des informations demandées dans sa forme non tronquée est retournée dans **StringLengthPtr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) le type d’informations demandé dans l' *infotype* requiert une connexion ouverte. Parmi les types d’informations réservés par ODBC, seuls les SQL_ODBC_VER peuvent être retournés sans connexion ouverte.|  
|08S01|Échec de la liaison de communication|Le lien de communication entre le pilote et la source de données à laquelle le pilote a été connecté a échoué avant la fin du traitement de la fonction.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucune SQLSTATE spécifique n’a été définie et pour lesquelles aucune SQLSTATE spécifique à l’implémentation n’a été définie. Le message d’erreur retourné par **SQLGetDiagRec** dans * \** la mémoire tampon MessageText décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer de la mémoire requise pour prendre en charge l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLExecute**, **SQLExecDirect**ou **SQLMoreResults** a été appelé pour *StatementHandle* et a retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres transmis en continu.|  
|HY013|Erreur de gestion de la mémoire|Impossible de traiter l’appel de fonction, car les objets mémoire sous-jacents sont inaccessibles, probablement en raison de conditions de mémoire insuffisante.|  
|HY024|Valeur d’attribut non valide|(DM) l’argument *infotype* était SQL_DRIVER_HSTMT, et la valeur désignée par *InfoValuePtr* n’était pas un descripteur d’instruction valide.<br /><br /> (DM) l’argument *infotype* était SQL_DRIVER_HDESC, et la valeur désignée par *InfoValuePtr* n’était pas un handle de descripteur valide.|  
|HY090|Longueur de chaîne ou de mémoire tampon non valide|(DM) la valeur spécifiée pour l’argument *BufferLength* est inférieure à 0.<br /><br /> (DM) la valeur spécifiée pour *BufferLength* était un nombre impair et * \*InfoValuePtr* était d’un type de données Unicode.|  
|HY096|Type d’information hors limites|La valeur spécifiée pour l' *infotype* de l’argument n’est pas valide pour la version de ODBC prise en charge par le pilote.|  
|HY117|La connexion est interrompue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Champ facultatif non implémenté|La valeur spécifiée pour l' *infotype* de l’argument était une valeur spécifique au pilote qui n’est pas prise en charge par le pilote.|  
|HYT01|Délai d’attente de connexion expiré|Le délai d’attente de connexion a expiré avant que la source de données ait répondu à la demande. Le délai d’expiration de la connexion est défini par le biais de **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le pilote ne prend pas en charge cette fonction|(DM) le pilote qui correspond au *ConnectionHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Les types d’informations actuellement définis sont présentés dans la section « types d’informations », plus loin dans cette section. Il est supposé que plus est défini pour tirer parti de différentes sources de données. Un ensemble de types d’informations est réservé par ODBC ; les développeurs de pilotes doivent réserver des valeurs pour leur propre utilisation propre au pilote à partir d’Open Group. **SQLGetInfo** n’effectue pas de conversion Unicode ou de *thunk* (voir [annexe A : codes d’erreur ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) du *Guide de référence du programmeur ODBC*) pour les *InfoTypes*définis par le pilote. Pour plus d’informations, consultez [types de données spécifiques au pilote, types de descripteurs, types d’informations, types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Le format des informations retournées \*dans *InfoValuePtr* dépend de l' *infotype* demandé. **SQLGetInfo** renverra des informations dans l’un des cinq formats suivants :  
  
-   Chaîne de caractères se terminant par un caractère null  
  
-   Valeur SQLUSMALLINT  
  
-   Masque de SQLUINTEGER  
  
-   Valeur SQLUINTEGER  
  
-   Valeur binaire SQLUINTEGER  
  
 Le format de chacun des types d’informations suivants est indiqué dans la description du type. L’application doit effectuer un cast de la valeur retournée dans **InfoValuePtr* en conséquence. Pour obtenir un exemple de la façon dont une application peut récupérer des données à partir d’un masque de SQLUINTEGER, consultez « exemple de code ».  
  
 Un pilote doit retourner une valeur pour chaque type d’informations défini dans les tableaux suivants. Si un type d’informations ne s’applique pas au pilote ou à la source de données, le pilote renvoie l’une des valeurs indiquées dans le tableau suivant.  
  
 Chaîne de caractères (« Y » ou « N »)  
 "N"  
  
 Chaîne de caractères (et non « Y » ou « N »)  
 Chaîne vide  
  
 SQLUSMALLINT  
 0  
  
 Masque de SQLUINTEGER ou valeur binaire SQLUINTEGER  
 0L  
  
 Par exemple, si une source de données ne prend pas en charge les procédures, **SQLGetInfo** retourne les valeurs répertoriées dans le tableau suivant pour les valeurs d' *infotype* associées aux procédures.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Chaîne vide  
  
 **SQLGetInfo** retourne SQLState HY096 (valeur d’argument non valide) pour les valeurs d' *infotype* qui se trouvent dans la plage de types d’informations réservée pour une utilisation par ODBC, mais qui ne sont pas définies par la version de ODBC prise en charge par le pilote. Pour déterminer la version d’ODBC avec laquelle un pilote est compatible, une application appelle **SQLGetInfo** avec le type d’informations SQL_DRIVER_ODBC_VER. **SQLGetInfo** retourne SQLState HYC00 (fonctionnalité facultative non implémentée) pour les valeurs d' *infotype* qui se trouvent dans la plage de types d’informations réservée à une utilisation propre au pilote, mais qui ne sont pas prises en charge par le pilote.  
  
 Tous les appels à **SQLGetInfo** nécessitent une connexion ouverte, sauf lorsque l' *infotype* est SQL_ODBC_VER, qui retourne la version du gestionnaire de pilotes.  
  
## <a name="information-types"></a>Types d’informations  
 Cette section répertorie les types d’informations pris en charge par **SQLGetInfo**. Les types d’informations sont regroupés par catégorie et répertoriés par ordre alphabétique. Les types d’informations qui ont été ajoutés ou renommés pour ODBC 3 *. x* sont également répertoriés.  
  
## <a name="driver-information"></a>Informations sur le pilote  
 Les valeurs suivantes de l’argument *infotype* renvoient des informations sur le pilote ODBC, telles que le nombre d’instructions actives, le nom de la source de données et le niveau de conformité des normes de l’interface :  
  
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
>  Lors de l’implémentation de **SQLGetInfo**, un pilote peut améliorer les performances en minimisant le nombre de fois où les informations sont envoyées ou demandées à partir du serveur.  
  
## <a name="dbms-product-information"></a>Informations sur le produit SGBD  
 Les valeurs suivantes de l’argument *infotype* retournent des informations sur le produit SGBD, telles que le nom et la version du SGBD :  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Informations sur la source de données  
 Les valeurs suivantes de l’argument *infotype* retournent des informations sur la source de données, telles que les caractéristiques de curseur et les fonctionnalités de transaction :  
  
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
  
## <a name="supported-sql"></a>SQL pris en charge  
 Les valeurs suivantes de l’argument *infotype* retournent des informations sur les instructions SQL prises en charge par la source de données. La syntaxe SQL de chaque fonctionnalité décrite par ces types d’informations est la syntaxe SQL-92. Ces types d’informations ne décrivent pas de façon exhaustive l’intégralité de la grammaire SQL-92. Au lieu de cela, ils décrivent les parties de la grammaire pour lesquelles les sources de données offrent généralement différents niveaux de prise en charge. Plus précisément, la plupart des instructions DDL dans SQL-92 sont couvertes.  
  
 Les applications doivent déterminer le niveau général de la grammaire prise en charge à partir du type d’informations SQL_SQL_CONFORMANCE et utiliser les autres types d’informations pour déterminer les variations du niveau de conformité des normes spécifiées.  
  
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
 Les valeurs suivantes de l’argument *infotype* renvoient des informations sur les limites appliquées aux identificateurs et aux clauses dans les instructions SQL, telles que les longueurs maximales des identificateurs et le nombre maximal de colonnes dans une liste de sélection. Les limitations peuvent être imposées par le pilote ou la source de données.  
  
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
 Les valeurs suivantes de l’argument *infotype* retournent des informations sur les fonctions scalaires prises en charge par la source de données et le pilote. Pour plus d’informations sur les fonctions scalaires, consultez [l’annexe E : fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Informations de conversion  
 Les valeurs suivantes de l’argument *infotype* renvoient la liste des types de données SQL vers lesquels la source de données peut convertir le type de données SQL spécifié avec la fonction scalaire **Convert** :  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>Types d’informations ajoutés pour ODBC 3. x  
 Les valeurs suivantes de l’argument *infotype* ont été ajoutées pour ODBC 3 *. x*:  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>Types d’informations renommés pour ODBC 3. x  
 Les valeurs suivantes de l’argument *infotype* ont été renommées pour ODBC 3 *. x*.  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Types d’informations déconseillés dans ODBC 3. x  
 Les valeurs suivantes de l’argument *infotype* ont été dépréciées dans ODBC 3 *. x*. Les pilotes ODBC 3 *. x* doivent continuer à prendre en charge ces types d’informations pour assurer la compatibilité descendante avec les applications ODBC 2 *. x* . (Pour plus d’informations sur ces types, consultez la page [prise en charge de SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md) dans annexe G : instructions relatives aux pilotes pour la compatibilité descendante.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Descriptions des types d’informations  
 Le tableau suivant répertorie par ordre alphabétique chaque type d’informations, la version de ODBC dans laquelle il a été introduit et sa description.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1,0)  
 Chaîne de caractères : « Y » si l’utilisateur peut exécuter toutes les procédures retournées par **SQLProcedures**; « N » s’il peut y avoir des procédures retournées que l’utilisateur ne peut pas exécuter.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1,0)  
 Chaîne de caractères : « Y » si l’utilisateur est assuré de **Sélectionner** des privilèges pour toutes les tables retournées par **SQLTables**; « N » s’il peut y avoir des tables renvoyées auxquelles l’utilisateur ne peut pas accéder.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3,0)  
 Valeur de SQLUSMALLINT qui spécifie le nombre maximal d’environnements actifs que le pilote peut prendre en charge. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3,0)  
 Un masque de SQLUINTEGER pour énumérer la prise en charge des fonctions d’agrégation :  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours toutes les options prises en charge.  
  
 SQL_ALTER_DOMAIN (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **ALTER Domain** , tel que défini dans SQL-92, pris en charge par la source de données. Un pilote compatible avec le niveau complet SQL-92 retourne toujours tous les masques de bits. Une valeur de retour de « 0 » signifie que l’instruction **ALTER Domain** n’est pas prise en charge.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = l’ajout d’une contrainte de domaine est pris en charge (niveau complet)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter Domain> \<définir le domaine par défaut> est pris en charge (niveau complet)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<la clause de définition du nom de la contrainte> est prise en charge pour la contrainte de domaine d’attribution de noms (niveau intermédiaire)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<supprimer la clause de contrainte de domaine> est pris en charge (niveau complet)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter Domain> \<supprimer la clause de domaine par défaut> est pris en charge (niveau complet)  
  
 Les bits suivants spécifient les \<attributs de contrainte pris \<en charge> si l’ajout d’une contrainte de domaine> est pris en charge (le bit SQL_AD_ADD_DOMAIN_CONSTRAINT est défini) :  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet)  
  
 SQL_ALTER_TABLE (ODBC 2,0)  
 Un masque de SQLUINTEGER qui énumère les clauses de l’instruction **ALTER TABLE** prise en charge par la source de données.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<la clause ADD COLUMN> est prise en charge, avec une fonction facilitant la spécification du classement de colonne (niveau complet) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<la clause ADD COLUMN> est prise en charge, avec Facility pour spécifier les valeurs par défaut des colonnes (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<ajout de> de colonne est pris en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_CONSTRAINT = \<la clause ADD COLUMN> est prise en charge, avec Facility pour spécifier des contraintes de colonne (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<la clause de> de contrainte Add table est prise en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<la> de définition du nom de la contrainte est prise en charge pour les contraintes de colonne et de table (niveau intermédiaire) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<DROP Column> cascade est pris en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<alter Column> \<clause de suppression de colonne par défaut> est pris en charge (niveau intermédiaire) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<la colonne de suppression> restreindre est pris en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<la colonne de suppression> restreindre est pris en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<alter Column> \<clause SET Column default> est pris en charge (niveau intermédiaire) (ODBC 3,0)  
  
 Les bits suivants spécifient les \<attributs de contrainte de prise en charge> si la spécification de contraintes de colonne ou de table est prise en charge (le bit SQL_AT_ADD_CONSTRAINT est défini) :  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (niveau complet) (ODBC 3,0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3,8)  
 Valeur SQLUINTEGER qui indique si le pilote peut exécuter des fonctions de manière asynchrone sur le handle de connexion.  
  
 SQL_ASYNC_DBC_CAPABLE = le pilote peut exécuter des fonctions de connexion de manière asynchrone.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = le pilote ne peut pas exécuter de fonctions de connexion de manière asynchrone.  
  
 SQL_ASYNC_MODE (ODBC 3,0)  
 Valeur SQLUINTEGER qui indique le niveau de prise en charge asynchrone dans le pilote :  
  
 SQL_AM_CONNECTION = l’exécution asynchrone au niveau de la connexion est prise en charge. Tous les descripteurs d’instruction associés à un handle de connexion donné sont en mode asynchrone ou tous sont en mode synchrone. Un descripteur d’instruction sur une connexion ne peut pas être en mode asynchrone alors qu’un autre descripteur d’instruction sur la même connexion est en mode synchrone, et vice versa.  
  
 SQL_AM_STATEMENT = l’exécution asynchrone au niveau de l’instruction est prise en charge. Certains descripteurs d’instruction associés à un handle de connexion peuvent être en mode asynchrone, tandis que les autres descripteurs d’instruction sur la même connexion sont en mode synchrone.  
  
 SQL_AM_NONE = le mode asynchrone n’est pas pris en charge.  
  
 SQL_ASYNC_NOTIFICATION  
 Valeur SQLUINTEGER qui indique si le pilote prend en charge la notification asynchrone :  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** La notification d’exécution asynchrone est prise en charge par le pilote.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** La notification d’exécution asynchrone n’est pas prise en charge par le pilote.  
  
 Il existe deux catégories d’opérations ODBC asynchrones : les opérations asynchrones au niveau de la connexion et les opérations asynchrones au niveau des instructions.  Si un pilote retourne SQL_ASYNC_NOTIFICATION_CAPABLE, il doit prendre en charge la notification pour toutes les API qu’il peut exécuter de manière asynchrone.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3,0)  
 Masque de SQLUINTEGER qui énumère le comportement du pilote en ce qui concerne la disponibilité des nombres de lignes. Les masques de données suivants sont utilisés avec le type d’informations :  
  
 SQL_BRC_ROLLED_UP = le nombre de lignes pour les instructions INSERT, DELETE ou UPDATE consécutives est cumulé dans un. Si ce bit n’est pas défini, les nombres de lignes sont disponibles pour chaque instruction.  
  
 SQL_BRC_PROCEDURES = le nombre de lignes, le cas échéant, est disponible lors de l’exécution d’un lot dans une procédure stockée. Si les nombres de lignes sont disponibles, ils peuvent être cumulés ou disponibles individuellement, selon le bit de SQL_BRC_ROLLED_UP.  
  
 SQL_BRC_EXPLICIT = les nombres de lignes, le cas échéant, sont disponibles lorsqu’un traitement est exécuté directement en appelant **SQLExecute** ou **SQLExecDirect**. Si les nombres de lignes sont disponibles, ils peuvent être cumulés ou disponibles individuellement, selon le bit de SQL_BRC_ROLLED_UP.  
  
 SQL_BATCH_SUPPORT (ODBC 3,0)  
 Masque de SQLUINTEGER qui énumère la prise en charge du pilote pour les lots. Les masques de détours suivants sont utilisés pour déterminer le niveau pris en charge :  
  
 SQL_BS_SELECT_EXPLICIT = le pilote prend en charge les lots explicites qui peuvent avoir des instructions de génération de jeu de résultats.  
  
 SQL_BS_ROW_COUNT_EXPLICIT = le pilote prend en charge les lots explicites qui peuvent avoir des instructions de génération de nombre de lignes.  
  
 SQL_BS_SELECT_PROC = le pilote prend en charge les procédures explicites qui peuvent avoir des instructions de génération de jeu de résultats.  
  
 SQL_BS_ROW_COUNT_PROC = le pilote prend en charge les procédures explicites qui peuvent avoir des instructions de génération de nombre de lignes.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2,0)  
 Masque de SQLUINTEGER qui énumère les opérations par le biais desquelles les signets sont conservés.  
  
 Les masques de transparence suivants sont utilisés avec l’indicateur pour déterminer les options de conservation des signets :  
  
 SQL_BP_CLOSE = les signets sont valides après qu’une application a appelé **SQLFreeStmt** avec l’option SQL_CLOSE, ou **SQLCloseCursor** pour fermer le curseur associé à une instruction.  
  
 SQL_BP_DELETE = le signet d’une ligne est valide après la suppression de cette ligne.  
  
 SQL_BP_DROP = les signets sont valides après qu’une application a appelé **SQLFreeHandle** avec un *comme HandleType* de SQL_HANDLE_STMT pour supprimer une instruction.  
  
 SQL_BP_TRANSACTION = les signets sont valides après qu’une application a validé ou annulé une transaction.  
  
 SQL_BP_UPDATE = le signet d’une ligne est valide après la mise à jour d’une colonne de cette ligne, y compris les colonnes clés.  
  
 SQL_BP_OTHER_HSTMT = un signet associé à une instruction peut être utilisé avec une autre instruction. À moins que SQL_BP_CLOSE ou SQL_BP_DROP soit spécifié, le curseur sur la première instruction doit être ouvert.  
  
 SQL_CATALOG_LOCATION (ODBC 2,0)  
 Valeur SQLUSMALLINT qui indique la position du catalogue dans un nom de table qualifié :  
  
 SQL_CL_STARTSQL_CL_END  
  
 Par exemple, un pilote xbase retourne SQL_CL_START, car le nom du répertoire (catalogue) se trouve au début du nom de la table, comme dans \EMPDATA\EMP. Paramètre. Un pilote de serveur ORACLE retourne SQL_CL_END, car le catalogue se trouve à la fin du nom de la ADMIN.EMP@EMPDATAtable, comme dans.  
  
 Un pilote SQL-92 Full-conforme retourne toujours SQL_CL_START. La valeur 0 est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’informations SQL_CATALOG_NAME.  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_QUALIFIER_LOCATION.  
  
 SQL_CATALOG_NAME (ODBC 3,0)  
 Chaîne de caractères : « Y » si le serveur prend en charge les noms de catalogue, ou « N » dans le cas contraire.  
  
 Un pilote SQL-92 de niveau complet-conforme retourne toujours « Y ».  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1,0)  
 Chaîne de caractères : le ou les caractères que la source de données définit comme séparateur entre un nom de catalogue et l’élément de nom qualifié qui suit ou le précède.  
  
 Une chaîne vide est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’informations SQL_CATALOG_NAME. Un pilote SQL-92 Full-conforme renverra toujours « . ».  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_QUALIFIER_NAME_SEPARATOR.  
  
 SQL_CATALOG_TERM (ODBC 1,0)  
 Chaîne de caractères avec le nom du fournisseur de la source de données d’un catalogue ; par exemple, « base de données » ou « répertoire ». Cette chaîne peut être en majuscules, en minuscules ou en casse mixte.  
  
 Une chaîne vide est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’informations SQL_CATALOG_NAME. Un pilote SQL-92 Full-conforme renverra toujours « Catalog ».  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_QUALIFIER_TERM.  
  
 SQL_CATALOG_USAGE (ODBC 2,0)  
 Masque de SQLUINTEGER qui énumère les instructions dans lesquelles les catalogues peuvent être utilisés.  
  
 Les masques de Troie suivants permettent de déterminer où les catalogues peuvent être utilisés :  
  
 SQL_CU_DML_STATEMENTS = les catalogues sont pris en charge dans toutes les instructions de langage de manipulation de données : **Sélectionner**, **Insérer**, **mettre à jour**, **supprimer**et, si pris en charge, **Sélectionner pour la mise à jour** et les instructions Update et DELETE positionnées.  
  
 SQL_CU_PROCEDURE_INVOCATION = les catalogues sont pris en charge dans l’instruction d’appel de procédure ODBC.  
  
 SQL_CU_TABLE_DEFINITION = les catalogues sont pris en charge dans toutes les instructions de définition de table : **Create table**, **Create View**, **ALTER TABLE**, **drop table**et **Drop View**.  
  
 SQL_CU_INDEX_DEFINITION = les catalogues sont pris en charge dans toutes les instructions de définition d’index : **Create index** et **Drop index**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = les catalogues sont pris en charge dans toutes les instructions de définition de privilèges : **Grant** et **Revoke**.  
  
 La valeur 0 est retournée si les catalogues ne sont pas pris en charge par la source de données. Pour déterminer si les catalogues sont pris en charge, une application appelle **SQLGetInfo** avec le type d’informations SQL_CATALOG_NAME. Un pilote SQL-92 Full-conforme renverra toujours un masque de bits avec tous ces bits définis.  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_QUALIFIER_USAGE.  
  
 SQL_COLLATION_SEQ (ODBC 3,0)  
 Nom de la séquence de classement. Il s’agit d’une chaîne de caractères qui indique le nom du classement par défaut pour le jeu de caractères par défaut pour ce serveur (par exemple, « ISO 8859-1 » ou EBCDIC). S’il est inconnu, une chaîne vide est retournée. Un pilote SQL-92 Full-conforme retourne toujours une chaîne non vide.  
  
 SQL_COLUMN_ALIAS (ODBC 2,0)  
 Chaîne de caractères : « Y » si la source de données prend en charge les alias de colonne ; Sinon, « N ».  
  
 Un alias de colonne est un autre nom qui peut être spécifié pour une colonne de la liste de sélection à l’aide d’une clause AS. Un pilote conforme au niveau d’entrée SQL-92 retourne toujours « Y ».  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1,0)  
 Valeur SQLUSMALLINT qui indique comment la source de données gère la concaténation des colonnes de type de données character de valeur NULL avec des colonnes de type de données character de valeur non NULL :  
  
 SQL_CB_NULL = le résultat est une valeur NULL.  
  
 SQL_CB_NON_NULL = le résultat est la concaténation d’une ou de plusieurs colonnes de valeur non NULL.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_ DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1,0)  
 Masque de SQLUINTEGER. Le masque de masque de données indique les conversions prises en charge par la source de données avec la fonction scalaire **Convert** pour les données du type nommé dans l' *infotype*. Si le masque de masque de données est égal à zéro, la source de données ne prend pas en charge les conversions de données du type nommé, y compris la conversion vers le même type de données.  
  
 Par exemple, pour déterminer si une source de données prend en charge la conversion de données SQL_INTEGER en SQL_BIGINT type de données, une application appelle **SQLGetInfo** avec l' *infotype* de SQL_CONVERT_INTEGER. L’application effectue une opération **and** avec le masque de masque et le SQL_CVT_BIGINT retournés. Si la valeur résultante est différente de zéro, la conversion est prise en charge.  
  
 Les masques de détours suivants sont utilisés pour déterminer les conversions prises en charge :  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1,0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1,0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL _CVT_INTERVAL_YEAR_MONTH (ODBC 3.0) SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0) SQL_CVT_LONGVARBINARY (ODBC 1.0) SQL_CVT_LONGVARCHAR (ODBC 1.0) SQL_CVT_NUMERIC (ODBC 1.0) SQL_CVT_REAL ODBC 1.0) SQL_CVT_SMALLINT (ODBC 1.0) SQL_CVT_TIME (ODBC 1.0) SQL_CVT_ TIMESTAMP (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1,0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1,0)  
 Masque de SQLUINTEGER qui énumère les fonctions de conversion scalaires prises en charge par le pilote et la source de données associée.  
  
 Le masque de masque suivant est utilisé pour déterminer les fonctions de conversion prises en charge :  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1,0)  
 Valeur SQLUSMALLINT qui indique si les noms de corrélation de table sont pris en charge :  
  
 SQL_CN_NONE = les noms de corrélation ne sont pas pris en charge.  
  
 SQL_CN_DIFFERENT = les noms de corrélation sont pris en charge, mais ils doivent être différents des noms des tables qu’ils représentent.  
  
 SQL_CN_ANY = les noms de corrélation sont pris en charge et peuvent être n’importe quel nom défini par l’utilisateur valide.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours SQL_CN_ANY.  
  
 SQL_CREATE_ASSERTION (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans l’instruction **Create assertion** , comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CA_CREATE_ASSERTION  
  
 Les bits suivants spécifient l’attribut de contrainte pris en charge si la possibilité de spécifier des attributs de contrainte explicitement est prise en charge (voir les types d’informations SQL_ALTER_TABLE et SQL_CREATE_TABLE) :  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Un pilote SQL-92 Full-conforme retourne toujours toutes les options prises en charge. Une valeur de retour de « 0 » signifie que l’instruction **Create assertion** n’est pas prise en charge.  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Create Character Set** , comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Un pilote SQL-92 Full-conforme retourne toujours toutes les options prises en charge. Une valeur de retour de « 0 » signifie que l’instruction **Create Character Set** n’est pas prise en charge.  
  
 SQL_CREATE_COLLATION (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans l’instruction **Create collation** , comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de masque suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Un pilote SQL-92 Full-conforme retourne toujours cette option comme pris en charge. La valeur de retour « 0 » signifie que l’instruction **Create collation** n’est pas prise en charge.  
  
 SQL_CREATE_DOMAIN (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Create Domain** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CDO_CREATE_DOMAIN = l’instruction CREATe DOMAIN est prise en charge (niveau intermédiaire).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<> de définition du nom de la contrainte est pris en charge pour l’attribution de noms aux contraintes de domaine (niveau intermédiaire).  
  
 Les bits suivants spécifient la possibilité de créer des contraintes de colonne : SQL_CDO_DEFAULT = la spécification de contraintes de domaine est prise en charge (niveau intermédiaire) SQL_CDO_CONSTRAINT = la spécification des valeurs par défaut du domaine est prise en charge (niveau intermédiaire) SQL_CDO_COLLATION = La spécification du classement du domaine est prise en charge (niveau complet)  
  
 Les bits suivants spécifient les attributs de contrainte pris en charge si la spécification de contraintes de domaine est prise en charge (SQL_CDO_DEFAULT est défini) :  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) SQL_CDO_CONSTRAINT_DEFERRABLE (niveau complet) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (niveau complet)  
  
 Une valeur de retour de « 0 » signifie que l’instruction **Create Domain** n’est pas prise en charge.  
  
 SQL_CREATE_SCHEMA (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Create Schema** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Un pilote conforme au niveau intermédiaire SQL-92 retourne toujours les options SQL_CS_CREATE_SCHEMA et SQL_CS_AUTHORIZATION prises en charge. Ils doivent également être pris en charge au niveau de l’entrée SQL-92, mais pas nécessairement en tant qu’instructions SQL. Un pilote SQL-92 Full-conforme retourne toujours toutes les options prises en charge.  
  
 SQL_CREATE_TABLE (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans l’instruction **Create table** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CT_CREATE_TABLE = l’instruction CREATE TABLE est prise en charge. (Niveau d’entrée)  
  
 SQL_CT_TABLE_CONSTRAINT = la spécification de contraintes de table est prise en charge (niveau de transition FIPS)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = la \<clause de> de définition du nom de la contrainte est prise en charge pour les contraintes de colonne et de table (niveau intermédiaire)  
  
 Les bits suivants spécifient la possibilité de créer des tables temporaires :  
  
 SQL_CT_COMMIT_PRESERVE = les lignes supprimées sont conservées lors de la validation. (Niveau complet) SQL_CT_COMMIT_DELETE = les lignes supprimées sont supprimées lors de la validation. (Niveau complet) SQL_CT_GLOBAL_TEMPORARY = les tables temporaires globales peuvent être créées. (Niveau complet) SQL_CT_LOCAL_TEMPORARY = les tables temporaires locales peuvent être créées. (Niveau complet)  
  
 Les bits suivants spécifient la possibilité de créer des contraintes de colonne :  
  
 SQL_CT_COLUMN_CONSTRAINT = la spécification de contraintes de colonne est prise en charge (niveau de transition FIPS) SQL_CT_COLUMN_DEFAULT = la spécification des valeurs par défaut des colonnes est prise en charge (niveau de transition FIPS) SQL_CT_COLUMN_COLLATION = la spécification du classement de la colonne est pris en charge (niveau complet)  
  
 Les bits suivants spécifient les attributs de contrainte pris en charge si la spécification de contraintes de colonne ou de table est prise en charge :  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) SQL_CT_CONSTRAINT_DEFERRABLE (niveau complet) SQL_CT_CONSTRAINT_NON_DEFERRABLE (niveau complet)  
  
 SQL_CREATE_TRANSLATION (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Create translation** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de masque suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Un pilote SQL-92 Full-conforme retourne toujours ces options comme pris en charge. La valeur de retour « 0 » signifie que l’instruction **Create translation** n’est pas prise en charge.  
  
 SQL_CREATE_VIEW (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Create View** , comme défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Une valeur de retour de « 0 » signifie que l’instruction **Create View** n’est pas prise en charge.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours les options SQL_CV_CREATE_VIEW et SQL_CV_CHECK_OPTION prises en charge.  
  
 Un pilote SQL-92 Full-conforme retourne toujours toutes les options prises en charge.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1,0)  
 Valeur SQLUSMALLINT qui indique comment une opération de **validation** affecte les curseurs et les instructions préparées dans la source de données (le comportement de la source de données lorsque vous validez une transaction).  
  
 La valeur de cet attribut reflète l’état actuel du paramètre suivant : SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = fermeture des curseurs et suppression des instructions préparées. Pour réutiliser le curseur, l’application doit repréparer et réexécuter l’instruction.  
  
 SQL_CB_CLOSE = fermer les curseurs. Pour les instructions préparées, l’application peut appeler **SQLExecute** sur l’instruction sans appeler de nouveau **SQLPrepare** . La valeur par défaut du pilote ODBC SQL est SQL_CB_CLOSE. Cela signifie que le pilote ODBC SQL va fermer vos curseurs lorsque vous validez une transaction.  
  
 SQL_CB_PRESERVE = conserver les curseurs à la même position qu’avant l’opération de **validation** . L’application peut continuer à extraire des données, ou elle peut fermer le curseur et exécuter à nouveau l’instruction sans la repréparer.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1,0)  
 Valeur SQLUSMALLINT qui indique comment une opération **Rollback** affecte les curseurs et les instructions préparées dans la source de données :  
  
 SQL_CB_DELETE = fermeture des curseurs et suppression des instructions préparées. Pour réutiliser le curseur, l’application doit repréparer et réexécuter l’instruction.  
  
 SQL_CB_CLOSE = fermer les curseurs. Pour les instructions préparées, l’application peut appeler **SQLExecute** sur l’instruction sans appeler de nouveau **SQLPrepare** .  
  
 SQL_CB_PRESERVE = conserver les curseurs à la même position qu’avant l’opération de **restauration** . L’application peut continuer à extraire des données, ou elle peut fermer le curseur et réexécuter l’instruction sans la repréparer.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3,0)  
 Valeur SQLUINTEGER qui indique la prise en charge de la sensibilité du curseur :  
  
 SQL_INSENSITIVE = tous les curseurs sur le descripteur d’instruction affichent le jeu de résultats sans refléter les modifications qui lui ont été apportées par un autre curseur au sein de la même transaction.  
  
 SQL_UNSPECIFIED = il n’est pas spécifié si les curseurs sur le descripteur d’instruction rendent visibles les modifications apportées à un jeu de résultats par un autre curseur au sein de la même transaction. Les curseurs sur le descripteur d’instruction peuvent rendre visible aucune, certaines ou toutes ces modifications.  
  
 SQL_SENSITIVE = les curseurs sont sensibles aux modifications apportées par d’autres curseurs au sein de la même transaction.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours l’option SQL_UNSPECIFIED comme pris en charge.  
  
 Un pilote SQL-92 Full-conforme retourne toujours l’option SQL_INSENSITIVE comme pris en charge.  
  
 SQL_DATA_SOURCE_NAME (ODBC 1,0)  
 Chaîne de caractères avec le nom de la source de données qui a été utilisée pendant la connexion. Si l’application appelée **SQLConnect**, il s’agit de la valeur de l’argument *szDSN* . Si l’application a appelé **SQLDriverConnect** ou **SQLBrowseConnect**, il s’agit de la valeur du mot clé DSN dans la chaîne de connexion transmise au pilote. Si la chaîne de connexion ne contenait pas le mot clé **DSN** (par exemple, si elle contient le mot clé **Driver** ), il s’agit d’une chaîne vide.  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1,0)  
 Chaîne de caractères. « Y » si la source de données est définie en mode lecture seule, « N » dans le cas contraire.  
  
 Cette caractéristique concerne uniquement la source de données elle-même ; il ne s’agit pas d’une caractéristique du pilote qui permet d’accéder à la source de données. Un pilote qui est en lecture/écriture peut être utilisé avec une source de données en lecture seule. Si un pilote est en lecture seule, toutes ses sources de données doivent être en lecture seule et doivent retourner SQL_DATA_SOURCE_READ_ONLY.  
  
 SQL_DATABASE_NAME (ODBC 1,0)  
 Chaîne de caractères avec le nom de la base de données actuelle en cours d’utilisation, si la source de données définit un objet nommé appelé « base de données ».  
  
> [!NOTE]
>  Dans ODBC 3 *. x*, la valeur retournée pour cet *infotype* peut également être retournée en appelant **SQLGetConnectAttr** avec un argument d' *attribut* de SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS (ODBC 3,0)  
 Masque de bits SQLUINTEGER énumérant les littéraux SQL-92 DateTime pris en charge par la source de données. Notez qu’il s’agit des littéraux datetime répertoriés dans la spécification SQL-92 et sont distincts des clauses d’échappement littérales DateTime définies par ODBC. Pour plus d’informations sur les clauses d’échappement littérales DateTime ODBC, consultez [littéraux de date, d’heure et d’horodatage](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Un pilote conforme au niveau de transition FIPS retourne toujours la valeur « 1 » dans le masque de bits pour les bits de la liste suivante. La valeur « 0 » signifie que les littéraux SQL-92 DateTime ne sont pas pris en charge.  
  
 Les masques de détours suivants sont utilisés pour déterminer les littéraux pris en charge :  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_ SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1,0)  
 Chaîne de caractères portant le nom du produit SGBD auquel le pilote accède.  
  
 SQL_DBMS_VER (ODBC 1,0)  
 Chaîne de caractères qui indique la version du produit SGBD accessible par le pilote. La version se présente sous la forme # #. # #. # # # #, où les deux premiers chiffres correspondent à la version principale, les deux chiffres suivants correspondent à la version mineure et les quatre derniers chiffres à la version finale. Le pilote doit afficher la version du produit SGBD dans ce format, mais il peut également ajouter la version propre au produit SGBD. Par exemple, « 04.01.0000 Rdb 4,1 ».  
  
 SQL_DDL_INDEX (ODBC 3,0)  
 Valeur SQLUINTEGER qui indique la prise en charge de la création et de la suppression d’index :  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1,0)  
 Valeur SQLUINTEGER qui indique le niveau d’isolation de la transaction par défaut pris en charge par le pilote ou la source de données, ou zéro si la source de données ne prend pas en charge les transactions. Les termes suivants sont utilisés pour définir les niveaux d’isolation des transactions :  
  
 **Lecture incorrecte** La transaction 1 modifie une ligne. La transaction 2 lit la ligne modifiée avant que la transaction 1 valide la modification. Si la transaction 1 restaure la modification, la transaction 2 aura lu une ligne considérée comme n’ayant jamais existé.  
  
 **Lecture non renouvelable** La transaction 1 lit une ligne. La transaction 2 met à jour ou supprime cette ligne et valide cette modification. Si la transaction 1 tente de relire la ligne, elle reçoit des valeurs de ligne différentes ou découvre que la ligne a été supprimée.  
  
 **Fantôme** La transaction 1 lit un ensemble de lignes qui répondent à certains critères de recherche. La transaction 2 génère une ou plusieurs lignes (à l’aide d’insertions ou de mises à jour) correspondant aux critères de recherche. Si la transaction 1 Réexécute l’instruction qui lit les lignes, elle reçoit un ensemble de lignes différent.  
  
 Si la source de données prend en charge les transactions, le pilote retourne l’un des masques de données suivants :  
  
 SQL_TXN_READ_UNCOMMITTED = les lectures erronées, les lectures non reproductibles et les fantômes sont possibles.  
  
 SQL_TXN_READ_COMMITTED = les lectures erronées ne sont pas possibles. Les lectures et fantômes qui ne sont pas reproductibles sont possibles.  
  
 SQL_TXN_REPEATABLE_READ = les lectures erronées et les lectures non reproductibles ne sont pas possibles. Les fantômes sont possibles.  
  
 SQL_TXN_SERIALIZABLE = les transactions sont sérialisables. Les transactions sérialisables n’autorisent pas les lectures erronées, les lectures non reproductibles ou les fantômes.  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3,0)  
 Chaîne de caractères : « Y » si les paramètres peuvent être décrits ; « N », dans le cas contraire.  
  
 Un pilote SQL-92 Full-conforme retourne généralement « Y », car il prend en charge l’instruction de **Description** de l’entrée. Étant donné que cela ne spécifie pas directement la prise en charge SQL sous-jacente, toutefois, la description des paramètres peut ne pas être prise en charge, même dans un pilote SQL-92 Full-conforme.  
  
 SQL_DM_VER (ODBC 3,0)  
 Chaîne de caractères avec la version du gestionnaire de pilotes. La version se présente sous la forme # #. # #. # # # #. # # # #, où :  
  
 Le premier ensemble de deux chiffres est la version principale de ODBC, comme indiqué par la constante SQL_SPEC_MAJOR.  
  
 Le deuxième ensemble de deux chiffres est la version ODBC mineure, comme indiqué par la constante SQL_SPEC_MINOR.  
  
 Le troisième ensemble de quatre chiffres est le numéro de version majeure du gestionnaire de pilotes.  
  
 Le dernier jeu de quatre chiffres est le numéro de build mineur du gestionnaire de pilotes.  
  
 La version du gestionnaire de pilotes Windows 7 est 03,80. La version du gestionnaire de pilotes Windows 8 est 03,81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3,8)  
 Valeur SQLUINTEGER qui indique si le pilote prend en charge le regroupement reconnaissant les pilotes. (Pour plus d’informations, consultez [regroupement de connexions prenant en charge les pilotes](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE indique que le pilote peut prendre en charge le mécanisme de regroupement prenant en charge les pilotes.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE indique que le pilote ne prend pas en charge le mécanisme de regroupement reconnaissant les pilotes.  
  
 Un pilote n’a pas besoin d’implémenter SQL_DRIVER_AWARE_POOLING_SUPPORTED et le gestionnaire de pilotes n’honorera pas la valeur de retour du pilote.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1,0)  
 Valeur SQLULEN, handle d’environnement ou descripteur de connexion du pilote, déterminé par l' *infotype*de l’argument.  
  
 Ces types d’informations sont implémentés uniquement par le gestionnaire de pilotes.  
  
 SQL_DRIVER_HDESC (ODBC 3,0)  
 Une valeur SQLULEN, le handle de descripteur du pilote, déterminé par le handle du descripteur du gestionnaire de pilotes \*, qui doit être transmis en entrée dans *InfoValuePtr* à partir de l’application. Dans ce cas, *InfoValuePtr* est à la fois un argument d’entrée et de sortie. Le handle de descripteur \*d’entrée passé dans *InfoValuePtr* doit avoir été alloué explicitement ou implicitement sur le *ConnectionHandle*.  
  
 L’application doit faire une copie du descripteur du gestionnaire de pilotes avant d’appeler **SQLGetInfo** avec ce type d’informations, afin de s’assurer que le descripteur n’est pas remplacé lors de la sortie.  
  
 Ce type d’informations est implémenté uniquement par le gestionnaire de pilotes.  
  
 SQL_DRIVER_HLIB (ODBC 2,0)  
 Une valeur SQLULEN, le *HINST* de la bibliothèque de chargement retourné au gestionnaire de pilotes lorsqu’il a chargé la dll du pilote sur un système d’exploitation Microsoft Windows, ou son équivalent sur un autre système d’exploitation. Le handle est valide uniquement pour le handle de connexion spécifié dans l’appel à **SQLGetInfo**.  
  
 Ce type d’informations est implémenté uniquement par le gestionnaire de pilotes.  
  
 SQL_DRIVER_HSTMT (ODBC 1,0)  
 Une valeur SQLULEN, le descripteur d’instruction du pilote déterminé par le descripteur d’instruction du gestionnaire de pilotes \*, qui doit être transmis en entrée dans *InfoValuePtr* à partir de l’application. Dans ce cas, *InfoValuePtr* est à la fois un argument d’entrée et un argument de sortie. Le descripteur d’instruction \*d’entrée passé dans *InfoValuePtr* doit avoir été alloué sur l’argument *ConnectionHandle*.  
  
 L’application doit faire une copie du descripteur d’instruction du gestionnaire de pilotes avant d’appeler **SQLGetInfo** avec ce type d’informations, pour s’assurer que le descripteur n’est pas remplacé lors de la sortie.  
  
 Ce type d’informations est implémenté uniquement par le gestionnaire de pilotes.  
  
 SQL_DRIVER_NAME (ODBC 1,0)  
 Chaîne de caractères avec le nom de fichier du pilote utilisé pour accéder à la source de données.  
  
 SQL_DRIVER_ODBC_VER (ODBC 2,0)  
 Chaîne de caractères avec la version d’ODBC que le pilote prend en charge. La version se présente sous la forme # #. # #, où les deux premiers chiffres correspondent à la version principale et les deux chiffres suivants à la version mineure. SQL_SPEC_MAJOR et SQL_SPEC_MINOR définir les numéros de version majeure et mineure. Pour la version de ODBC décrite dans ce manuel, il s’agit de 3 et 0, et le pilote doit retourner « 03,00 ».  
  
 Le gestionnaire de pilotes ODBC ne modifiera pas la valeur de retour de SQLGetInfo (SQL_DRIVER_ODBC_VER) pour maintenir la compatibilité descendante pour les applications existantes. Le pilote spécifie la valeur qui sera retournée. Toutefois, un pilote qui prend en charge l’extensibilité du type de données C doit retourner 3,8 (ou une version ultérieure) lorsqu’une application appelle **SQLSetEnvAttr** pour définir SQL_ATTR_ODBC_VERSION sur 3,8. Pour plus d’informations, consultez [types de données C dans ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER (ODBC 1,0)  
 Chaîne de caractères avec la version du pilote et éventuellement une description du pilote. Au minimum, la version se présente sous la forme # #. # #. # # # #, où les deux premiers chiffres correspondent à la version principale, les deux chiffres suivants correspondent à la version mineure et les quatre derniers chiffres à la version finale.  
  
 SQL_DROP_ASSERTION (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans l’instruction **Drop assertion** , comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de masque suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DA_DROP_ASSERTION  
  
 Un pilote SQL-92 Full-conforme retourne toujours cette option comme pris en charge.  
  
 SQL_DROP_CHARACTER_SET (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Drop Character Set** , comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de masque suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Un pilote SQL-92 Full-conforme retourne toujours cette option comme pris en charge.  
  
 SQL_DROP_COLLATION (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans l’instruction **Drop collation** , comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de masque suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DC_DROP_COLLATION  
  
 Un pilote SQL-92 Full-conforme retourne toujours cette option comme pris en charge.  
  
 SQL_DROP_DOMAIN (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses dans l’instruction **Drop Domain** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Un pilote conforme au niveau intermédiaire SQL-92 retourne toujours toutes les options prises en charge.  
  
 SQL_DROP_SCHEMA (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Drop Schema** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Un pilote conforme au niveau intermédiaire SQL-92 retourne toujours toutes les options prises en charge.  
  
 SQL_DROP_TABLE (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **drop table** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Un pilote conforme au niveau de transition FIPS retourne toujours toutes les options prises en charge.  
  
 SQL_DROP_TRANSLATION (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Drop translation** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Le masque de masque suivant est utilisé pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Un pilote SQL-92 Full-conforme retourne toujours cette option comme pris en charge.  
  
 SQL_DROP_VIEW (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **Drop View** , tel que défini dans SQL-92, pris en charge par la source de données.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Un pilote conforme au niveau de transition FIPS retourne toujours toutes les options prises en charge.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Masque de SQLUINTEGER qui décrit les attributs d’un curseur dynamique qui sont pris en charge par le pilote. Ce masque de réinitialisation contient le premier sous-ensemble d’attributs ; pour le deuxième sous-ensemble, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Les masques de détours suivants sont utilisés pour déterminer les attributs pris en charge :  
  
 SQL_CA1_NEXT = un argument *FetchOrientation* de SQL_FETCH_NEXT est pris en charge dans un appel à **SQLFetchScroll** lorsque le curseur est un curseur dynamique.  
  
 Les arguments SQL_CA1_ABSOLUTE = *FetchOrientation* des SQL_FETCH_FIRST, SQL_FETCH_LAST et SQL_FETCH_ABSOLUTE sont pris en charge dans un appel à **SQLFetchScroll** lorsque le curseur est un curseur dynamique. (L’ensemble de lignes qui sera récupéré est indépendant de la position actuelle du curseur.)  
  
 Les arguments SQL_CA1_RELATIVE = *FetchOrientation* de SQL_FETCH_PRIOR et SQL_FETCH_RELATIVE sont pris en charge dans un appel à **SQLFetchScroll** lorsque le curseur est un curseur dynamique. (L’ensemble de lignes qui sera récupéré dépend de la position actuelle du curseur. Notez que cela est séparé de SQL_FETCH_NEXT, car dans un curseur avant uniquement, seul SQL_FETCH_NEXT est pris en charge.)  
  
 SQL_CA1_BOOKMARK = un argument *FetchOrientation* de SQL_FETCH_BOOKMARK est pris en charge dans un appel à **SQLFetchScroll** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_EXCLUSIVE = un argument *LockType* de SQL_LOCK_EXCLUSIVE est pris en charge dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_NO_CHANGE = un argument *LockType* de SQL_LOCK_NO_CHANGE est pris en charge dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_LOCK_UNLOCK = un argument *LockType* de SQL_LOCK_UNLOCK est pris en charge dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_POSITION = un argument *operation* de SQL_POSITION est pris en charge dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_UPDATE = un argument *operation* de SQL_UPDATE est pris en charge dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_DELETE = un argument *operation* de SQL_DELETE est pris en charge dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POS_REFRESH = un argument *operation* de SQL_REFRESH est pris en charge dans un appel à **SQLSetPos** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_POSITIONED_UPDATE = mise à jour dans laquelle l’instruction SQL CURRENT est prise en charge lorsque le curseur est un curseur dynamique. (Un pilote conforme au niveau d’entrée SQL-92 retourne toujours cette option comme pris en charge.)  
  
 SQL_CA1_POSITIONED_DELETE = une instruction DELETE où CURRENT de l’instruction SQL est prise en charge lorsque le curseur est un curseur dynamique. (Un pilote conforme au niveau d’entrée SQL-92 retourne toujours cette option comme pris en charge.)  
  
 SQL_CA1_SELECT_FOR_UPDATE = une instruction SELECT FOR UPDATE SQL est prise en charge lorsque le curseur est un curseur dynamique. (Un pilote conforme au niveau d’entrée SQL-92 retourne toujours cette option comme pris en charge.)  
  
 SQL_CA1_BULK_ADD = un argument *operation* de SQL_ADD est pris en charge dans un appel à **SQLBulkOperations** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = un argument *operation* de SQL_UPDATE_BY_BOOKMARK est pris en charge dans un appel à **SQLBulkOperations** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = un argument *operation* de SQL_DELETE_BY_BOOKMARK est pris en charge dans un appel à **SQLBulkOperations** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = un argument *operation* de SQL_FETCH_BY_BOOKMARK est pris en charge dans un appel à **SQLBulkOperations** lorsque le curseur est un curseur dynamique.  
  
 Un pilote de conformité de niveau intermédiaire SQL-92 retourne généralement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE comme pris en charge, car il prend en charge les curseurs à défilement par le biais de l’instruction SQL FETCH incorporée. Étant donné que cela ne détermine pas directement la prise en charge SQL sous-jacente, toutefois, les curseurs avec défilement peuvent ne pas être pris en charge, même pour un pilote conforme au niveau intermédiaire SQL-92.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Masque de SQLUINTEGER qui décrit les attributs d’un curseur dynamique qui sont pris en charge par le pilote. Ce masque de réplicas contient le deuxième sous-ensemble d’attributs ; pour le premier sous-ensemble, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Les masques de détours suivants sont utilisés pour déterminer les attributs pris en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = un curseur dynamique en lecture seule, dans lequel aucune mise à jour n’est autorisée, est pris en charge. (L’attribut d’instruction SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_READ_ONLY pour un curseur dynamique).  
  
 SQL_CA2_LOCK_CONCURRENCY = un curseur dynamique qui utilise le niveau de verrouillage le plus bas suffisant pour s’assurer que la ligne peut être mise à jour est prise en charge. (L’attribut d’instruction SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_LOCK pour un curseur dynamique.) Ces verrous doivent être cohérents avec le niveau d’isolation de la transaction défini par l’attribut de connexion SQL_ATTR_TXN_ISOLATION.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = un curseur dynamique qui utilise le contrôle d’accès concurrentiel optimiste comparant les versions de ligne est pris en charge. (L’attribut d’instruction SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_ROWVER pour un curseur dynamique.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = un curseur dynamique qui utilise le contrôle d’accès concurrentiel optimiste comparant les valeurs est pris en charge. (L’attribut d’instruction SQL_ATTR_CONCURRENCY peut être SQL_CONCUR_VALUES pour un curseur dynamique.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = des lignes ajoutées sont visibles par un curseur dynamique ; le curseur peut défiler jusqu’à ces lignes. (Où ces lignes sont ajoutées au curseur dépend du pilote.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = les lignes supprimées ne sont plus disponibles pour un curseur dynamique et ne laissent pas de « trous » dans le jeu de résultats ; une fois que le curseur dynamique fait défiler une ligne supprimée, il ne peut pas revenir à cette ligne.  
  
 SQL_CA2_SENSITIVITY_UPDATES = les mises à jour des lignes sont visibles par un curseur dynamique ; Si le curseur dynamique défile et retourne à une ligne mise à jour, les données retournées par le curseur sont les données mises à jour, et non les données d’origine.  
  
 SQL_CA2_MAX_ROWS_SELECT = l’attribut d’instruction SQL_ATTR_MAX_ROWS affecte les instructions **Select** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_INSERT = l’attribut d’instruction SQL_ATTR_MAX_ROWS affecte les instructions **Insert** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_DELETE = l’attribut d’instruction SQL_ATTR_MAX_ROWS affecte les instructions **Delete** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_UPDATE = l’attribut d’instruction SQL_ATTR_MAX_ROWS affecte les instructions **Update** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_CATALOG = l’attribut d’instruction SQL_ATTR_MAX_ROWS affecte les jeux de résultats de **catalogue** lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = l’attribut d’instruction SQL_ATTR_MAX_ROWS affecte les instructions **Select**, **Insert**, **Delete**et **Update** , ainsi que les jeux de résultats de **catalogue** , lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_CRC_EXACT = le nombre exact de lignes est disponible dans le champ SQL_DIAG_CURSOR_ROW_COUNT diagnostic lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_CRC_APPROXIMATE = un nombre de lignes approximatif est disponible dans le champ SQL_DIAG_CURSOR_ROW_COUNT diagnostic lorsque le curseur est un curseur dynamique.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = le pilote ne garantit pas que les instructions de mise à jour ou de suppression positionnées n’affecteront qu’une seule ligne quand le curseur est un curseur dynamique ; C’est la responsabilité de l’application de le garantir. (Si une instruction affecte plus d’une ligne, **SQLExecute** ou **SQLExecDirect** retourne SQLState 01001 [curseur opération Conflict].) Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_SIMULATE_CURSOR défini sur SQL_SC_NON_UNIQUE.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = le pilote tente de garantir que les instructions de mise à jour ou de suppression positionnées n’affectent qu’une seule ligne lorsque le curseur est un curseur dynamique. Le pilote exécute toujours ces instructions, même si elles peuvent affecter plusieurs lignes, par exemple en l’absence de clé unique. (Si une instruction affecte plus d’une ligne, **SQLExecute** ou **SQLExecDirect** retourne SQLState 01001 [curseur opération Conflict].) Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_SIMULATE_CURSOR défini sur SQL_SC_TRY_UNIQUE.  
  
 SQL_CA2_SIMULATE_UNIQUE = le pilote garantit que les instructions Update ou DELETE positionnées n’affecteront qu’une seule ligne lorsque le curseur est un curseur dynamique. Si le pilote ne peut pas garantir cela pour une instruction donnée, **SQLExecDirect** ou **SQLPrepare** retourne SQLState 01001 (conflit d’opération de curseur). Pour définir ce comportement, l’application appelle **SQLSetStmtAttr** avec l’attribut SQL_ATTR_SIMULATE_CURSOR défini sur SQL_SC_UNIQUE.  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1,0)  
 Chaîne de caractères : « Y » si la source de données prend en charge les expressions dans la liste **order by** ; « N » dans le cas contraire.  
  
 SQL_FILE_USAGE (ODBC 2,0)  
 Valeur SQLUSMALLINT qui indique comment un pilote à un seul niveau traite directement les fichiers dans une source de données :  
  
 SQL_FILE_NOT_SUPPORTED = le pilote n’est pas un pilote à niveau unique. Par exemple, un pilote ORACLE est un pilote à deux niveaux.  
  
 SQL_FILE_TABLE = un pilote à niveau unique traite les fichiers d’une source de données en tant que tables. Par exemple, un pilote xbase traite chaque fichier xbase comme une table.  
  
 SQL_FILE_CATALOG = un pilote à niveau unique traite les fichiers d’une source de données comme un catalogue. Par exemple, un pilote Microsoft Access traite chaque fichier Microsoft Access comme une base de données complète.  
  
 Une application peut l’utiliser pour déterminer la manière dont les utilisateurs sélectionnent les données. Par exemple, xbase les utilisateurs considèrent souvent les données comme stockées dans des fichiers, tandis que les utilisateurs ORACLE et Microsoft Access considèrent généralement les données comme stockées dans les tables.  
  
 Lorsqu’un utilisateur sélectionne une source de données xBase, l’application peut afficher la boîte de dialogue **ouvrir un fichier** commun de Windows. Lorsque l’utilisateur sélectionne une source de données Microsoft Access ou ORACLE, l’application peut afficher une boîte de dialogue **Sélectionner une table** personnalisée.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Masque de bits SQLUINTEGER qui décrit les attributs d’un curseur avant uniquement qui sont pris en charge par le pilote. Ce masque de réinitialisation contient le premier sous-ensemble d’attributs ; pour le deuxième sous-ensemble, consultez SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Les masques de détours suivants sont utilisés pour déterminer les attributs pris en charge :  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_ UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (et remplacez « curseur avant uniquement » par « curseur dynamique » dans les descriptions).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Masque de bits SQLUINTEGER qui décrit les attributs d’un curseur avant uniquement qui sont pris en charge par le pilote. Ce masque de réplicas contient le deuxième sous-ensemble d’attributs ; pour le premier sous-ensemble, consultez SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Les masques de détours suivants sont utilisés pour déterminer les attributs pris en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (et remplacez « curseur avant uniquement » par « curseur dynamique » dans les descriptions).  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2,0)  
 Un masque de SQLUINTEGER qui énumère les extensions de **SQLGetData**.  
  
 Les masques de transparence suivants sont utilisés avec l’indicateur pour déterminer les extensions communes prises en charge par le pilote pour **SQLGetData**:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** peut être appelé pour toute colonne non liée, y compris celles antérieures à la dernière colonne liée. Notez que les colonnes doivent être appelées par ordre croissant de nombre de colonnes, sauf si SQL_GD_ANY_ORDER est également retourné.  
  
 SQL_GD_ANY_ORDER = **SQLGetData** peut être appelé pour les colonnes indépendantes dans n’importe quel ordre. Notez que **SQLGetData** peut être appelé uniquement pour les colonnes qui suivent la dernière colonne liée, sauf si SQL_GD_ANY_COLUMN est également retourné.  
  
 SQL_GD_BLOCK = **SQLGetData** peut être appelé pour une colonne indépendante dans n’importe quelle ligne d’un bloc (où la taille de l’ensemble de lignes est supérieure à 1) des données après leur positionnement sur cette ligne avec **SQLSetPos**.  
  
 SQL_GD_BOUND = **SQLGetData** peut être appelé pour les colonnes dépendantes en plus des colonnes indépendantes. Un pilote ne peut pas retourner cette valeur sauf s’il retourne également SQL_GD_ANY_COLUMN.  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData** peut être appelé pour retourner les valeurs des paramètres de sortie. Pour plus d’informations, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** est requis pour retourner des données uniquement à partir de colonnes indépendantes qui se trouvent après la dernière colonne liée, sont appelées par ordre d’incrémentation du numéro de colonne et ne figurent pas dans une ligne d’un bloc de lignes.  
  
 Si un pilote prend en charge les signets (de longueur fixe ou variable), il doit prendre en charge l’appel de **SQLGetData** sur la colonne 0. Cette prise en charge est requise indépendamment de ce que le pilote retourne pour un appel à **SQLGetInfo** avec l' *infotype*SQL_GETDATA_EXTENSIONS.  
  
 SQL_GROUP_BY (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie la relation entre les colonnes dans la clause **Group by** et les colonnes non agrégées dans la liste de sélection :  
  
 SQL_GB_COLLATE = une clause **COLLATE** peut être spécifiée à la fin de chaque colonne de regroupement. (ODBC 3,0)  
  
 SQL_GB_NOT_SUPPORTED = les clauses **Group by** ne sont pas prises en charge. (ODBC 2,0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = la clause **Group by** doit contenir toutes les colonnes non agrégées dans la liste de sélection. Elle ne peut pas contenir d’autres colonnes. Par exemple, **Sélectionnez Dept, Max (salary) from employee Group by Dept**. (ODBC 2,0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = la clause **Group by** doit contenir toutes les colonnes non agrégées dans la liste de sélection. Elle peut contenir des colonnes qui ne figurent pas dans la liste de sélection. Par exemple, **Sélectionnez Dept, Max (salary) from employee Group by Dept, Age**. (ODBC 2,0)  
  
 SQL_GB_NO_RELATION = les colonnes dans la clause **Group by** et la liste de sélection ne sont pas liées. La signification des colonnes non groupées non regroupées dans la liste de sélection dépend de la source de données. Par exemple, **Sélectionnez Dept, Salary from employee Group by Dept, Age**. (ODBC 2,0)  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours l’option SQL_GB_GROUP_BY_EQUALS_SELECT comme pris en charge. Un pilote SQL-92 Full-conforme retourne toujours l’option SQL_GB_COLLATE comme pris en charge. Si aucune des options n’est prise en charge, la clause **Group by** n’est pas prise en charge par la source de données.  
  
 SQL_IDENTIFIER_CASE (ODBC 1,0)  
 Une valeur SQLUSMALLINT comme suit :  
  
 SQL_IC_UPPER = les identificateurs dans SQL ne respectent pas la casse et sont stockés en majuscules dans le catalogue système.  
  
 SQL_IC_LOWER = les identificateurs dans SQL ne respectent pas la casse et sont stockés en minuscules dans le catalogue système.  
  
 SQL_IC_SENSITIVE = les identificateurs dans SQL respectent la casse et sont stockés en casse mixte dans le catalogue système.  
  
 SQL_IC_MIXED = les identificateurs dans SQL ne respectent pas la casse et sont stockés en casse mixte dans le catalogue système.  
  
 Étant donné que les identificateurs dans SQL-92 ne respectent jamais la casse, un pilote qui est strictement conforme à SQL-92 (tout niveau) ne retournera jamais l’option SQL_IC_SENSITIVE comme pris en charge.  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1,0)  
 Chaîne de caractères utilisée comme délimiteur de début et de fin d’un identificateur entre guillemets (délimité) dans les instructions SQL. (Les identificateurs passés comme arguments aux fonctions ODBC n’ont pas besoin d’être entre guillemets.) Si la source de données ne prend pas en charge les identificateurs entre guillemets, un espace est retourné.  
  
 Cette chaîne de caractères peut également être utilisée pour citer des arguments de fonction de catalogue lorsque l’attribut de connexion SQL_ATTR_METADATA_ID est défini sur SQL_TRUE.  
  
 Étant donné que le guillemet d’identificateur dans SQL-92 est le guillemet double ("), un pilote qui est strictement conforme à SQL-92 retourne toujours le caractère guillemet double.  
  
 SQL_INDEX_KEYWORDS (ODBC 3,0)  
 Un masque de SQLUINTEGER qui énumère les mots clés de l’instruction CREATe INDEX qui sont pris en charge par le pilote :  
  
 SQL_IK_NONE = aucun des mots clés n’est pris en charge.  
  
 SQL_IK_ASC = le mot clé ASC est pris en charge.  
  
 Le mot clé SQL_IK_DESC = DESC est pris en charge.  
  
 SQL_IK_ALL = tous les mots clés sont pris en charge.  
  
 Pour déterminer si l’instruction CREATe INDEX est prise en charge, une application appelle **SQLGetInfo** avec le type d’informations SQL_DLL_INDEX.  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3,0)  
 Masque de SQLUINTEGER qui énumère les vues dans le INFORMATION_SCHEMA qui sont prises en charge par le pilote. Les vues dans et le contenu de, INFORMATION_SCHEMA sont définis dans SQL-92.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer les vues prises en charge :  
  
 SQL_ISV_ASSERTIONS = identifie les assertions du catalogue qui sont détenues par un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_CHARACTER_SETS = identifie les jeux de caractères du catalogue accessibles à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_CHECK_CONSTRAINTS = identifie les contraintes de validation qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_COLLATIONS = identifie les classements de caractères pour le catalogue qui sont accessibles à un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = identifie les colonnes du catalogue qui dépendent des domaines définis dans le catalogue et qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_COLUMN_PRIVILEGES = identifie les privilèges sur les colonnes de tables persistantes qui sont disponibles ou accordées par un utilisateur donné. (Niveau de transition FIPS)  
  
 SQL_ISV_COLUMNS = identifie les colonnes de tables persistantes accessibles par un utilisateur donné. (Niveau de transition FIPS)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = similaire à la vue de CONSTRAINT_TABLE_USAGE, les colonnes sont identifiées pour les différentes contraintes détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = identifie les tables utilisées par les contraintes (référentiel, unique et assertions) et qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = identifie les contraintes de domaine (des domaines dans le catalogue) accessibles à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_DOMAINS = identifie les domaines définis dans un catalogue qui sont accessibles à l’utilisateur. (Niveau intermédiaire)  
  
 SQL_ISV_KEY_COLUMN_USAGE = identifie les colonnes définies dans le catalogue qui sont restreintes en tant que clés par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = identifie les contraintes référentielles qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_SCHEMATA = identifie les schémas appartenant à un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_SQL_LANGUAGES = identifie les niveaux de conformité, les options et les dialectes SQL pris en charge par l’implémentation SQL. (Niveau intermédiaire)  
  
 SQL_ISV_TABLE_CONSTRAINTS = identifie les contraintes de table qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_TABLE_PRIVILEGES = identifie les privilèges sur les tables persistantes qui sont disponibles ou accordées par un utilisateur donné. (Niveau de transition FIPS)  
  
 SQL_ISV_TABLES = identifie les tables persistantes définies dans un catalogue qui sont accessibles à un utilisateur donné. (Niveau de transition FIPS)  
  
 SQL_ISV_TRANSLATIONS = identifie les traductions de caractères pour le catalogue qui sont accessibles à un utilisateur donné. (Niveau complet)  
  
 SQL_ISV_USAGE_PRIVILEGES = identifie les privilèges d’utilisation sur les objets de catalogue qui sont disponibles ou détenus par un utilisateur donné. (Niveau de transition FIPS)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = identifie les colonnes dont dépendent les vues du catalogue qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_VIEW_TABLE_USAGE = identifie les tables dont dépendent les vues du catalogue qui sont détenues par un utilisateur donné. (Niveau intermédiaire)  
  
 SQL_ISV_VIEWS = identifie les tables affichées définies dans ce catalogue qui sont accessibles à un utilisateur donné. (Niveau de transition FIPS)  
  
 SQL_INSERT_STATEMENT (ODBC 3,0)  
 Un masque de SQLUINTEGER qui indique la prise en charge des instructions **Insert** :  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours toutes les options prises en charge.  
  
 SQL_INTEGRITY (ODBC 1,0)  
 Chaîne de caractères : « Y » si la source de données prend en charge la fonctionnalité d’amélioration de l’intégrité ; « N » dans le cas contraire.  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_ODBC_SQL_OPT_IEF.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Masque de SQLUINTEGER qui décrit les attributs d’un curseur de jeu de clés pris en charge par le pilote. Ce masque de réinitialisation contient le premier sous-ensemble d’attributs ; pour le deuxième sous-ensemble, consultez SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Les masques de détours suivants sont utilisés pour déterminer les attributs pris en charge :  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (et remplacez « curseur piloté par jeu de clés » par « curseur dynamique » dans les descriptions).  
  
 Un pilote conforme au niveau intermédiaire SQL-92 retourne généralement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE comme étant prises en charge, car le pilote prend en charge les curseurs à défilement via l’instruction SQL FETCH incorporée. Étant donné que cela ne détermine pas directement la prise en charge SQL sous-jacente, toutefois, les curseurs avec défilement peuvent ne pas être pris en charge, même pour un pilote conforme au niveau intermédiaire SQL-92.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Masque de SQLUINTEGER qui décrit les attributs d’un curseur de jeu de clés pris en charge par le pilote. Ce masque de réplicas contient le deuxième sous-ensemble d’attributs ; pour le premier sous-ensemble, consultez SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Les masques de détours suivants sont utilisés pour déterminer les attributs pris en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Pour obtenir une description de ces masques de bits, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (et remplacez « curseur piloté par jeu de clés » par « curseur dynamique » dans les descriptions).  
  
 SQL_KEYWORDS (ODBC 2,0)  
 Chaîne de caractères qui contient une liste séparée par des virgules de tous les mots clés spécifiques à la source de données. Cette liste ne contient pas de mots clés spécifiques à ODBC ou de mots clés utilisés à la fois par la source de données et ODBC. Cette liste représente tous les mots clés réservés. les applications interopérables ne doivent pas utiliser ces mots dans les noms d’objets.  
  
 Pour obtenir la liste des mots clés ODBC, consultez la section [Mots clés réservés](../../../odbc/reference/appendixes/reserved-keywords.md) dans [annexe C : grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). La valeur **#define** SQL_ODBC_KEYWORDS contient une liste de mots clés ODBC séparés par des virgules.  
  
 Annexe C : Grammaire SQL  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2,0)  
 Chaîne de caractères : « Y » si la source de données prend en charge un caractère d’échappement pour le caractère de pourcentage (%) et le caractère de soulignement (_) dans un prédicat **Like** et le pilote prend en charge la syntaxe ODBC pour définir un caractère d’échappement de prédicat **Like** ; « N » dans le cas contraire.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3,0)  
 Valeur SQLUINTEGER qui spécifie le nombre maximal d’instructions simultanées actives en mode asynchrone que le pilote peut prendre en charge sur une connexion donnée. S’il n’existe aucune limite spécifique ou si la limite est inconnue, cette valeur est égale à zéro.  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2,0)  
 Valeur SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères hexadécimaux, à l’exclusion du préfixe littéral et du suffixe retournés par **SQLGetTypeInfo**) d’un littéral binaire dans une instruction SQL. Par exemple, le littéral binaire 0xFFAA a une longueur de 4. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de catalogue dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 Un pilote conforme au niveau complet FIPS renverra au moins 128.  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_MAX_QUALIFIER_NAME_LEN.  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2,0)  
 Valeur SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères, à l’exclusion du préfixe littéral et du suffixe retournés par **SQLGetTypeInfo**) d’un littéral de caractère dans une instruction SQL. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de colonne dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS retourne au moins 18. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans une clause **Group by** . Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS renverra au moins 6. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 15.  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans un index. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans une clause **order by** . Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS renverra au moins 6. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 15.  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans une liste de sélection. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS renverra au moins 100. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 250.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie le nombre maximal de colonnes autorisées dans une table. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS renverra au moins 100. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 250.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie le nombre maximal d’instructions actives que le pilote peut prendre en charge pour une connexion. Une instruction est définie comme active si elle a des résultats en attente, le terme « Results » signifiant les lignes d’une opération **Select** ou les lignes affectées par une opération d' **insertion**, de **mise à jour**ou de **suppression** (par exemple, un nombre de lignes) ou si elle est dans un État NEED_DATA. Cette valeur peut refléter une limitation imposée par le pilote ou par la source de données. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_ACTIVE_STATEMENTS.  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de curseur dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS retourne au moins 18. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 128.  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie le nombre maximal de connexions actives que le pilote peut prendre en charge pour un environnement. Cette valeur peut refléter une limitation imposée par le pilote ou par la source de données. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_ACTIVE_CONNECTIONS.  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3,0)  
 SQLUSMALLINT qui indique la taille maximale, en caractères, prise en charge par la source de données pour les noms définis par l’utilisateur.  
  
 Un pilote conforme au niveau de l’entrée FIPS retourne au moins 18. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 128.  
  
 SQL_MAX_INDEX_SIZE (ODBC 2,0)  
 Valeur SQLUINTEGER qui spécifie le nombre maximal d’octets autorisés dans les champs combinés d’un index. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de procédure dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 SQL_MAX_ROW_SIZE (ODBC 2,0)  
 Valeur SQLUINTEGER qui spécifie la longueur maximale d’une ligne unique dans une table. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS renverra au moins 2 000. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 8 000.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3,0)  
 Chaîne de caractères : « Y » si la taille de ligne maximale retournée pour le type d’informations SQL_MAX_ROW_SIZE comprend la longueur de toutes les colonnes SQL_LONGVARCHAR et SQL_LONGVARBINARY dans la ligne ; « N » dans le cas contraire.  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de schéma dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS retourne au moins 18. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 128.  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_MAX_OWNER_NAME_LEN.  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2,0)  
 Valeur de SQLUINTEGER qui spécifie la longueur maximale (nombre de caractères, y compris l’espace blanc) d’une instruction SQL. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom de table dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS retourne au moins 18. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 128.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie le nombre maximal de tables autorisées dans la clause **from** d’une instruction **Select** . Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 Un pilote conforme au niveau de l’entrée FIPS renverra au moins 15. Un pilote conforme au niveau intermédiaire FIPS renverra au moins 50.  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie la longueur maximale d’un nom d’utilisateur dans la source de données. S’il n’y a pas de longueur maximale ou si la longueur est inconnue, cette valeur est définie sur zéro.  
  
 SQL_MULT_RESULT_SETS (ODBC 1,0)  
 Chaîne de caractères : « Y » si la source de données prend en charge plusieurs jeux de résultats, « N » si ce n’est pas le cas.  
  
 Pour plus d’informations sur les jeux de résultats multiples, consultez [résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1,0)  
 Chaîne de caractères : « Y » si le pilote prend en charge plusieurs transactions actives en même temps, « N » si une seule transaction peut être active à tout moment.  
  
 Les informations retournées pour ce type d’informations ne s’appliquent pas dans le cas des transactions distribuées.  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2,0)  
 Chaîne de caractères : « Y » si la source de données a besoin de la longueur d’une valeur de données de type long (le type de données est SQL_LONGVARCHAR, SQL_LONGVARBINARY ou un type de données long spécifique à la source de données) avant que cette valeur soit envoyée à la source de données, « N » si ce n’est pas le cas. Pour plus d’informations, consultez [SQLBindParameter Function](../../../odbc/reference/syntax/sqlbindparameter-function.md) et [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1,0)  
 Valeur SQLUSMALLINT qui spécifie si la source de données prend en charge NOT NULL dans les colonnes :  
  
 SQL_NNC_NULL = toutes les colonnes doivent avoir la valeur null.  
  
 SQL_NNC_NON_NULL = les colonnes ne peuvent pas avoir la valeur null. (La source de données prend en charge la contrainte de colonne **not null** dans les instructions **Create table** .)  
  
 Un pilote conforme au niveau d’entrée SQL-92 renverra SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION (ODBC 2,0)  
 Valeur SQLUSMALLINT qui spécifie où les valeurs NULL sont triées dans un jeu de résultats :  
  
 SQL_NC_END = les valeurs NULL sont triées à la fin du jeu de résultats, quels que soient les mots clés ASC ou DESC.  
  
 SQL_NC_HIGH = les valeurs NULL sont triées à l’extrémité supérieure du jeu de résultats, en fonction des mots clés ASC ou DESC.  
  
 SQL_NC_LOW = les valeurs NULL sont triées à la fin du jeu de résultats, en fonction des mots clés ASC ou DESC.  
  
 SQL_NC_START = les valeurs NULL sont triées au début du jeu de résultats, quels que soient les mots clés ASC ou DESC.  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1,0)  
 Remarque : le type d’information a été introduit dans ODBC 1,0 ; Chaque masque de masque est étiqueté avec la version dans laquelle il a été introduit.  
  
 Masque de SQLUINTEGER qui énumère les fonctions numériques scalaires prises en charge par le pilote et la source de données associée.  
  
 Les masques de détours suivants sont utilisés pour déterminer les fonctions numériques prises en charge :  
  
 SQL_FN_NUM_ABS (ODBC 1.0) SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COT (ODBC 1.0) SQL_FN_NUM_DEGREES (ODBC 2.0) SQL_ FN_NUM_EXP (ODBC 1.0) SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (ODBC 1.0) SQL_FN_NUM_LOG10 (ODBC 2.0) SQL_FN_NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_RAND (ODBC 1.0) SQL_FN_ NUM_ROUND (ODBC 2.0) SQL_FN_NUM_SIGN (ODBC 1.0) SQL_FN_NUM_SIN (ODBC 1.0) SQL_FN_NUM_SQRT (ODBC 1.0) SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2,0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3,0)  
 Valeur SQLUINTEGER qui indique le niveau de l’interface ODBC 3 *. x* avec lequel le pilote est compatible.  
  
 SQL_OIC_CORE : niveau minimal auquel tous les pilotes ODBC sont censés se conformer. Ce niveau comprend les éléments d’interface de base tels que les fonctions de connexion, les fonctions de préparation et d’exécution d’une instruction SQL, les fonctions de métadonnées du jeu de résultats de base, les fonctions de catalogue de base, etc.  
  
 SQL_OIC_LEVEL1 : un niveau incluant la fonctionnalité de niveau de conformité des normes de base, ainsi que des curseurs déroulants, des signets, des mises à jour et des suppressions positionnées, etc.  
  
 SQL_OIC_LEVEL2 : un niveau comprenant une fonctionnalité de niveau de conformité de niveau 1, ainsi que des fonctionnalités avancées telles que des curseurs sensibles. mettre à jour, supprimer et actualiser par signets ; prise en charge des procédures stockées ; fonctions de catalogue pour les clés primaires et étrangères ; prise en charge de plusieurs catalogues ; et ainsi de suite.  
  
 Pour plus d’informations, consultez [niveaux de conformité](../../../odbc/reference/develop-app/interface-conformance-levels.md)de l’interface.  
  
 SQL_ODBC_VER (ODBC 1,0)  
 Chaîne de caractères avec la version de ODBC à laquelle le gestionnaire de pilotes est conforme. La version se présente sous la forme # #. # #. 0000, où les deux premiers chiffres correspondent à la version principale et les deux chiffres suivants à la version mineure. Elle est implémentée uniquement dans le gestionnaire de pilotes.  
  
 SQL_OJ_CAPABILITIES (ODBC 2,01)  
 Masque de SQLUINTEGER qui énumère les types de jointures externes pris en charge par le pilote et la source de données. Les masques de détours suivants sont utilisés pour déterminer les types pris en charge :  
  
 SQL_OJ_LEFT = les jointures externes gauches sont prises en charge.  
  
 SQL_OJ_RIGHT = les jointures externes droites sont prises en charge.  
  
 SQL_OJ_FULL = les jointures externes complètes sont prises en charge.  
  
 SQL_OJ_NESTED = les jointures externes imbriquées sont prises en charge.  
  
 SQL_OJ_NOT_ORDERED = les noms de colonnes dans la clause ON de la jointure externe n’ont pas besoin d’être dans le même ordre que leurs noms de tables respectifs dans la clause de **jointure externe** .  
  
 SQL_OJ_INNER = la table interne (la table de droite dans une jointure externe gauche ou la table de gauche dans une jointure externe droite) peut également être utilisée dans une jointure interne. Cela ne s’applique pas aux jointures externes entières, qui n’ont pas de table interne.  
  
 SQL_OJ_ALL_COMPARISON_OPS = l’opérateur de comparaison dans la clause ON peut être l’un des opérateurs de comparaison ODBC. Si ce bit n’est pas défini, seul l’opérateur de comparaison égal à (=) peut être utilisé dans les jointures externes.  
  
 Si aucune de ces options n’est retournée comme étant prise en charge, aucune clause de jointure externe n’est prise en charge.  
  
 Pour plus d’informations sur la prise en charge des opérateurs de jointure relationnelle dans une instruction SELECT, comme défini par SQL-92, consultez SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2,0)  
 Chaîne de caractères : « Y » si les colonnes de la clause **order by** doivent figurer dans la liste de sélection ; Sinon, « N ».  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3,0)  
 SQLUINTEGER énumérant les propriétés du pilote en ce qui concerne la disponibilité du nombre de lignes dans une exécution paramétrée. A les valeurs suivantes :  
  
 SQL_PARC_BATCH = les nombres de lignes individuelles sont disponibles pour chaque ensemble de paramètres. Il s’agit d’un concept équivalent au pilote qui génère un lot d’instructions SQL, un pour chaque jeu de paramètres dans le tableau. Les informations d’erreur étendues peuvent être récupérées à l’aide du champ descripteur SQL_PARAM_STATUS_PTR.  
  
 SQL_PARC_NO_BATCH = il n’y a qu’un seul nombre de lignes disponibles, qui est le nombre de lignes cumulées résultant de l’exécution de l’instruction pour l’ensemble du tableau de paramètres. Cela équivaut d’un point de vue conceptuel à traiter l’instruction avec le tableau de paramètres complet comme une seule unité atomique. Les erreurs sont gérées de la même façon qu’une instruction.  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3,0)  
 SQLUINTEGER énumérant les propriétés du pilote en ce qui concerne la disponibilité des jeux de résultats dans une exécution paramétrée. A les valeurs suivantes :  
  
 SQL_PAS_BATCH = un jeu de résultats est disponible par ensemble de paramètres. Il s’agit d’un concept équivalent au pilote qui génère un lot d’instructions SQL, un pour chaque jeu de paramètres dans le tableau.  
  
 SQL_PAS_NO_BATCH = un seul jeu de résultats est disponible, qui représente le jeu de résultats cumulé résultant de l’exécution de l’instruction pour le tableau complet de paramètres. Cela équivaut d’un point de vue conceptuel à traiter l’instruction avec le tableau de paramètres complet comme une seule unité atomique.  
  
 SQL_PAS_NO_SELECT = un pilote n’autorise pas l’exécution d’une instruction de génération de jeu de résultats avec un tableau de paramètres.  
  
 SQL_PROCEDURE_TERM (ODBC 1,0)  
 Chaîne de caractères avec le nom du fournisseur de la source de données pour une procédure ; par exemple, « procédure de base de données », « procédure stockée », « procédure », « package » ou « requête stockée ».  
  
 SQL_PROCEDURES (ODBC 1,0)  
 Chaîne de caractères : « Y » si la source de données prend en charge les procédures et que le pilote prend en charge la syntaxe d’appel de procédure ODBC ; « N » dans le cas contraire.  
  
 SQL_POS_OPERATIONS (ODBC 2,0)  
 Masque de SQLINTEGER destinée qui énumère les opérations de prise en charge dans **SQLSetPos**.  
  
 Les masques de transparence suivants sont utilisés avec l’indicateur pour déterminer les options prises en charge.  
  
 SQL_POS_POSITION (ODBC 2,0) SQL_POS_REFRESH (ODBC 2,0) SQL_POS_UPDATE (ODBC 2,0) SQL_POS_DELETE (ODBC 2,0) SQL_POS_ADD (ODBC 2,0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2,0)  
 Une valeur SQLUSMALLINT comme suit :  
  
 SQL_IC_UPPER = les identificateurs entre guillemets dans SQL ne respectent pas la casse et sont stockés en majuscules dans le catalogue système.  
  
 SQL_IC_LOWER = les identificateurs entre guillemets dans SQL ne respectent pas la casse et sont stockés en minuscules dans le catalogue système.  
  
 SQL_IC_SENSITIVE = les identificateurs entre guillemets dans SQL sont sensibles à la casse et sont stockés en casse mixte dans le catalogue système. (Dans une base de données conforme à SQL-92, les identificateurs entre guillemets sont toujours sensibles à la casse.)  
  
 SQL_IC_MIXED = les identificateurs entre guillemets dans SQL ne respectent pas la casse et sont stockés en casse mixte dans le catalogue système.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours SQL_IC_SENSITIVE.  
  
 SQL_ROW_UPDATES (ODBC 1,0)  
 Chaîne de caractères : « Y » si un curseur de jeu de clés ou mixte conserve des versions de ligne ou des valeurs pour toutes les lignes extraites et peut, par conséquent, détecter les mises à jour effectuées sur une ligne par n’importe quel utilisateur depuis la dernière extraction de la ligne. (Cela s’applique uniquement aux mises à jour, pas aux suppressions ou insertions.) Le pilote peut retourner l’indicateur SQL_ROW_UPDATED au tableau d’état de ligne lorsque **SQLFetchScroll** est appelé. Sinon, « N ».  
  
 SQL_SCHEMA_TERM (ODBC 1,0)  
 Chaîne de caractères avec le nom du fournisseur de la source de données pour un schéma ; par exemple, « propriétaire », « ID d’autorisation » ou « schéma ».  
  
 La chaîne de caractères peut être retournée en majuscules, en minuscules ou en majuscules.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours « schéma ».  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_OWNER_TERM.  
  
 SQL_SCHEMA_USAGE (ODBC 2,0)  
 Un masque de SQLUINTEGER qui énumère les instructions dans lesquelles les schémas peuvent être utilisés :  
  
 SQL_SU_DML_STATEMENTS = les schémas sont pris en charge dans toutes les instructions de langage de manipulation de données : **Select**, **Insert**, **Update**, **Delete**et, si pris en charge, **sélectionne pour Update** et les instructions Update et DELETE positionnées.  
  
 SQL_SU_PROCEDURE_INVOCATION = les schémas sont pris en charge dans l’instruction d’appel de procédure ODBC.  
  
 SQL_SU_TABLE_DEFINITION = les schémas sont pris en charge dans toutes les instructions de définition de table : **Create table**, **Create View**, **ALTER TABLE**, **drop table**et **Drop View**.  
  
 SQL_SU_INDEX_DEFINITION = les schémas sont pris en charge dans toutes les instructions de définition d’index : **Create index** et **Drop index**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = les schémas sont pris en charge dans toutes les instructions de définition de privilèges : **Grant** et **Revoke**.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours les options SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION et SQL_SU_PRIVILEGE_DEFINITION, comme cela est pris en charge.  
  
 Cet *infotype* a été renommé pour ODBC 3,0 à partir de l' *infotype* ODBC 2,0 SQL_OWNER_USAGE.  
  
 SQL_SCROLL_OPTIONS (ODBC 1,0)  
 Remarque : le type d’information a été introduit dans ODBC 1,0 ; Chaque masque de masque est étiqueté avec la version dans laquelle il a été introduit.  
  
 Masque de SQLUINTEGER qui énumère les options de défilement prises en charge pour les curseurs à défilement.  
  
 Les masques de détours suivants sont utilisés pour déterminer les options prises en charge :  
  
 SQL_SO_FORWARD_ONLY = le curseur ne fait que faire défiler vers l’avant. (ODBC 1,0)  
  
 SQL_SO_STATIC = les données du jeu de résultats sont statiques. (ODBC 2,0)  
  
 SQL_SO_KEYSET_DRIVEN = le pilote enregistre et utilise les clés pour chaque ligne du jeu de résultats. (ODBC 1,0)  
  
 SQL_SO_DYNAMIC = le pilote conserve les clés pour chaque ligne de l’ensemble de lignes (la taille du jeu de clés est la même que la taille de l’ensemble de lignes). (ODBC 1,0)  
  
 SQL_SO_MIXED = le pilote conserve les clés pour chaque ligne du jeu de clés, et la taille du keyset est supérieure à la taille de l’ensemble de lignes. Le curseur est piloté par keyset dans le jeu de clés et dynamiquement en dehors du jeu de clés. (ODBC 1,0)  
  
 Pour plus d’informations sur les curseurs de défilement, consultez [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1,0)  
 Chaîne de caractères qui spécifie ce que le pilote prend en charge comme caractère d’échappement, ce qui permet d’utiliser le caractère de soulignement (_) et le signe de pourcentage (%) comme caractères valides dans les modèles de recherche. Ce caractère d’échappement s’applique uniquement aux arguments de fonction de catalogue qui prennent en charge les chaînes de recherche. Si cette chaîne est vide, le pilote ne prend pas en charge le caractère d’échappement d’un modèle de recherche.  
  
 Étant donné que ce type d’informations n’indique pas la prise en charge générale du caractère d’échappement dans le prédicat **Like** , SQL-92 n’inclut pas de spécifications pour cette chaîne de caractères.  
  
 Cet *infotype* est limité aux fonctions de catalogue. Pour obtenir une description de l’utilisation du caractère d’échappement dans les chaînes de modèle de recherche, consultez arguments de la [valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME (ODBC 1,0)  
 Chaîne de caractères avec le nom réel du serveur propre à la source de données ; utile lorsqu’un nom de source de données est utilisé lors de **SQLConnect**, **SQLDriverConnect**et **SQLBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2,0)  
 Chaîne de caractères qui contient tous les caractères spéciaux (c’est-à-dire tous les caractères à l’exception de a à z, de A à Z, de 0 à 9 et de trait de soulignement) qui peuvent être utilisés dans un nom d’identificateur, tel qu’un nom de table, un nom de colonne ou un nom d’index, sur la source de données. Par exemple, « # $ ^ ». Si un identificateur contient un ou plusieurs de ces caractères, l’identificateur doit être un identificateur délimité.  
  
 SQL_SQL_CONFORMANCE (ODBC 3,0)  
 Valeur SQLUINTEGER qui indique le niveau de SQL-92 pris en charge par le pilote :  
  
 SQL_SC_SQL92_ENTRY = conforme à la norme SQL-92 de niveau d’entrée.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = conforme au niveau transitoire FIPS 127-2.  
  
 SQL_SC_SQL92_FULL = conforme à SQL-92 de niveau complet.  
  
 SQL_SC_ SQL92_INTERMEDIATE = niveau intermédiaire conforme à SQL-92.  
  
 SQL_SQL92_DATETIME_FUNCTIONS (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les fonctions scalaires DateTime prises en charge par le pilote et la source de données associée, comme défini dans SQL-92.  
  
 Les masques de détours suivants sont utilisés pour déterminer les fonctions DateTime prises en charge :  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les règles prises en charge pour une clé étrangère dans une instruction **Delete** , comme défini dans SQL-92.  
  
 Les masques de détours suivants sont utilisés pour déterminer les clauses qui sont prises en charge par la source de données :  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Un pilote conforme au niveau de transition FIPS retourne toujours toutes les options prises en charge.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les règles prises en charge pour une clé étrangère dans une instruction **Update** , comme défini dans SQL-92.  
  
 Les masques de détours suivants sont utilisés pour déterminer les clauses qui sont prises en charge par la source de données :  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Un pilote SQL-92 Full-conforme retourne toujours toutes les options prises en charge.  
  
 SQL_SQL92_GRANT (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses prises en charge dans l’instruction **Grant** , comme défini dans SQL-92.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer les clauses qui sont prises en charge par la source de données :  
  
 SQL_SG_DELETE_TABLE (niveau d’entrée) SQL_SG_INSERT_COLUMN (niveau intermédiaire) SQL_SG_INSERT_TABLE (niveau d’entrée) SQL_SG_REFERENCES_TABLE (niveau d’entrée) SQL_SG_REFERENCES_COLUMN (niveau d’entrée) SQL_SG_SELECT_TABLE (niveau d’entrée) SQL_SG_UPDATE_COLUMN ( Niveau d’entrée) SQL_SG_UPDATE_TABLE (niveau d’entrée) SQL_SG_USAGE_ON_DOMAIN (niveau de transition FIPS) SQL_SG_USAGE_ON_CHARACTER_SET (niveau de transition FIPS) SQL_SG_USAGE_ON_COLLATION (niveau de transition FIPS) SQL_SG_USAGE_ON_TRANSLATION (FIPS Niveau de transition) SQL_SG_WITH_GRANT_OPTION (niveau d’entrée)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les fonctions scalaires de valeur numérique qui sont prises en charge par le pilote et la source de données associée, comme défini dans SQL-92.  
  
 Les masques de détours suivants sont utilisés pour déterminer les fonctions numériques prises en charge :  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les prédicats pris en charge dans une instruction **Select** , comme défini dans SQL-92.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer les options prises en charge par la source de données :  
  
 SQL_SP_BETWEEN (niveau d’entrée) SQL_SP_COMPARISON (niveau d’entrée) SQL_SP_EXISTS (niveau d’entrée) SQL_SP_IN (niveau d’entrée) SQL_SP_ISNOTNULL (niveau d’entrée) SQL_SP_ISNULL (niveau d’entrée) SQL_SP_LIKE (niveau d’entrée) SQL_SP_MATCH_FULL (niveau complet) SQL_SP_MATCH_PARTIAL (Niveau complet) SQL_SP_MATCH_UNIQUE_FULL (niveau complet) SQL_SP_MATCH_UNIQUE_PARTIAL (niveau complet) SQL_SP_OVERLAPS (niveau de transition FIPS) SQL_SP_QUANTIFIED_COMPARISON (niveau d’entrée) SQL_SP_UNIQUE (niveau d’entrée)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les opérateurs de jointure relationnelle pris en charge dans une instruction **Select** , comme défini dans SQL-92.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer les options prises en charge par la source de données :  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (niveau intermédiaire) SQL_SRJO_CROSS_JOIN (niveau complet) SQL_SRJO_EXCEPT_JOIN (niveau intermédiaire) SQL_SRJO_FULL_OUTER_JOIN (niveau intermédiaire) SQL_SRJO_INNER_JOIN (niveau de transition FIPS) SQL_SRJO_INTERSECT_JOIN (Niveau intermédiaire) SQL_SRJO_LEFT_OUTER_JOIN (niveau de transition FIPS) SQL_SRJO_NATURAL_JOIN (niveau de transition FIPS) SQL_SRJO_RIGHT_OUTER_JOIN (niveau de transition FIPS) SQL_SRJO_UNION_JOIN (niveau complet)  
  
 SQL_SRJO_INNER_JOIN indique la prise en charge de la syntaxe de **jointure interne** , et non de la fonctionnalité de jointure interne. La prise en charge de la syntaxe de **jointure interne** est la transition FIPS, tandis que la prise en charge de la fonctionnalité de jointure interne est une **entrée**.  
  
 SQL_SQL92_REVOKE (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses prises en charge dans l’instruction **Revoke** , comme défini dans SQL-92, pris en charge par la source de données.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer les clauses qui sont prises en charge par la source de données :  
  
 SQL_SR_CASCADE (niveau de transition FIPS) SQL_SR_DELETE_TABLE (niveau d’entrée) SQL_SR_GRANT_OPTION_FOR (niveau intermédiaire) SQL_SR_INSERT_COLUMN (niveau intermédiaire) SQL_SR_INSERT_TABLE (niveau d’entrée) SQL_SR_REFERENCES_COLUMN (niveau d’entrée) SQL_SR_ REFERENCES_TABLE (niveau d’entrée) SQL_SR_RESTRICT (niveau de transition FIPS) SQL_SR_SELECT_TABLE (niveau d’entrée) SQL_SR_UPDATE_COLUMN (niveau d’entrée) SQL_SR_UPDATE_TABLE (niveau d’entrée) SQL_SR_USAGE_ON_DOMAIN (niveau de transition FIPS) SQL_SR_USAGE_ON_ CHARACTER_SET (niveau de transition FIPS) SQL_SR_USAGE_ON_COLLATION (niveau de transition FIPS) SQL_SR_USAGE_ON_TRANSLATION (niveau de transition FIPS)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les expressions de constructeur de valeur de ligne prises en charge dans une instruction **Select** , comme défini dans SQL-92. Les masques de détours suivants sont utilisés pour déterminer les options prises en charge par la source de données :  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les fonctions scalaires de chaîne prises en charge par le pilote et la source de données associée, comme défini dans SQL-92.  
  
 Les masques de détours suivants sont utilisés pour déterminer les fonctions de chaîne prises en charge :  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les expressions de valeur prises en charge, comme défini dans SQL-92.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer les options prises en charge par la source de données :  
  
 SQL_SVE_CASE (niveau intermédiaire) SQL_SVE_CAST (niveau de transition FIPS) SQL_SVE_COALESCE (niveau intermédiaire) SQL_SVE_NULLIF (niveau intermédiaire)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3,0)  
 Masque de SQLUINTEGER qui énumère les normes ou normes CLI auxquelles le pilote se conforme. Les masques de détours suivants sont utilisés pour déterminer les niveaux auxquels le pilote est conforme :  
  
 SQL_SCC_XOPEN_CLI_VERSION1 : le pilote est conforme à la version 1 de l’interface CLI Open Group.  
  
 SQL_SCC_ISO92_CLI : le pilote est conforme à la norme ISO 92 CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Masque de SQLUINTEGER qui décrit les attributs d’un curseur statique pris en charge par le pilote. Ce masque de réinitialisation contient le premier sous-ensemble d’attributs ; pour le deuxième sous-ensemble, consultez SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Les masques de détours suivants sont utilisés pour déterminer les attributs pris en charge :  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Pour obtenir une description de ces masques de détourage, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (et remplacez « curseur statique » par « curseur dynamique » dans les descriptions).  
  
 Un pilote conforme au niveau intermédiaire SQL-92 retourne généralement les options SQL_CA1_NEXT, SQL_CA1_ABSOLUTE et SQL_CA1_RELATIVE comme étant prises en charge, car le pilote prend en charge les curseurs à défilement via l’instruction SQL FETCH incorporée. Étant donné que cela ne détermine pas directement la prise en charge SQL sous-jacente, toutefois, les curseurs avec défilement peuvent ne pas être pris en charge, même pour un pilote conforme au niveau intermédiaire SQL-92.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Masque de SQLUINTEGER qui décrit les attributs d’un curseur statique pris en charge par le pilote. Ce masque de réplicas contient le deuxième sous-ensemble d’attributs ; pour le premier sous-ensemble, consultez SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Les masques de détours suivants sont utilisés pour déterminer les attributs pris en charge :  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Pour obtenir une description de ces masques de détourage, consultez SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (et remplacez « curseur statique » par « curseur dynamique » dans les descriptions).  
  
 SQL_STRING_FUNCTIONS (ODBC 1,0)  
 Remarque : le type d’information a été introduit dans ODBC 1,0 ; Chaque masque de masque est étiqueté avec la version dans laquelle il a été introduit.  
  
 Masque de SQLUINTEGER qui énumère les fonctions de chaîne scalaires prises en charge par le pilote et la source de données associée.  
  
 Les masques de détours suivants sont utilisés pour déterminer les fonctions de chaîne prises en charge :  
  
 SQL_FN_STR_ASCII (ODBC 1.0) SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 2.0) SQL_FN_STR_INSERT (ODBC 1.0) SQL_FN_STR_LCASE (ODBC 1.0) SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1,0) SQL_FN_STR_LTRIM (ODBC 1,0) SQL_FN_STR_OCTET_LENGTH (ODBC 3,0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_ STR_REPLACE (ODBC 1.0) SQL_FN_STR_RIGHT (ODBC 1.0) SQL_FN_STR_RTRIM (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) SQL_FN_STR_SPACE (ODBC 2.0) SQL_FN_STR_SUBSTRING (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1,0)  
  
 Si une application peut appeler la fonction **Locate** Scala avec les arguments *string_exp1*, *string_exp2*et *Start* , le pilote retourne le masque de réSQL_FN_STR_LOCATE. Si une application peut appeler la fonction LOCATe Scala avec uniquement les arguments *string_exp1* et *string_exp2* , le pilote retourne le masque de réSQL_FN_STR_LOCATE_2. Les pilotes qui prennent entièrement en charge la fonction de **localisation** scalaire renvoient les deux masques de.  
  
 (Pour plus d’informations, consultez [fonctions de chaîne](../../../odbc/reference/appendixes/string-functions.md) dans l’annexe E, « fonctions scalaires ».)  
  
 SQL_SUBQUERIES (ODBC 2,0)  
 Un masque de SQLUINTEGER qui énumère les prédicats qui prennent en charge les sous-requêtes :  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Le masque de SQL_SQ_CORRELATED_SUBQUERIES indique que tous les prédicats qui prennent en charge les sous-requêtes prennent en charge les sous-requêtes corrélées.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours un masque de bits dans lequel tous ces bits sont définis.  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1,0)  
 Masque de SQLUINTEGER qui énumère les fonctions système scalaires prises en charge par le pilote et la source de données associée.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles fonctions système sont prises en charge :  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1,0)  
 Chaîne de caractères avec le nom du fournisseur de la source de données pour une table ; par exemple, « table » ou « file ».  
  
 Cette chaîne de caractères peut être en majuscules, en minuscules ou en casse mixte.  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours « table ».  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2,0)  
 Masque de SQLUINTEGER qui énumère les intervalles d’horodatage pris en charge par le pilote et la source de données associée pour la fonction scalaire TIMESTAMPADD.  
  
 Les masques de détours suivants sont utilisés pour déterminer les intervalles pris en charge :  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Un pilote conforme au niveau de transition FIPS renverra toujours un masque de bits dans lequel tous ces éléments sont définis.  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2,0)  
 Masque de SQLUINTEGER qui énumère les intervalles d’horodatage pris en charge par le pilote et la source de données associée pour la fonction scalaire TIMESTAMPDIFF.  
  
 Les masques de détours suivants sont utilisés pour déterminer les intervalles pris en charge :  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Un pilote conforme au niveau de transition FIPS renverra toujours un masque de bits dans lequel tous ces éléments sont définis.  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1,0)  
 Remarque : le type d’information a été introduit dans ODBC 1,0 ; Chaque masque de masque est étiqueté avec la version dans laquelle il a été introduit.  
  
 Masque de SQLUINTEGER qui énumère les fonctions scalaires de date et d’heure prises en charge par le pilote et la source de données associée.  
  
 Les masques de détours suivants sont utilisés pour déterminer les fonctions de date et d’heure prises en charge :  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURTIME (ODBC 1,0) SQL_FN_TD_DAYNAME (ODBC 2.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK ( ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1,0) SQL_FN_TD_EXTRACT (ODBC 3.0) SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_ DEUXIÈME (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0) SQL_FN_TD_WEEK (ODBC 1.0) SQL_FN_TD_YEAR (ODBC 1,0)  
  
 SQL_TXN_CAPABLE (ODBC 1,0)  
 Remarque : le type d’information a été introduit dans ODBC 1,0 ; chaque valeur de retour est étiquetée avec la version dans laquelle elle a été introduite.  
  
 Valeur SQLUSMALLINT décrivant la prise en charge des transactions dans le pilote ou la source de données :  
  
 SQL_TC_NONE = transactions non prises en charge. (ODBC 1,0)  
  
 SQL_TC_DML = les transactions peuvent contenir uniquement des instructions de langage de manipulation de données (DML) (**Select**, **Insert**, **Update**, **Delete**). Les instructions DDL (Data Definition Language) rencontrées dans une transaction provoquent une erreur. (ODBC 1,0)  
  
 SQL_TC_DDL_COMMIT = les transactions ne peuvent contenir que des instructions DML. Les instructions DDL (**Create table**, **Drop index**, etc.) rencontrées dans une transaction provoquent la validation de la transaction. (ODBC 2,0)  
  
 SQL_TC_DDL_IGNORE = les transactions ne peuvent contenir que des instructions DML. Les instructions DDL rencontrées dans une transaction sont ignorées. (ODBC 2,0)  
  
 SQL_TC_ALL = les transactions peuvent contenir des instructions DDL et des instructions DML dans n’importe quel ordre. (ODBC 1,0)  
  
 (Étant donné que la prise en charge des transactions est obligatoire dans SQL-92, un pilote conforme à SQL-92 [n’importe quel niveau] ne retourne jamais SQL_TC_NONE.)  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1,0)  
 Un masque de SQLUINTEGER qui énumère les niveaux d’isolation de la transaction disponibles à partir du pilote ou de la source de données.  
  
 Les masques de transparence suivants sont utilisés avec l’indicateur pour déterminer les options prises en charge :  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Pour obtenir une description de ces niveaux d’isolation, consultez la description de SQL_DEFAULT_TXN_ISOLATION.  
  
 Pour définir le niveau d’isolation de la transaction, une application appelle **SQLSetConnectAttr** pour définir l’attribut SQL_ATTR_TXN_ISOLATION. Pour plus d’informations, consultez [fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours SQL_TXN_SERIALIZABLE pris en charge. Un pilote de conformité au niveau de la transition FIPS retourne toujours toutes ces options prises en charge.  
  
 SQL_UNION (ODBC 2,0)  
 Un masque de SQLUINTEGER qui énumère la prise en charge de la clause **Union** :  
  
 SQL_U_UNION = la source de données prend en charge la clause **Union** .  
  
 SQL_U_UNION_ALL = la source de données prend en charge le mot clé **All** dans la clause **Union** . (**SQLGetInfo** retourne à la fois SQL_U_UNION et SQL_U_UNION_ALL dans ce cas.)  
  
 Un pilote conforme au niveau de l’entrée SQL-92 retourne toujours ces deux options prises en charge.  
  
 SQL_USER_NAME (ODBC 1,0)  
 Chaîne de caractères portant le nom utilisé dans une base de données particulière, qui peut être différente du nom de connexion.  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3,0)  
 Chaîne de caractères qui indique l’année de publication de la spécification de groupe ouverte avec laquelle la version du gestionnaire de pilotes ODBC est entièrement conforme.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1,0)  
 Chaîne de caractères : « Y » si l’utilisateur peut exécuter toutes les procédures retournées par **SQLProcedures**; « N » s’il peut y avoir des procédures retournées que l’utilisateur ne peut pas exécuter.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1,0)  
 Chaîne de caractères : « Y » si l’utilisateur est assuré de **Sélectionner** des privilèges pour toutes les tables retournées par **SQLTables**; « N » s’il peut y avoir des tables renvoyées auxquelles l’utilisateur ne peut pas accéder.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3,0)  
 Valeur de SQLUSMALLINT qui spécifie le nombre maximal d’environnements actifs que le pilote peut prendre en charge. Si aucune limite n’est spécifiée ou si la limite est inconnue, cette valeur est définie à zéro.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3,0)  
 Un masque de SQLUINTEGER pour énumérer la prise en charge des fonctions d’agrégation :  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Un pilote conforme au niveau d’entrée SQL-92 retourne toujours toutes les options prises en charge.  
  
 SQL_ALTER_DOMAIN (ODBC 3,0)  
 Un masque de bits SQLUINTEGER énumérant les clauses de l’instruction **ALTER Domain** , tel que défini dans SQL-92, pris en charge par la source de données. Un pilote compatible avec le niveau complet SQL-92 retourne toujours tous les masques de bits. Une valeur de retour de « 0 » signifie que l’instruction **ALTER Domain** n’est pas prise en charge.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = l’ajout d’une contrainte de domaine est pris en charge (niveau complet)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter Domain> \<définir le domaine par défaut> est pris en charge (niveau complet)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<la clause de définition du nom de la contrainte> est prise en charge pour la contrainte de domaine d’attribution de noms (niveau intermédiaire)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<supprimer la clause de contrainte de domaine> est pris en charge (niveau complet)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter Domain> \<supprimer la clause de domaine par défaut> est pris en charge (niveau complet)  
  
 Les bits suivants spécifient les \<attributs de contrainte pris \<en charge> si l’ajout d’une contrainte de domaine> est pris en charge (le bit SQL_AD_ADD_DOMAIN_CONSTRAINT est défini) :  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet)  
  
 SQL_ALTER_TABLE (ODBC 2,0)  
 Un masque de SQLUINTEGER qui énumère les clauses de l’instruction **ALTER TABLE** prise en charge par la source de données.  
  
 Le niveau de conformité de SQL-92 ou FIPS auquel cette fonctionnalité doit être prise en charge est indiqué entre parenthèses en regard de chaque masque de bits.  
  
 Les masques de détours suivants sont utilisés pour déterminer quelles clauses sont prises en charge :  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<la clause ADD COLUMN> est prise en charge, avec une fonction facilitant la spécification du classement de colonne (niveau complet) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<la clause ADD COLUMN> est prise en charge, avec Facility pour spécifier les valeurs par défaut des colonnes (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<ajout de> de colonne est pris en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_CONSTRAINT = \<la clause ADD COLUMN> est prise en charge, avec Facility pour spécifier des contraintes de colonne (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<la clause de> de contrainte Add table est prise en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<la> de définition du nom de la contrainte est prise en charge pour les contraintes de colonne et de table (niveau intermédiaire) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<DROP Column> cascade est pris en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<alter Column> \<clause de suppression de colonne par défaut> est pris en charge (niveau intermédiaire) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<la colonne de suppression> restreindre est pris en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<la colonne de suppression> restreindre est pris en charge (niveau de transition FIPS) (ODBC 3,0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<alter Column> \<clause SET Column default> est pris en charge (niveau intermédiaire) (ODBC 3,0)  
  
 Les bits suivants spécifient les \<attributs de contrainte de prise en charge> si la spécification de contraintes de colonne ou de table est prise en charge (le bit SQL_AT_ADD_CONSTRAINT est défini) :  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (niveau complet) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (niveau complet) (ODBC 3,0)  
  
 SQL_ASYNC_MODE (ODBC 3,0)  
 Valeur SQLUINTEGER qui indique le niveau de prise en charge asynchrone dans le pilote :  
  
 SQL_AM_CONNECTION = l’exécution asynchrone au niveau de la connexion est prise en charge. Tous les descripteurs d’instruction associés à un handle de connexion donné sont en mode asynchrone ou tous sont en mode synchrone. Un descripteur d’instruction sur une connexion ne peut pas être en mode asynchrone alors qu’un autre descripteur d’instruction sur la même connexion est en mode synchrone, et vice versa.  
  
 SQL_AM_STATEMENT = l’exécution asynchrone au niveau de l’instruction est prise en charge. Certains descripteurs d’instruction associés à un handle de connexion peuvent être en mode asynchrone, alors que d’autres descripteurs d’instruction sur la même connexion sont en mode synchrone.  
  
 SQL_AM_NONE = le mode asynchrone n’est pas pris en charge.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3,0)  
 Masque de SQLUINTEGER qui énumère le comportement du pilote en ce qui concerne la disponibilité des nombres de lignes. Les masques de données suivants sont utilisés avec le type d’informations :  
  
 SQL_BRC_ROLLED_UP = le nombre de lignes pour les instructions INSERT, DELETE ou UPDATE consécutives est cumulé dans un. Si ce bit n’est pas défini, les nombres de lignes sont disponibles pour chaque instruction.  
  
 SQL_BRC_PROCEDURES = le nombre de lignes, le cas échéant, est disponible lors de l’exécution d’un lot dans une procédure stockée. Si les nombres de lignes sont disponibles, ils peuvent être cumulés ou disponibles individuellement, selon le bit de SQL_BRC_ROLLED_UP.  
  
 SQL_BRC_EXPLICIT = les nombres de lignes, le cas échéant, sont disponibles lorsqu’un traitement est exécuté directement en appelant **SQLExecute** ou **SQLExecDirect**. Si les nombres de lignes sont disponibles, ils peuvent être cumulés ou disponibles individuellement, selon le bit de SQL_BRC_ROLLED_UP.  
  
## <a name="example"></a>Exemple  
 **SQLGetInfo** retourne les listes d’options prises en charge en tant que masque de SQLUINTEGER dans **InfoValuePtr*. Le masque de transparence pour chaque option est utilisé avec l’indicateur pour déterminer si l’option est prise en charge.  
  
 Par exemple, une application peut utiliser le code suivant pour déterminer si la fonction scalaire de sous-chaîne est prise en charge par le pilote associé à la connexion.  
  
 Pour un autre exemple d’utilisation de **SQLGetInfo**, consultez [fonction SQLTables](../../../odbc/reference/syntax/sqltables-function.md).  
  
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
 Renvoi du paramètre d’un attribut de connexion  
 [Fonction SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Déterminer si un pilote prend en charge une fonction  
 [Fonction SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Renvoi du paramètre d’un attribut d’instruction  
 [Fonction SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Retour d’informations sur les types de données d’une source de données  
 [Fonction SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
