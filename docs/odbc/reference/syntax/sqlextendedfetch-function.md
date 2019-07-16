---
title: SQLExtendedFetch, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExtendedFetch
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExtendedFetch
helpviewer_keywords:
- SQLExtendedFetch function [ODBC]
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce4bd75b2a1ffac44b14c9906e669421d55888c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003079"
---
# <a name="sqlextendedfetch-function"></a>SQLExtendedFetch, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : Déconseillé  
  
 **Résumé**  
 **SQLExtendedFetch** extrait l’ensemble spécifié de lignes de données du jeu de résultats et retourne les données pour toutes les colonnes liées. Ensembles de lignes peut être spécifié à une position relative ou absolue ou par signet.  
  
> [!NOTE]
>  Dans ODBC 3 *.x*, **SQLExtendedFetch** a été remplacé par **SQLFetchScroll**. ODBC 3 *.x* applications ne doivent pas appeler **SQLExtendedFetch**; au lieu de cela, ils doivent appeler **SQLFetchScroll**. Le Gestionnaire de pilotes mappe **SQLFetchScroll** à **SQLExtendedFetch** lorsque vous travaillez avec un ODBC 2 *.x* pilote. ODBC 3 *.x* pilotes doivent prendre en charge **SQLExtendedFetch** s’ils souhaitent travailler avec ODBC 2 *.x* les applications qui l’appellent. Pour plus d’informations, consultez « Commentaires » et [curseurs de bloc, curseurs avec défilement et compatibilité descendante](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) dans g : annexe Instructions de pilote pour la compatibilité descendante.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLExtendedFetch(  
      SQLHSTMT         StatementHandle,  
      SQLUSMALLINT     FetchOrientation,  
      SQLLEN           FetchOffset,  
      SQLULEN *        RowCountPtr,  
      SQLUSMALLINT *   RowStatusArray);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
 *FetchOrientation*  
 [Entrée] Type d’extraction. Cela est identique à *FetchOrientation* dans **SQLFetchScroll**.  
  
 *FetchOffset*  
 [Entrée] Numéro de la ligne à récupérer. Cela est identique à *FetchOffset* dans **SQLFetchScroll**, à une exception près. Lorsque *FetchOrientation* est SQL_FETCH_BOOKMARK, *FetchOffset* est un signet de longueur fixe, pas un décalage à partir d’un signet. En d’autres termes, **SQLExtendedFetch** récupère le signet à partir de cet argument, pas l’attribut d’instruction SQL_ATTR_FETCH_BOOKMARK_PTR. Il ne prend pas en charge les signets de longueur variable et ne prend pas en charge l’extraction d’un ensemble de lignes à un offset (autre que 0) à partir d’un signet.  
  
 *RowCountPtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre de lignes réellement extraites. Cette mémoire tampon est utilisé dans la même manière que la mémoire tampon spécifiée par l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR. Cette mémoire tampon est utilisé uniquement par **SQLExtendedFetch**. Il n’est pas utilisé par **SQLFetch** ou **SQLFetchScroll**.  
  
 *RowStatusArray*  
 [Sortie] Pointeur vers un tableau dans lequel retourner l’état de chaque ligne. Ce tableau est utilisé dans la même manière que le tableau spécifié par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR.  
  
 Toutefois, l’adresse de ce tableau n’est pas stockée dans le champ SQL_DESC_STATUS_ARRAY_PTR dans le descripteur IRD. En outre, ce tableau est utilisé uniquement par **SQLExtendedFetch** et par **SQLBulkOperations** avec un *opération* de SQL_ADD ou **SQLSetPos**lorsqu’elle est appelée après **SQLExtendedFetch**. Il n’est pas utilisé par **SQLFetch** ou **SQLFetchScroll**, et il n’est pas utilisé par **SQLBulkOperations** ou **SQLSetPos** lorsqu’elles sont appelées après **SQLFetch** ou **SQLFetchScroll**. Il est également utilisé lorsque **SQLBulkOperations** avec un *opération* SQL_ADD est appelé avant l’appel de n’importe quelle fonction d’extraction. En d’autres termes, il est utilisé uniquement dans l’état de l’instruction S7. Il n’est pas utilisé dans les États d’instruction S5 ou S6. Pour plus d’informations, consultez [Transitions d’instruction](../../../odbc/reference/appendixes/statement-transitions.md) dans l’annexe b : Tableaux des transitions d’état ODBC.  
  
 Applications doivent fournir un pointeur valide dans le *RowStatusArray* argument ; si ce n’est pas, le comportement de **SQLExtendedFetch** et le comportement des appels à **SQLBulkOperations**ou **SQLSetPos** une fois un curseur a été placé par **SQLExtendedFetch** ne sont pas définis.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLExtendedFetch** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLError**. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLExtendedFetch** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire. Si une erreur se produit sur une colonne unique, **SQLGetDiagField** peut être appelée avec un *DiagIdentifier* de SQL_DIAG_COLUMN_NUMBER pour déterminer la colonne de l’erreur s’est produite sur ; et  **SQLGetDiagField** peut être appelée avec un *DiagIdentifier* de SQL_DIAG_ROW_NUMBER pour déterminer la ligne qui contient cette colonne.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|Données de chaîne ou binaire retournées pour une colonne a entraîné la troncation des caractères non vides ou non NULL des données binaires. S’il s’agissait d’une valeur de chaîne, il a été tronquée à droite. S’il s’agissait d’une valeur numérique, la partie fractionnaire du nombre a été tronquée.  (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S01|Erreur de ligne|Une erreur s’est produite lors de l’extraction d’une ou plusieurs lignes. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S06|Tentative d’extraction avant que le jeu de résultats renvoyé le premier ensemble de lignes|L’ensemble de lignes demandé avec chevauchement le début du jeu de résultats si la position actuelle a été au-delà de la première ligne et soit *FetchOrientation* a été SQL_PRIOR ou *FetchOrientation* a été SQL_RELATIVE avec un négatif *FetchOffset* dont la valeur absolue est inférieure ou égale à la SQL_ROWSET_SIZE actuel. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S07|Troncation fractionnelle|Les données retournées pour une colonne a été tronquées. Types de données numériques, la partie fractionnaire du nombre ont été tronquée. Pour heure, timestamp et les types de données interval contenant un composant au moment, la partie fractionnaire du temps a été tronquée.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation de l’attribut de type de données restreint|Une valeur de données n’a pas pu être convertie au type de données C spécifié par *TargetType* dans **SQLBindCol**.|  
|07009|Index de descripteur non valide|La colonne 0 a été liée avec **SQLBindCol**, et l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS était définie sur SQL_UB_OFF.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|22002|Variable indicateur requise mais non fournie|Données de type NULL a été récupérées dans une colonne dont la propriété *StrLen_or_IndPtr* définie par **SQLBindCol** était un pointeur null.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|22003|Valeur numérique hors limites|Retourner la valeur numérique (comme numérique ou chaîne) pour une ou plusieurs colonnes aurait entraîné la partie entière (par opposition à fractionnaire) du nombre à tronquer.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)<br /><br /> Pour plus d’informations, consultez [instructions pour l’intervalle et des Types de données numériques](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md) dans l’annexe d : Types de données.|  
|22007|Format datetime non valide|Une colonne de type caractère dans le jeu de résultats a été liée à une date, d’une heure ou d’une structure d’horodateur C, et une valeur dans la colonne a été, respectivement, une date non valide, une heure ou un horodatage.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|22012|Division par zéro|Une valeur à partir d’une expression arithmétique a été retournée, ce qui a entraîné de division par zéro.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|22015|Dépassement du champ Intervalle|Affectation d’une valeur numérique exacte ou d’intervalle de type SQL à un type d’intervalle C a provoqué une perte de chiffres significatifs dans le champ Début.<br /><br /> Lors de la récupération des données à un type d’intervalle C, il n’a aucune représentation de la valeur du type SQL dans le type d’intervalle C.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|22018|Valeur de caractère non valide pour la spécification de la casse|Le type C était une valeur numérique exact ou approximatif, une valeur datetime ou un type de données d’intervalle ; le type SQL de la colonne a un type de données caractère ; et la valeur dans la colonne n’est pas un littéral valid du type C lié.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|24000|État de curseur non valide|Le *au paramètre StatementHandle* était dans un état exécuté, mais aucun jeu de résultats a été associé le *au paramètre StatementHandle*.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLError** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*, puis la fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLExtendedFetch** fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) spécifié *au paramètre StatementHandle* n’était pas dans un état d’exécution. La fonction a été appelée sans préalablement appeler **SQLExecDirect**, **SQLExecute**, ou une fonction de catalogue.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) **SQLExtendedFetch** a été appelé pour le *au paramètre StatementHandle* après **SQLFetch** ou **SQLFetchScroll** a été appelée et avant  **SQLFreeStmt** a été appelée avec l’option SQL_CLOSE.<br /><br /> (DM) **SQLBulkOperations** a été appelée pour une instruction avant **SQLFetch**, **SQLFetchScroll**, ou **SQLExtendedFetch** a été appelée, et puis **SQLExtendedFetch** a été appelé avant **SQLFreeStmt** a été appelée avec l’option SQL_CLOSE.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY106|Type de récupération hors plage|(DM) la valeur spécifiée pour l’argument *FetchOrientation* n’était pas valide. (Voir « Commentaires ».)<br /><br /> L’argument *FetchOrientation* a été SQL_FETCH_BOOKMARK, et l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS était définie sur SQL_UB_OFF.<br /><br /> La valeur de l’option d’instruction SQL_CURSOR_TYPE était SQL_CURSOR_FORWARD_ONLY et la valeur d’argument *FetchOrientation* n’était pas SQL_FETCH_NEXT.<br /><br /> L’argument *FetchOrientation* a été SQL_FETCH_RESUME.|  
|HY107|Valeur de ligne hors limites|La valeur spécifiée avec l’option d’instruction SQL_CURSOR_TYPE était SQL_CURSOR_KEYSET_DRIVEN, mais la valeur spécifiée avec l’attribut d’instruction SQL_KEYSET_SIZE était supérieur à 0 et inférieur à la valeur spécifiée avec l’attribut d’instruction SQL_ROWSET_SIZE .|  
|HY111|Valeur de signet non valide|L’argument *FetchOrientation* a été SQL_FETCH_BOOKMARK, et le signet spécifié dans le *FetchOffset* argument n’était pas valide.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|Pilote ou la source de données ne prend pas en charge le type d’extraction spécifié.<br /><br /> La source de données ou le pilote ne prend pas en charge la conversion spécifiée par la combinaison de la *TargetType* dans **SQLBindCol** et le type de données SQL de la colonne correspondante. Cette erreur s’applique uniquement lorsque le type de données SQL de la colonne a été mappé à un type de données spécifiques au pilote SQL.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant que la source de données a retourné le jeu de résultats. Le délai d’expiration est défini via **SQLSetStmtOption**, SQL_QUERY_TIMEOUT.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Le comportement de **SQLExtendedFetch** est identique à celle de **SQLFetchScroll**, avec les exceptions suivantes :  
  
-   **SQLExtendedFetch** et **SQLFetchScroll** utiliser différentes méthodes pour retourner le nombre de lignes extraites. **SQLExtendedFetch** retourne le nombre de lignes extraites dans  *\*RowCountPtr*; **SQLFetchScroll** retourne le nombre de lignes extraites directement à la mémoire tampon vers laquelle pointée SQL_ATTR_ROWS_FETCHED_PTR. Pour plus d’informations, consultez le *RowCountPtr* argument.  
  
-   **SQLExtendedFetch** et **SQLFetchScroll** retourner l’état de chaque ligne dans plusieurs groupes différents. Pour plus d’informations, consultez le *RowStatusArray* argument.  
  
-   **SQLExtendedFetch** et **SQLFetchScroll** utiliser différentes méthodes pour récupérer le signet lorsque *FetchOrientation* est SQL_FETCH_BOOKMARK. **SQLExtendedFetch** ne prend pas en charge les signets de longueur variable ou de la récupération des ensembles de lignes à un offset différent de 0 à partir d’un signet. Pour plus d’informations, consultez le *FetchOffset* argument.  
  
-   **SQLExtendedFetch** et **SQLFetchScroll** utiliser l’ensemble de lignes de différentes tailles. **SQLExtendedFetch** utilise la valeur de l’attribut d’instruction SQL_ROWSET_SIZE, et **SQLFetchScroll** utilise la valeur de l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE.  
  
-   **SQLExtendedFetch** a légèrement différente erreur sémantique que de gestion des **SQLFetchScroll**. Pour plus d’informations, consultez « Gestion des erreurs » dans la section « Remarques » de [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
-   **SQLExtendedFetch** ne prend pas en charge les décalages des liaisons (l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR).  
  
-   Les appels à **SQLExtendedFetch** ne peut pas être combinée avec les appels à **SQLFetch** ou **SQLFetchScroll**et si **SQLBulkOperations** est appelée avant d’appeler n’importe quelle fonction d’extraction, **SQLExtendedFetch** ne peut pas être appelée jusqu'à ce que le curseur est fermé et rouvert. Autrement dit, **SQLExtendedFetch** peut être appelée uniquement dans l’état de l’instruction S7. Pour plus d’informations, consultez [Transitions d’instruction](../../../odbc/reference/appendixes/statement-transitions.md) dans l’annexe b : Tableaux des transitions d’état ODBC.  
  
 Lorsqu’une application appelle **SQLFetchScroll** lors de l’utilisation d’une API ODBC 2 *.x* pilote, le Gestionnaire de pilotes est mappé à cet appel à **SQLExtendedFetch**. Pour plus d’informations, consultez « SQLFetchScroll et ODBC 2 *.x* pilotes » dans [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 Dans ODBC 2 *.x*, **SQLExtendedFetch** a été appelé pour extraire plusieurs lignes et **SQLFetch** a été appelé pour extraire une seule ligne. Dans ODBC 3 *.x*, quant à eux, **SQLFetch** peut être appelé pour extraire plusieurs lignes.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à une colonne dans un jeu de résultats|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Exécution d’instruction bulk insert, update ou opérations de suppression|[SQLBulkOperations, fonction](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Retour d’informations sur une colonne dans un jeu de résultats|[SQLDescribeCol, fonction](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|L’exécution d’une instruction SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécuter une instruction SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Définie les colonnes de retour du nombre de résultats|[SQLNumResultCols, fonction](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionnement du curseur, l’actualisation des données dans l’ensemble de lignes, ou la mise à jour ou suppression de données dans le jeu de résultats|[SQLSetPos, fonction](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Définition d’un attribut d’instruction|[SQLSetStmtAttr, fonction](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
