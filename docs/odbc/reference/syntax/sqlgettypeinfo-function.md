---
title: SQLGetTypeInfo, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aef1e90053eba71db84e1fe89aa90684829a4941
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536531"
---
# <a name="sqlgettypeinfo-function"></a>Fonction SQLGetTypeInfo
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLGetTypeInfo** retourne des informations sur les types de données pris en charge par la source de données. Le pilote retourne les informations sous la forme d’un jeu de résultats SQL. Les types de données sont destinées à être utilisés dans les instructions de langage de définition de données (DDL).  
  
> [!IMPORTANT]  
>  Les applications doivent utiliser les noms de type retournés dans la colonne TYPE_NAME de le **SQLGetTypeInfo** jeu de résultats **ALTER TABLE** et **CREATE TABLE** instructions. **SQLGetTypeInfo** peut retourner plusieurs lignes avec la même valeur dans la colonne DATA_TYPE.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetTypeInfo(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   DataType);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction du jeu de résultats.  
  
 *DataType*  
 [Entrée] Le type de données SQL. Il doit s’agir des valeurs dans le [les Types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md) section de l’annexe d : Types de données, ou un type de données spécifiques au pilote SQL. SQL_ALL_TYPES Spécifie que les informations sur tous les types de données doivent être retournées.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetTypeInfo** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL _HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLGetTypeInfo** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur d’option modifiée|Un attribut d’instruction spécifiée non valide en raison de conditions de travail d’implémentation, donc une valeur similaire a été remplacée temporairement. (Appelez **SQLGetStmtAttr** pour déterminer la valeur temporairement substituée.) La valeur de remplacement n’est valide pour le *au paramètre StatementHandle* jusqu'à ce que le curseur est fermé. Les attributs d’instruction qui peuvent être modifiés sont : SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT et SQL_ATTR_SIMULATE_CURSOR. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|24000|État de curseur non valide|Un curseur a été ouvert sur le *au paramètre StatementHandle,* et **SQLFetch** ou **SQLFetchScroll** avait été appelée. Cette erreur est retournée par le Gestionnaire de pilotes si **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_NO_DATA et est retourné par le pilote si **SQLFetch** ou **SQLFetchScroll** a retourné SQL_NO_DATA.<br /><br /> Un jeu de résultats a été ouvert sur le *au paramètre StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelée.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY004|Type de données SQL non valide|La valeur spécifiée pour l’argument *DataType* n’est ni un identificateur de type de données ODBC SQL valide ni un identificateur de type de données spécifique au pilote pris en charge par le pilote.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*, puis la fonction a été appelée et, avant qu’il l’exécution achevée, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*. La fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et, avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLGetTypeInfo** fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|La combinaison des paramètres actuels des attributs d’instruction SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE n’était pas pris en charge par la pilote ou source de données.<br /><br /> L’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a été défini sur SQL_UB_VARIABLE, et l’attribut d’instruction SQL_ATTR_CURSOR_TYPE a été défini pour un type de curseur pour lequel le pilote ne prend pas en charge les signets.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant que la source de données a retourné le jeu de résultats. Le délai d’expiration est défini via **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le pilote correspondant à la *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLGetTypeInfo** retourne les résultats sous la forme d’un jeu de résultats standard, trié par DATA_TYPE, puis par quelle mesure le type de données est mappé au type de données ODBC SQL correspondant. Types de données définis par la source de données sont prioritaires sur les types de données définis par l’utilisateur. Par conséquent, l’ordre de tri ne correspond pas nécessairement mais peut être généralisé en tant que DATA_TYPE tout d’abord, suivi de TYPE_NAME, les deux par ordre croissant. Par exemple, supposons qu’une source de données défini par les types de données entier et compteur, où le compteur est à incrémentation automatique, et qu’un type de données défini par l’utilisateur WHOLENUM a également été défini. Il serait retournée dans l’ordre entier, WHOLENUM et compteur, étant donné que mappe WHOLENUM étroitement aux données SQL ODBC type SQL_INTEGER, tandis que le type de données auto-incrémentée, même si la prise en charge par la source de données ne mappe pas étroitement à un type de données ODBC SQL. Pour plus d’informations sur la façon dont ces informations peuvent être utilisées, consultez [instructions DDL](../../../odbc/reference/develop-app/ddl-statements.md).  
  
 Si le *DataType* argument spécifie un type de données qui est valide pour la version d’ODBC pris en charge par le pilote, mais n’est pas pris en charge par le pilote, puis elle retournera le jeu de résultats vide.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, consultez [fonctions de catalogue](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Les colonnes suivantes ont été renommées pour ODBC 3. *x*. Les modifications de nom de colonne n’affectent pas la compatibilité descendante, car les applications lier par numéro de colonne.  
  
|Colonne de ODBC 2.0|ODBC 3. *x* colonne|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 Les colonnes suivantes ont été ajoutées pour le jeu de résultats retourné par **SQLGetTypeInfo** pour ODBC 3. *x*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 Le tableau suivant répertorie les colonnes du jeu de résultats. Les colonnes supplémentaires au-delà de la colonne 19 (INTERVAL_PRECISION) peuvent être définies par le pilote. Une application doit accéder à des colonnes spécifiques aux pilotes à rebours à partir de la fin du jeu de résultats au lieu d’en spécifiant une position ordinale explicite. Pour plus d’informations, consultez [les données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** peut ne pas retourner tous les types de données. Par exemple, un pilote peuvent ne pas retourne des types de données définis par l’utilisateur. Applications peuvent utiliser n’importe quel type de données valides, indépendamment de si elle est retournée par **SQLGetTypeInfo**. Les types de données retournés par **SQLGetTypeInfo** sont pris en charge par la source de données. Elles sont destinées à utiliser dans les instructions de langage de définition de données (DDL). Pilotes peuvent retourner des données de jeu de résultats à l’aide des types de données autres que les types retournés par **SQLGetTypeInfo**. Lors de la création du jeu de résultats pour une fonction de catalogue, le pilote peut utiliser un type de données qui n’est pas pris en charge par la source de données.  
  
|Nom de colonne|colonne<br /><br /> nombre|Type de données|Commentaires|  
|-----------------|-----------------------|---------------|--------------|  
|TYPE_NAME (ODBC 2.0)|1|Varchar non NULL|Nom du type de données dépend de la source de données ; par exemple, « CHAR() », « VARCHAR() », « Argent », « LONG VARBINARY » ou « CHAR () pour les données BIT ». Les applications doivent utiliser ce nom dans **CREATE TABLE** et **ALTER TABLE** instructions.|  
|DATA_TYPE (ODBC 2.0)|2|Smallint non NULL|Type de données SQL. Cela peut être un type de données ODBC SQL ou un type de données spécifiques au pilote SQL. Pour les types de données datetime ou interval, cette colonne renvoie le type de données concis (par exemple, SQL_TYPE_TIME ou SQL_INTERVAL_YEAR_TO_MONTH). Pour obtenir la liste des types de données ODBC SQL valides, consultez [les Types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md) dans l’annexe d : Types de données. Pour plus d’informations sur les types de données spécifiques au pilote SQL, consultez la documentation du pilote.|  
|COLUMN_SIZE (ODBC 2.0)|3|Entier|La taille maximale de la colonne que le serveur prend en charge pour ce type de données. Pour les données numériques, il s’agit de la précision maximale. Pour les données de chaîne, il s’agit de la longueur en caractères. Pour les types de données datetime, il s’agit de la longueur en caractères de la représentation sous forme de chaîne (en supposant la précision maximale autorisée du composant en fractions de seconde). La valeur NULL est retournée pour les types de données où la taille de la colonne n’est pas applicable. Pour les types de données d’intervalle, il s’agit du nombre de caractères dans la représentation sous forme de caractère de l’intervalle de littéral (tel que défini par l’intervalle de début de précision ; consultez [longueur du Type de données intervalle](../../../odbc/reference/appendixes/interval-data-type-length.md) dans l’annexe d : Types de données).<br /><br /> Pour plus d’informations sur la taille de colonne, consultez [taille de colonne, des chiffres décimaux, transférer la longueur en octets et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe d : Types de données.|  
|LITERAL_PREFIX (ODBC 2.0)|4|Varchar|Ou les caractères utilisés pour préfixer un littéral ; par exemple, un guillemet simple (') pour les types de données caractère ou 0 x pour les types de données binaires ; La valeur NULL est retournée pour les types de données où un préfixe n’est pas applicable.|  
|LITERAL_SUFFIX (ODBC 2.0)|5|Varchar|Ou les caractères utilisés pour mettre fin à un littéral ; par exemple, un guillemet simple (') pour les types de données de caractères ; La valeur NULL est retournée pour les types de données où un suffixe littéral n’est pas applicable.|  
|CREATE_PARAMS (ODBC 2.0)|6|Varchar|Une liste de mots-clés, séparés par des virgules, correspondant à chaque paramètre que l’application peut spécifier entre parenthèses lorsque vous utilisez le nom qui est retourné dans le champ TYPE_NAME. Les mots clés dans la liste peuvent être une des opérations suivantes : longueur, la précision ou l’échelle. Ils apparaissent dans l’ordre que la syntaxe en a besoin pour être utilisé. Par exemple, CREATE_PARAMS pour décimale serait « precision, scale » ; CREATE_PARAMS pour VARCHAR serait égale à « longueur ». La valeur NULL est retournée si aucun paramètre pour la définition de type de données ; par exemple, d’entier.<br /><br /> Le pilote fournit le texte CREATE_PARAMS dans la langue du pays/région où il est utilisé.|  
|NULLABLE (ODBC 2.0)|7|Smallint non NULL|Indique si le type de données accepte une valeur NULL :<br /><br /> SQL_NO_NULLS si le type de données n’accepte pas les valeurs NULL.<br /><br /> SQL_NULLABLE si le type de données accepte les valeurs NULL.<br /><br /> SQL_NULLABLE_UNKNOWN si on ne sait pas si la colonne accepte les valeurs NULL.|  
|CASE_SENSITIVE (ODBC 2.0)|8|Smallint non NULL|Si un type de données de caractères respecte la casse dans les classements et les comparaisons :<br /><br /> SQL_TRUE si le type de données est un type de données caractères et respecte la casse.<br /><br /> SQL_FALSE si le type de données n’est pas un type de données caractère ou ne respecte pas la casse.|  
|POSSIBILITÉ DE RECHERCHE (ODBC 2.0)|9|Smallint non NULL|Comment le type de données est utilisé dans un **où** clause :<br /><br /> SQL_PRED_NONE si la colonne ne peut pas être utilisée dans un **où** clause. (Cela est identique à la valeur SQL_UNSEARCHABLE dans ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR si la colonne peut être utilisée dans un **où** clause, mais uniquement avec les **comme** prédicat. (Cela est identique à la valeur SQL_LIKE_ONLY dans ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC si la colonne peut être utilisée dans un **où** clause avec tous les opérateurs de comparaison à l’exception **comme** (comparaison, de comparaison, **BETWEEN**,  **DISTINCT**, **IN**, **correspondance**, et **UNIQUE**). (Cela est identique à la valeur SQL_ALL_EXCEPT_LIKE dans ODBC 2. *x*.)<br /><br /> SQL_SEARCHABLE si la colonne peut être utilisée dans un **où** clause avec n’importe quel opérateur de comparaison.|  
|UNSIGNED_ATTRIBUTE (ODBC 2.0)|10|Smallint|Indique si le type de données n’est pas signé :<br /><br /> SQL_TRUE si le type de données n’est pas signé.<br /><br /> SQL_FALSE si le type de données est signé.<br /><br /> La valeur NULL est retournée si l’attribut n’est pas applicable au type de données ou le type de données n’est pas numérique.|  
|FIXED_PREC_SCALE (ODBC 2.0)|11|Smallint non NULL|Indique si le type de données a prédéfinies fixe la précision et l’échelle (qui sont spécifiques à la source de données), comme un type de données money :<br /><br /> Précision et échelle fixes SQL_TRUE si elle a prédéfinies.<br /><br /> SQL_FALSE si elle n’a pas de mise à l’échelle et une précision fixe prédéfinie.|  
|AUTO_UNIQUE_VALUE (ODBC 2.0)|12|Smallint|Indique si le type de données est incrémentée automatiquement :<br /><br /> SQL_TRUE si le type de données est à auto-incrémentation.<br /><br /> SQL_FALSE si le type de données n’est pas incrémentée automatiquement.<br /><br /> La valeur NULL est retournée si l’attribut n’est pas applicable au type de données ou le type de données n’est pas numérique.<br /><br /> Une application peut insérer des valeurs dans une colonne possédant cet attribut, mais en général, ne peut pas mettre à jour les valeurs dans la colonne.<br /><br /> Lorsqu’une instruction insert est effectuée dans une colonne à incrémentation automatique, une valeur unique est insérée dans la colonne au moment de l’insertion. L’incrément n’est pas défini, mais il est spécifique à la source de données. Une application ne doit pas supposer qu’une colonne à incrémentation automatique démarre à n’importe quel point particulier ou d’une incrémentation par n’importe quelle valeur particulière.|  
|LOCAL_TYPE_NAME (ODBC 2.0)|13|Varchar|Version localisée du nom de type de données dépendant de la source de données. La valeur NULL est retournée si un nom localisé n'est pas pris en charge par la source de données. Ce nom est conçu pour l’affichage uniquement, par exemple, dans les boîtes de dialogue.|  
|MINIMUM_SCALE (ODBC 2.0)|14|Smallint|Échelle minimale du type de données sur la source de données. Si un type de données possède une échelle fixe, les colonnes MINIMUM_SCALE et MAXIMUM_SCALE contiennent toutes les deux cette valeur. Par exemple, une colonne SQL_TYPE_TIMESTAMP peut avoir une échelle fixe pour les fractions. La valeur NULL est retournée lorsque l'échelle n'est pas applicable. Pour plus d’informations, consultez [taille de colonne, des chiffres décimaux, transférer la longueur en octets et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe d : Types de données.|  
|MAXIMUM_SCALE (ODBC 2.0)|15|Smallint|L’échelle maximale du type de données sur la source de données. La valeur NULL est retournée lorsque l'échelle n'est pas applicable. Si l’échelle maximale n’est pas définie séparément dans la source de données, mais il est défini à la place pour être le même que la précision maximale, cette colonne contient la même valeur que la colonne COLUMN_SIZE. Pour plus d’informations, consultez [taille de colonne, des chiffres décimaux, transférer la longueur en octets et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe d : Types de données.|  
|SQL_DATA_TYPE (ODBC 3.0)|16|smallint non NULL|La valeur du type de données SQL telle qu’elle apparaît dans le champ SQL_DESC_TYPE du descripteur. Cette colonne est la même que la colonne DATA_TYPE, à l’exception des types de données date/heure et intervalle.<br /><br /> Pour les types de données date/heure et intervalle, le champ SQL_DATA_TYPE dans le jeu de résultats retournera SQL_INTERVAL ou SQL_DATETIME, et le champ SQL_DATETIME_SUB renverra le sous-code pour le type de données intervalle ou date/heure spécifique. (Consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|17|Smallint|Lorsque la valeur de SQL_DATA_TYPE est SQL_DATETIME ou SQL_INTERVAL, cette colonne contient le sous-code/intervalle datetime. Pour les types de données autres que datetime et interval, ce champ est NULL.<br /><br /> Pour les types de données intervalle ou date/heure, le champ SQL_DATA_TYPE dans le jeu de résultats retournera SQL_INTERVAL ou SQL_DATETIME, et le champ SQL_DATETIME_SUB renverra le sous-code pour le type de données intervalle ou date/heure spécifique. (Consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|NUM_PREC_RADIX (ODBC 3.0)|18|Entier|Si le type de données est un type numérique approximatif, cette colonne contient la valeur 2 pour indiquer que COLUMN_SIZE spécifie un nombre de bits. Pour les types numériques exacts, cette colonne contient la valeur 10 pour indiquer que COLUMN_SIZE spécifie un nombre de chiffres décimaux. Sinon, cette colonne est NULL.|  
|INTERVAL_PRECISION (ODBC 3.0)|19|Smallint|Si le type de données est un type de données d’intervalle, cette colonne contient la valeur de la précision de début d’intervalle. (Consultez [précision du Type de données de l’intervalle](../../../odbc/reference/appendixes/interval-data-type-precision.md) dans l’annexe d : Types de données.) Sinon, cette colonne est NULL.|  
  
 Informations sur les attributs peuvent appliquer aux types de données ou à des colonnes spécifiques dans un jeu de résultats. **SQLGetTypeInfo** retourne des informations sur les attributs associés aux types de données ; **SQLColAttribute** retourne des informations sur les attributs associés aux colonnes dans un jeu de résultats.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à une colonne dans un jeu de résultats|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Retour d’informations sur une colonne dans un jeu de résultats|[SQLColAttribute, fonction](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll, fonction](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|L’extraction d’une seule ligne ou un bloc de données dans une direction avant uniquement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Retour d’informations sur un pilote ou d’une source de données|[SQLGetInfo, fonction](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
