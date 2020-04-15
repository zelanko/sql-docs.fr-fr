---
title: Fonction SQLGetTypeInfo (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetTypeInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTypeInfo
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC]
ms.assetid: bdedb044-8924-4ca4-85f3-8b37578e0257
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47273c75a005f11b33e9929977b57607b36898de
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303260"
---
# <a name="sqlgettypeinfo-function"></a>Fonction SQLGetTypeInfo
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetTypeInfo** renvoie des informations sur les types de données pris en charge par la source de données. Le conducteur retourne l’information sous la forme d’un ensemble de résultats SQL. Les types de données sont destinés à être utilisés dans les énoncés de définition des données (DDL).  
  
> [!IMPORTANT]  
>  Les applications doivent utiliser les noms de type retournés dans la colonne TYPE_NAME du résultat **SQLGetTypeInfo** définis dans les instructions **ALTER TABLE** et **CREATE TABLE.** **SQLGetTypeInfo** peut retourner plus d’une ligne avec la même valeur dans la colonne DATA_TYPE.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetTypeInfo(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   DataType);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée d’énoncé pour l’ensemble de résultats.  
  
 *DataType*  
 [Entrée] Le type de données SQL. Il doit s’agir de l’une des valeurs de la section types de [données SQL](../../../odbc/reference/appendixes/sql-data-types.md) de l’Annexe D : Data Types, ou d’un type de données SQL spécifique au conducteur. SQL_ALL_TYPES précise que les informations sur tous les types de données doivent être retournées.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetTypeInfo** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLGetTypeInfo** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur de l’option modifiée|Un attribut de déclaration spécifiée était invalide en raison des conditions de travail de mise en œuvre, de sorte qu’une valeur similaire a été temporairement substituée. (Appelez **SQLGetStmtAttr** pour déterminer la valeur temporairement substituée.) La valeur de remplacement est valide pour le *StatementHandle* jusqu’à ce que le curseur soit fermé. Les attributs de déclaration qui peuvent être modifiés sont les : SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT et SQL_ATTR_SIMULATE_CURSOR. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|24 000|État de curseur non valide|Un curseur était ouvert sur le *StatementHandle,* et **SQLFetch** ou **SQLFetchScroll** avaient été appelés. Cette erreur est retournée par le gestionnaire du conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA, et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.<br /><br /> Un ensemble de résultats a été ouvert sur le *StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelé.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY004|Type de données SQL invalide|La valeur spécifiée pour l’argument *DataType* n’était ni un identifiant de type de données ODBC SQL valide, ni un identifiant de type de données spécifique au conducteur pris en charge par le conducteur.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*, puis la fonction a été appelée et, avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée et, avant qu’elle ne termine son exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLGetTypeInfo** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|La combinaison des paramètres actuels des attributs SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE de l’énoncé n’a pas été prise en charge par le conducteur ou la source de données.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur correspondant à la *DéclarationHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLGetTypeInfo** renvoie les résultats comme un résultat standard établi, commandé par DATA_TYPE puis par la façon dont les cartes de type de données au type de données correspondant ODBC SQL. Les types de données définis par la source de données ont préséance sur les types de données définis par l’utilisateur. Par conséquent, l’ordre de tri n’est pas nécessairement cohérent, mais peut être généralisé comme DATA_TYPE première, suivi par TYPE_NAME, tous deux ascendants. Supposons, par exemple, qu’une source de données ait défini les types de données INTEGER et COUNTER, où COUNTER est auto-incrémentation, et qu’un type de données défini par l’utilisateur WHOLENUM a également été défini. Ceux-ci seraient retournés dans l’ordre INTEGER, WHOLENUM, et COUNTER, parce que les cartes WHOLENUM étroitement au type de données ODBC SQL SQL_INTEGER, tandis que le type de données d’incrémentation automatique, même si pris en charge par la source de données, ne cartographie pas étroitement à un type de données SQL ODBC. Pour plus d’informations sur la façon dont ces informations pourraient être utilisées, voir [les déclarations DDL](../../../odbc/reference/develop-app/ddl-statements.md).  
  
 Si l’argument *de DataType* spécifie un type de données qui est valable pour la version d’ODBC prise en charge par le conducteur, mais n’est pas pris en charge par le conducteur, alors il retournera un ensemble de résultat vide.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, voir [Catalog Functions](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Les colonnes suivantes ont été rebaptisées pour ODBC 3. *x*. Les modifications du nom de colonne n’affectent pas la compatibilité vers l’arrière parce que les applications se lient par numéro de colonne.  
  
|Colonne ODBC 2.0|ODBC 3. *colonne x*|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 Les colonnes suivantes ont été ajoutées aux résultats établis par **SQLGetTypeInfo** pour ODBC 3. *x*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 Le tableau suivant répertorie les colonnes dans l’ensemble de résultats. Des colonnes supplémentaires au-delà de la colonne 19 (INTERVAL_PRECISION) peuvent être définies par le conducteur. Une application doit avoir accès à des colonnes spécifiques au conducteur en comptant à partir de la fin de l’ensemble de résultats plutôt que de spécifier une position ordinaire explicite. Pour plus d’informations, voir [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** pourrait ne pas retourner tous les types de données. Par exemple, un pilote peut ne pas retourner les types de données définis par l’utilisateur. Les applications peuvent utiliser n’importe quel type de données valide, qu’elles soient retournées ou non par **SQLGetTypeInfo**. Les types de données retournés par **SQLGetTypeInfo** sont ceux pris en charge par la source de données. Ils sont destinés à être utilisés dans les énoncés de langage de définition des données (DDL). Les conducteurs peuvent retourner les données de l’ensemble de résultats à l’aide de types de données autres que les types retournés par **SQLGetTypeInfo**. En créant l’ensemble de résultat pour une fonction de catalogue, le pilote peut utiliser un type de données qui n’est pas pris en charge par la source de données.  
  
|Nom de la colonne|Colonne<br /><br /> nombre|Type de données|Commentaires|  
|-----------------|-----------------------|---------------|--------------|  
|TYPE_NAME (ODBC 2.0)|1|Varchar pas NULL|Nom de type données dépendante des sources de données; par exemple, "CHAR()", "VARCHAR()", "MONEY", "LONG VARBINARY", ou "CHAR ( ) FOR BIT DATA". Les applications doivent utiliser ce nom dans les instructions **CREATE TABLE** et **ALTER TABLE.**|  
|DATA_TYPE (ODBC 2.0)|2|Smallint non NULL|Type de données SQL. Il peut s’agir d’un type de données SQL ODBC ou d’un type de données SQL spécifique au conducteur. Pour les types de données de date ou d’intervalle, cette colonne renvoie le type de données concis (comme SQL_TYPE_TIME ou SQL_INTERVAL_YEAR_TO_MONTH). Pour une liste des types de données SQL ODBC valides, consultez [les types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md) à l’annexe D : Data Types. Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur.|  
|COLUMN_SIZE (ODBC 2.0)|3|Integer|La taille maximale de la colonne que le serveur prend en charge pour ce type de données. Pour les données numériques, c’est la précision maximale. Pour les données de chaîne, c’est la longueur des caractères. Pour les types de données date, c’est la longueur des caractères de la représentation des cordes (en supposant la précision maximale autorisée du composant fractionnaire des secondes). NULL est retourné pour les types de données où la taille de la colonne n’est pas applicable. Pour les types de données d’intervalle, il s’agit du nombre de caractères dans la représentation des caractères de l’intervalle littéral (tel que défini par la précision de tête d’intervalle; voir [Interval Data Type Length](../../../odbc/reference/appendixes/interval-data-type-length.md) in Annexe D: Data Types).<br /><br /> Pour plus d’informations sur la taille de la colonne, voir [La taille de la colonne, les chiffres décimaux, la longueur d’octet de transfert et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe D : Types de données.|  
|LITERAL_PREFIX (ODBC 2.0)|4|Varchar|Caractère ou caractères utilisés pour préfixer un littéral; par exemple, une seule marque de de cotation (') pour les types de données de caractère ou 0x pour les types de données binaires; NULL est retourné pour les types de données où un préfixe littéral n’est pas applicable.|  
|LITERAL_SUFFIX (ODBC 2.0)|5|Varchar|Caractère ou caractères utilisés pour mettre fin à un littéral; par exemple, une seule marque de de cotation (') pour les types de données de caractère; NULL est retourné pour les types de données où un suffixe littéral n’est pas applicable.|  
|CREATE_PARAMS (ODBC 2.0)|6|Varchar|Une liste de mots clés, séparés par des virgules, correspondant à chaque paramètre que l’application peut spécifier entre parenthèses lors de l’utilisation du nom qui est retourné dans le champ TYPE_NAME. Les mots clés de la liste peuvent être l’un des éléments suivants : longueur, précision ou échelle. Ils apparaissent dans l’ordre que la syntaxe exige qu’ils soient utilisés. Par exemple, CREATE_PARAMS pour DECIMAL serait « précision, échelle »; CREATE_PARAMS pour VARCHAR serait égale « longueur ». NULL est retourné s’il n’y a pas de paramètres pour la définition de type de données; par exemple, INTEGER.<br /><br /> Le conducteur fournit le texte CREATE_PARAMS dans la langue du pays/région où il est utilisé.|  
|NULLABLE (ODBC 2.0)|7|Smallint non NULL|Si le type de données accepte une valeur NULL :<br /><br /> SQL_NO_NULLS si le type de données n’accepte pas les valeurs NULL.<br /><br /> SQL_NULLABLE si le type de données accepte les valeurs NULL.<br /><br /> SQL_NULLABLE_UNKNOWN s’on ne sait pas si la colonne accepte les valeurs NULL.|  
|CASE_SENSITIVE (ODBC 2.0)|8|Smallint non NULL|Si un type de données de caractère est sensible aux cas dans les collations et les comparaisons :<br /><br /> SQL_TRUE si le type de données est un type de données de caractère et est sensible aux cas.<br /><br /> SQL_FALSE si le type de données n’est pas un type de données de caractère ou n’est pas sensible aux cas.|  
|CONSULTABLE (ODBC 2.0)|9|Smallint non NULL|Comment le type de données est utilisé dans une clause **WHERE** :<br /><br /> SQL_PRED_NONE si la colonne ne peut pas être utilisée dans une clause **WHERE.** (C’est la même chose que la valeur SQL_UNSEARCHABLE dans ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR si la colonne peut être utilisée dans une clause **WHERE,** mais seulement avec le **predicate LIKE.** (C’est la même chose que la valeur SQL_LIKE_ONLY dans ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC si la colonne peut être utilisée dans une clause **WHERE** avec tous les opérateurs de comparaison à l’exception **de LIKE** (comparaison, comparaison quantifiée, **BETWEEN**, **DISTINCT**, **IN**, **MATCH**, et **UNIQUE**). (C’est la même chose que la valeur SQL_ALL_EXCEPT_LIKE dans ODBC 2. *x*.)<br /><br /> SQL_SEARCHABLE si la colonne peut être utilisée dans une clause **WHERE** avec n’importe quel opérateur de comparaison.|  
|UNSIGNED_ATTRIBUTE (ODBC 2.0)|10|Smallint|Que le type de données ne soit pas signé :<br /><br /> SQL_TRUE si le type de données n’est pas signé.<br /><br /> SQL_FALSE si le type de données est signé.<br /><br /> NULL est retourné si l’attribut n’est pas applicable au type de données ou si le type de données n’est pas numérique.|  
|FIXED_PREC_SCALE (ODBC 2.0)|11|Smallint non NULL|Si le type de données a prédéfinis la précision fixe et l’échelle (qui sont spécifiques à la source de données), comme un type de données monétaires :<br /><br /> SQL_TRUE s’il a prédéfinie la précision fixe et l’échelle.<br /><br /> SQL_FALSE s’il n’a pas prédéfinie la précision fixe et l’échelle.|  
|AUTO_UNIQUE_VALUE (ODBC 2.0)|12|Smallint|Si le type de données est autoincrémentation:<br /><br /> SQL_TRUE si le type de données est autoincrémentant.<br /><br /> SQL_FALSE si le type de données n’est pas autoincrément.<br /><br /> NULL est retourné si l’attribut n’est pas applicable au type de données ou si le type de données n’est pas numérique.<br /><br /> Une application peut insérer des valeurs dans une colonne ayant cet attribut, mais ne peut généralement pas mettre à jour les valeurs de la colonne.<br /><br /> Lorsqu’un insert est transformé en colonne d’incrément automatique, une valeur unique est insérée dans la colonne au moment de l’insérer. L’augmentation n’est pas définie, mais est spécifique à la source de données. Une application ne doit pas supposer qu’une colonne d’incrément automatique commence à un point ou à une incréments particuliers d’une valeur particulière.|  
|LOCAL_TYPE_NAME (ODBC 2.0)|13|Varchar|Version localisée du nom de type de données dépendant de la source de données. La valeur NULL est retournée si un nom localisé n'est pas pris en charge par la source de données. Ce nom est destiné à l’affichage seulement, comme dans les boîtes de dialogue.|  
|MINIMUM_SCALE (ODBC 2.0)|14|Smallint|L’échelle minimale du type de données sur la source de données. Si un type de données possède une échelle fixe, les colonnes MINIMUM_SCALE et MAXIMUM_SCALE contiennent toutes les deux cette valeur. Par exemple, une colonne SQL_TYPE_TIMESTAMP peut avoir une échelle fixe pour les fractions. La valeur NULL est retournée lorsque l'échelle n'est pas applicable. Pour plus d’informations, voir [Taille de colonne, chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.|  
|MAXIMUM_SCALE (ODBC 2.0)|15|Smallint|L’échelle maximale du type de données sur la source de données. La valeur NULL est retournée lorsque l'échelle n'est pas applicable. Si l’échelle maximale n’est pas définie séparément sur la source de données, mais est plutôt définie comme étant la même que la précision maximale, cette colonne contient la même valeur que la colonne COLUMN_SIZE. Pour plus d’informations, voir [Taille de colonne, chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.|  
|SQL_DATA_TYPE (ODBC 3.0)|16|Smallint PAS NULL|La valeur du type de données SQL tel qu’il apparaît dans le domaine SQL_DESC_TYPE du descripteur. Cette colonne est la même que la colonne DATA_TYPE, à l’exception des types de données d’intervalle et de date.<br /><br /> Pour les types de données d’intervalle et de date, le champ SQL_DATA_TYPE dans l’ensemble de résultat retournera SQL_INTERVAL ou SQL_DATETIME, et le champ SQL_DATETIME_SUB retournera le sous-code pour le type spécifique de données d’intervalle ou de date. (Voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|17|Smallint|Lorsque la valeur de SQL_DATA_TYPE est SQL_DATETIME ou SQL_INTERVAL, cette colonne contient le sous-code datetime/intervalle. Pour les types de données autres que l’heure de date et l’intervalle, ce champ est NULL.<br /><br /> Pour les types de données d’intervalle ou de date, le champ SQL_DATA_TYPE dans l’ensemble de résultat retournera SQL_INTERVAL ou SQL_DATETIME, et le champ SQL_DATETIME_SUB retournera le sous-code pour le type spécifique de données d’intervalle ou de date. (Voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|NUM_PREC_RADIX (ODBC 3.0)|18|Integer|Si le type de données est un type numérique approximatif, cette colonne contient la valeur 2 pour indiquer que COLUMN_SIZE spécifie un certain nombre de bits. Pour les types numériques exacts, cette colonne contient la valeur 10 pour indiquer que COLUMN_SIZE spécifie un certain nombre de chiffres décimaux. Sinon, cette colonne est NULL.|  
|INTERVAL_PRECISION (ODBC 3.0)|19|Smallint|Si le type de données est un type de données d’intervalle, cette colonne contient la valeur de la précision de direction de l’intervalle. (Voir [précision de type de données d’intervalle](../../../odbc/reference/appendixes/interval-data-type-precision.md) à l’annexe D : Types de données.) Sinon, cette colonne est NULL.|  
  
 Les informations d’attribut peuvent s’appliquer aux types de données ou à des colonnes spécifiques dans un ensemble de résultats. **SQLGetTypeInfo** renvoie des informations sur les attributs associés aux types de données; **SQLColAttribute renvoie** des informations sur les attributs associés aux colonnes dans un ensemble de résultats.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Informations de retour sur une colonne dans un ensemble de résultats|[Fonction SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Aller chercher une seule rangée ou un bloc de données dans une direction avant-seulement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Retour d’informations sur un conducteur ou une source de données|[Fonction SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
