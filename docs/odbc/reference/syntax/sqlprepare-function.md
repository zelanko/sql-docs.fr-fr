---
title: Fonction SQLPrepare (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPrepare
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPrepare
helpviewer_keywords:
- SQLPrepare function [ODBC]
ms.assetid: 332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e9aedd665df2a943627207902d592d597c503c63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306880"
---
# <a name="sqlprepare-function"></a>Fonction SQLPrepare
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLPrepare** prépare une corde SQL pour l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLPrepare(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     StatementText,  
     SQLINTEGER    TextLength);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *DéclarationTexte*  
 [Entrée] Corde de texte SQL.  
  
 *TextLength*  
 [Entrée] Longueur de *' StatementText* dans les caractères.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLPrepare** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLPrepare** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur de l’option modifiée|Un attribut de déclaration spécifiée était invalide en raison des conditions de travail de mise en œuvre, de sorte qu’une valeur similaire a été temporairement substituée. (**SQLGetStmtAttr** peut être appelé pour déterminer quelle est la valeur temporairement substituée.) La valeur de remplacement est valide pour le *StatementHandle* jusqu’à ce que le curseur soit fermé. Les attributs de déclaration qui peuvent être modifiés sont les : SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE SQL_ATTR_KEYSET_SIZE SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT SQL_ATTR_SIMULATE_CURSOR<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|21S01|La liste de valeur d’insertion ne correspond pas à la liste de colonnes|\**StatementText* contenait une instruction **INSERT,** et le nombre de valeurs à insérer ne correspondait pas au degré de la table dérivée.|  
|21S02|Le degré de tableau dérivé ne correspond pas à la liste des colonnes|\**StatementText* contenait une instruction **CREATE VIEW,** et le nombre de noms spécifiés n’est pas le même degré que le tableau dérivé défini par la spécification de requête.|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|**StatementText* contenait une déclaration SQL qui contenait un littéal ou un paramètre, et la valeur était incompatible avec le type de données de la colonne de tableau associée.|  
|22019|Caractère d’évasion invalide|*L’argument StatementText* contenait un **prédicat LIKE** avec un **ESCAPE** dans la clause **WHERE,** et la longueur du caractère d’évasion suivant **ESCAPE** n’était pas égale à 1.|  
|22025|Séquence d’évasion invalide|*L’argument StatementText* contenait «**LIKE** _pattern value_ **ESCAPE** _escape character_» dans la clause **WHERE,** et le caractère suivant le caractère d’évasion dans la valeur de modèle n’était ni « % » ni « ».|  
|24 000|État de curseur non valide|(DM) Un curseur était ouvert sur le *StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avaient été appelés.<br /><br /> Un curseur était ouvert sur le *StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelé.|  
|34000|Nom de curseur non valide|\**StatementText* contenait un **DELETE** positionné ou une **MISE À JOUR**positionnée , et le curseur référencé par la déclaration en cours de préparation n’était pas ouvert.|  
|3D000|Nom du catalogue invalide|Le nom du catalogue spécifié dans *StatementText* était invalide.|  
|3F000|Nom de schéma invalide|Le nom du schéma spécifié dans *StatementText* était invalide.|  
|42000|Erreur de syntaxe ou violation d’accès|\**DéclarationText* contenait une déclaration SQL qui n’était pas préparable ou contenait une erreur de syntaxe.<br /><br /> **StatementText* contenait une déclaration pour laquelle l’utilisateur n’avait pas les privilèges requis.|  
|42S01|La table de base ou la vue existe déjà|\**StatementText* contenait une **instruction CREATE TABLE** ou CREATE **VIEW,** et le nom de table ou le nom de vue spécifié existe déjà.|  
|42S02|Table de base ou vue non trouvée|\**StatementText* contenait une **TABLE DROP** ou une déclaration **DROP VIEW,** et le nom de table ou de vue spécifié n’existait pas.<br /><br /> \**StatementText* contenait une déclaration **ALTER TABLE,** et le nom de table spécifié n’existait pas.<br /><br /> \**StatementText* contenait une déclaration **CREATE VIEW,** et un nom de table ou un nom de vue défini par les spécifications de requête n’existait pas.<br /><br /> \**StatementText* contenait une déclaration **CREATE INDEX,** et le nom de table spécifié n’existait pas.<br /><br /> \**StatementText* contenait une déclaration **GRANT** ou **REVOKE,** et le nom de table ou de vue spécifié n’existait pas.<br /><br /> \**StatementText* contenait une déclaration **SELECT,** et un nom de table ou de vue spécifié n’existait pas.<br /><br /> \**StatementText* contenait une **déclaration DELETE**, **INSERT**, ou **UPDATE,** et le nom de table spécifié n’existait pas.<br /><br /> \**StatementText* contenait une déclaration **CREATE TABLE,** et un tableau spécifié dans une contrainte (référence à un tableau autre que celui en cours de création) n’existait pas.|  
|42S11|L’indice existe déjà|\**StatementText* contenait une déclaration **CREATE INDEX,** et le nom de l’index spécifié existait déjà.|  
|42S12|Index non trouvé|\**StatementText* contenait une déclaration **DROP INDEX,** et le nom de l’index spécifié n’existait pas.|  
|42S21|Colonne existe déjà|\**StatementText* contenait une déclaration **ALTER TABLE,** et la colonne spécifiée dans la clause **ADD** n’est pas unique ou identifie une colonne existante dans le tableau de base.|  
|42S22|Colonne non trouvée|\**StatementText* contenait une déclaration **CREATE INDEX,** et un ou plusieurs des noms de colonne spécifiés dans la liste de colonnes n’existaient pas.<br /><br /> \**StatementText* contenait une déclaration **GRANT** ou **REVOKE,** et un nom de colonne spécifié n’existait pas.<br /><br /> \**StatementText* contenait une **déclaration SELECT**, **DELETE**, **INSERT**, ou **UPDATE,** et un nom de colonne spécifié n’existait pas.<br /><br /> \**StatementText* contenait une déclaration **CREATE TABLE,** et une colonne spécifiée dans une contrainte (référence à un tableau autre que celui en cours de création) n’existait pas.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*, puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|(DM) *StatementText* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLPrepare** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) L’argument *TextLength* était inférieur ou égal à 0, mais pas égal à SQL_NTS.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le paramètre de concordance était invalide pour le type de curseur défini.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 La demande appelle **SQLPrepare** pour envoyer une déclaration SQL à la source de données pour la préparation. Pour plus d’informations sur l’exécution préparée, voir [l’exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md). L’application peut inclure un ou plusieurs marqueurs de paramètres dans l’énoncé SQL. Pour inclure un marqueur de paramètres, l’application intègre un point d’interrogation (?) dans la chaîne SQL à la position appropriée. Pour plus d’informations sur les paramètres, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).  
  
> [!NOTE]  
>  Si une application utilise **SQLPrepare** pour préparer et **SQLExecute** pour soumettre une déclaration **COMMIT** ou **ROLLBACK,** elle ne sera pas interopérable entre les produits DBMS. Pour valider ou annuler une transaction, appelez **SQLEndTran**.  
  
 Le conducteur peut modifier l’instruction pour utiliser le formulaire de SQL utilisé par la source de données, puis le soumettre à la source de données pour la préparation. En particulier, le conducteur modifie les séquences d’évacuation utilisées pour définir la syntaxe SQL pour certaines fonctionnalités. (Pour une description de la grammaire de déclaration SQL, voir [Escape Sequences in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) et [Appendix C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).) Pour le conducteur, une poignée de déclaration est similaire à un identifiant de déclaration dans le code SQL intégré. Si la source de données prend en charge les identifiants de relevé, le pilote peut envoyer un identifiant de relevé et des valeurs de paramètres à la source de données.  
  
 Une fois qu’une déclaration est préparée, l’application utilise la poignée de déclaration pour se référer à l’instruction dans les appels de fonction ultérieures. L’instruction préparée associée à la poignée de déclaration peut être réexécutée en appelant **SQLExecute** jusqu’à ce que l’application libère la déclaration avec un appel à **SQLFreeStmt** avec l’option SQL_DROP ou jusqu’à ce que la poignée de déclaration soit utilisée dans un appel à **SQLPrepare**, **SQLExecDirect**, ou l’une des fonctions du catalogue (**SQLColumns**, **SQLTables**, et ainsi de suite). Une fois que l’application prépare une déclaration, elle peut demander des informations sur le format de l’ensemble de résultats. Pour certaines implémentations, appeler **SQLDescribeCol** ou **SQLDescribeParam** après **SQLPrepare** pourrait ne pas être aussi efficace que d’appeler la fonction après **SQLExecute** ou **SQLExecDirect**.  
  
 Certains conducteurs ne peuvent pas retourner les erreurs de syntaxe ou les violations d’accès lorsque l’application appelle **SQLPrepare**. Un conducteur peut gérer les erreurs de syntaxe et les violations d’accès, seulement les erreurs de syntaxe, ni les erreurs de syntaxe ni les violations d’accès. Par conséquent, une application doit être en mesure de gérer ces conditions lors de l’appel des fonctions connexes ultérieures telles que **SQLNumResultCols**, **SQLDescribeCol**, **SQLColAttribute**, et **SQLExecute**.  
  
 Selon les capacités du conducteur et de la source de données, les informations sur les paramètres (tels que les types de données) peuvent être vérifiées lorsque l’instruction est préparée (si tous les paramètres ont été liés) ou lorsqu’elle est exécutée (si tous les paramètres n’ont pas été liés). Pour une interopérabilité maximale, une demande doit délier tous les paramètres qui s’appliquaient à une ancienne déclaration SQL avant de préparer une nouvelle déclaration SQL sur la même déclaration. Cela empêche les erreurs qui sont dues à l’application d’informations sur les anciens paramètres à la nouvelle déclaration.  
  
> [!IMPORTANT]  
>  L’engagement d’une transaction, soit en appelant explicitement **SQLEndTran,** soit en travaillant en mode autocommission, peut amener la source de données à supprimer les plans d’accès pour toutes les instructions sur une connexion. Pour plus d’informations, consultez les types d’information SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) et [Effect of Transactions on Cursors et Prepared Statements](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
## <a name="code-example"></a>Exemple de code  
 Voir [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), et [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Répartition d’une poignée de déclaration|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Lier un tampon à un paramètre|[Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Exécution d’une opération de validation ou de restauration|[Fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Retour du nombre de lignes touchées par une déclaration|[SQLRowCount (fonction)](../../../odbc/reference/syntax/sqlrowcount-function.md)|  
|Définir un nom de curseur|[SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
