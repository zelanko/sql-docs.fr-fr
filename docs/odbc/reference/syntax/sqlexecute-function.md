---
title: Fonction SQLExecute (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExecute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExecute
helpviewer_keywords:
- SQLExecute function [ODBC]
ms.assetid: 9286a01d-cde2-4b90-af94-9fd7f8da48bf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5306567aebc229a8bc9d1d3c91bcbd8e79391752
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286069"
---
# <a name="sqlexecute-function"></a>SQLExecute, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLExecute** exécute une déclaration préparée, en utilisant les valeurs actuelles des variables de marqueur de paramètres si des marqueurs de paramètres existent dans l’énoncé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLExecute(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE ou SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLExecute** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLExecute** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01001|Conflit d’opération cursor|L’instruction préparée associée au *StatementHandle* contenait une mise à jour ou une déclaration de suppression positionnée, et aucune ligne ou plus d’une rangée n’a été mise à jour ou supprimée. (Pour plus d’informations sur les mises à jour de plus d’une rangée, voir la description de *l’attribut* SQL_ATTR_SIMULATE_CURSOR dans **SQLSetStmtAttr .)**<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01003|Valeur NULL éliminée dans la fonction définie|L’instruction préparée associée à *StatementHandle* contenait une fonction définie (comme **AVG**, **MAX**, **MIN**, et ainsi de suite), mais pas la fonction définie **COUNT,** et les valeurs d’argument NULL ont été éliminées avant l’application de la fonction. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Les données de chaîne ou binaires retournées pour un paramètre de sortie ont abouti à la troncation de caractères non-blank ou de données binaires non-NULL. Si c’était une valeur de chaîne, il était juste-tronqué. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01006|Privilège non révoqué|L’instruction préparée associée au *StatementHandle* était une déclaration **DE RÉVOCation,** et l’utilisateur n’avait pas le privilège spécifié. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01007|Privilège non accordé|L’énoncé préparé associé à la *Déclaration Est* une déclaration **grant,** et l’utilisateur ne pouvait pas obtenir le privilège spécifié.|  
|01S02|Valeur de l’option modifiée|Un attribut de déclaration spécifiée était invalide en raison des conditions de travail de mise en œuvre, de sorte qu’une valeur similaire a été temporairement substituée. (**SQLGetStmtAttr** peut être appelé pour déterminer quelle est la valeur temporairement substituée.) La valeur de remplacement est valide pour le *StatementHandle* jusqu’à ce que le curseur soit fermé, à ce moment-là l’attribut de déclaration revient à sa valeur précédente. Les attributs de déclaration qui peuvent être modifiés sont les : SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT et SQL_ATTR_SIMULATE_CURSOR. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S07|Troncation fractionnaire|Les données retournées pour un paramètre d’entrée/sortie ou de sortie ont été tronquées de telle sorte que la partie fractionnelle d’un type de données numérique a été tronquée ou que la partie fractionnelle du composant de temps d’un type de temps, d’un fuseaux ou d’un type de données d’intervalle ait été tronquée.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07002|LE champ COUNT incorrect|Le nombre de paramètres spécifiés dans **SQLBindParameter** était inférieur au nombre de \* *StatementText*paramètres contenu dans la déclaration SQL.<br /><br /> **SQLBindParameter** a été appelé avec *ParameterValuePtr* réglé à un pointeur nul, *StrLen_or_IndPtr* pas réglé pour SQL_NULL_DATA ou SQL_DATA_AT_EXEC, et *InputOutputType* pas mis à SQL_PARAM_OUTPUT, de sorte que le nombre de paramètres spécifiés dans **SQLBindParameter** était plus élevé que le nombre de paramètres dans la déclaration SQLL contenu dans -*StatementText*.|  
|07006|Violation restreinte d’attribut de type de données|La valeur des données identifiée par *l’argument valueType* dans **SQLBindParameter** pour le paramètre lié n’a pas pu être convertie au type de données identifié par *l’argument de ParameterType* dans **SQLBindParameter**.<br /><br /> La valeur des données retournée pour un paramètre lié comme SQL_PARAM_INPUT_OUTPUT ou SQL_PARAM_OUTPUT n’a pas pu être convertie au type de données identifié par l’argument *ValueType* dans **SQLBindParameter**.<br /><br /> (Si les valeurs de données d’une ou plusieurs lignes ne pouvaient pas être converties, mais qu’une ou plusieurs lignes ont été retournées avec succès, cette fonction revient SQL_SUCCESS_WITH_INFO.)|  
|07007|Violation restreinte de la valeur des paramètres|Le type de paramètre SQL_PARAM_INPUT_OUTPUT_STREAM n’est utilisé que pour un paramètre qui envoie et reçoit des données en pièces. Un tampon lié à l’entrée n’est pas autorisé pour ce type de paramètre.<br /><br /> Cette erreur se produira lorsque le type de \*paramètre est SQL_PARAM_INPUT_OUTPUT, et lorsque le *StrLen_or_IndPtr* spécifié dans **SQLBindParameter** n’est pas égal à SQL_NULL_DATA, SQL_DEFAULT_PARAM, SQL_LEN_DATA_AT_EXEC (len), ou SQL_DATA_AT_EXEC.|  
|07S01|Utilisation invalide du paramètre par défaut|Une valeur de paramètre, définie avec **SQLBindParameter**, était SQL_DEFAULT_PARAM, et le paramètre correspondant n’était pas un paramètre pour une invocation canonique D’ODBC.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|21S02|Le degré de tableau dérivé ne correspond pas à la liste des colonnes|L’énoncé préparé associé au *StatementHandle* contenait une déclaration **CREATE VIEW,** et la liste de colonnes non qualifiée (le nombre de colonnes spécifiées pour la vue dans les arguments de la *colonne-identifiante* de la déclaration SQL) contenait plus de noms que le nombre de colonnes dans le tableau dérivé défini par *l’argument* de spécification de requête de la déclaration SQL.|  
|22001|Données de chaîne, troncation droite|L’attribution d’un personnage ou d’une valeur binaire à une colonne a entraîné la troncation de caractères ou d’octets non-nulls (binaires).|  
|22002|Variable d’indicateur requise mais non fournie|Les données NULL étaient liées à un paramètre de sortie dont *le StrLen_or_IndPtr* établi par **SQLBindParameter** était un pointeur nul.|  
|22003|Valeur numérique hors de portée|L’énoncé préparé associé au *StatementHandle* contenait un paramètre numérique lié, et la valeur du paramètre a fait tronquer la partie entière (par opposition à fractionnelle) du nombre lorsqu’elle était affectée à la colonne de table associée.<br /><br /> Le retour d’une valeur numérique (en tant que numérique ou chaîne) pour un ou plusieurs paramètres d’entrée/sortie ou de sortie aurait fait tronquer l’ensemble (par opposition à la fractionnement) de la partie du nombre.|  
|22007|Format de date invalide|L’énoncé préparé associé au *StatementHandle* contenait une déclaration SQL qui contenait une structure de date, d’heure ou d’humidité temporelle comme paramètre lié, et le paramètre était, respectivement, une date, une heure ou un fuseau horaires non valides.<br /><br /> Un paramètre d’entrée/sortie ou de sortie était lié à une structure de date, d’heure ou de timetamp C, et une valeur dans le paramètre retourné était, respectivement, une date, une heure ou un fuseur horaires non valides. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|22008|Débordement de champ datetime|L’énoncé préparé associé au *StatementHandle* contenait une déclaration de SQL qui contenait une expression relative à l’heure de la date qui, une fois calculée, a donné lieu à une structure de date, d’heure ou d’humidité temporelle qui était invalide.<br /><br /> Une expression de date calculée pour un paramètre d’entrée/sortie ou de sortie a donné lieu à une structure de date, d’heure ou de timetamp C qui était invalide.|  
|22012|Division par zéro|L’énoncé préparé associé au *StatementHandle* contenait une expression arithmétique qui causait la division par zéro.<br /><br /> Une expression arithmétique calculée pour un paramètre d’entrée/sortie ou de sortie a entraîné une division par zéro.|  
|22015|Débordement de champ d’intervalle|StatementText contenait un paramètre numérique ou d’intervalle exact qui, lorsqu’il est converti en type de données SQL d’intervalle, causait une perte de chiffres importants. * \**<br /><br /> StatementText contenait un paramètre d’intervalle avec plus d’un champ qui, une fois converti en type de données numériques dans une colonne, n’avait aucune représentation dans le type de données numériques. * \**<br /><br /> DéclarationText contenait des données de paramètres qui ont été attribuées à un type SQL d’intervalle, et il n’y avait aucune représentation de la valeur du type C dans le type SQL d’intervalle. * \**<br /><br /> L’attribution d’un paramètre d’entrée/sortie ou de sortie qui était d’un type SQL numérique ou d’intervalle exact à un type d’intervalle C a causé une perte de chiffres importants.<br /><br /> Lorsqu’un paramètre d’entrée/sortie ou de sortie a été attribué à une structure d’intervalle C, il n’y a pas eu de représentation des données dans la structure des données d’intervalle.|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|StatementText contenait un type C qui était un numérique exact ou approximatif, une date ou un type de données d’intervalle; * \** le type SQL de la colonne était un type de données de caractère; et la valeur de la colonne n’était pas un littéral valide du type C lié.<br /><br /> Lorsqu’un paramètre d’entrée/sortie ou de sortie a été retourné, le type SQL était un produit numérique exact ou approximatif, une date ou un type de données d’intervalle; le type C était SQL_C_CHAR; et la valeur de la colonne n’était pas un littéral valide du type SQL lié.|  
|22019|Caractère d’évasion invalide|La déclaration préparée associée à *StatementHandle* contenait un **justiciant** avec un **ESCAPE** dans la clause **WHERE,** et la longueur du caractère d’évasion suivant **ESCAPE** n’était pas égale à 1.|  
|22025|Séquence d’évasion invalide|La déclaration préparée associée à *StatementHandle* contenait «**LIKE** _pattern value_ **ESCAPE** _escape character_» dans la clause **WHERE,** et le caractère suivant le caractère d’évasion dans la valeur de modèle n’était pas un de « % » ou « ».|  
|23000|Violation de la contrainte d’intégrité|L’énoncé préparé associé au *StatementHandle* contenait un paramètre. La valeur du paramètre était NULL pour une colonne définie comme NOT NULL dans la colonne de table associée, une valeur en double a été fournie pour une colonne contrainte de ne contenir que des valeurs uniques, ou une autre contrainte d’intégrité a été violée.|  
|24 000|État de curseur non valide|Un curseur a été positionné sur le *StatementHandle* par **SQLFetch** ou **SQLFetchScroll**. Cette erreur est retournée par le gestionnaire du conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA, et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.<br /><br /> Un curseur était ouvert sur le *StatementHandle*.<br /><br /> L’instruction préparée associée à la *DéclarationHandle* contenait une mise à jour ou une suppression des statemen positionnés, et le curseur était positionné avant le début de l’ensemble de résultats ou après la fin de l’ensemble de résultats.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|42000|Erreur de syntaxe ou violation d’accès|L’utilisateur n’avait pas la permission d’exécuter l’instruction préparée associée à *la DéclarationHandle*.|  
|44000|Violation de WITH CHECK OPTION|L’énoncé préparé associé à *StatementHandle* contenait une déclaration **INSERT** effectuée sur une table vue ou une table dérivée de la table vue qui a été créée en spécifiant **AVEC CHECK OPTION**, de sorte qu’une ou plusieurs lignes touchées par l’énoncé **INSERT** ne seront plus présentes dans la table vue.<br /><br /> L’énoncé préparé associé au *StatementHandle* contenait une déclaration **UPDATE** effectuée sur une table vue ou un tableau dérivé du tableau vu qui a été créé en spécifiant **AVEC CHECK OPTION**, de sorte qu’une ou plusieurs lignes touchées par l’énoncé **UPDATE** ne seront plus présentes dans le tableau vu.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLExecute** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Le *communiqué n’a* pas été préparé.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|Une valeur de paramètre, définie avec **SQLBindParameter**, était un pointeur nul, et la valeur de longueur de paramètres n’était pas 0, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM, ou moins ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Une valeur de paramètre, définie avec **SQLBindParameter**, n’était pas un pointeur nul; le type de données C était SQL_C_BINARY ou SQL_C_CHAR; et la valeur de longueur du paramètre était inférieure à 0, mais n’était pas SQL_NTS, SQL_NULL_DATA, SQL_DEFAULT_PARAM ou SQL_DATA_AT_EXEC, ou moins ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Une valeur de longueur de paramètre liée par **SQLBindParameter** a été réglée pour SQL_DATA_AT_EXEC; le type SQL était soit SQL_LONGVARCHAR, SQL_LONGVARBINARY, soit un type de données spécifique à une source de données longue; et le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était « Y ».|  
|Hy105|Type de paramètre invalide|La valeur spécifiée pour l’argument *InputOutputType* dans **SQLBindParameter** était SQL_PARAM_OUTPUT, et le paramètre était un paramètre d’entrée.|  
|HY109 HY109|Position de curseur invalide|L’énoncé préparé était une mise à jour ou une déclaration de suppression positionnée, et le curseur était positionné (par **SQLSetPos** ou **SQLFetchScroll**) sur une rangée qui avait été supprimée ou ne pouvait pas être récupérée.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|La combinaison des paramètres actuels des attributs SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE de l’énoncé n’a pas été prise en charge par le conducteur ou la source de données.<br /><br /> L’attribut de SQL_ATTR_USE_BOOKMARKS déclaration a été réglé pour SQL_UB_VARIABLE, et l’attribut de déclaration SQL_ATTR_CURSOR_TYPE a été réglé à un type de curseur pour lequel le conducteur ne prend pas en charge les signets.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
 **SQLExecute** peut renvoyer n’importe quel SQLSTATE qui peut être retourné par **SQLPrepare**, en fonction du moment où la source de données évalue la déclaration SQL associée à la déclaration.  
  
## <a name="comments"></a>Commentaires  
 **SQLExecute** exécute une déclaration préparée par **SQLPrepare**. Après que l’application traite ou rejette les résultats d’un appel à **SQLExecute**, l’application peut appeler **SQLExecute** à nouveau avec de nouvelles valeurs de paramètres. Pour plus d’informations sur l’exécution préparée, voir [l’exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
 Pour exécuter une déclaration **SELECT** plus d’une fois, l’application doit appeler **SQLCloseCursor** avant de réexaminer la déclaration **SELECT.**  
  
 Si la source de données est en mode de validation manuelle (nécessitant une ouverture explicite des transactions) et qu’une transaction n’a pas encore été entreprise, le conducteur lance une transaction avant d’envoyer la déclaration SQL. Pour plus d’informations, consultez [Transactions](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Si une application utilise **SQLPrepare** pour préparer et **SQLExecute** pour soumettre une déclaration **COMMIT** ou **ROLLBACK,** elle ne sera pas interopérable entre les produits DBMS. Pour valider ou annuler une transaction, appelez **SQLEndTran**.  
  
 Si **SQLExecute** rencontre un paramètre de données à l’exécution, il renvoie SQL_NEED_DATA. L’application envoie les données à l’aide **de SQLParamData** et **SQLPutData**. Voir [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), et [Sending Long Data](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 Si **SQLExecute** exécute une mise à jour, un insérer ou supprimer une déclaration recherchée qui n’affecte aucune ligne à la source de données, l’appel à **SQLExecute** renvoie SQL_NO_DATA.  
  
 Si la valeur de l’attribut de l’SQL_ATTR_PARAMSET_SIZE’énoncé est supérieure à 1 et que l’énoncé SQL contient au moins un marqueur de paramètres, **SQLExecute** exécute la déclaration SQL une fois pour chaque ensemble de valeurs de paramètres dans les tableaux pointés par l’argument * \*de ParameterValuePtr* dans les appels à **SQLBindParameter**. Pour plus d’informations, voir [Arrays of Parameter Values](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Si des signets sont activés et qu’une requête est exécutée qui ne peut pas prendre en charge les signets, le conducteur doit tenter de contraindre l’environnement à un qui prend en charge les signets en changeant une valeur d’attribut et en retournant SQLSTATE 01S02 (valeur d’option modifiée). Si l’attribut ne peut pas être modifié, le conducteur doit retourner SQLSTATE HY024 (valeur d’attribut invalide).  
  
> [!NOTE]  
>  Lors de l’utilisation de la mise en commun des connexions, une application ne doit pas exécuter les instructions SQL qui modifient la base de données ou le contexte de la base de données, comme la base _de données_ **USE** dans SQL Server, qui modifie le catalogue utilisé par une source de données.  
  
## <a name="code-example"></a>Exemple de code  
 Voir [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), et [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Fermeture du curseur|[SQLCloseCursor, fonction](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Exécution d’une opération de validation ou de restauration|[Fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Aller chercher plusieurs rangées de données|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Libérer une poignée de déclaration|[Fonction SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Retour d’un nom curseur|[SQLGetCursorName Function](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Aller chercher une partie ou la totalité d’une colonne de données|[Fonction SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Retour du paramètre suivant pour envoyer des données pour|[SQLParamData, fonction](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Préparation d’une déclaration pour l’exécution|[Fonction SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Envoi de données de paramètres au moment de l’exécution|[Fonction SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Définir un nom de curseur|[SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
