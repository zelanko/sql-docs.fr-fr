---
title: SQLExecute, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df0021bf5b3ac905ddf63ede8d4dfd65710662aa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789907"
---
# <a name="sqlexecute-function"></a>SQLExecute, fonction
**Conformité**  
 Version introduite : La mise en conformité des normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLExecute** exécute une instruction préparée, en utilisant les valeurs actuelles des variables de marqueur de paramètre si les marqueurs de paramètres existent dans l’instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLExecute(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *Au paramètre StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE ou SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLExecute** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLExecute** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01001|Conflit d’opération de curseur|L’instruction préparée associée à la *au paramètre StatementHandle* relation contenant-contenu un positionnées de mettre à jour ou de l’instruction delete, et aucune ligne ou plusieurs lignes ont été mis à jour ou supprimés. (Pour plus d’informations sur les mises à jour de plusieurs lignes, consultez la description de la SQL_ATTR_SIMULATE_CURSOR *attribut* dans **SQLSetStmtAttr**.)<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01003|Valeur NULL supprimée dans la fonction définie|L’instruction préparée associée *au paramètre StatementHandle* contenait une fonction set (tel que **AVG**, **MAX**, **MIN**, et ainsi de suite), mais pas le **nombre** définir la fonction et l’argument NULL valeurs ont été éliminés avant que la fonction a été appliquée. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|Données de chaîne ou binaire retournées pour un paramètre de sortie a entraîné la troncation des caractères non vides ou non NULL des données binaires. S’il s’agissait d’une valeur de chaîne, il a été tronquée à droite. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01006|Privilège non révoqué|L’instruction préparée associée à la *au paramètre StatementHandle* a été un **RÉVOQUER** instruction et l’utilisateur ne disposait pas le privilège spécifié. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01007|Privilège non accordé|L’instruction préparée associée à la *au paramètre StatementHandle* a été un **GRANT** instruction et l’utilisateur n’ont pas reçu le privilège spécifié.|  
|01S02|Valeur d’option modifiée|Un attribut d’instruction spécifiée non valide en raison de conditions de travail d’implémentation, donc une valeur similaire a été remplacée temporairement. (**SQLGetStmtAttr** peut être appelée pour déterminer quelle est la valeur substituée temporairement.) La valeur de remplacement n’est valide pour le *au paramètre StatementHandle* jusqu'à ce que le curseur est fermé, à quel point l’attribut d’instruction reprend sa valeur précédente. Les attributs d’instruction qui peuvent être modifiés sont : SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT et SQL_ATTR_SIMULATE_CURSOR. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01 S 07|Troncation fractionnelle|Les données retournées pour une entrée/sortie ou paramètre de sortie a été tronqué de sorte que la partie fractionnaire d’un type de données numériques ont été tronquée ou la partie fractionnaire du composant de temps un intervalle de temps, timestamp ou du type de données a été tronquée.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07002|Champ COUNT incorrect|Le nombre de paramètres spécifiés dans **SQLBindParameter** était inférieur au nombre de paramètres dans l’instruction SQL contenue dans \* *StatementText*.<br /><br /> **SQLBindParameter** a été appelé avec *ParameterValuePtr* un pointeur null, la valeur *StrLen_or_IndPtr* ne pas la valeur SQL_NULL_DATA ou SQL_DATA_AT_EXEC, et *InputOutputType*  ne pas la valeur SQL_PARAM_OUTPUT, afin que le nombre de paramètres spécifié dans **SQLBindParameter** a été supérieur au nombre de paramètres dans l’instruction SQL contenue dans **StatementText* .|  
|07006|Violation de l’attribut de type de données restreint|La valeur de données identifiée par le *ValueType* argument dans **SQLBindParameter** pour le paramètre dépendant n’a pas pu être converti au type de données identifié par le *ParameterType*argument dans **SQLBindParameter**.<br /><br /> La valeur de données retournée pour un paramètre lié comme SQL_PARAM_INPUT_OUTPUT ou SQL_PARAM_OUTPUT pas pu être convertie au type de données identifié par le *ValueType* argument dans **SQLBindParameter**.<br /><br /> (Si les valeurs de données pour une ou plusieurs lignes n’a pas pu être converties, mais une ou plusieurs lignes ont été retournés avec succès, cette fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07007|Violation de valeur de paramètre restreint|Le type de paramètre SQL_PARAM_INPUT_OUTPUT_STREAM est utilisé uniquement pour un paramètre qui envoie et reçoit des données en parties. Un tampon d’entrée dépendant n’est pas autorisé pour ce type de paramètre.<br /><br /> Cette erreur se produit lorsque le type de paramètre est SQL_PARAM_INPUT_OUTPUT et lorsque le \* *StrLen_or_IndPtr* spécifié dans **SQLBindParameter** n’est pas égal à SQL_NULL_DATA, SQL_DEFAULT_ PARAM, SQL_LEN_DATA_AT_EXEC(len) ou SQL_DATA_AT_EXEC.|  
|07 S 01|Utilisation non valide du paramètre par défaut|Un paramètre défini avec **SQLBindParameter**, a été SQL_DEFAULT_PARAM, et le paramètre correspondant n’est pas un paramètre pour un appel de procédure canonique ODBC.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|21S02|Degré de la table dérivée ne correspond pas à la liste des colonnes|L’instruction préparée associée à la *au paramètre StatementHandle* contenus un **CREATE VIEW** instruction et la liste de colonnes non qualifiés (le nombre de colonnes spécifié pour l’affichage dans le  *identificateur de colonne* arguments de l’instruction SQL) contenait plus de noms que le nombre de colonnes dans la table dérivée définie par le *spécification de requête* argument de l’instruction SQL.|  
|22001|Données String, troncation à droite|L’attribution d’un caractère ou d’une valeur binaire à une colonne a entraîné la troncation de non vides (caractère) ou d’octets ou caractères (binaires) non null.|  
|22002|Variable indicateur requise mais non fournie|Données de type NULL a été liées à un paramètre de sortie dont *StrLen_or_IndPtr* définie par **SQLBindParameter** était un pointeur null.|  
|22003|Valeur numérique hors limites|L’instruction préparée associée à la *au paramètre StatementHandle* contenait un paramètre numérique lié, et la valeur du paramètre a provoqué la partie entière (par opposition aux fractions de seconde) le nombre à tronquer lorsque affectés à associé colonne de table.<br /><br /> Renvoi d’une valeur numérique (comme numérique ou chaîne) pour un ou plusieurs paramètres d’entrée/sortie ou de sortie aurait entraîné la partie entière (par opposition à fractionnaire) du nombre à tronquer.|  
|22007|Format datetime non valide|L’instruction préparée associée à la *au paramètre StatementHandle* contenait une instruction SQL qui contenait une date, d’une heure ou d’une structure d’horodateur en tant qu’un paramètre dépendant, et le paramètre a été, respectivement, une date non valide, l’heure ou horodatage.<br /><br /> Un paramètre d’entrée/sortie ou de sortie a été lié à une date, d’une heure ou d’une structure d’horodateur C, et une valeur dans le paramètre retourné a été, respectivement, une date non valide, une heure ou un horodatage. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|22008|Dépassement du champ DateTime|L’instruction préparée associée à la *au paramètre StatementHandle* relation contenant-contenu pour une instruction SQL qui contenait une expression datetime que, lorsque calculée, a entraîné une date, heure ou timestamp structure qui n’est pas valide.<br /><br /> Une expression datetime calculée pour une entrée/sortie ou paramètre de sortie a entraîné une date, heure ou structure d’horodateur C qui n’était pas valide.|  
|22012|Division par zéro|L’instruction préparée associée à la *au paramètre StatementHandle* contenait une expression arithmétique ayant provoqué la division par zéro.<br /><br /> Une expression arithmétique calculée pour une entrée/sortie ou paramètre de sortie a entraîné de division par zéro.|  
|22015|Dépassement du champ Intervalle|*\*StatementText* contenait un paramètre numérique ou intervalle exact qui, lors de la convertir en un intervalle de type de données SQL, a entraîné une perte de chiffres significatifs.<br /><br /> *\*StatementText* contenait un paramètre d’intervalle avec plusieurs champs que, lorsque converti en un type de données numériques dans une colonne, n’avait aucune représentation dans le type de données numérique.<br /><br /> *\*StatementText* contenait des données de paramètre qui a été affectées à un intervalle de type SQL, et il n’existait aucune représentation de la valeur du type C dans l’intervalle de type SQL.<br /><br /> Affectation d’un paramètre d’entrée/sortie ou de sortie qui a une valeur numérique exacte ou un intervalle de type SQL à un type d’intervalle C a entraîné une perte de chiffres significatifs.<br /><br /> Lorsqu’un paramètre d’entrée/sortie ou de sortie a été affecté à une structure d’intervalle C, il n’a pas de représentation des données dans la structure de données d’intervalle.|  
|22018|Valeur de caractère non valide pour la spécification de la casse|*\*StatementText* contenait un type C qui a une valeur numérique exact ou approximatif, une valeur datetime ou un type de données d’intervalle ; le type SQL de la colonne a un type de données caractère ; et la valeur dans la colonne n’est pas un littéral valid du type C lié.<br /><br /> Lorsqu’un paramètre d’entrée/sortie ou de sortie a été retourné, le type SQL était une valeur numérique exact ou approximatif, une valeur datetime ou un type de données d’intervalle ; le type C a été SQL_C_CHAR ; et la valeur dans la colonne n’est pas un littéral valid du type SQL dépendant.|  
|22019|Caractère d’échappement non valide|L’instruction préparée associée *au paramètre StatementHandle* contenus un **comme** prédicat avec une **d’échappement** dans le **où** clause, et la longueur de ces caractères d’échappement **échappement** n’était pas égale à 1.|  
|22025|Séquence d’échappement non valide|L’instruction préparée associée *au paramètre StatementHandle* contenus «**comme** *valeur de modèle* **échappement** *escape caractère*» dans le **où** clause et le caractère qui suit le caractère d’échappement dans la valeur de modèle n’est pas une « % » ou « _ ».|  
|23000|Violation de contrainte d’intégrité|L’instruction préparée associée à la *au paramètre StatementHandle* contient un paramètre. La valeur du paramètre était NULL pour une colonne définie comme NOT NULL dans la colonne de table associée, une valeur en double a été fournie pour une colonne obligée de contenir uniquement des valeurs uniques ou une autre contrainte d’intégrité a été violée.|  
|24000|État de curseur non valide|Un curseur a été positionné sur le *au paramètre StatementHandle* par **SQLFetch** ou **SQLFetchScroll**. Cette erreur est retournée par le Gestionnaire de pilotes si **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_NO_DATA et est retourné par le pilote si **SQLFetch** ou **SQLFetchScroll** a retourné SQL_NO_DATA.<br /><br /> Un curseur a été ouvert sur le *au paramètre StatementHandle*.<br /><br /> L’instruction préparée associée à la *au paramètre StatementHandle* contenait une mise à jour positionnée ou delete statemen, t et le curseur est positionné avant le début du jeu de résultats ou après la fin du jeu de résultats.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|42000|Syntaxe ou violation d’accès|L’utilisateur n’a pas d’autorisation d’exécuter l’instruction préparée associée à la *au paramètre StatementHandle*.|  
|44000|Violation de WITH CHECK OPTION|L’instruction préparée associée *au paramètre StatementHandle* contenait un **insérer** instruction exécutée sur une table affichée ou une table dérivée à partir de la table affichée qui a été créée en spécifiant **WITH CHECK OPTION**, de sorte qu’une ou plusieurs lignes affectées par la **insérer** instruction ne pourra plus être présente dans la table affichée.<br /><br /> L’instruction préparée associée à la *au paramètre StatementHandle* contenus un **mise à jour** instruction exécutée sur une table affichée ou une table dérivée à partir de la table affichée qui a été créée en spécifiant **WITH CHECK OPTION**, de sorte qu’une ou plusieurs lignes affectées par la **mise à jour** instruction ne pourra plus être présente dans la table affichée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*. La fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLExecute** fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) le *au paramètre StatementHandle* n’était pas préparée.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|Un paramètre défini avec **SQLBindParameter**, était un pointeur null, et la valeur de paramètre de longueur n’était pas 0, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM, ou inférieure ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Un paramètre défini avec **SQLBindParameter**, n’était pas un pointeur null ; le type de données C a été SQL_C_BINARY ou SQL_C_CHAR ; et la valeur de paramètre de longueur est inférieure à 0 mais n’était pas SQL_NTS, SQL_NULL_DATA, SQL_DEFAULT_PARAM ou SQL_DATA_ AT_EXEC, ou inférieure ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Une valeur de longueur de paramètre lié par **SQLBindParameter** a été défini sur SQL_DATA_AT_EXEC ; le type SQL a été SQL_LONGVARCHAR, SQL_LONGVARBINARY, ou un type de données de spécifique à la source de données de type long ; et les informations de SQL_NEED_LONG_DATA_LEN Tapez dans **SQLGetInfo** a été « Y ».|  
|HY105|Type de paramètre non valide|La valeur spécifiée pour l’argument *InputOutputType* dans **SQLBindParameter** a été SQL_PARAM_OUTPUT, et le paramètre est un paramètre d’entrée.|  
|HY109|Position de curseur non valide|L’instruction préparée a été une mise à jour positionnée ou une instruction delete, et le curseur a été positionné (par **SQLSetPos** ou **SQLFetchScroll**) sur une ligne qui a été supprimée ou ne peut pas être récupérée.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|La combinaison des paramètres actuels des attributs d’instruction SQL_ATTR_CONCURRENCY et SQL_ATTR_CURSOR_TYPE n’était pas pris en charge par la pilote ou source de données.<br /><br /> L’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a été défini sur SQL_UB_VARIABLE, et l’attribut d’instruction SQL_ATTR_CURSOR_TYPE a été défini pour un type de curseur pour lequel le pilote ne prend pas en charge les signets.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant que la source de données a retourné le jeu de résultats. Le délai d’expiration est défini via **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
 **SQLExecute** peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLPrepare**, en fonction lorsque la source de données évalue l’instruction SQL associée à l’instruction.  
  
## <a name="comments"></a>Commentaires  
 **SQLExecute** exécute une instruction préparée par **SQLPrepare**. Une fois que l’application traite ou ignore les résultats d’un appel à **SQLExecute**, l’application peut appeler **SQLExecute** à nouveau avec les nouvelles valeurs de paramètre. Pour plus d’informations sur l’exécution préparée, consultez [exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
 Pour exécuter un **sélectionnez** instruction plusieurs fois, l’application doit appeler **SQLCloseCursor** avant de réexécuter la **sélectionnez** instruction.  
  
 Si la source de données est en mode de validation manuelle (nécessitant l’émission de la transaction explicite) et une transaction n’a pas déjà été lancée, le pilote initie une transaction avant qu’il envoie l’instruction SQL. Pour plus d’informations, consultez [Transactions](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Si une application utilise **SQLPrepare** pour préparer et **SQLExecute** pour soumettre un **valider** ou **ROLLBACK** instruction, il ne sera pas interopérabilité entre les produits de SGBD. Pour valider ou restaurer une transaction, appelez **SQLEndTran**.  
  
 Si **SQLExecute** rencontre un paramètre data-at-execution, elle retourne SQL_NEED_DATA. L’application envoie les données à l’aide **SQLParamData** et **SQLPutData**. Consultez [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), et [envoi de données de type Long](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 Si **SQLExecute** exécute une mise à jour recherchée, une insertion ou une instruction delete qui n’affecte pas toutes les lignes à la source de données, l’appel à **SQLExecute** retourne SQL_NO_DATA.  
  
 Si la valeur de l’attribut d’instruction SQL_ATTR_PARAMSET_SIZE est supérieure à 1 et l’instruction SQL contient au moins un marqueur de paramètre, **SQLExecute** exécute l’instruction SQL une fois pour chaque ensemble de valeurs de paramètre dans les tableaux vers lequel pointe le  *\*ParameterValuePtr* argument dans les appels à **SQLBindParameter**. Pour plus d’informations, consultez [tableaux de valeurs de paramètre](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Si les signets sont activés et exécution d’une requête qui ne peut pas prendre en charge des signets, le pilote doit tenter de forcer l’environnement pour qu’il prend en charge des signets en modifiant une valeur d’attribut et en retournant SQLSTATE 01 s 02 (valeur d’Option modifiée). Si l’attribut ne peut pas être modifié, le pilote doit retourner SQLSTATE HY024 (valeur d’attribut non valide).  
  
> [!NOTE]  
>  Lorsque vous utilisez le regroupement de connexions, une application ne doit pas exécuter les instructions SQL qui modifient la base de données ou le contexte de la base de données, telles que la **utilisation** *base de données* instruction dans SQL Server, ce qui change le catalogue utilisé par une source de données.  
  
## <a name="code-example"></a>Exemple de code  
 Consultez [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), et [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à une colonne dans un jeu de résultats|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Fermeture du curseur|[SQLCloseCursor, fonction](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|L’exécution d’une opération commit ou rollback|[SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|L’exécution d’une instruction SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Extraction de plusieurs lignes de données|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll, fonction](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Libération d’un descripteur d’instruction|[SQLFreeStmt, fonction](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Retourner un nom de curseur|[SQLGetCursorName, fonction](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|L’extraction de tout ou partie d’une colonne de données|[SQLGetData, fonction](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Retourner le paramètre suivant pour envoyer des données|[SQLParamData, fonction](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Préparation d’une instruction pour l’exécution|[SQLPrepare, fonction](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Envoi de données de paramètre au moment de l’exécution|[SQLPutData, fonction](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Définition d’un nom de curseur|[SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
|Définition d’un attribut d’instruction|[SQLSetStmtAttr, fonction](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
