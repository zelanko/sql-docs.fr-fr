---
title: Fonction SQLForeignKeys (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLForeignKeys
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLForeignKeys
helpviewer_keywords:
- SQLForeignKeys function [ODBC]
ms.assetid: 07f3f645-f643-4d39-9a10-70a72f24e608
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5f2769fb378a5ee989fb6a0351537edb3de03469
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285859"
---
# <a name="sqlforeignkeys-function"></a>Fonction SQLForeignKeys
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLForeignKeys** peut revenir:  
  
-   Une liste de clés étrangères dans le tableau spécifié (colonnes dans le tableau spécifié qui se réfèrent aux touches primaires dans d’autres tables).  
  
-   Une liste de clés étrangères dans d’autres tableaux qui se réfèrent à la clé principale dans le tableau spécifié.  
  
 Le conducteur renvoie chaque liste à la suite définie sur l’instruction spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLForeignKeys(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      PKCatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      PKSchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      PKTableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      FKCatalogName,  
     SQLSMALLINT    NameLength4,  
     SQLCHAR *      FKSchemaName,  
     SQLSMALLINT    NameLength5,  
     SQLCHAR *      FKTableName,  
     SQLSMALLINT    NameLength6);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *PKCatalogName*  
 [Entrée] Nom principal du catalogue de table. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, une chaîne vide ("") dénote les tables qui n’ont pas de catalogues. *PKCatalogName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *PKCatalogName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *PKCatalogName* est un argument ordinaire; il est traité littéralement, et son cas est significatif. Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur de*PKCatalogName*, en caractères.  
  
 *PKSchemaName*  
 [Entrée] Nom principal de schéma de table de clef. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, une chaîne vide («)) dénote les tables qui n’ont pas de schémas. *PKSchemaName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *PKSchemaName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *PKSchemaName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength2*  
 [Entrée] Longueur de*PKSchemaName*, en caractères.  
  
 *PKTableName (en)*  
 [Entrée] Nom de table principal. *PKTableName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID est réglé pour SQL_TRUE, *PKTableName* est traité comme un identifiant et son cas n’est pas significatif. S’il s’agit d’SQL_FALSE, *PKTableName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength3*  
 [Entrée] Longueur de*PKTableName*, en caractères.  
  
 *FKCatalogName*  
 [Entrée] Nom étranger du catalogue de table clé. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, une chaîne vide ("") dénote les tables qui n’ont pas de catalogues. *FKCatalogName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *FKCatalogName* est traité comme un identifiant et son cas n’est pas significatif. Si c’est SQL_FALSE, *FKCatalogName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength4*  
 [Entrée] Longueur de*FKCatalogName*, en caractères.  
  
 *FKSchemaName*  
 [Entrée] Nom de schéma de table clé étranger. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, une chaîne vide («)) dénote les tables qui n’ont pas de schémas. *FKSchemaName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *FKSchemaName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *FKSchemaName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength5*  
 [Entrée] Longueur de*FKSchemaName*, en caractères.  
  
 *FKTableName (en)*  
 [Entrée] Nom de table clé étranger. *FKTableName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *FKTableName* est traité comme un identifiant et son cas n’est pas significatif. S’il s’agit d’SQL_FALSE, *FKTableName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength6*  
 [Entrée] Longueur de*FKTableName*, en caractères.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLForeignKeys** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLForeignKeys** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|24 000|État de curseur non valide|Un curseur était ouvert sur le *StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avaient été appelés. Cette erreur est retournée par le gestionnaire du conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA, et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.<br /><br /> Un curseur était ouvert sur le *StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelé.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*, puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|(DM) Les arguments *PKTableName* et *FKTableName* étaient tous deux des pointeurs nuls.<br /><br /> L’attribut de déclaration SQL_ATTR_METADATA_ID a été réglé pour SQL_TRUE, l’argument *FKCatalogName* ou *PKCatalogName* était un pointeur nul, et le SQL_CATALOG_NAME *InfoType* retourne que les noms de catalogue sont pris en charge.<br /><br /> (DM) L’attribut de déclaration SQL_ATTR_METADATA_ID a été fixé à SQL_TRUE, et le *FKSchemaName*, *PKSchemaName*, *FKTableName*, ou *PKTableName* argument était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction SQLForeignKeys a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur de l’un des arguments de longueur de nom était inférieure à 0, mais pas égale à SQL_NTS.|  
|||La valeur de l’un des arguments de longueur du nom a dépassé la valeur maximale de longueur pour le nom correspondant. (Voir "Commentaires.")|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Un nom de catalogue a été spécifié, et le pilote ou la source de données ne prend pas en charge les catalogues.<br /><br /> Un nom de schéma a été spécifié, et le conducteur ou la source de données ne prend pas en charge les schémas.|  
|||La combinaison des paramètres actuels des attributs SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE de l’énoncé n’a pas été prise en charge par le conducteur ou la source de données.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Pour plus d’informations sur la façon dont les informations retournées par cette fonction peuvent être utilisées, voir [Uses of Catalog Data](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Si \* *PKTableName* contient un nom de table, **SQLForeignKeys** retourne un ensemble de résultats qui contient la clé principale de la table spécifiée et toutes les clés étrangères qui s’y réfèrent. La liste des clés étrangères dans d’autres tableaux n’inclut pas les clés étrangères qui indiquent des contraintes uniques dans le tableau spécifié.  
  
 Si \* *FKTableName* contient un nom de table, **SQLForeignKeys** retourne un ensemble de résultats qui contient toutes les clés étrangères dans le tableau spécifié qui pointent vers les touches primaires dans d’autres tables, et les clés principales dans les autres tables auxquelles ils se réfèrent. La liste des clés étrangères dans le tableau spécifié ne contient pas de clés étrangères qui se réfèrent à des contraintes uniques dans d’autres tableaux.  
  
 \*Si *PKTableName* \*et *FKTableName* contiennent des noms de table, **SQLForeignKeys** retourne les clés étrangères dans le tableau spécifiées dans \* *FKTableName* qui se réfèrent à la clé principale du tableau spécifié dans*PKTableName*. Cela devrait être une clé tout au plus.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, voir [Catalog Functions](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLForeignKeys** retourne les résultats comme un résultat standard. Si les clés étrangères associées à une clé principale sont demandées, l’ensemble de résultats est commandé par FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME et KEY_SEQ. Si les clés principales associées à une clé étrangère sont demandées, l’ensemble de résultat est commandé par PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME et KEY_SEQ. Le tableau suivant répertorie les colonnes dans l’ensemble de résultats.  
  
 Les longueurs des colonnes VARCHAR ne sont pas indiquées dans le tableau; les longueurs réelles dépendent de la source de données. Pour déterminer la longueur réelle des colonnes PKTABLE_CAT ou FKTABLE_CAT, PKTABLE_SCHEM ou FKTABLE_SCHEM, PKTABLE_NAME ou FKTABLE_NAME, et PKCOLUMN_NAME ou FKCOLUMN_NAME colonnes, une application peut appeler **SQLGetInfo** avec les options de SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN et SQL_MAX_COLUMN_NAME_LEN.  
  
 Les colonnes suivantes ont été rebaptisées pour ODBC 3 *.x.* Les modifications du nom de colonne n’affectent pas la compatibilité vers l’arrière parce que les applications se lient par numéro de colonne.  
  
|Colonne ODBC 2.0|Colonne ODBC 3 *.x*|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 Le tableau suivant répertorie les colonnes dans l’ensemble de résultats. Des colonnes supplémentaires au-delà de la colonne 14 (REMARQUE) peuvent être définies par le conducteur. Une application doit avoir accès à des colonnes spécifiques au conducteur en comptant à partir de la fin de l’ensemble de résultat au lieu de spécifier une position ordinaire explicite. Pour plus d’informations, voir [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de la colonne|Numéro de colonne|Type de données|Commentaires|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1.0)|1|Varchar|Nom principal du catalogue de table clé; NULL s’il n’est pas applicable à la source de données. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de catalogues.|  
|PKTABLE_SCHEM (ODBC 1.0)|2|Varchar|Nom principal de schéma de table clé ; NULL s’il n’est pas applicable à la source de données. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de schémas.|  
|PKTABLE_NAME (ODBC 1.0)|3|Varchar pas NULL|Nom de table principal.|  
|PKCOLUMN_NAME (ODBC 1.0)|4|Varchar pas NULL|Nom de colonne principale. Le conducteur retourne une chaîne vide pour une colonne qui n’a pas de nom.|  
|FKTABLE_CAT (ODBC 1.0)|5|Varchar|Nom étranger du catalogue de table clé; NULL s’il n’est pas applicable à la source de données. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de catalogues.|  
|FKTABLE_SCHEM (ODBC 1.0)|6|Varchar|Nom étranger de schéma de table clé ; NULL s’il n’est pas applicable à la source de données. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, il retourne une chaîne vide ("") pour les tables qui n’ont pas de schémas.|  
|FKTABLE_NAME (ODBC 1.0)|7|Varchar pas NULL|Nom de table clé étranger.|  
|FKCOLUMN_NAME (ODBC 1.0)|8|Varchar pas NULL|Nom de colonne de clé étranger. Le conducteur retourne une chaîne vide pour une colonne qui n’a pas de nom.|  
|KEY_SEQ (ODBC 1.0)|9|Smallint non NULL|Numéro de séquence de colonne dans la clé (à partir de 1).|  
|UPDATE_RULE (ODBC 1.0)|10|Smallint|Action à appliquer à la clé étrangère lorsque l’opération SQL est **UPDATE**. Peut avoir l’une des valeurs suivantes. (Le tableau référencé est le tableau qui a la clé principale; la table de référencement est la table qui a la clé étrangère.)<br /><br /> SQL_CASCADE : Lorsque la clé principale du tableau référencé est mise à jour, la clé étrangère du tableau de référencement est également mise à jour.<br /><br /> SQL_NO_ACTION : Si une mise à jour de la clé principale du tableau référencé provoquerait une « référence » dans le tableau de référencement (c’est-à-dire que les lignes dans le tableau de référence n’auraient pas de contreparties dans le tableau référencé), la mise à jour est rejetée. Si une mise à jour de la clé étrangère du tableau de référence introduit une valeur qui n’existe pas comme valeur de la clé principale du tableau référencé, la mise à jour est rejetée. (Cette action est la même que l’action SQL_RESTRICT dans ODBC 2 *.x*.)<br /><br /> SQL_SET_NULL : Lorsqu’une ou plusieurs lignes du tableau référencé sont mises à jour de manière à ce qu’un ou plusieurs composants de la clé principale soient modifiés, les composants de la clé étrangère dans le tableau de référencement qui correspondent aux composants modifiés de la clé principale sont réglés à NULL dans toutes les rangées correspondantes de la table de référencement.<br /><br /> SQL_SET_DEFAULT : Lorsqu’une ou plusieurs lignes du tableau référencé sont mises à jour de manière à ce qu’un ou plusieurs composants de la clé principale soient modifiés, les composants de la clé étrangère dans le tableau de référencement qui correspondent aux composants modifiés de la clé principale sont réglés aux valeurs par défaut applicables dans toutes les lignes correspondantes de la table de référencement.<br /><br /> NULL s’il n’est pas applicable à la source de données.|  
|DELETE_RULE (ODBC 1.0)|11|Smallint|Action à appliquer à la clé étrangère lorsque l’opération SQL est **DELETE**. Peut avoir l’une des valeurs suivantes. (Le tableau référencé est le tableau qui a la clé principale; la table de référencement est la table qui a la clé étrangère.)<br /><br /> SQL_CASCADE : Lorsqu’une rangée dans le tableau référencé est supprimée, toutes les lignes correspondantes dans les tableaux de référencement sont également supprimées.<br /><br /> SQL_NO_ACTION : Si une suppression d’une ligne dans le tableau référencé provoquerait une « référence » dans le tableau de référencement (c’est-à-dire que les lignes dans le tableau de référence n’auraient pas de contreparties dans le tableau référencé), la mise à jour est rejetée. (Cette action est la même que l’action SQL_RESTRICT dans ODBC 2 *.x*.)<br /><br /> SQL_SET_NULL : Lorsqu’une ou plusieurs lignes dans le tableau référencé sont supprimées, chaque composant de la clé étrangère de la table de référencement est réglé à NULL dans toutes les rangées correspondantes de la table de référencement.<br /><br /> SQL_SET_DEFAULT : Lorsqu’une ou plusieurs lignes dans le tableau référencé sont supprimées, chaque composant de la clé étrangère de la table de référencement est réglé à la valeur par défaut applicable dans toutes les lignes correspondantes de la table de référencement.<br /><br /> NULL s’il n’est pas applicable à la source de données.|  
|FK_NAME (ODBC 2.0)|12|Varchar|Nom clé étranger. NULL s’il n’est pas applicable à la source de données.|  
|PK_NAME (ODBC 2.0)|13|Varchar|Nom clé principal. NULL s’il n’est pas applicable à la source de données.|  
|REPORTRABILITÉ (ODBC 3.0)|14|Smallint|SQL_INITIALLY_DEFERRED, SQL_INITIALLY_IMMEDIATE, SQL_NOT_DEFERRABLE.|  
  
## <a name="code-example"></a>Exemple de code  
 Comme illustré dans le tableau suivant, cet exemple utilise trois tableaux, nommés ORDERS, LINES et CUSTOMERS.  
  
|ORDERS|Lignes|Clients|  
|------------|-----------|---------------|  
|ORDRE|ORDRE|CUSTID|  
|CUSTID|Lignes|NAME|  
|OPENDATE (EN)|PartiD (PARTID)|Adresse|  
|Vendeur|Quantité|TÉLÉPHONE|  
|STATUT|||  
  
 Dans le tableau ORDERS, CUSTID identifie le client à qui la vente a été faite. Il s’agit d’une clé étrangère qui se réfère à CUSTID dans le tableau customers.  
  
 Dans le tableau LINES, ORDERID identifie l’ordre de vente auquel l’élément de ligne est associé. Il s’agit d’une clé étrangère qui se réfère à ORDERID dans le tableau ORDERS.  
  
 Cet exemple appelle **SQLPrimaryKeys** pour obtenir la clé principale de la table ORDERS. L’ensemble de résultats aura une rangée; les colonnes significatives sont indiquées dans le tableau suivant.  
  
|TABLE_NAME|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ORDERS|ORDRE|1|  
  
 Ensuite, l’exemple appelle **SQLForeignKeys** pour obtenir les clés étrangères dans d’autres tables qui font référence à la clé principale de la table ORDERS. L’ensemble de résultats aura une rangée; les colonnes significatives sont indiquées dans le tableau suivant.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ORDERS|CUSTID|Lignes|CUSTID|1|  
  
 Enfin, l’exemple appelle **SQLForeignKeys** pour obtenir les clés étrangères dans le tableau ORDERS qui se réfèrent aux clés principales d’autres tables. L’ensemble de résultats aura une rangée; les colonnes significatives sont indiquées dans le tableau suivant.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|Clients|CUSTID|ORDERS|CUSTID|1|  
  
```cpp  
#define TAB_LEN SQL_MAX_TABLE_NAME_LEN + 1  
#define COL_LEN SQL_MAX_COLUMN_NAME_LEN + 1  
  
LPSTR   szTable;              /* Table to display */  
  
UCHAR szPkTable[TAB_LEN];   /* Primary key table name */  
UCHAR szFkTable[TAB_LEN];   /* Foreign key table name */  
UCHAR szPkCol[COL_LEN];     /* Primary key column */  
UCHAR szFkCol[COL_LEN];     /* Foreign key column */  
  
SQLHSTMT      hstmt;  
SQLINTEGER    cbPkTable, cbPkCol, cbFkTable, cbFkCol, cbKeySeq;  
SQLSMALLINT   iKeySeq;  
SQLRETURN     retcode;  
  
// Bind the columns that describe the primary and foreign keys.  
// Ignore the table schema, name, and catalog for this example.  
  
SQLBindCol(hstmt, 3, SQL_C_CHAR, szPkTable, TAB_LEN, &cbPkTable);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, szPkCol, COL_LEN, &cbPkCol);  
SQLBindCol(hstmt, 5, SQL_C_SSHORT, &iKeySeq, TAB_LEN, &cbKeySeq);  
SQLBindCol(hstmt, 7, SQL_C_CHAR, szFkTable, TAB_LEN, &cbFkTable);  
SQLBindCol(hstmt, 8, SQL_C_CHAR, szFkCol, COL_LEN, &cbFkCol);  
  
strcpy_s(szTable, sizeof(szTable), "ORDERS");  
  
/* Get the names of the columns in the primary key. */  
  
retcode = SQLPrimaryKeys(hstmt,  
         NULL, 0,             /* Catalog name */  
         NULL, 0,             /* Schema name */  
         szTable, SQL_NTS);   /* Table name */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL SUCCESS_WITH_INFO)) {  
  
   /* Fetch and display the result set. This will be a list of the */  
   /* columns in the primary key of the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "Table: %s Column: %s Key Seq: %hd \n", szPkTable, szPkCol,  
      iKeySeq);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys that refer to ORDERS primary key.*/   
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,            /* Primary catalog */  
         NULL, 0,            /* Primary schema */  
         szTable, SQL_NTS,   /* Primary table */  
         NULL, 0,            /* Foreign catalog */  
         NULL, 0,            /* Foreign schema */  
         NULL, 0);           /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* foreign keys in other tables that refer to the ORDERS */  
/* primary key. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s ) <-- %-s ( %-s )\n", szPkTable,  
               szPkCol, szFkTable, szFkCol);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys in the ORDERS table. */  
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,             /* Primary catalog */  
         NULL, 0,             /* Primary schema */  
         NULL, 0,             /* Primary table */  
         NULL, 0,             /* Foreign catalog */  
         NULL, 0,             /* Foreign schema */  
         szTable, SQL_NTS);   /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* primary keys in other tables that are referred to by foreign */  
/* keys in the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s )--> %-s ( %-s )\n", szFkTable, szFkCol, szPkTable, szPkCol);  
}  
  
/* Free the hstmt. */  
SQLFreeStmt(hstmt, SQL_DROP);  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Aller chercher une seule rangée ou un bloc de données dans une direction avant-seulement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Retour des colonnes d’une clé primaire|[Fonction SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|Retour des statistiques et des indices de table|[Fonction SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
