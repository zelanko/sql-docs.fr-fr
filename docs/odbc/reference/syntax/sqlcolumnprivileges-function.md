---
title: SQLColumnPrivileges, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColumnPrivileges
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumnPrivileges
helpviewer_keywords:
- SQLColumnPrivileges function [ODBC]
ms.assetid: ef233d9a-6ed5-4986-9d42-5e0b1a79fb6e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83253faf14d1ccabaa39aabb52d7d1265e13e728
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53207688"
---
# <a name="sqlcolumnprivileges-function"></a>Fonction SQLColumnPrivileges
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ODBC  
  
 **Résumé**  
 **SQLColumnPrivileges** renvoie une liste de colonnes et les privilèges associés pour la table spécifiée. Le pilote retourne les informations comme jeu de résultats sur spécifié *au paramètre StatementHandle*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLColumnPrivileges(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>Arguments  
 *Au paramètre StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
 *Nom de catalogue*  
 [Entrée] Nom du catalogue. Si un pilote prend en charge les noms pour certains catalogues, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, une chaîne vide (« ») désigne ces catalogues qui n’ont pas de noms. *CatalogName* ne peut pas contenir un modèle de recherche de chaîne.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *CatalogName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *CatalogName* est un argument ordinaire ; il est traité littéralement, et sa casse est significatif. Pour plus d’informations, consultez [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur en caractères de **CatalogName*.  
  
 *SchemaName*  
 [Entrée] Nom de schéma. Si un pilote prend en charge les schémas pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, une chaîne vide (« ») indique les tables qui n’ont pas de schémas. *SchemaName* ne peut pas contenir un modèle de recherche de chaîne.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *SchemaName* est traité comme un identificateur. S’il s’agit de SQL_FALSE, *SchemaName* est un argument ordinaire ; il est traité littéralement, et sa casse est significatif.  
  
 *NameLength2*  
 [Entrée] Longueur en caractères de **SchemaName*.  
  
 *TableName*  
 [Entrée] Nom de la table. Cet argument ne peut pas être un pointeur null. *TableName* ne peut pas contenir un modèle de recherche de chaîne.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *TableName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *TableName* est un argument ordinaire ; il est traité littéralement, et sa casse est significatif.  
  
 *NameLength3*  
 [Entrée] Longueur en caractères de **TableName*.  
  
 *ColumnName*  
 [Entrée] Modèle de recherche de chaîne pour les noms de colonne.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, *ColumnName* est traité comme un identificateur et ses cas n’est pas significatif. S’il s’agit de SQL_FALSE, *ColumnName* est un argument de valeur de modèle ; il est traité littéralement, et sa casse est significatif.  
  
 *NameLength4*  
 [Entrée] Longueur en caractères de **ColumnName*.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLColumnPrivileges** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLColumnPrivileges** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le pilote Gestionnaire. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|24000|État de curseur non valide|Un curseur a été ouvert sur le *au paramètre StatementHandle,* et **SQLFetch** ou **SQLFetchScroll** avait été appelée. Cette erreur est retournée par le Gestionnaire de pilotes si **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_NO_DATA et est retourné par le pilote si **SQLFetch** ou **SQLFetchScroll** a retourné SQL_NO_DATA.<br /><br /> Un curseur a été ouvert sur le *au paramètre StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelée.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*. La fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY009|Utilisation non valide de pointeur null|Le *TableName* argument était un pointeur null.<br /><br /> L’attribut d’instruction SQL_ATTR_METADATA_ID a été défini avec SQL_TRUE, le *CatalogName* argument était un pointeur null et le SQL_CATALOG_NAME *InfoType* retourne les noms de catalogue est pris en charge.<br /><br /> (DM) l’attribut d’instruction SQL_ATTR_METADATA_ID a été défini avec SQL_TRUE et le *SchemaName* ou *ColumnName* argument était un pointeur null.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur d’un des arguments de longueur de nom était inférieure à 0 mais pas égale à SQL_NTS.|  
|||La valeur d’un des arguments de longueur de nom a dépassé la valeur de longueur maximale pour le nom correspondant. (Voir « Commentaires ».)|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|Un nom de catalogue a été spécifié, et le pilote ou une source de données ne prend pas en charge les catalogues.<br /><br /> Un nom de schéma a été spécifié, et le pilote ou une source de données ne prend pas en charge les schémas.<br /><br /> Un modèle de recherche de chaîne a été spécifié pour le nom de colonne, et la source de données ne prend pas en charge les modèles de recherche pour cet argument.<br /><br /> La combinaison des paramètres actuels des attributs d’instruction SQL_CONCURRENCY et SQL_CURSOR_TYPE n’était pas pris en charge par la pilote ou source de données.<br /><br /> L’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a été défini sur SQL_UB_VARIABLE, et l’attribut d’instruction SQL_ATTR_CURSOR_TYPE a été défini pour un type de curseur pour lequel le pilote ne prend pas en charge les signets.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant que la source de données a retourné le jeu de résultats. Le délai d’expiration est défini via **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLColumnPrivileges** retourne les résultats sous la forme d’un jeu de résultats standard, classé par TABLE_CAT, TABLE_SCHEM, TABLE_NAME, COLUMN_NAME et privilège.  
  
> [!NOTE]  
>  **SQLColumnPrivileges** peuvent ne pas retourner de privilèges pour toutes les colonnes. Par exemple, un pilote peut ne pas retourne des informations sur les privilèges pour pseudo colonnes, telles que Oracle ROWID. Les applications peuvent utiliser n’importe quelle colonne valide, indépendamment de si elle est retournée par **SQLColumnPrivileges**.  
  
 Les longueurs des colonnes VARCHAR ne figurent pas dans la table ; les longueurs réelles dépendent de la source de données. Pour déterminer les longueurs réelles des colonnes CATALOG_NAME, SCHEMA_NAME, TABLE_NAME et COLUMN_NAME, une application peut appeler **SQLGetInfo** avec la SQL_MAX_TABLE_NAME_ SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, LEN et les options de SQL_MAX_COLUMN_NAME_LEN.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, consultez [fonctions de catalogue](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Les colonnes suivantes ont été renommées pour ODBC 3. *x*. Les modifications de nom de colonne n’affectent pas la compatibilité descendante, car les applications lier par numéro de colonne.  
  
|Colonne de ODBC 2.0|ODBC 3. *x* colonne|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Le tableau suivant répertorie les colonnes du jeu de résultats. Les colonnes supplémentaires au-delà de la colonne 8 (IS_GRANTABLE) peuvent être définies par le pilote. Une application doit accéder à des colonnes spécifiques aux pilotes à rebours à partir de la fin du jeu de résultats au lieu d’en spécifiant une position ordinale explicite. Pour plus d’informations, consultez [les données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de colonne|Numéro de colonne|Type de données|Commentaires|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Identificateur du catalogue ; NULL si non applicable à la source de données. Si un pilote prend en charge les catalogues pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, elle retourne une chaîne vide (" ») pour les tables qui n’ont pas de catalogues.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Identificateur de schéma ; NULL si non applicable à la source de données. Si un pilote prend en charge les schémas pour certaines tables, mais pas pour d’autres, telles que lorsque le pilote récupère les données à partir de différents SGBD, elle retourne une chaîne vide (" ») pour les tables qui n’ont pas de schémas.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar non NULL|Identificateur de la table.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar non NULL|Nom de colonne. Le pilote retourne une chaîne vide pour une colonne qui n’a pas de nom.|  
|FOURNISSEUR D’AUTORISATIONS (ODBC 1.0)|5|Varchar|Nom de l’utilisateur qui dispose du privilège ; NULL si non applicable à la source de données.<br /><br /> Pour toutes les lignes dans lequel la valeur dans la colonne GRANTEE est le propriétaire de l’objet, la colonne GRANTOR sera « _système ».|  
|BÉNÉFICIAIRE (ODBC 1.0)|6|Varchar non NULL|Nom de l’utilisateur auquel l’autorisation a été accordée.|  
|PRIVILÈGE (ODBC 1.0)|7|Varchar non NULL|Identifie le privilège de la colonne. Peut être une des opérations suivantes (ou d’autres prises en charge par les données source défini par l’implémentation) :<br /><br /> SÉLECTIONNEZ : Le grantee est autorisé à récupérer des données pour la colonne.<br /><br /> INSERTION : Le grantee est autorisé à fournir des données pour la colonne dans les nouvelles lignes sont insérées dans la table associée.<br /><br /> MISE À JOUR : Le grantee est autorisé à mettre à jour des données dans la colonne.<br /><br /> RÉFÉRENCES : Le grantee est autorisé pour faire référence à la colonne dans une contrainte (par exemple, une valeur unique, référentielle, ou une contrainte de validation de table).|  
|IS_GRANTABLE (ODBC 1.0)|8|Varchar|Indique si le grantee est autorisé à accorder le privilège à d’autres utilisateurs ; « Oui », « Non » ou « NULL » si inconnu ou non applicable à la source de données.<br /><br /> Un privilège est possible d’accorder ou non transférables, mais pas les deux. Le jeu de résultats retourné par **SQLColumnPrivileges** ne contient jamais les deux lignes pour lequel toutes les colonnes à l’exception de la colonne IS_GRANTABLE contiennent la même valeur.|  
  
## <a name="code-example"></a>Exemple de code  
 Pour obtenir un exemple de code d’une fonction similaire, consultez [fonction SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à une colonne dans un jeu de résultats|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Retourner les colonnes dans une table ou des tables|[SQLColumns, fonction](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll, fonction](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Extraction de plusieurs lignes de données|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Retour de privilèges pour une table ou de tables|[SQLTablePrivileges, fonction](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
|Retour d’une liste de tables dans une source de données|[SQLTables, fonction](../../../odbc/reference/syntax/sqltables-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
