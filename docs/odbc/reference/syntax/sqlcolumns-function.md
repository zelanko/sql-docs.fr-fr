---
title: Fonction SQLColumns (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumns
helpviewer_keywords:
- SQLColumns function [ODBC]
ms.assetid: 4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36293c1f2393e9a57351fc8cd19dcc6e3338f5cc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301255"
---
# <a name="sqlcolumns-function"></a>Fonction SQLColumns
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: Open Group  
  
 **Résumé**  
 **SQLColumns** renvoie la liste des noms de colonnes dans des tableaux spécifiés. Le conducteur renvoie ces informations à la suite définies sur le *StatementHandle*spécifié .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLColumns(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      ColumnName,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Nom du catalogue*  
 [Entrée] Nom du catalogue. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, une chaîne vide ("") indique les tables qui n’ont pas de catalogues. *CatalogName* ne peut pas contenir un modèle de recherche de chaînes.  
  
> [!NOTE]  
>  Si l’attribut de l’SQL_ATTR_METADATA_ID est configuré pour SQL_TRUE, *CatalogName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *CatalogName* est un argument ordinaire; il est traité littéralement, et son cas est significatif. Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur dans les caractères de*CatalogName*.  
  
 *SchemaName (SchemaName)*  
 [Entrée] Modèle de recherche de cordes pour les noms de schéma. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, une chaîne vide («)) indique les tables qui n’ont pas de schémas.  
  
> [!NOTE]  
>  Si l’attribut de SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *SchemaName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *SchemaName* est un argument de valeur modèle; il est traité littéralement, et son cas est significatif.  
  
 *NomLength2*  
 [Entrée] Longueur dans les personnages de*SchemaName*.  
  
 *TableName*  
 [Entrée] Modèle de recherche de cordes pour les noms de table.  
  
> [!NOTE]  
>  Si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *TableName* est traité comme un identifiant et son cas n’est pas significatif. S’il s’agit d’SQL_FALSE, *TableName* est un argument de valeur de modèle; il est traité littéralement, et son cas est significatif.  
  
 *NomLength3*  
 [Entrée] Longueur dans les caractères de*TableName*.  
  
 *ColumnName*  
 [Entrée] Modèle de recherche de chaîne pour les noms de colonne.  
  
> [!NOTE]  
>  Si l’attribut de l’SQL_ATTR_METADATA_ID est réglé pour SQL_TRUE, *ColumnName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *ColumnName* est un argument de valeur de modèle ; il est traité littéralement, et son cas est significatif.  
  
 *NomLength4*  
 [Entrée] Longueur dans les caractères de *'ColumnName*.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLColumns** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLColumns** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|24 000|État de curseur non valide|Un curseur était ouvert sur le *StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avaient été appelés. Cette erreur est retournée par le gestionnaire du conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA, et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.<br /><br /> Un curseur était ouvert sur le *StatementHandle,* mais **SQLFetch** ou **SQLFetchScroll** n’avaient pas été appelés.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|L’attribut de déclaration SQL_ATTR_METADATA_ID a été réglé pour SQL_TRUE, l’argument *CatalogName* était un pointeur nul, et le SQL_CATALOG_NAME *InfoType* retourne que les noms de catalogue sont pris en charge.<br /><br /> (DM) L’attribut de déclaration SQL_ATTR_METADATA_ID a été réglé pour SQL_TRUE, et l’argument *SchemaName*, *TableName*, ou *ColumnName* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLColumns** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur de l’un des arguments de longueur de nom était inférieure à 0, mais pas égale à SQL_NTS.|  
|||La valeur de l’un des arguments de longueur de nom a dépassé la valeur maximale de longueur pour le catalogue ou le nom correspondant. La longueur maximale de chaque catalogue ou nom peut être obtenue en appelant **SQLGetInfo** avec les valeurs *InfoType.* (Voir "Commentaires.")|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Un nom de catalogue a été spécifié, et le pilote ou la source de données ne prend pas en charge les catalogues.<br /><br /> Un nom de schéma a été spécifié, et le conducteur ou la source de données ne prend pas en charge les schémas.<br /><br /> Un modèle de recherche de chaîne a été spécifié pour le nom de schéma, le nom de table ou le nom de colonne, et la source de données ne prend pas en charge les modèles de recherche pour un ou plusieurs de ces arguments.<br /><br /> La combinaison des paramètres actuels des attributs SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE de l’énoncé n’a pas été prise en charge par le conducteur ou la source de données.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est généralement utilisée avant l’exécution des déclarations pour récupérer des informations sur les colonnes d’une table ou de tables du catalogue de la source de données. **SQLColumns** peut être utilisé pour récupérer des données pour tous les types d’articles retournés par **SQLTables**. En plus des tables de base, cela peut inclure (mais ne se limite pas) à) des vues, des synonymes, des tables système, et ainsi de suite. En revanche, les fonctions **SQLColAttribute** et **SQLDescribeCol** décrivent les colonnes dans un ensemble de résultats et la fonction **SQLNumResultCols** renvoie le nombre de colonnes dans un ensemble de résultats. Pour plus d’informations, voir [Utilisations des données de catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, voir [Catalog Functions](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLColumns** retourne les résultats comme un résultat standard établi, commandé par TABLE_CAT, TABLE_SCHEM, TABLE_NAME et ORDINAL_POSITION.  
  
> [!NOTE]  
>  Lorsqu’une application fonctionne avec un ODBC 2. *x* pilote, aucune colonne ORDINAL_POSITION n’est retournée dans l’ensemble de résultats. Par conséquent, lorsque vous travaillez avec ODBC 2. *x* pilotes, l’ordre des colonnes dans la liste de colonnes retournées par **SQLColumns** n’est pas nécessairement le même que l’ordre des colonnes retournées lorsque l’application effectue une déclaration SELECT sur toutes les colonnes de ce tableau.  
  
> [!NOTE]  
>  **SQLColumns** pourrait ne pas retourner toutes les colonnes. Par exemple, un pilote peut ne pas retourner d’informations sur les pseudo-colonnes, telles qu’Oracle ROWID. Les applications peuvent utiliser n’importe quelle colonne valide, si elle est retournée par **SQLColumns**.  
>   
>  Certaines colonnes qui peuvent être retournées par **SQLStatistics** ne sont pas retournées par **SQLColumns**. Par exemple, **SQLColumns** ne retourne pas les colonnes dans un index créé sur une expression ou un filtre, comme SALARY - BENEFITS ou DEPT - 0012.  
  
 Les longueurs des colonnes VARCHAR ne sont pas indiquées dans le tableau; les longueurs réelles dépendent de la source de données. Pour déterminer la longueur réelle des colonnes TABLE_CAT, TABLE_SCHEM, TABLE_NAME et COLUMN_NAME, une application peut appeler **SQLGetInfo** avec les options de SQL_MAX_CATALOG_NAME_LEN, de SQL_MAX_SCHEMA_NAME_LEN, de SQL_MAX_TABLE_NAME_LEN et de SQL_MAX_COLUMN_NAME_LEN.  
  
 Les colonnes suivantes ont été rebaptisées pour ODBC 3. *x*. Les modifications du nom de colonne n’affectent pas la compatibilité vers l’arrière parce que les applications se lient par numéro de colonne.  
  
|Colonne ODBC 2.0|ODBC 3. *colonne x*|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Les colonnes suivantes ont été ajoutées à l’ensemble de résultats retournés par **SQLColumns** pour ODBC 3. *x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 Le tableau suivant répertorie les colonnes dans l’ensemble de résultats. Des colonnes supplémentaires au-delà de la colonne 18 (IS_NULLABLE) peuvent être définies par le conducteur. Une application doit avoir accès à des colonnes spécifiques au conducteur en comptant à partir de la fin de l’ensemble de résultat au lieu de spécifier une position ordinaire explicite. Pour plus d’informations, voir [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de la colonne|Colonne<br /><br /> nombre|Type de données|Commentaires|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Nom du catalogue; NULL s’il n’est pas applicable à la source de données. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de catalogues.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Nom de Schema; NULL s’il n’est pas applicable à la source de données. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de schémas.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar pas NULL|Nom de la table.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar pas NULL|Nom de la colonne. Le conducteur retourne une chaîne vide pour une colonne qui n’a pas de nom.|  
|DATA_TYPE (ODBC 1.0)|5|Smallint non NULL|Type de données SQL. Il peut s’agir d’un type de données SQL ODBC ou d’un type de données SQL spécifique au conducteur. Pour les types de données de date et d’intervalle, cette colonne renvoie le type de données concis (comme SQL_TYPE_DATE ou SQL_INTERVAL_YEAR_TO_MONTH, au lieu du type de données nonconcise tel que SQL_DATETIME ou SQL_INTERVAL). Pour une liste des types de données SQL ODBC valides, consultez [les types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md) à l’annexe D : Data Types. Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur.<br /><br /> Les types de données retournés pour ODBC 3. *x* et ODBC 2. *x* applications peuvent être différentes. Pour plus d’informations, voir [Compatibilité vers l’arrière et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|TYPE_NAME (ODBC 1.0)|6|Varchar pas NULL|Nom de type de données dépendante des sources de données; par exemple, "CHAR", "VARCHAR", "MONEY", "LONG VARBINAR", ou "CHAR ( ) FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 1.0)|7|Integer|Si DATA_TYPE est SQL_CHAR ou SQL_VARCHAR, cette colonne contient la longueur maximale des caractères de la colonne. Pour les types de données date, il s’agit du nombre total de caractères requis pour afficher la valeur lorsqu’il est converti en caractères. Pour les types de données numériques, il s’agit soit du nombre total de chiffres, soit du nombre total de bits autorisés dans la colonne, selon la colonne NUM_PREC_RADIX. Pour les types de données d’intervalle, il s’agit du nombre de caractères dans la représentation des caractères de l’intervalle littéral (tel que défini par la précision de tête d’intervalle, voir [Interval Data Type Length](../../../odbc/reference/appendixes/interval-data-type-length.md) in Annexe D: Data Types). Pour plus d’informations, voir [Taille de colonne, chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.|  
|BUFFER_LENGTH (ODBC 1.0)|8|Integer|La longueur des octets de données transférées sur une opération SQLGetData, SQLFetch ou SQLFetchScroll si SQL_C_DEFAULT est spécifiée. Pour les données numériques, cette taille peut différer de la taille des données stockées sur la source de données. Cette valeur peut différer de COLUMN_SIZE colonne pour les données de caractère. Pour plus d’informations sur la longueur, voir [Taille de colonne, Chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.|  
|DECIMAL_DIGITS (ODBC 1.0)|9|Smallint|Le nombre total de chiffres significatifs à droite du point décimal. Pour SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP, cette colonne contient le nombre de chiffres dans le composant fractionnaire secondes. Pour les autres types de données, il s’agit des chiffres décimaux de la colonne sur la source de données. Pour les types de données d’intervalle qui contiennent un composant de temps, cette colonne contient le nombre de chiffres à droite du point décimal (fractions de secondes). Pour les types de données d’intervalle qui ne contiennent pas de composant de temps, cette colonne est de 0. Pour plus d’informations sur les chiffres décimaux, voir [La taille de colonne, les chiffres décimaux, la longueur d’octet de transfert et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe D : Data Types. NULL est retourné pour les types de données où DECIMAL_DIGITS n’est pas applicable.|  
|NUM_PREC_RADIX (ODBC 1.0)|10|Smallint|Pour les types de données numériques, soit 10 ou 2. S’il est de 10, les valeurs dans COLUMN_SIZE et DECIMAL_DIGITS donnent le nombre de chiffres décimaux autorisés pour la colonne. Par exemple, une colonne DECIMAL(12,5) rendrait un NUM_PREC_RADIX de 10, un COLUMN_SIZE de 12 et un DECIMAL_DIGITS de 5; une colonne FLOAT pourrait rendre un NUM_PREC_RADIX de 10, un COLUMN_SIZE de 15, et un DECIMAL_DIGITS de NULL.<br /><br /> Si c’est 2, les valeurs dans COLUMN_SIZE et DECIMAL_DIGITS donnent le nombre de bits autorisés dans la colonne. Par exemple, une colonne FLOAT peut renvoyer un RADIX de 2, un COLUMN_SIZE de 53, et une DECIMAL_DIGITS de NULL.<br /><br /> NULL est retourné pour les types de données où NUM_PREC_RADIX n’est pas applicable.|  
|NULLABLE (ODBC 1.0)|11|Smallint non NULL|SQL_NO_NULLS si la colonne ne pouvait pas inclure les valeurs NULL.<br /><br /> SQL_NULLABLE si la colonne accepte les valeurs NULL.<br /><br /> SQL_NULLABLE_UNKNOWN s’on ne sait pas si la colonne accepte les valeurs NULL.<br /><br /> La valeur retournée pour cette colonne diffère de la valeur retournée pour la colonne IS_NULLABLE. La colonne NULLABLE indique avec certitude qu’une colonne peut accepter des NULLs, mais ne peut pas indiquer avec certitude qu’une colonne n’accepte pas les NULLs. La colonne IS_NULLABLE indique avec certitude qu’une colonne ne peut pas accepter les NULLs, mais ne peut pas indiquer avec certitude qu’une colonne accepte les NULLs.|  
|REMARQUEs (ODBC 1.0)|12|Varchar|Une description de la colonne.|  
|COLUMN_DEF (ODBC 3.0)|13|Varchar|Valeur par défaut de la colonne. La valeur de cette colonne doit être interprétée comme une chaîne si elle est incluse dans des guillemets.<br /><br /> Si NULL a été spécifié comme valeur par défaut, cette colonne est le mot NULL, non inclus dans les guillemets. Si la valeur par défaut ne peut pas être représentée sans troncation, cette colonne contient TRUNCATED, sans joindre des guillemets uniques. Si aucune valeur par défaut n’a été spécifiée, cette colonne est NULL.<br /><br /> La valeur de COLUMN_DEF peut être utilisée pour générer une nouvelle définition de colonne, sauf lorsqu’elle contient la valeur TRUNCATED.|  
|SQL_DATA_TYPE (ODBC 3.0)|14|Smallint non NULL|Type de données SQL, tel qu’il apparaît dans le domaine des records SQL_DESC_TYPE dans l’IRD. Il peut s’agir d’un type de données SQL ODBC ou d’un type de données SQL spécifique au conducteur. Cette colonne est la même que la colonne DATA_TYPE, à l’exception des types de données de date et d’intervalle. Cette colonne renvoie le type de données nonconcise (comme SQL_DATETIME ou SQL_INTERVAL), au lieu du type de données concis (comme SQL_TYPE_DATE ou SQL_INTERVAL_YEAR_TO_MONTH) pour les types de données de date et d’intervalle. Si cette colonne renvoie SQL_DATETIME ou SQL_INTERVAL, le type de données spécifique peut être déterminé à partir de la colonne SQL_DATETIME_SUB. Pour une liste des types de données SQL ODBC valides, consultez [les types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md) à l’annexe D : Data Types. Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur.<br /><br /> Les types de données retournés pour ODBC 3. *x* et ODBC 2. *x* applications peuvent être différentes. Pour plus d’informations, voir [Compatibilité vers l’arrière et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|SQL_DATETIME_SUB (ODBC 3.0)|15|Smallint|Le code de sous-type pour les types de données de date et d’intervalle. Pour d’autres types de données, cette colonne renvoie un NULL. Pour plus d’informations sur les sous-codes de date et d’intervalle, voir « SQL_DESC_DATETIME_INTERVAL_CODE » dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|16|Integer|La longueur maximale dans les octets d’un personnage ou d’une colonne de type de données binaires. Pour tous les autres types de données, cette colonne retourne une valeur NULL.|  
|ORDINAL_POSITION (ODBC 3.0)|17|Entier non NULL|Position ordinale de la colonne dans la table. La première colonne dans le tableau est le numéro 1.|  
|IS_NULLABLE (ODBC 3.0)|18|Varchar|"NON" si la colonne n’inclut pas les NULLs.<br /><br /> "OUI" si la colonne peut inclure nulLs.<br /><br /> Cette colonne renvoie une chaîne de longueur zéro si la possibilité de valeurs Null n'est pas connue.<br /><br /> Les règles ISO sont utilisées pour déterminer la possibilité de valeur Null. Un SGBD compatible avec la norme ISO SQL ne peut pas renvoyer de chaîne vide.<br /><br /> La valeur retournée pour cette colonne diffère de la valeur retournée pour la colonne NULLABLE. (Voir la description de la colonne NULLABLE.)|  
  
## <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une demande déclare des tampons pour le résultat établi par **SQLColumns**. Il appelle **SQLColumns** pour retourner un ensemble de résultats qui décrit chaque colonne dans le tableau EMPLOYEE. Il appelle ensuite **SQLBindCol** pour lier les colonnes dans le résultat réglé aux tampons. Enfin, l’application récupère chaque série de données avec **SQLFetch** et les traite.  
  
```cpp  
// SQLColumns_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#define STR_LEN 128 + 1  
#define REM_LEN 254 + 1  
  
// Declare buffers for result set data  
SQLCHAR szSchema[STR_LEN];  
SQLCHAR szCatalog[STR_LEN];  
SQLCHAR szColumnName[STR_LEN];  
SQLCHAR szTableName[STR_LEN];  
SQLCHAR szTypeName[STR_LEN];  
SQLCHAR szRemarks[REM_LEN];  
SQLCHAR szColumnDefault[STR_LEN];  
SQLCHAR szIsNullable[STR_LEN];  
  
SQLINTEGER ColumnSize;  
SQLINTEGER BufferLength;  
SQLINTEGER CharOctetLength;  
SQLINTEGER OrdinalPosition;  
  
SQLSMALLINT DataType;  
SQLSMALLINT DecimalDigits;  
SQLSMALLINT NumPrecRadix;  
SQLSMALLINT Nullable;  
SQLSMALLINT SQLDataType;  
SQLSMALLINT DatetimeSubtypeCode;  
  
SQLHSTMT hstmt = NULL;  
  
// Declare buffers for bytes available to return  
SQLINTEGER cbCatalog;  
SQLINTEGER cbSchema;  
SQLINTEGER cbTableName;  
SQLINTEGER cbColumnName;  
SQLINTEGER cbDataType;  
SQLINTEGER cbTypeName;  
SQLINTEGER cbColumnSize;  
SQLLEN cbBufferLength;  
SQLINTEGER cbDecimalDigits;  
SQLINTEGER cbNumPrecRadix;  
SQLINTEGER cbNullable;  
SQLINTEGER cbRemarks;  
SQLINTEGER cbColumnDefault;  
SQLINTEGER cbSQLDataType;  
SQLINTEGER cbDatetimeSubtypeCode;  
SQLINTEGER cbCharOctetLength;  
SQLINTEGER cbOrdinalPosition;  
SQLINTEGER cbIsNullable;  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retcode = SQLColumns(hstmt, NULL, 0, NULL, 0, (SQLCHAR*)"CUSTOMERS", SQL_NTS, NULL, 0);  
  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      // Bind columns in result set to buffers  
      SQLBindCol(hstmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&cbCatalog);  
      SQLBindCol(hstmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);  
      SQLBindCol(hstmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&cbTableName);  
      SQLBindCol(hstmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);  
      SQLBindCol(hstmt, 5, SQL_C_SSHORT, &DataType, 0, &cbDataType);  
      SQLBindCol(hstmt, 6, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);  
      SQLBindCol(hstmt, 7, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);  
      SQLBindCol(hstmt, 8, SQL_C_SLONG, &BufferLength, 0, &cbBufferLength);  
      SQLBindCol(hstmt, 9, SQL_C_SSHORT, &DecimalDigits, 0, &cbDecimalDigits);  
      SQLBindCol(hstmt, 10, SQL_C_SSHORT, &NumPrecRadix, 0, &cbNumPrecRadix);  
      SQLBindCol(hstmt, 11, SQL_C_SSHORT, &Nullable, 0, &cbNullable);  
      SQLBindCol(hstmt, 12, SQL_C_CHAR, szRemarks, REM_LEN, &cbRemarks);  
      SQLBindCol(hstmt, 13, SQL_C_CHAR, szColumnDefault, STR_LEN, &cbColumnDefault);  
      SQLBindCol(hstmt, 14, SQL_C_SSHORT, &SQLDataType, 0, &cbSQLDataType);  
      SQLBindCol(hstmt, 15, SQL_C_SSHORT, &DatetimeSubtypeCode, 0, &cbDatetimeSubtypeCode);  
      SQLBindCol(hstmt, 16, SQL_C_SLONG, &CharOctetLength, 0, &cbCharOctetLength);  
      SQLBindCol(hstmt, 17, SQL_C_SLONG, &OrdinalPosition, 0, &cbOrdinalPosition);  
      SQLBindCol(hstmt, 18, SQL_C_CHAR, szIsNullable, STR_LEN, &cbIsNullable);  
  
      while (SQL_SUCCESS == retcode) {  
         retcode = SQLFetch(hstmt);  
         /*  
         if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // show_error();  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // Process fetched data  
         else  
            break;  
        */  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Privilèges de retour pour une colonne ou des colonnes|[Fonction SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Aller chercher plusieurs rangées de données|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Retour de colonnes qui identifient uniquement une ligne, ou des colonnes automatiquement mises à jour par une transaction|[Fonction SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|Retour des statistiques et des indices de table|[Fonction SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Retour d’une liste de tableaux dans une source de données|[Fonction SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
|Privilèges de retour pour une table ou une table|[Fonction SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
