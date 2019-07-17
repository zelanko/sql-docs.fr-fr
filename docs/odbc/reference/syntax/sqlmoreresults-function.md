---
title: SQLMoreResults, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLMoreResults
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLMoreResults
helpviewer_keywords:
- SQLMoreResults function [ODBC]
ms.assetid: bf169ed5-4d55-412c-b184-12065a726e89
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3ca7ed4f6bbcd31b8f67b95dc14a2c6c301b5a59
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138828"
---
# <a name="sqlmoreresults-function"></a>Fonction SQLMoreResults
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ODBC  
  
 **Résumé**  
 **SQLMoreResults** détermine si plus de résultats sont disponibles sur une instruction contenant **sélectionnez**, **mise à jour**, **insérer**, ou  **SUPPRIMER** instructions et, dans ce cas, initialise le traitement de ces résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE OU SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLMoreResults** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL _HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLMoreResults** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur de l’option a changé.|La valeur d’un attribut d’instruction modifié en tant que le lot a été en cours de traitement. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. Le **SQLMoreResults** fonction a été appelée et, avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* . Le **SQLMoreResults** fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> Le **SQLMoreResults** fonction a été appelée et, avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*  d’un thread différent dans une application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLMoreResults** fonction a été appelée.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **Sélectionnez** instructions retournent des jeux de résultats. **Mise à jour**, **insérer**, et **supprimer** instructions retournent un nombre de lignes affectées. Si une de ces instructions sont exécutées par lot soumis avec des tableaux de paramètres (numérotées dans l’ordre de paramètre, dans l’ordre où ils apparaissent dans le lot croissant) ou dans les procédures, elles peuvent retourner plusieurs jeux de résultats, ou le nombre de lignes. Pour plus d’informations sur les lots d’instructions et des tableaux de paramètres, consultez [Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md) et [tableaux de valeurs de paramètre](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Après l’exécution du lot, l’application est positionnée sur le premier jeu de résultats. L’application peut appeler **SQLBindCol**, **SQLBulkOperations**, **SQLFetch**, **SQLGetData**, **SQLFetchScroll** , **SQLSetPos**et toutes les fonctions de métadonnées, sur les première ou tous les résultats les jeux, tout comme il le ferait s’il y avait simplement un seul jeu de résultats. Une fois que cela est fait avec le premier jeu de résultats, l’application appelle **SQLMoreResults** pour déplacer vers le jeu de résultats suivant. Si un autre jeu de résultats ou count est disponible, **SQLMoreResults** retourne SQL_SUCCESS et initialise le jeu de résultats ou un nombre pour un traitement supplémentaire. Si les instructions de génération de nombre de ligne apparaissent entre les deux entraîner des instructions de génération de jeu, ils peuvent être échelonnées en appelant **SQLMoreResults**. Après avoir appelé **SQLMoreResults** pour **mise à jour**, **insérer**, ou **supprimer** instructions, une application peut appeler **SQLRowCount**.  
  
 S’il y avait un jeu avec des lignes, de résultats actuel **SQLMoreResults** ignore ce jeu de résultats et rend l’autre jeu de résultats ou de nombre disponibles. Si tous les résultats ont été traités, **SQLMoreResults** retourne SQL_NO_DATA. Pour certains pilotes, paramètres de sortie et les valeurs de retour ne sont pas disponibles jusqu'à ce que tous les jeux de résultats et les nombres de lignes ont été traités. Pour ces pilotes, les paramètres de sortie et retourner des valeurs deviennent disponibles lorsque **SQLMoreResults** retourne SQL_NO_DATA.  
  
 Toutes les liaisons qui ont été établies pour le résultat précédent, définissez toujours restent valides. Si les structures de colonne sont différents pour ce jeu de résultats, puis en appelant **SQLFetch** ou **SQLFetchScroll** peut entraîner une erreur ou troncation. Pour éviter ce problème, l’application doit appeler **SQLBindCol** explicitement relier comme il convient (ou faire en définissant les champs de descripteur). Vous pouvez également l’application peut appeler **SQLFreeStmt** avec un *Option* de SQL_UNBIND pour séparer les tampons de colonnes.  
  
 Les valeurs des attributs d’instruction, telles que le type de curseur, accès concurrentiel au curseur, taille de jeu de clés ou longueur maximale, peuvent changer, comme l’application parcourt le lot par les appels à **SQLMoreResults**. Si cela se produit, **SQLMoreResults** retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01 s 02 (la valeur de l’Option a changé).  
  
 Appel **SQLCloseCursor**, ou **SQLFreeStmt** avec un *Option* de SQL_CLOSE, ignore tous les jeux de résultats et les nombres de lignes qui étaient disponibles à la suite de l’exécution de le lot. Le descripteur d’instruction retourne à l’état alloué ou préparé. Appel **SQLCancel** pour annuler une fonction de façon asynchrone en cours d’exécution lorsqu’un lot a été exécuté et le descripteur d’instruction est exécutée, curseur positionné ou état asynchrone des résultats dans les résultats de tous les jeux et le nombre de lignes généré par le lot est ignoré si l’appel d’annulation a réussi. L’instruction retourne ensuite à l’état alloué ou préparé.  
  
 Si un lot d’instructions ou d’une procédure combine des autres instructions SQL avec **sélectionnez**, **mise à jour**, **insérer**, et **supprimer** instructions, ces autres instructions n’affectent pas **SQLMoreResults**.  
  
 Pour plus d’informations, consultez [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Si une recherche update, insert ou delete, instruction dans un lot d’instructions n’affecte pas toutes les lignes à la source de données **SQLMoreResults** retourne SQL_SUCCESS. Cela est différent du cas d’une mise à jour recherchée, insérer ou supprimer l’instruction est exécutée via **SQLExecDirect**, **SQLExecute**, ou **SQLParamData**, qui Retourne SQL_NO_DATA si elle n’affecte pas toutes les lignes à la source de données. Si une application appelle **SQLRowCount** pour récupérer le nombre de lignes après un appel à **SQLMoreResults** n’a pas affecté aucune ligne, **SQLRowCount** retourne SQL_NO_DATA.  
  
 Pour plus d’informations sur la mise en séquence valide de fonctions de traitement des résultats, consultez [annexe b : Tableaux des transitions d’état ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Pour plus d’informations sur les SQL_PARAM_DATA_AVAILABLE et les paramètres de sortie diffusées en continu, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="availability-of-row-counts"></a>Disponibilité des nombres de lignes  
 Lorsqu’un lot contient plusieurs instructions de génération de nombre de lignes consécutives, il est possible que ces nombres de lignes soient restaurées en nombre de lignes qu’une seule. Par exemple, si un lot contient cinq instructions insert, certaines sources de données est capables de retourner des cinq nombres de lignes individuelles. Certaines autres sources de données retournent le nombre qu’une seule ligne qui représente la somme des nombres de lignes individuelles cinq.  
  
 Lorsqu’un lot contienne une combinaison d’instructions de génération de nombre de lignes et de génération de jeu de résultats, nombre de lignes peut ou ne peut pas être disponibles à tout. Le comportement du pilote en ce qui concerne la disponibilité des nombres de lignes est énuméré dans le type d’information SQL_BATCH_ROW_COUNT disponible via un appel à **SQLGetInfo**. Par exemple, supposons que le lot contient un **sélectionnez**, suivie de deux **insérer**s et l’autre **sélectionnez**. Ensuite, les cas suivants sont possibles :  
  
-   Le nombre de lignes correspondant aux deux **insérer** instructions ne sont pas disponibles du tout. Le premier appel à **SQLMoreResults** sera vous positionner sur le jeu de résultats de la deuxième **sélectionnez** instruction.  
  
-   Le nombre de lignes correspondant aux deux **insérer** instructions sont disponibles individuellement. (Un appel à **SQLGetInfo** ne retourne pas le bit SQL_BRC_ROLLED_UP SQL_BATCH_ROW_COUNT type d’informations.) Le premier appel à **SQLMoreResults** vous placer sur le nombre de lignes de la première **insérer**, et le deuxième appel vous placer sur le nombre de lignes du deuxième **insérer**. Le troisième appel **SQLMoreResults** sera vous positionner sur le jeu de résultats de la deuxième **sélectionnez** instruction.  
  
-   Le nombre de lignes correspondant aux deux **insère** sont ajoutées à un nombre de lignes unique qui est disponible. (Un appel à **SQLGetInfo** retourne le SQL_BRC_ROLLED_UP bit SQL_BATCH_ROW_COUNT type d’informations.) Le premier appel à **SQLMoreResults** vous placer sur le nombre de lignes de cumul de données et le deuxième appel à **SQLMoreResults** sera vous positionner sur le jeu de résultats de la deuxième **sélectionnez**.  
  
 Certains pilotes à disposition des nombres de lignes uniquement pour les lots explicites et pas pour les procédures stockées.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll, fonction](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|L’extraction d’une seule ligne ou un bloc de données dans une direction avant uniquement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|L’extraction de tout ou partie d’une colonne de données|[SQLGetData, fonction](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Récupération des paramètres de sortie à l’aide de SQLGetData ](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
