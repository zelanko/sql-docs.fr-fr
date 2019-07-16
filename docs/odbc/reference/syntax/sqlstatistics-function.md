---
title: SQLStatistics, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLStatistics
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLStatistics
helpviewer_keywords:
- SQLStatistics function [ODBC]
ms.assetid: 45210682-cfea-4e5d-9951-bcf1cbe10f41
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef0f25660a0faa0747752a8ca15c207c1e939669
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039551"
---
# <a name="sqlstatistics-function"></a>Fonction SQLStatistics
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLStatistics** récupère une liste des statistiques sur une seule table et les index associés à la table. Le pilote retourne les informations comme jeu de résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLStatistics(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CatalogName,  
     SQLSMALLINT     NameLength1,  
     SQLCHAR *       SchemaName,  
     SQLSMALLINT     NameLength2,  
     SQLCHAR *       TableName,  
     SQLSMALLINT     NameLength3,  
     SQLUSMALLINT    Unique,  
     SQLUSMALLINT    Reserved);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
 *CatalogName*  
 [Entrée] Nom du catalogue. Si un pilote prend en charge les catalogues pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, une chaîne vide (« ») indique les tables qui n’ont pas de catalogues. *CatalogName* ne peut pas contenir un modèle de recherche de chaîne.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *CatalogName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *CatalogName* est un argument ordinaire ; il est traité littéralement, et sa casse est significatif. Pour plus d’informations, consultez [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur en caractères de **CatalogName*.  
  
 *SchemaName*  
 [Entrée] Nom de schéma. Si un pilote prend en charge les schémas pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, une chaîne vide (« ») indique les tables qui n’ont pas de schémas. *SchemaName* ne peut pas contenir un modèle de recherche de chaîne.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *SchemaName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *SchemaName* est un argument ordinaire ; il est traité littéralement, et sa casse est significatif.  
  
 *NameLength2*  
 [Entrée] Longueur en caractères de **SchemaName*.  
  
 *TableName*  
 [Entrée] Nom de la table. Cet argument ne peut pas être un pointeur null. *SchemaName* ne peut pas contenir un modèle de recherche de chaîne.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *TableName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *TableName* est un argument ordinaire ; il est traité littéralement, et sa casse est significatif.  
  
 *NameLength3*  
 [Entrée] Longueur en caractères de **TableName*.  
  
 *Unique*  
 [Entrée] Type d’index : SQL_INDEX_UNIQUE ou SQL_INDEX_ALL.  
  
 *Reserved*  
 [Entrée] Indique l’importance des colonnes de cardinalité et des PAGES dans le jeu de résultats. Les options suivantes affectent le retour des cardinalité et des PAGES uniquement des colonnes ; informations d’index sont retournées même si la cardinalité et des PAGES ne sont pas retournés.  
  
 SQL_ENSURE demande que le pilote de manière inconditionnelle extraire des statistiques. (Les pilotes qui sont conformes uniquement à la norme Open Group et ne prennent pas en charge les extensions ODBC seront pas en mesure de prendre en charge SQL_ENSURE.)  
  
 SQL_QUICK demande que le pilote de récupérer la cardinalité et des PAGES uniquement si elles sont immédiatement disponibles à partir du serveur. Dans ce cas, le pilote ne s'assure pas que les valeurs sont actuelles. (Les applications qui sont écrits dans la norme Open Group toujours obtiennent SQL_QUICK comportement à partir d’ODBC *3.x*-pilotes conformes.)  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLStatistics** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLStatistics** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|24000|État de curseur non valide|Un curseur a été ouvert sur le *au paramètre StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avait été appelée. Cette erreur est retournée par le Gestionnaire de pilotes si **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_NO_DATA et est retourné par le pilote si **SQLFetch** ou **SQLFetchScroll** a retourné SQL_NO_DATA.<br /><br /> Un curseur a été ouvert sur le *au paramètre StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelée.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer de la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*, puis la fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY009|Utilisation non valide de pointeur null|Le *TableName* argument était un pointeur null.<br /><br /> L’attribut d’instruction SQL_ATTR_METADATA_ID a été défini avec SQL_TRUE, le *CatalogName* argument était un pointeur null et le SQL_CATALOG_NAME *InfoType* retourne les noms de catalogue est pris en charge.<br /><br /> (DM) l’attribut d’instruction SQL_ATTR_METADATA_ID a été défini avec SQL_TRUE et le *SchemaName* argument était un pointeur null.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLStatistics** fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur d’un des arguments de longueur de nom était inférieure à 0 mais pas égale à SQL_NTS.<br /><br /> La valeur d’un des arguments de longueur de nom a dépassé la valeur de longueur maximale pour le nom correspondant.|  
|HY100|Type d’option unique hors limites|(DM) non valide *Unique* valeur a été spécifiée.|  
|HY101|Type d’option de précision hors limite|(DM) non valide *réservé* valeur a été spécifiée.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|Un catalogue a été spécifié, et le pilote ou une source de données ne prend pas en charge les catalogues.<br /><br /> Un schéma a été spécifié, et le pilote ou une source de données ne prend pas en charge les schémas.<br /><br /> La combinaison des paramètres actuels des attributs d’instruction SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE n’était pas pris en charge par la pilote ou source de données.<br /><br /> L’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a été défini sur SQL_UB_VARIABLE, et l’attribut d’instruction SQL_ATTR_CURSOR_TYPE a été défini pour un type de curseur pour lequel le pilote ne prend pas en charge les signets.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant la source de données a retourné le jeu de résultat demandé. Le délai d’expiration est défini via **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLStatistics** retourne des informations sur une seule table comme un jeu de résultats standard, classé par NON_UNIQUE, TYPE, INDEX_QUALIFIER, INDEX_NAME et ORDINAL_POSITION. Le jeu de résultats combine les informations statistiques (dans les colonnes de cardinalité et des PAGES du jeu de résultats) pour la table avec des informations sur chaque index. Pour plus d’informations sur la façon dont ces informations peuvent être utilisées, consultez [utilise des données de catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Pour déterminer les longueurs réelles des colonnes TABLE_CAT, TABLE_SCHEM, TABLE_NAME et COLUMN_NAME, une application peut appeler **SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN, options et de SQL_MAX_COLUMN_NAME_LEN.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, consultez [fonctions de catalogue](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Les colonnes suivantes ont été renommées pour ODBC *3.x*. Les modifications de nom de colonne n’affectent pas la compatibilité descendante, car les applications lier par numéro de colonne.  
  
|Colonne de ODBC 2.0|ODBC *3.x* colonne|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|SEQ_IN_INDEX|ORDINAL_POSITION|  
|COLLATION|ASC_OR_DESC|  
  
 Le tableau suivant répertorie les colonnes du jeu de résultats. Les colonnes supplémentaires au-delà de la colonne 13 (FILTER_CONDITION) peuvent être définies par le pilote. Une application doit accéder à des colonnes spécifiques aux pilotes à rebours à partir de la fin de l’ensemble au lieu de spécifier une position ordinale explicite de résultats. Pour plus d’informations, consultez [les données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de la colonne|Numéro de colonne|Type de données|Commentaires|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Nom du catalogue de la table à laquelle l’index ou statistique s’applique ; NULL si non applicable à la source de données. Si un pilote prend en charge les catalogues pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, elle retourne une chaîne vide (" ») pour les tables qui n’ont pas de catalogues.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Nom du schéma de la table à laquelle l’index ou statistique s’applique ; NULL si non applicable à la source de données. Si un pilote prend en charge les schémas pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, elle retourne une chaîne vide (" ») pour les tables qui n’ont pas de schémas.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar non NULL|Nom de la table de la table à laquelle s’applique l’index ou statistique.|  
|NON_UNIQUE (ODBC 1.0)|4|Smallint|Indique si l’index n’autorise pas les valeurs en double :<br /><br /> SQL_TRUE si les valeurs d’index peuvent être non uniques.<br /><br /> SQL_FALSE si les valeurs d’index doivent être uniques.<br /><br /> La valeur NULL est retournée si le TYPE est SQL_TABLE_STAT.|  
|INDEX_QUALIFIER (ODBC 1.0)|5\.|Varchar|Nom de l’identificateur qui est utilisé pour qualifier l’index sous peine un **DROP INDEX**; La valeur NULL est retournée si un qualificateur de l’index n’est pas pris en charge par la source de données ou si le TYPE est SQL_TABLE_STAT. Si une valeur non null est retournée dans cet article, il doit être utilisé pour qualifier le nom d’index sur une **DROP INDEX** instruction ; sinon, le TABLE_SCHEM doit servir à qualifier le nom d’index.|  
|INDEX_NAME (ODBC 1.0)|6\.|Varchar|Nom de l’index ; La valeur NULL est retournée si le TYPE est SQL_TABLE_STAT.|  
|TYPE (ODBC 1.0)|7|Smallint non NULL|Type d’informations renvoyées :<br /><br /> SQL_TABLE_STAT indique une statistique pour la table (dans la colonne de cardinalité ou de PAGES).<br /><br /> SQL_INDEX_BTREE indique un index B-Tree.<br /><br /> SQL_INDEX_CLUSTERED indique un index cluster.<br /><br /> SQL_INDEX_CONTENT indique un index de contenu.<br /><br /> SQL_INDEX_HASHED indique un index haché.<br /><br /> SQL_INDEX_OTHER indique un autre type d’index.|  
|ORDINAL_POSITION (ODBC 1.0)|8|Smallint|Numéro de séquence de colonne dans l’index (à partir de 1) ; La valeur NULL est retournée si le TYPE est SQL_TABLE_STAT.|  
|COLUMN_NAME (ODBC 1.0)|9|Varchar|Nom de colonne. Si la colonne est basée sur une expression, telles que le salaire + avantages, l’expression est retournée ; Si l’expression ne peut pas être déterminée, une chaîne vide est retournée. La valeur NULL est retournée si le TYPE est SQL_TABLE_STAT.|  
|ASC_OR_DESC (ODBC 1.0)|10|Char (1)|Ordre de tri pour la colonne : « A » pour l’ordre croissant ; « D » pour l’ordre décroissant ; La valeur NULL est retournée si la séquence de tri de la colonne n’est pas pris en charge par la source de données ou si le TYPE est SQL_TABLE_STAT.|  
|CARDINALITÉ (ODBC 1.0)|11|Entier|Cardinalité de la table ou un index ; nombre de lignes dans la table si le TYPE est SQL_TABLE_STAT ; nombre de valeurs uniques dans l’index si TYPE n’est pas SQL_TABLE_STAT ; La valeur NULL est retournée si la valeur n’est pas disponible à partir de la source de données.|  
|PAGES (ODBC 1.0)|12|Entier|Nombre de pages utilisées pour stocker l’index ou la table ; nombre de pages pour la table si le TYPE est SQL_TABLE_STAT ; nombre de pages pour l’index si TYPE n’est pas SQL_TABLE_STAT ; La valeur NULL est retournée si la valeur n’est pas disponible à partir de la source de données ou si non applicable à la source de données.|  
|FILTER_CONDITION (ODBC 2.0)|13|Varchar|Si l’index est un index filtré, il s’agit de la condition de filtre, tels que les salaires > 30000 ; Si la condition de filtre ne peut pas être déterminée, il s’agit d’une chaîne vide.<br /><br /> NULL si l’index n’est pas un index filtré, il ne peut pas être déterminé si l’index est un index filtré ou le TYPE est SQL_TABLE_STAT.|  
  
 Si la ligne du jeu de résultats correspond à une table, le pilote définit TYPE à SQL_TABLE_STAT et NON_UNIQUE INDEX_QUALIFIER, INDEX_NAME, ORDINAL_POSITION, COLUMN_NAME et ASC_OR_DESC avec la valeur NULL. Si la cardinalité ou PAGES ne sont pas disponibles à partir de la source de données, le pilote les définit avec la valeur NULL.  
  
## <a name="code-example"></a>Exemple de code  
 Pour obtenir un exemple de code d’une fonction similaire, consultez [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à une colonne dans un jeu de résultats|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Extraction d’une seule ligne ou un bloc de données dans une direction avant uniquement.|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll, fonction](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Retourner les colonnes de clés étrangères|[SQLForeignKeys, fonction](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|Retourner les colonnes d’une clé primaire|[SQLPrimaryKeys, fonction](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
