---
title: FONCTION SQLSpecialColumns (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSpecialColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSpecialColumns
helpviewer_keywords:
- SQLSpecialColumns function [ODBC]
ms.assetid: bb2d9f21-bda0-4e50-a8be-f710db660034
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 826630e1d344322268a2f2638310b3a1e182de6d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287169"
---
# <a name="sqlspecialcolumns-function"></a>Fonction SQLSpecialColumns
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: Open Group  
  
 **Résumé**  
 **SQLSpecialColumns** récupère les informations suivantes sur les colonnes dans un tableau spécifié :  
  
-   L’ensemble optimal de colonnes qui identifie uniquement une ligne dans la table.  
  
-   Colonnes qui sont automatiquement mises à jour lorsque toute valeur de la ligne est mise à jour par une transaction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLSpecialColumns(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   IdentifierType,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3,  
     SQLSMALLINT   Scope,  
     SQLSMALLINT   Nullable);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *IdentifierType*  
 [Entrée] Type de colonne à retourner. Il doit s’agir de l’une des valeurs suivantes :   
  
 SQL_BEST_ROWID : Renvoie la colonne ou l’ensemble optimal de colonnes qui, en récupérant les valeurs de la colonne ou des colonnes, permettent d’identifier de manière unique toute ligne dans la table spécifiée. Une colonne peut être soit une pseudo-colonne spécialement conçue à cet effet (comme dans Oracle ROWID ou Ingres TID) ou la colonne ou les colonnes de tout indice unique pour la table.  
  
 SQL_ROWVER : Retourne la colonne ou les colonnes dans le tableau spécifié, le cas échéant, qui sont automatiquement mises à jour par la source de données lorsque toute valeur de la ligne est mise à jour par toute transaction (comme dans SQLBase ROWID ou Sybase TIMESTAMP).  
  
 *Nom du catalogue*  
 [Entrée] Nom du catalogue pour la table. Si un pilote prend en charge des catalogues pour certaines tables, mais pas pour d’autres, comme lorsque le pilote récupère des données de différents DBMS, une chaîne vide ("") dénote les tables qui n’ont pas de catalogues. *CatalogName* ne peut pas contenir un modèle de recherche de chaînes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID est configuré pour SQL_TRUE, *CatalogName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *CatalogName* est un argument ordinaire; il est traité littéralement, et son cas est significatif. Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Entrée] Longueur dans les caractères de*CatalogName*.  
  
 *SchemaName (SchemaName)*  
 [Entrée] Nom de Schema pour la table. Si un conducteur prend en charge des schémas pour certaines tables, mais pas pour d’autres, comme lorsque le conducteur récupère des données de différents DBMS, une chaîne vide («)) dénote les tables qui n’ont pas de schémas. *SchemaName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *SchemaName* est traité comme un identifiant et son cas n’est pas significatif. S’il est SQL_FALSE, *SchemaName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength2*  
 [Entrée] Longueur dans les personnages de*SchemaName*.  
  
 *TableName*  
 [Entrée] Nom de table. Cet argument ne peut pas être un pointeur nul. *TableName* ne peut pas contenir un modèle de recherche de cordes.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, *TableName* est traité comme un identifiant et son cas n’est pas significatif. S’il s’agit d’SQL_FALSE, *TableName* est un argument ordinaire; il est traité littéralement, et son cas est significatif.  
  
 *NomLength3*  
 [Entrée] Longueur dans les caractères de*TableName*.  
  
 *Étendue*  
 [Entrée] Portée minimale requise du rowid. Le rowid retourné peut être d’une plus grande portée. Doit prendre l'une des valeurs suivantes :  
  
 SQL_SCOPE_CURROW: Le rowid est garanti d’être valide seulement lorsqu’il est positionné sur cette rangée. Une réélectage ultérieure à l’aide de rowid peut ne pas retourner une rangée si la ligne a été mise à jour ou supprimée par une autre transaction.  
  
 SQL_SCOPE_TRANSACTION : Le rowid est garanti valide pour la durée de la transaction en cours.  
  
 SQL_SCOPE_SESSION : Le rowid est garanti pour être valide pour la durée de la session (au-delà des limites des transactions).  
  
 *Nullable*  
 [Entrée] Détermine s’il faut retourner des colonnes spéciales qui peuvent avoir une valeur NULL. Doit prendre l'une des valeurs suivantes :  
  
 SQL_NO_NULLS: Exclure les colonnes spéciales qui peuvent avoir des valeurs NULL. Certains conducteurs ne peuvent pas prendre en charge SQL_NO_NULLS, et ces conducteurs retourneront un jeu de résultat vide si SQL_NO_NULLS a été spécifié. Les demandes doivent être préparées pour cette affaire et demander SQL_NO_NULLS seulement si elle est absolument nécessaire.  
  
 SQL_NULLABLE: Retourner les colonnes spéciales, même si elles peuvent avoir des valeurs NULL.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSpecialColumns** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLSpecialColumns** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|24 000|État de curseur non valide|Un curseur était ouvert sur le *StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avaient été appelés. Cette erreur est retournée par le gestionnaire du conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.<br /><br /> Un curseur était ouvert sur le *StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelé.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|*L’argument de TableName* était un pointeur nul.<br /><br /> L’attribut de déclaration SQL_ATTR_METADATA_ID a été réglé pour SQL_TRUE, l’argument *CatalogName* était un pointeur nul, et le SQL_CATALOG_NAME *InfoType* retourne que les noms de catalogue sont pris en charge.<br /><br /> (DM) L’attribut de déclaration SQL_ATTR_METADATA_ID a été fixé à SQL_TRUE, et l’argument *de SchemaName* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction était encore en cours d’exécution lorsque **SQLSpecialColumns** a été appelé.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur de l’un des arguments de longueur était inférieure à 0, mais pas égale à SQL_NTS.<br /><br /> La valeur de l’un des arguments de longueur dépassait la valeur maximale de longueur pour le nom correspondant. La longueur maximale de chaque nom peut être obtenue en appelant **SQLGetInfo** avec les valeurs *InfoType* : SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN ou SQL_MAX_TABLE_NAME_LEN.|  
|HY097 HY097|Type de colonne hors de portée|(DM) Une valeur *d’identification type* non valide a été spécifiée.|  
|HY098 HY098|Type de portée hors de portée|(DM) Une valeur *de portée* non valide a été spécifiée.|  
|HY099 HY099|Type nul hors de portée|(DM) Une valeur *invalide a* été spécifiée.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Un catalogue a été spécifié, et le pilote ou la source de données ne prend pas en charge les catalogues.<br /><br /> Un schéma a été spécifié, et le conducteur ou la source de données ne prend pas en charge les schémas.<br /><br /> La combinaison des paramètres actuels des attributs SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE de l’énoncé n’a pas été prise en charge par le conducteur ou la source de données.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats demandé. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Lorsque *l’argument d’IdentificationType* est SQL_BEST_ROWID, **SQLSpecialColumns** renvoie la colonne ou les colonnes qui identifient uniquement chaque rangée dans la table. Ces colonnes peuvent toujours être utilisées dans une *liste de sélection* ou **quelle** clause. **SQLColumns**, qui est utilisé pour retourner une variété d’informations sur les colonnes d’une table, ne renvoie pas nécessairement les colonnes qui identifient uniquement chaque ligne, ou les colonnes qui sont automatiquement mises à jour lorsque toute valeur de la ligne est mise à jour par une transaction. Par exemple, **SQLColumns** pourrait ne pas retourner la pseudo-colonne Oracle ROWID. C’est pourquoi **SQLSpecialColumns** est utilisé pour retourner ces colonnes. Pour plus d’informations, voir [Utilisations des données de catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation générale, les arguments et les données retournées des fonctions de catalogue ODBC, voir [Catalog Functions](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 S’il n’y a pas de colonnes qui identifient uniquement chaque rangée dans la table, **SQLSpecialColumns** retourne un ensemble de rangées sans lignes; un appel ultérieur à **SQLFetch** ou **SQLFetchScroll** sur les déclarations de retour SQL_NO_DATA.  
  
 Si les arguments *IdentifierType,* *Scope*, ou *Nullable* spécifient des caractéristiques qui ne sont pas prises en charge par la source de données, **SQLSpecialColumns** retourne un ensemble de résultats vide.  
  
 Si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_TRUE, le *CatalogName*, *SchemaName*, et *TableName* arguments sont traités comme des identificateurs, de sorte qu’ils ne peuvent pas être réglés à un pointeur nul dans certaines situations. (Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).)  
  
 **SQLSpecialColumns** retourne les résultats comme un résultat standard établi, commandé par SCOPE.  
  
 Les colonnes suivantes ont été rebaptisées pour ODBC *3.x*. Les modifications du nom de colonne n’affectent pas la compatibilité vers l’arrière parce que les applications se lient par numéro de colonne.  
  
|Colonne ODBC 2.0|Colonne *ODBC 3.x*|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
  
 Pour déterminer la longueur réelle de la colonne COLUMN_NAME, une application peut appeler **SQLGetInfo** avec l’option SQL_MAX_COLUMN_NAME_LEN.  
  
 Le tableau suivant répertorie les colonnes dans l’ensemble de résultats. Des colonnes supplémentaires au-delà de la colonne 8 (PSEUDO_COLUMN) peuvent être définies par le conducteur. Une application doit avoir accès à des colonnes spécifiques au conducteur en comptant à partir de la fin de l’ensemble de résultats plutôt que de spécifier une position ordinaire explicite. Pour plus d’informations, voir [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nom de la colonne|Numéro de colonne|Type de données|Commentaires|  
|-----------------|-------------------|---------------|--------------|  
|PORTÉE (ODBC 1.0)|1|Smallint|Portée réelle du rowid. Contient l’une des valeurs suivantes :<br /><br /> SQL_SCOPE_CURROW SQL_SCOPE_TRANSACTION SQL_SCOPE_SESSION<br /><br /> NULL est retourné lorsque *IdentifierType* est SQL_ROWVER. Pour une description de chaque valeur, voir la description de *la portée* dans "Syntax", plus tôt dans cette section.|  
|COLUMN_NAME (ODBC 1.0)|2|Varchar pas NULL|Nom de la colonne. Le conducteur retourne une chaîne vide pour une colonne qui n’a pas de nom.|  
|DATA_TYPE (ODBC 1.0)|3|Smallint non NULL|Type de données SQL. Il peut s’agir d’un type de données SQL ODBC ou d’un type de données SQL spécifique au conducteur. Pour une liste des types de données SQL ODBC valides, consultez [les types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md). Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur.|  
|TYPE_NAME (ODBC 1.0)|4|Varchar pas NULL|Nom de type de données dépendante des sources de données; par exemple, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY", ou "CHAR ( ) FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 1.0)|5|Integer|La taille de la colonne sur la source de données. Pour plus d’informations sur la taille de la colonne, voir [La taille de colonne, les chiffres décimaux, la longueur d’octet de transfert, et la taille d’affichage.](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)|  
|BUFFER_LENGTH (ODBC 1.0)|6|Integer|La longueur des octets de données transférées sur une opération **SQLGetData** ou **SQLFetch** si SQL_C_DEFAULT est spécifiée. Pour les données numériques, cette taille peut être différente de la taille des données stockées sur la source de données. Cette valeur est la même que la colonne COLUMN_SIZE pour les données de caractère ou binaires. Pour plus d’informations, voir [Taille de colonne, Chiffres décimaux, Longueur Octet de transfert, et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|DECIMAL_DIGITS (ODBC 1.0)|7|Smallint|Les chiffres décimaux de la colonne sur la source de données. NULL est retourné pour les types de données où les chiffres décimaux ne sont pas applicables. Pour plus d’informations sur les chiffres décimaux, voir [La taille de colonne, les chiffres décimaux, la longueur d’octet de transfert, et la taille d’affichage.](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)|  
|PSEUDO_COLUMN (ODBC 2.0)|8|Smallint|Indique si la colonne est une pseudo-colonne, comme Oracle ROWID:<br /><br /> SQL_PC_UNKNOWN SQL_PC_NOT_PSEUDO SQL_PC_PSEUDO **Note:** Pour une interopérabilité maximale, les pseudo-colonnes ne doivent pas être citées avec le personnage de citation d’identification retourné par **SQLGetInfo**.|  
  
 Une fois que l’application récupère des valeurs pour SQL_BEST_ROWID, l’application peut utiliser ces valeurs pour rééllecter cette ligne dans la portée définie. **L’instruction SELECT** est garantie de retourner soit pas de lignes ou d’une rangée.  
  
 Si une application rééllect une ligne en fonction de la colonne ou des colonnes en rangée et que la ligne n’est pas trouvée, l’application peut supposer que la ligne a été supprimée ou que les colonnes de rowid ont été modifiées. Le contraire n’est pas vrai: même si le rowid n’a pas changé, les autres colonnes de la rangée peuvent avoir changé.  
  
 Les colonnes retournées pour le type de colonne SQL_BEST_ROWID sont utiles pour les applications qui doivent faire défiler vers l’avant et le dos dans un ensemble de résultats pour récupérer les données les plus récentes d’un ensemble de lignes. La colonne ou les colonnes de la rangée sont garanties de ne pas changer lorsqu’elles sont positionnées sur cette rangée.  
  
 La colonne ou les colonnes du rowid peuvent rester valides même lorsque le curseur n’est pas positionné sur la rangée; l’application peut le déterminer en vérifiant la colonne SCOPE dans l’ensemble de résultats.  
  
 Les colonnes retournées pour le type de colonne SQL_ROWVER sont utiles pour les applications qui ont besoin de la possibilité de vérifier si des colonnes dans une rangée donnée ont été mises à jour pendant que la ligne a été réélectionné à l’aide du rowid. Par exemple, après avoir réélié une ligne à l’aide de rowid, l’application peut comparer les valeurs précédentes dans les colonnes SQL_ROWVER à ceux qui viennent d’être récupérés. Si la valeur d’une colonne SQL_ROWVER diffère de la valeur précédente, l’application peut alerter l’utilisateur que les données de l’écran ont changé.  
  
## <a name="code-example"></a>Exemple de code  
 Pour un exemple de code d’une fonction similaire, voir [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Retour des colonnes dans une table ou une table|[Fonction SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Aller chercher une seule rangée ou un bloc de données dans une direction avant-seulement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Retour des colonnes d’une clé primaire|[Fonction SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
