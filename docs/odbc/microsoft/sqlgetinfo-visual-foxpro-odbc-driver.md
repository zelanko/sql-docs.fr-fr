---
title: SQLGetInfo (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: fbc39e3d-67d9-4331-bf5f-76dbd74c4c45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2d4b976083b46bf632c4890c7fce3b0f13a9a761
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295189"
---
# <a name="sqlgetinfo-visual-foxpro-odbc-driver"></a>SQLGetInfo (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 1  
  
 Retourne des informations générales sur le visual FoxPro ODBC Driver et la source de données associées à une poignée de connexion, *hdbc*. La liste suivante montre la valeur retournée par le visual FoxPro ODBC Driver pour chaque argument *fInfoType* et commentaires concernant les valeurs retournées.  
  
 Pour plus d’informations, voir [SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md) dans la *référence du programmeur ODBC*.  
  
## <a name="a"></a>Un  
 SQL_ACCESSIBLE_PROCEDURES renvoie 'N'.  
  
 SQL_ACCESSIBLE_TABLES renvoie 'Y'.  
  
 SQL_ACTIVE_CONNECTIONS revient 0.  
  
 SQL_ACTIVE_STATEMENTS revient 0.  
  
 SQL_ALTER_TABLE renvoie SQL_AT_ADD_COLUMN ou SQL_AT_DROP_COLUMN.  
  
## <a name="b"></a>B  
 SQL_BOOKMARK_PERSISTENCE retourne SQL_BP_SCROLL.  
  
## <a name="c"></a>C  
 SQL_COLUMN_ALIAS renvoie 'Y'.  
  
 SQL_CONCAT_NULL_BEHAVIOR retourne SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINT revient 0. Le visual FoxPro ODBC Driver ne prend pas en charge *BigInt*.  
  
 SQL_CONVERT_BINARY revient 0.  
  
 SQL_CONVERT_BIT revient 0.  
  
 SQL_CONVERT_CHAR revient 0.  
  
 SQL_CONVERT_DATE revient 0.  
  
 SQL_CONVERT_DECIMAL revient 0.  
  
 SQL_CONVERT_DOUBLE revient 0.  
  
 SQL_CONVERT_FLOAT revient 0.  
  
 SQL_CONVERT_INTEGER revient 0.  
  
 SQL_CONVERT_LONGVARBINARY revient 0.  
  
 SQL_CONVERT_LONGVARCHAR revient 0.  
  
 SQL_CONVERT_NUMERIC revient 0.  
  
 SQL_CONVERT_REAL revient 0.  
  
 SQL_CONVERT_SMALLINT revient 0.  
  
 SQL_CONVERT_TIME revient 0.  
  
 SQL_CONVERT_TIMESTAMP revient 0.  
  
 SQL_CONVERT_TINYINT revient 0.  
  
 SQL_CONVERT_VARBINARY revient 0.  
  
 SQL_CONVERT_VARCHAR revient 0.  
  
 SQL_CONVERT_FUNCTIONS revient 0.  
  
 SQL_CORRELATION_NAME retourne SQL_CN_ANY.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR retourne SQL_CB_PRESERVE.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR retourne SQL_CB_PRESERVE.  
  
## <a name="d"></a>D  
 SQL_DATA_SOURCE_NAME retourne la valeur passée sous le titre DSN à [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), ou [SQLDriverConnect;](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) retourne une chaîne vide si aucun DSN n’est spécifié.  
  
 SQL_DATA_SOURCE_READ_ONLY renvoie 'N'.  
  
 SQL_DATABASE_NAME retourne un chemin complet de l’UNC vers la base de données actuelle si la source de données est une [base de données](../../odbc/microsoft/visual-foxpro-terminology.md). Si la source de données se connecte à un répertoire de [tables,](../../odbc/microsoft/visual-foxpro-terminology.md)la fonction retourne le chemin vers le répertoire.  
  
 SQL_DBMS_NAME revient "Visual FoxPro".  
  
 SQL_DBMS_VER revient "03.00.0000".  
  
 SQL_DEFAULT_TXN_ISOLATION retourne SQL_TXN_READ_COMMITTED. Des lectures sales ne sont pas possibles, mais des lectures nonrepeatables et des fantômes sont possibles.  
  
 SQL_DRIVER_HDBC est mise en œuvre par le Driver Manager.  
  
 SQL_DRIVER_HENV est mise en œuvre par le Driver Manager.  
  
 SQL_DRIVER_HLIB est mise en œuvre par le Driver Manager.  
  
 SQL_DRIVER_HSTMT est mise en œuvre par le Driver Manager.  
  
 SQL_DRIVER_NAME retourne "vfpodbc.dll".  
  
 SQL_DRIVER_ODBC_VER renvoie "02.50" (SQL_SPEC_MAJOR, SQL_SPEC_MINOR).  
  
 SQL_DRIVER_VER revient "01.00.0000".  
  
## <a name="e"></a>E  
 SQL_EXPRESSIONS_IN_ORDERBY renvoie 'N'.  
  
## <a name="f"></a>F  
 SQL_FETCH_DIRECTION revient :  
  
-   SQL_FD_FETCH_NEXT  
  
-   SQL_FD_FETCH_FIRST  
  
-   SQL_FD_FETCH_LAST  
  
-   SQL_FD_FETCH_PRIOR  
  
-   SQL_FD_FETCH_ABSOLUTE  
  
-   SQL_FD_FETCH_RELATIVE  
  
-   SQL_FD_FETCH_BOOKMARK.  
  
 SQL_FILE_USAGE renvois SQL_FILE_QUALIFIER à la fois pour les sources de données de base de données (.dbc fichier) et pour les sources de données gratuites de table (.dbf file).  
  
## <a name="g-h"></a>G-H  
 SQL_GETDATA_EXENSIONS revient :  
  
-   SQL_GD_ANY_COLUMN  
  
-   SQL_GD_ANY_BLOCK  
  
-   SQL_GD_ANY_BOUND  
  
-   SQL_GD_ANY_ORDER  
  
 SQL_GROUP_BY retourne SQL_GB_NO_RELATION.  
  
## <a name="i-j"></a>I-J (en)  
 SQL_IDENTIFIER_CASE retourne SQL_IC_MIXED.  
  
 SQL_IDENTIFIER_QUOTE_CHAR revient '.  
  
## <a name="k"></a>K  
 SQL_KEYWORDS revient "".  
  
## <a name="l"></a>L  
 SQL_LIKE_ESCAPE_CLAUSE renvoie 'N'.  
  
 SQL_LOCK_TYPES retourne SQL_LCK_NO_CHANGE.  
  
## <a name="m"></a>M  
 SQL_MAX_BINARY_LITERAL_LEN revient 0.  
  
 SQL_MAX_CHAR_LITERAL_LEN revient 254.  
  
 SQL_MAX_COLUMN_NAME_LEN revient 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY revient 16.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY revient 16.  
  
 SQL_MAX_COLUMNS_IN_INDEX revient 0.  
  
 SQL_MAX_COLUMNS_IN_SELECT revient 254.  
  
 SQL_MAX_COLUMNS_IN_TABLE revient 254.  
  
 SQL_MAX_CURSOR_NAME_LEN revient 254.  
  
 SQL_MAX_INDEX_SIZE revient 0.  
  
 SQL_MAX_OWNER_NAME_LEN revient 0.  
  
 SQL_MAX_PROCEDURE_NAME_LEN revient 0. Le visual FoxPro ODBC Driver n’autorise pas l’accès direct aux procédures stockées Visual FoxPro.  
  
 SQL_MAX_QUALIFIER_NAME_LEN retourne la longueur maximale du système d’exploitation.  
  
 SQL_MAX_ROW_SIZE revient 254-2.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG renvoie 'N'.  
  
 SQL_MAX_STATEMENT_LEN revient 8192.  
  
 SQL_MAX_TABLE_NAME_LEN revient 128.  
  
 SQL_MAX_TABLES_IN_SELECT revient 16.  
  
 SQL_MAX_USER_NAME_LEN revient 0.  
  
 SQL_MULT_RESULT_SETS renvoie 'Y'.  
  
 SQL_MULTIPLE_ACTIVE_TXN renvoie 'Y'. Plusieurs connexions peuvent avoir plusieurs transactions ouvertes à la fois.  
  
## <a name="n"></a>N  
 SQL_NEED_LONG_DATA_LEN renvoie 'N'.  
  
 SQL_NON_NULLABLE_COLUMNS retourne SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION retourne SQL_NC_LOW.  
  
 SQL_NUMERIC_FUNCTIONS renvoie toutes les fonctions sauf SQL_FN_NUM_POWER, qui n’est pas pris en charge par le visual FoxPro ODBC Driver. Les fonctions suivantes sont prises en charge :  
  
-   SQL_FN_NUM_ABS  
  
-   SQL_FN_NUM_ACOS  
  
-   SQL_FN_NUM_ASIN  
  
-   SQL_FN_NUM_ATAN  
  
-   SQL_FN_NUM_ATAN2  
  
-   SQL_FN_NUM_CELING  
  
-   SQL_FN_NUM_COS  
  
-   SQL_FN_NUM_COT  
  
-   SQL_FN_NUM_DEGREES  
  
-   SQL_FN_NUM_EXP  
  
-   SQL_FN_NUM_FLOOR  
  
-   SQL_FN_NUM_LOG  
  
-   SQL_FN_NUM_LOG10  
  
-   SQL_FN_NUM_MOD  
  
-   SQL_FN_NUM_PI  
  
-   SQL_FN_NUM_RADIANS  
  
-   SQL_FN_NUM_RAND  
  
-   SQL_FN_NUM_ROUND  
  
-   SQL_FN_NUM_SIGN  
  
-   SQL_FN_NUM_SIN  
  
-   SQL_FN_NUM_SQRT  
  
-   SQL_FN_NUM_TAN  
  
## <a name="o"></a>O  
 SQL_ODBC_API_CONFORMANCE retourne SQL_OAC_LEVEL1.  
  
 SQL_ODBC_SAG_CLI_CONFORMANCE retourne SQL_OSCC_COMPLIANT.  
  
 SQL_ODBC_SQL_CONFORMANCE retourne SQL_OSC_MINIMUM. La syntaxe SQL minimale est prise en charge.  
  
 SQL_ODBC_SQL_OPT_IEF renvoie "N".  
  
 SQL_ODBC_VER est mise en œuvre par le Driver Manager.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT renvoie "N".  
  
 SQL_OUTER_JOINS renvoie "N".  
  
 SQL_OWNER_TERM revient "". Le Visual FoxPro ODBC Driver ne prend pas en charge les propriétaires de ses objets.  
  
 SQL_OWNER_USAGE revient 0. Le Visual FoxPro ODBC Driver ne prend pas en charge les propriétaires de ses objets.  
  
## <a name="p"></a>P  
 SQL_POS_OPERATIONS retourne SQL_POS_POSITION.  
  
 SQL_POSITIONED_STATEMENTS revient 0.  
  
 SQL_PROCEDURE_TERM revient "".  
  
 SQL_PROCEDURES renvoie 'N'.  
  
## <a name="q"></a>Q  
 SQL_QUALIFIER_LOCATION retourne SQL_QL_START.  
  
 SQL_QUALIFIER_NAME_SEPARATOR revient '!' ou\\'. Le séparateur entre la base de données et le\\tableau est «!» pour les sources de données connectées aux bases de données , et « pour les sources de données qui sont des répertoires de [tables gratuites](../../odbc/microsoft/visual-foxpro-terminology.md). [databases](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
 SQL_QUALIFIER_TERM renvoie "base de données" ou "annuaire". Le qualificatif est "base de données" pour les sources de données [connectées](../../odbc/microsoft/visual-foxpro-terminology.md)aux bases de données , et "répertoire" pour les sources de données qui sont des répertoires de [tables gratuites](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 SQL_QUALIFIER_USAGE n’appuie pas SQL_QU_PRIVILEGE_DEFINITION; il renvoie soit SQL_QU_DML_STATEMENT, soit SQL_QU_TABLE_DEFINITION.  
  
 SQL_QUOTED_IDENTIFIER_CASE retourne SQL_IC_MIXED.  
  
## <a name="r"></a>R  
 SQL_ROW_UPDATES renvoie "N". Le visual FoxPro ODBC Driver ne prend en charge que les curseurs statiques et avant.  
  
## <a name="s"></a>S  
 SQL_SCROLL_CONCURRENCY retourne SQL_SCCO_READ_ONLY.  
  
 SQL_SCROLL_OPTIONS renvoie SQL_SO_STATIC ou SQL_SO_READONLY.  
  
 SQL_SEARCH_PATTERN_ESCAPE revient "\\".  
  
 SQL_SERVER_NAME revient "".  
  
 SQL_SPECIAL_CHARACTERS revient « 1 $$%».  
  
 SQL_STATIC_SENSITIVITY revient 0. Le visual FoxPro ODBC Driver ne prend pas en charge les mises à jour de position.  
  
 SQL_STRING_FUNCTIONS n’appuie pas SQL_FN_STR_INSERT, SQL_FN_STR_LOCATE, SQL_FN_STR_LOCATE_2 ou SQL_FN_STR_SOUNDEX.  
  
 Cela renvoie :  
  
-   SQL_FN_STR_ASCII  
  
-   SQL_FN_STR_CHAR  
  
-   SQL_FN_STR_CONCAT  
  
-   SQL_FN_STR_DIFFERENCE  
  
-   SQL_FN_STR_LCASE  
  
-   SQL_FN_STR_LEFT  
  
-   SQL_FN_STR_LENGTH  
  
-   SQL_FN_STR_LTRIM  
  
-   SQL_FN_STR_REPEAT  
  
-   SQL_FN_STR_REPLACE  
  
-   SQL_FN_STR_RIGHT  
  
-   SQL_FN_STR_RTRIM  
  
-   SQL_FN_STR_SUBSTRING  
  
-   SQL_FN_STR_UCASE  
  
-   SQL_FN_STR_SPACE.  
  
 SQL_SUBQUERIES revient :  
  
-   SQL_SQ_CORRELATED_SUBQUERIES  
  
-   SQL_SQ_COMPARISON  
  
-   SQL_SQ_EXISTS  
  
-   SQL_SQ_IN  
  
-   SQL_SQ_QUANTIFIED.  
  
 SQL_SYSTEM_FUNCTIONS revient :  
  
-   SQL_FN_SYS_DBNAME  
  
-   SQL_FN_SYS_IFNULL  
  
 mais pas:  
  
-   SQL_FN_SYS_USERNAME  
  
## <a name="t"></a>T  
 SQL_TABLE_TERM renvoie "table".  
  
 SQL_TIMEDATE_ADD_INTERVALS revient :  
  
-   SQL_FN_TSI_ SECOND  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 mais pas:  
  
-   SQL_FN_TSI_FRAC_SECOND  
  
-   SQL_FN_TSI_WEEK  
  
-   SQL_FN_TSI_QUARTER  
  
 SQL_TIMEDATE_DIFF_INTERVALS revient :  
  
-   SQL_FN_TSI_ SECOND  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 SQL_TIMEDATE_FUNCTIONS n’appuie pas SQL_FN_TD_QUARTER, SQL_FN_TD_TIMESTAMPADD, SQL_FN_TD_DAYOFYEAR ou SQL_FN_TD_WEEK.  
  
 Cela renvoie :  
  
-   SQL_FN_TD_CURDATE  
  
-   SQL_FN_TD_CURTIME  
  
-   SQL_FN_TD_DAYNAME  
  
-   SQL_FN_TD_DAYOFMONTH  
  
-   SQL_FN_TD_DAYOFWEEK  
  
-   SQL_FN_TD_HOUR  
  
-   SQL_FN_TD_MINUTE  
  
-   SQL_FN_TD_MONTH  
  
-   SQL_FN_TD_MONTHNAME  
  
-   SQL_FN_TD_NOW  
  
-   SQL_FN_TD_SECOND  
  
-   SQL_FN_TD_TIMESTAMPDIFF  
  
-   SQL_FN_TD_YEAR .  
  
 SQL_TXN_CAPABLE retourne SQL_TC_DML.  
  
 SQL_TXN_ISOLATION_OPTION retourne SQL_TXN_READ_COMMITTED.  
  
## <a name="u-z"></a>U-Z  
 SQL_UNION renvoie SQL_U_UNION ou SQL_U_UNION_ALL.  
  
 SQL_USER_NAME renvoie \<des> vierges.
