---
title: Fonction SQLPrimaryKeys (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPrimaryKeys
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPrimaryKeys
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC]
ms.assetid: 3f809b09-3c1b-415e-80c5-a603e8e25d5b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 24407670ab9f1489a14bec19d910060b49d4bda0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306864"
---
# <a name="sqlprimarykeys-function"></a>Fonction SQLPrimaryKeys
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLPrimaryKeys** renvoie les noms de colonnes qui constituent la clé principale d’une table. Le conducteur renvoie l’information à la suite de l’ensemble. Cette fonction ne prend pas en charge le retour des touches primaires de plusieurs tables en un seul appel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLPrimaryKeys(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Nom du catalogue*  
 [Entrée] Nom du catalogue. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, une chaîne vide ("") dénote les tables qui n’ont pas de catalogues. *CatalogName* ne peut pas contenir un modèle de recherche de chaînes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID est configuré pour SQL_TRUE, *CatalogName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *CatalogName* est un argument ordinaire; il est traité littéralement, et son cas est significatif. Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur dans les caractères de*CatalogName*.  
  
 *SchemaName (SchemaName)*  
 [Entrée] Nom de Schema. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, une chaîne vide («)) dénote les tables qui n’ont pas de schémas. *SchemaName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *SchemaName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *SchemaName* est un argument ordinaire; il est traité littéralement, et son cas n’est pas significatif.  
  
 *NomLength2*  
 [Entrée] Longueur dans les personnages de*SchemaName*.  
  
 *TableName*  
 [Entrée] Nom de table. Cet argument ne peut pas être un pointeur nul. *TableName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *TableName* est traité comme un identifiant et son cas n’est pas significatif. S’il s’agit d’SQL_FALSE, *TableName* est un argument ordinaire; il est traité littéralement, et son cas n’est pas significatif.  
  
 *NomLength3*  
 [Entrée] Longueur dans les caractères de*TableName*.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLPrimaryKeys** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLPrimaryKeys** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|24 000|État de curseur non valide|(DM) Un curseur était ouvert sur le *StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avaient été appelés.<br /><br /> Un curseur était ouvert sur le *StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelé.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|(DM) *L’argument de TableName* était un pointeur nul.<br /><br /> L’attribut de déclaration SQL_ATTR_METADATA_ID a été réglé pour SQL_TRUE, l’argument *CatalogName* était un pointeur nul, et **SQLGetInfo** avec les retours de type SQL_CATALOG_NAME d’information que les noms de catalogue sont pris en charge.<br /><br /> (DM) L’attribut de déclaration SQL_ATTR_METADATA_ID a été fixé à SQL_TRUE, et l’argument *de SchemaName* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLPrimaryKeys** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur de l’un des arguments de longueur de nom était inférieure à 0, mais pas égale à SQL_NTS, et l’argument du nom associé n’est pas un pointeur nul.<br /><br /> La valeur de l’un des arguments de longueur du nom a dépassé la valeur maximale de longueur pour le nom correspondant.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Un catalogue a été spécifié, et le pilote ou la source de données ne prend pas en charge les catalogues.<br /><br /> Un schéma a été spécifié et le conducteur ou la source de données ne prend pas en charge les schémas.<br /><br /> La combinaison des paramètres actuels des attributs SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE de l’énoncé n’a pas été prise en charge par le conducteur ou la source de données.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai a expiré avant que la source de données ne rende l’ensemble de résultats demandé. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLPrimaryKeys** retourne les résultats comme un résultat standard établi, commandé par TABLE_CAT, TABLE_SCHEM, TABLE_NAME et KEY_SEQ. Pour plus d’informations sur la façon dont ces informations pourraient être utilisées, voir [Uses of Catalog Data](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Les colonnes suivantes ont été rebaptisées pour ODBC 3. *x*. Les modifications du nom de colonne n’affectent pas la compatibilité vers l’arrière parce que les applications se lient par numéro de colonne.  
  
|Colonne ODBC 2.0|ODBC 3. *colonne x*|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Pour déterminer la longueur réelle des colonnes TABLE_CAT, TABLE_SCHEM, TABLE_NAME et COLUMN_NAME, appelez **SQLGetInfo** avec les options SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN et SQL_MAX_COLUMN_NAME_LEN.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, voir [Catalog Functions](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Le tableau suivant répertorie les colonnes dans l’ensemble de résultats. Des colonnes supplémentaires au-delà de la colonne 6 (PK_NAME) peuvent être définies par le conducteur. Une application doit avoir accès à des colonnes spécifiques au conducteur en comptant à partir de la fin de l’ensemble de résultats plutôt que de spécifier une position ordinaire explicite. Pour plus d’informations, voir [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de la colonne|Numéro de colonne|Type de données|Commentaires|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Nom principal du catalogue de table clé; NULL s’il n’est pas applicable à la source de données. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de catalogues.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Nom principal de schéma de table clé ; NULL s’il n’est pas applicable à la source de données. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de schémas.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar pas NULL|Nom de table principal.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar pas NULL|Nom de colonne principale. Le conducteur retourne une chaîne vide pour une colonne qui n’a pas de nom.|  
|KEY_SEQ (ODBC 1.0)|5|Smallint non NULL|Numéro de séquence de colonne dans la clé (à partir de 1).|  
|PK_NAME (ODBC 2.0)|6|Varchar|Nom clé principal. NULL s’il n’est pas applicable à la source de données.|  
  
## <a name="code-example"></a>Exemple de code  
 Voir [SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Aller chercher une seule rangée ou un bloc de données dans une direction avant-seulement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Retour des colonnes de clés étrangères|[Fonction SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|Retour des statistiques et des indices de table|[Fonction SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
