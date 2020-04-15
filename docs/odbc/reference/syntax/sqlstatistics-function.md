---
title: Fonction SQLStatistics (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c2a5ef0b0e54e17a2dc091a98efc972fa608ef15
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302943"
---
# <a name="sqlstatistics-function"></a>Fonction SQLStatistics
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLStatistics** récupère une liste de statistiques sur un tableau unique et les index associés au tableau. Le conducteur renvoie l’information à la suite de l’ensemble.  
  
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
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Nom du catalogue*  
 [Entrée] Nom du catalogue. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, une chaîne vide ("") indique les tables qui n’ont pas de catalogues. *CatalogName* ne peut pas contenir un modèle de recherche de chaînes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID est configuré pour SQL_TRUE, *CatalogName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *CatalogName* est un argument ordinaire; il est traité littéralement, et son cas est significatif. Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur dans les caractères de*CatalogName*.  
  
 *SchemaName (SchemaName)*  
 [Entrée] Nom de Schema. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, une chaîne vide («)) indique les tables qui n’ont pas de schémas. *SchemaName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *SchemaName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *SchemaName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength2*  
 [Entrée] Longueur dans les personnages de*SchemaName*.  
  
 *TableName*  
 [Entrée] Nom de table. Cet argument ne peut pas être un pointeur nul. *SchemaName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *TableName* est traité comme un identifiant et son cas n’est pas significatif. S’il s’agit d’SQL_FALSE, *TableName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength3*  
 [Entrée] Longueur dans les caractères de*TableName*.  
  
 *Unique*  
 [Entrée] Type d’indice : SQL_INDEX_UNIQUE ou SQL_INDEX_ALL.  
  
 *Réservé*  
 [Entrée] Indique l’importance des colonnes CARDINALITY et PAGES dans l’ensemble de résultats. Les options suivantes n’affectent que le retour des colonnes CARDINALITY et PAGES; l’information index est retournée même si CARDINALITY et PAGES ne sont pas retournées.  
  
 SQL_ENSURE demande au conducteur de récupérer sans condition les statistiques. (Les conducteurs qui se conforment uniquement à la norme Open Group et ne prennent pas en charge les extensions ODBC ne seront pas en mesure de prendre en charge SQL_ENSURE.)  
  
 SQL_QUICK demande que le pilote ne récupère le CARDINALITY et les PAGES que s’ils sont facilement disponibles sur le serveur. Dans ce cas, le pilote ne s'assure pas que les valeurs sont actuelles. (Les applications qui sont écrites à la norme Open Group obtiendront toujours SQL_QUICK comportement des pilotes ODBC *3.x-conformes.)*  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLStatistics** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLStatistics** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|24 000|État de curseur non valide|Un curseur était ouvert sur le *StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avaient été appelés. Cette erreur est retournée par le gestionnaire du conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.<br /><br /> Un curseur était ouvert sur le *StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelé.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*, puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|*L’argument de TableName* était un pointeur nul.<br /><br /> L’attribut de déclaration SQL_ATTR_METADATA_ID a été réglé pour SQL_TRUE, l’argument *CatalogName* était un pointeur nul, et le SQL_CATALOG_NAME *InfoType* retourne que les noms de catalogue sont pris en charge.<br /><br /> (DM) L’attribut de déclaration SQL_ATTR_METADATA_ID a été fixé à SQL_TRUE, et l’argument *de SchemaName* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLStatistics** a été appelé.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur de l’un des arguments de longueur de nom était inférieure à 0, mais pas égale à SQL_NTS.<br /><br /> La valeur de l’un des arguments de longueur du nom a dépassé la valeur maximale de longueur pour le nom correspondant.|  
|Hy100|Type d’option d’unicité hors de portée|(DM) Une valeur *unique* non valide a été spécifiée.|  
|Hy101|Type d’option de précision hors de portée|(DM) Une valeur *réservée* non valide a été spécifiée.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Un catalogue a été spécifié, et le pilote ou la source de données ne prend pas en charge les catalogues.<br /><br /> Un schéma a été spécifié, et le conducteur ou la source de données ne prend pas en charge les schémas.<br /><br /> La combinaison des paramètres actuels des attributs SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE de l’énoncé n’a pas été prise en charge par le conducteur ou la source de données.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats demandé. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLStatistics** renvoie des informations sur une seule table à titre de résultat standard, commandée par NON_UNIQUE, TYPE, INDEX_QUALIFIER, INDEX_NAME et ORDINAL_POSITION. L’ensemble de résultats combine des informations statistiques (dans les colonnes CARDINALITY et PAGES de l’ensemble de résultats) pour le tableau avec des informations sur chaque index. Pour plus d’informations sur la façon dont ces informations pourraient être utilisées, voir [Uses of Catalog Data](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Pour déterminer la longueur réelle des colonnes TABLE_CAT, TABLE_SCHEM, TABLE_NAME et COLUMN_NAME, une application peut appeler **SQLGetInfo** avec les options de SQL_MAX_CATALOG_NAME_LEN, de SQL_MAX_SCHEMA_NAME_LEN, de SQL_MAX_TABLE_NAME_LEN et de SQL_MAX_COLUMN_NAME_LEN.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, voir [Catalog Functions](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Les colonnes suivantes ont été rebaptisées pour ODBC *3.x*. Les modifications du nom de colonne n’affectent pas la compatibilité vers l’arrière parce que les applications se lient par numéro de colonne.  
  
|Colonne ODBC 2.0|Colonne *ODBC 3.x*|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|SEQ_IN_INDEX|ORDINAL_POSITION|  
|COLLATION|ASC_OR_DESC|  
  
 Le tableau suivant répertorie les colonnes dans l’ensemble de résultats. Des colonnes supplémentaires au-delà de la colonne 13 (FILTER_CONDITION) peuvent être définies par le conducteur. Une application doit avoir accès à des colonnes spécifiques au conducteur en comptant à partir de la fin de l’ensemble de résultat au lieu de spécifier une position ordinaire explicite. Pour plus d’informations, voir [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de la colonne|Numéro de colonne|Type de données|Commentaires|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Nom catalogue du tableau auquel la statistique ou l’indice s’applique; NULL s’il n’est pas applicable à la source de données. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de catalogues.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Nom schématique du tableau auquel la statistique ou l’indice s’applique; NULL s’il n’est pas applicable à la source de données. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de schémas.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar pas NULL|Nom de table du tableau auquel la statistique ou l’indice s’applique.|  
|NON_UNIQUE (ODBC 1.0)|4|Smallint|Indique si l’indice n’autorise pas les valeurs en double :<br /><br /> SQL_TRUE si les valeurs de l’indice peuvent être non uniques.<br /><br /> SQL_FALSE si les valeurs indiciels doivent être uniques.<br /><br /> NULL est retourné si TYPE est SQL_TABLE_STAT.|  
|INDEX_QUALIFIER (ODBC 1.0)|5|Varchar|L’identifiant qui est utilisé pour qualifier le nom de l’index faisant un **INDEX DROP**; NULL est retourné si un qualificatif d’index n’est pas pris en charge par la source de données ou si TYPE est SQL_TABLE_STAT. Si une valeur non nulle est retournée dans cette colonne, elle doit être utilisée pour qualifier le nom de l’index d’une déclaration **DROP INDEX;** autrement, le TABLE_SCHEM devrait être utilisé pour qualifier le nom de l’index.|  
|INDEX_NAME (ODBC 1.0)|6|Varchar|Nom de l’index; NULL est retourné si TYPE est SQL_TABLE_STAT.|  
|TYPE (ODBC 1.0)|7|Smallint non NULL|Type d’information retournée :<br /><br /> SQL_TABLE_STAT indique une statistique pour le tableau (dans la colonne CARDINALITY ou PAGES).<br /><br /> SQL_INDEX_BTREE indique un indice B-Tree.<br /><br /> SQL_INDEX_CLUSTERED indique un indice groupé.<br /><br /> SQL_INDEX_CONTENT indique un index de contenu.<br /><br /> SQL_INDEX_HASHED indique un indice de hachage.<br /><br /> SQL_INDEX_OTHER indique un autre type d’indice.|  
|ORDINAL_POSITION (ODBC 1.0)|8|Smallint|Numéro de séquence de colonne dans l’index (à partir de 1); NULL est retourné si TYPE est SQL_TABLE_STAT.|  
|COLUMN_NAME (ODBC 1.0)|9|Varchar|Nom de la colonne. Si la colonne est basée sur une expression, telle que SALARY - BENEFITS, l’expression est retournée; si l’expression ne peut pas être déterminée, une corde vide est retournée. NULL est retourné si TYPE est SQL_TABLE_STAT.|  
|ASC_OR_DESC (ODBC 1.0)|10|Char (1)|Séquence de tri pour la colonne : « A » pour l’ascension ; "D" pour descendre; NULL est retourné si la séquence de tri de colonne n’est pas prise en charge par la source de données ou si TYPE est SQL_TABLE_STAT.|  
|CARDINALITÉ (ODBC 1.0)|11|Integer|Cardinalité de tableau ou d’index; nombre de rangées dans le tableau si le TYPE est SQL_TABLE_STAT; nombre de valeurs uniques dans l’indice si LE TYPE n’est pas SQL_TABLE_STAT; NULL est retourné si la valeur n’est pas disponible à partir de la source de données.|  
|PAGES (ODBC 1.0)|12|Integer|Nombre de pages utilisées pour stocker l’index ou le tableau; nombre de pages pour la table si LE TYPE est SQL_TABLE_STAT; nombre de pages pour l’index si LE TYPE n’est pas SQL_TABLE_STAT; NULL est retourné si la valeur n’est pas disponible à partir de la source de données ou si elle n’est pas applicable à la source de données.|  
|FILTER_CONDITION (ODBC 2.0)|13|Varchar|Si l’indice est un indice filtré, c’est l’état du filtre, tel que SALARY > 30000; si l’état du filtre ne peut pas être déterminé, il s’agit d’une chaîne vide.<br /><br /> NULL si l’indice n’est pas un indice filtré, il ne peut pas être déterminé si l’indice est un indice filtré, ou TYPE est SQL_TABLE_STAT.|  
  
 Si la ligne dans l’ensemble de résultat correspond à une table, le conducteur définit TYPE pour SQL_TABLE_STAT et définit NON_UNIQUE, INDEX_QUALIFIER, INDEX_NAME, ORDINAL_POSITION, COLUMN_NAME et ASC_OR_DESC à NULL. Si CARDINALITY ou PAGES ne sont pas disponibles à partir de la source de données, le pilote les fixe à NULL.  
  
## <a name="code-example"></a>Exemple de code  
 Pour un exemple de code d’une fonction similaire, voir [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Aller chercher une seule rangée ou un bloc de données dans une direction avant-seulement.|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Retour des colonnes de clés étrangères|[Fonction SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|Retour des colonnes d’une clé primaire|[Fonction SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
