---
title: Fonction SQLProcedureColumns (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLProcedureColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedureColumns
helpviewer_keywords:
- SQLProcedureColumns function [ODBC]
ms.assetid: 4ca37b28-a6df-465b-8988-d422d37fc025
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d81e44b116ed6f26319d31430999a61a8a17f21
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306850"
---
# <a name="sqlprocedurecolumns-function"></a>Fonction SQLProcedureColumns
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLProcedureColumns** retourne la liste des paramètres d’entrée et de sortie, ainsi que les colonnes qui composent le résultat défini pour les procédures spécifiées. Le conducteur renvoie les informations sur l’instruction spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLProcedureColumns(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     ProcName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Nom du catalogue*  
 [Entrée] Nom du catalogue de procédure. Si un pilote prend en charge les catalogues pour certaines procédures, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, une chaîne vide ("") désigne les procédures qui n’ont pas de catalogues. *CatalogName* ne peut pas contenir un modèle de recherche de chaînes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID est configuré pour SQL_TRUE, *CatalogName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *CatalogName* est un argument ordinaire; il est traité littéralement, et son cas est significatif. Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur dans les caractères de*CatalogName*.  
  
 *SchemaName (SchemaName)*  
 [Entrée] Modèle de recherche de chaîne pour les noms de schéma de procédure. Si un conducteur prend en charge des schémas pour certaines procédures, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, une chaîne vide («)) désigne les procédures qui n’ont pas de schémas.  
  
 Si l’attribut de SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *SchemaName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *SchemaName* est un argument de valeur modèle; il est traité littéralement, et son cas est significatif.  
  
 *NomLength2*  
 [Entrée] Longueur dans les personnages de*SchemaName*.  
  
 *ProcName (ProcName)*  
 [Entrée] Modèle de recherche de chaîne pour les noms de procédure.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *ProcName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *ProcName* est un argument de valeur de modèle ; il est traité littéralement, et son cas est significatif.  
  
 *NomLength3*  
 [Entrée] Longueur dans les caractères de*ProcName*.  
  
 *ColumnName*  
 [Entrée] Modèle de recherche de chaîne pour les noms de colonne.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID est réglé pour SQL_TRUE, *ColumnName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *ColumnName* est un argument de valeur de modèle ; il est traité littéralement, et son cas est significatif.  
  
 *NomLength4*  
 [Entrée] Longueur dans les caractères de *'ColumnName*.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLProcedureColumns** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLProcedureColumns** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|24 000|État de curseur non valide|Un curseur était ouvert sur le *StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avaient été appelés. Cette erreur est retournée par le gestionnaire du conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA, et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.<br /><br /> Un curseur était ouvert sur le *StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelé.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLError** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|L’attribut de déclaration SQL_ATTR_METADATA_ID a été réglé pour SQL_TRUE, l’argument *CatalogName* était un pointeur nul, et le SQL_CATALOG_NAME *InfoType* retourne que les noms de catalogue sont pris en charge.<br /><br /> (DM) L’attribut de déclaration SQL_ATTR_METADATA_ID a été réglé pour SQL_TRUE, et l’argument *SchemaName*, *ProcName*, ou *ColumnName* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction aynschroneuse était encore en cours d’exécution lorsque la fonction SQLProcedureColumns a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur de l’un des arguments de longueur de nom était inférieure à 0, mais pas égale à SQL_NTS.<br /><br /> La valeur de l’un des arguments de longueur de nom a dépassé la valeur maximale de longueur pour le catalogue, le schéma, la procédure ou le nom de colonne correspondant.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Un catalogue de procédure a été spécifié, et le pilote ou la source de données ne prend pas en charge les catalogues.<br /><br /> Un schéma de procédure a été spécifié, et le conducteur ou la source de données ne prend pas en charge les schémas.<br /><br /> Un modèle de recherche de chaîne a été spécifié pour le schéma de procédure, le nom de la procédure ou le nom de colonne, et la source de données ne prend pas en charge les modèles de recherche pour un ou plusieurs de ces arguments.<br /><br /> La combinaison des paramètres actuels des attributs SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE de l’énoncé n’a pas été prise en charge par le conducteur ou la source de données.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est généralement utilisée avant l’exécution des relevés pour récupérer des informations sur les paramètres de procédure et les colonnes qui composent le paramètre de résultat ou les ensembles retournés par la procédure, le cas échéant. Pour plus d’informations, consultez [Procédures](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
> [!NOTE]  
>  **SQLProcedureColumns** pourrait ne pas retourner toutes les colonnes utilisées par une procédure. Par exemple, un pilote ne peut retourner que des informations sur les paramètres utilisés par une procédure et non sur les colonnes dans un ensemble de résultats qu’elle génère.  
  
 Les arguments *SchemaName*, *ProcName*et *ColumnName* acceptent les modèles de recherche. Pour plus d’informations sur les modèles de recherche valides, voir [Arguments de valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, voir [Catalog Functions](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLProcedureColumns** retourne les résultats comme un résultat standard établi, commandé par PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME et COLUMN_TYPE. Les noms de colonnes sont retournés pour chaque procédure dans l’ordre suivant : le nom de la valeur de déclaration, les noms de chaque paramètre dans l’invocation de la procédure (dans l’ordre d’appel), puis les noms de chaque colonne dans le résultat défini retourné par la procédure (dans l’ordre de colonne).  
  
 Les applications doivent lier les colonnes spécifiques au conducteur par rapport à la fin de l’ensemble de résultats. Pour plus d’informations, voir [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
 Pour déterminer la longueur réelle des colonnes PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME et COLUMN_NAME, une application peut appeler **SQLGetInfo** avec les options de SQL_MAX_CATALOG_NAME_LEN, de SQL_MAX_SCHEMA_NAME_LEN, de SQL_MAX_PROCEDURE_NAME_LEN et de SQL_MAX_COLUMN_NAME_LEN.  
  
 Les colonnes suivantes ont été rebaptisées pour ODBC 3. *x*. Les modifications du nom de colonne n’affectent pas la compatibilité vers l’arrière parce que les applications se lient par numéro de colonne.  
  
|Colonne ODBC 2.0|ODBC 3. *colonne x*|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|PROCÉDURE _OWNER|PROCEDURE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Les colonnes suivantes ont été ajoutées aux résultats établis retournés par **SQLProcedureColumns** pour ODBC 3. *x*:  
  
-   COLUMN_DEF  
  
-   DATETIME_CODE  
  
-   CHAR_OCTET_LENGTH  
  
-   ORDINAL_POSITION  
  
-   IS_NULLABLE  
  
 Le tableau suivant répertorie les colonnes dans l’ensemble de résultats. Des colonnes supplémentaires au-delà de la colonne 19 (IS_NULLABLE) peuvent être définies par le conducteur. Une application doit avoir accès à des colonnes spécifiques au conducteur en comptant à partir de la fin de l’ensemble de résultats plutôt que de spécifier une position ordinaire explicite. Pour plus d’informations, voir [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de la colonne|Numéro de colonne|Type de données|Commentaires|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|Nom du catalogue de procédure; NULL s’il n’est pas applicable à la source de données. Si un pilote prend en charge des catalogues pour certaines procédures, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les procédures qui n’ont pas de catalogues.|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|Nom du schéma de procédure; NULL s’il n’est pas applicable à la source de données. Si un conducteur prend en charge des schémas pour certaines procédures, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, il retourne une chaîne vide («)) pour les procédures qui n’ont pas de schémas.|  
|PROCEDURE_NAME (ODBC 2.0)|3|Varchar pas NULL|Nom de procédure. Une chaîne vide est retournée pour une procédure qui n’a pas de nom.|  
|COLUMN_NAME (ODBC 2.0)|4|Varchar pas NULL|Nom de colonne de procédure. Le conducteur retourne une chaîne vide pour une colonne de procédure qui n’a pas de nom.|  
|COLUMN_TYPE (ODBC 2.0)|5|Smallint non NULL|Définit la colonne de procédure comme un paramètre ou une colonne de résultat :<br /><br /> SQL_PARAM_TYPE_UNKNOWN: La colonne de procédure est un paramètre dont le type est inconnu. (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT : La colonne de procédure est un paramètre d’entrée. (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT_OUTPUT : La colonne de procédure est un paramètre d’entrée/sortie. (ODBC 1.0)<br /><br /> SQL_PARAM_OUTPUT : La colonne de procédure est un paramètre de sortie. (ODBC 2.0)<br /><br /> SQL_RETURN_VALUE : La colonne de procédure est la valeur de retour de la procédure. (ODBC 2.0)<br /><br /> SQL_RESULT_COL : La colonne de procédure est une colonne de résultat définie. (ODBC 1.0)|  
|DATA_TYPE (ODBC 2.0)|6|Smallint non NULL|Type de données SQL. Il peut s’agir d’un type de données SQL ODBC ou d’un type de données SQL spécifique au conducteur. Pour les types de données de date et d’intervalle, cette colonne renvoie les types de données concis (par exemple, SQL_TYPE_TIME ou SQL_INTERVAL_YEAR_TO_MONTH). Pour une liste des types de données SQL ODBC valides, consultez [les types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md) à l’annexe D : Data Types. Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur.|  
|TYPE_NAME (ODBC 2.0)|7|Varchar pas NULL|Nom de type de données dépendante des sources de données; par exemple, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY", ou "CHAR ( ) FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 2.0)|8|Integer|La taille de la colonne de la colonne de procédure sur la source de données. NULL est retourné pour les types de données où la taille de la colonne n’est pas applicable. Pour plus d’informations sur la précision, voir [Taille de colonne, Chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.|  
|BUFFER_LENGTH (ODBC 2.0)|9|Integer|La longueur des octets de données transférées sur une opération **SQLGetData** ou **SQLFetch** si SQL_C_DEFAULT est spécifiée. Pour les données numériques, cette taille peut être différente de la taille des données stockées sur la source de données. Pour plus d’informations, voir [Taille de colonne, Chiffres décimaux, Longueur Octet de transfert, et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md), dans l’annexe D: Data Types.|  
|DECIMAL_DIGITS (ODBC 2.0)|10|Smallint|Les chiffres décimaux de la colonne de procédure sur la source de données. NULL est retourné pour les types de données où les chiffres décimaux ne sont pas applicables. Pour plus d’informations sur les chiffres décimaux, voir [La taille de colonne, les chiffres décimaux, la longueur d’octet de transfert, et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md), dans l’annexe D : Data Types.|  
|NUM_PREC_RADIX (ODBC 2.0)|11|Smallint|Pour les types de données numériques, soit 10 ou 2.<br /><br /> Si 10, les valeurs dans COLUMN_SIZE et DECIMAL_DIGITS donnent le nombre de chiffres décimaux autorisés pour la colonne. Par exemple, une colonne DECIMAL(12,5) rendrait un NUM_PREC_RADIX de 10, un COLUMN_SIZE de 12 et un DECIMAL_DIGITS de 5; une colonne FLOAT pourrait rendre un NUM_PREC_RADIX de 10, un COLUMN_SIZE de 15, et un DECIMAL_DIGITS de NULL.<br /><br /> Si 2, les valeurs dans COLUMN_SIZE et DECIMAL_DIGITS donnent le nombre de bits autorisés dans la colonne. Par exemple, une colonne FLOAT peut retourner un NUM_PREC_RADIX de 2, un COLUMN_SIZE de 53, et une DECIMAL_DIGITS de NULL.<br /><br /> NULL est retourné pour les types de données où NUM_PREC_RADIX n’est pas applicable.|  
|NULLABLE (ODBC 2.0)|12|Smallint non NULL|Si la colonne de procédure accepte une valeur NULL :<br /><br /> SQL_NO_NULLS : La colonne de procédure n’accepte pas les valeurs NULL.<br /><br /> SQL_NULLABLE : La colonne de procédure accepte les valeurs NULL.<br /><br /> SQL_NULLABLE_UNKNOWN: On ne sait pas si la colonne de procédure accepte les valeurs NULL.|  
|REMARQUEs (ODBC 2.0)|13|Varchar|Une description de la colonne de procédure.|  
|COLUMN_DEF (ODBC 3.0)|14|Varchar|Valeur par défaut de la colonne.<br /><br /> Si NULL a été spécifié comme valeur par défaut, cette colonne est le mot NULL, non inclus dans les guillemets. Si la valeur par défaut ne peut pas être représentée sans troncation, cette colonne contient TRUNCATED, sans marques de citation unique. Si aucune valeur par défaut n’a été spécifiée, cette colonne est NULL.<br /><br /> La valeur de COLUMN_DEF peut être utilisée pour générer une nouvelle définition de colonne, sauf lorsqu’elle contient la valeur TRUNCATED.|  
|SQL_DATA_TYPE (ODBC 3.0)|15|Smallint non NULL|La valeur du type de données SQL tel qu’il apparaît dans le domaine SQL_DESC_TYPE du descripteur. Cette colonne est la même que la colonne DATA_TYPE, à l’exception des types de données de date et d’intervalle.<br /><br /> Pour les types de données de date et d’intervalle, le champ SQL_DATA_TYPE dans l’ensemble de résultat retournera SQL_INTERVAL ou SQL_DATETIME, et le champ SQL_DATETIME_SUB retournera le sous-code pour le type spécifique de données d’intervalle ou de date. (Voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|16|Smallint|Le code de sous-type pour les types de données de date et d’intervalle. Pour d’autres types de données, cette colonne renvoie un NULL.|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|17|Integer|La longueur maximale dans les octets d’un personnage ou d’une colonne de type de données binaires. Pour tous les autres types de données, cette colonne retourne une valeur NULL.|  
|ORDINAL_POSITION (ODBC 3.0)|18|Entier non NULL|Pour les paramètres d’entrée et de sortie, la position ordinaire du paramètre dans la définition de la procédure (dans l’ordre de paramètres croissant, à partir de 1). Pour une valeur de retour (le cas échéant), 0 est retourné. Pour les colonnes définies par résultat, la position ordinaire de la colonne dans l’ensemble de résultat, avec la première colonne dans l’ensemble de résultat étant le numéro 1. S’il y a plusieurs ensembles de résultats, les positions de colonne sont retournées d’une manière spécifique au conducteur.|  
|IS_NULLABLE (ODBC 3.0)|19|Varchar|"NON" si la colonne n’inclut pas les NULLs.<br /><br /> "OUI" si la colonne peut inclure des NULLs.<br /><br /> Cette colonne renvoie une chaîne de longueur zéro si la possibilité de valeurs Null n'est pas connue.<br /><br /> Les règles ISO sont utilisées pour déterminer la possibilité de valeur Null. Un SGBD compatible avec la norme ISO SQL ne peut pas renvoyer de chaîne vide.<br /><br /> La valeur renvoyée pour cette colonne est différente de celle renvoyée pour la colonne NULLABLE. (Voir la description de la colonne NULLABLE.)|  
  
## <a name="code-example"></a>Exemple de code  
 Voir [Les appels de procédure](../../../odbc/reference/develop-app/procedure-calls.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Aller chercher une seule rangée ou un bloc de données dans une direction avant-seulement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Retour d’une liste de procédures dans une source de données|[Fonction SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
