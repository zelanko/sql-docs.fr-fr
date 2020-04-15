---
title: Fonction SQLMoreResults (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78bbb277e4b783eb46c79f59939a1080feae2b60
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304740"
---
# <a name="sqlmoreresults-function"></a>Fonction SQLMoreResults
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLMoreResults** détermine si d’autres résultats sont disponibles sur une déclaration contenant **SELECT**, **UPDATE**, **INSERT**, ou **DELETE** déclarations et, si oui, initialise le traitement de ces résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE, ou SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLMoreResults** revient SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLMoreResults** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S02|La valeur de l’option a changé|La valeur d’un attribut de déclaration a changé au fur et à mesure que le lot était en cours de traitement. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction **SQLMoreResults** a été appelée et, avant d’être exécutée, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Ensuite, la fonction **SQLMoreResults** a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction **SQLMoreResults** a été appelée et, avant d’être exécutée, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLMoreResults** a été appelée.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **Les** énoncés SELECT retournent les ensembles de résultats. **UPDATE**, **INSERT**, et les déclarations **DELETE** renvoient un compte de lignes affectées. Si l’un de ces relevés est en lots, soumis avec des tableaux de paramètres (numérotés dans l’ordre de paramètres croissants, dans l’ordre qu’ils apparaissent dans le lot), ou dans les procédures, ils peuvent retourner plusieurs ensembles de résultats ou des nombres de lignes. Pour plus d’informations sur les lots d’énoncés et de tableaux de paramètres, voir [Lots of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md) and [Arrays of Parameter Values](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Après l’exécution du lot, l’application est positionnée sur le premier ensemble de résultats. L’application peut appeler **SQLBindCol**, **SQLBulkOperations**, **SQLFetch**, **SQLGetData**, **SQLFetchScroll**, **SQLSetPos**, et toutes les fonctions de métadonnées, sur les premiers ou les ensembles de résultats suivants, tout comme il le ferait s’il n’y avait qu’un seul ensemble de résultats. Une fois qu’il est fait avec le premier ensemble de résultats, l’application appelle **SQLMoreResults** pour passer à l’ensemble de résultat suivant. Si un autre ensemble de résultats ou de comptage est disponible, **SQLMoreResults** retourne SQL_SUCCESS et initialise l’ensemble de résultats ou le compte pour un traitement supplémentaire. Si des relevés générateurs de nombres de lignes apparaissent entre les énoncés générateurs de résultats, ils peuvent être dépassés en appelant **SQLMoreResults**. Après avoir appelé **SQLMoreResults** pour **UPDATE**, **INSERT**, ou **DELETE** déclarations, une application peut appeler **SQLRowCount**.  
  
 S’il y avait un résultat actuel défini avec des lignes non verrouillées, **SQLMoreResults** rejette cet ensemble de résultats et rend le prochain ensemble de résultats ou compte disponible. Si tous les résultats ont été traités, **SQLMoreResults** retourne SQL_NO_DATA. Pour certains conducteurs, les paramètres de sortie et les valeurs de retour ne sont pas disponibles tant que tous les ensembles de résultats et les nombres de lignes n’ont pas été traités. Pour ces conducteurs, les paramètres de sortie et les valeurs de retour deviennent disponibles lorsque **SQLMoreResults** revient SQL_NO_DATA.  
  
 Toute fixation établie pour le résultat précédent demeure valable. Si les structures de colonne sont différentes pour cet ensemble de résultats, alors appeler **SQLFetch** ou **SQLFetchScroll** peut entraîner une erreur ou une troncation. Pour éviter cela, l’application doit appeler **SQLBindCol** pour se rebiner explicitement le cas échéant (ou le faire en fixant des champs descripteur). Alternativement, l’application peut appeler **SQLFreeStmt** avec une *option* de SQL_UNBIND pour délier tous les tampons de colonne.  
  
 Les valeurs des attributs de déclaration, telles que le type de curseur, la concurrence de curseur, la taille de l’ensemble de clés, ou la longueur maximale, peuvent changer pendant que l’application navigue à travers le lot par des appels à **SQLMoreResults**. Si cela se produit, **SQLMoreResults** retournera SQL_SUCCESS_WITH_INFO et SQLSTATE 01S02 (la valeur de l’option a changé).  
  
 Appeler **SQLCloseCursor**, ou **SQLFreeStmt** avec une *option* de SQL_CLOSE, écarte tous les ensembles de résultats et les nombres de rangées qui étaient disponibles à la suite de l’exécution du lot. La poignée de la déclaration revient à l’état alloué ou préparé. Appeler **SQLCancel** pour annuler une fonction d’exécution asynchrone lorsqu’un lot a été exécuté et que la poignée de déclaration se trouve dans l’état exécuté, placé par le curseur ou asynchrone, dans tous les ensembles de résultats et les dénombrements de ligne générés par le lot étant jetés si l’appel d’annulation a été réussi. La déclaration retourne ensuite à l’état préparé ou attribué.  
  
 Si un lot d’instructions ou une procédure mélange d’autres déclarations SQL avec **SELECT**, **UPDATE**, **INSERT**, et les déclarations **DELETE,** ces autres déclarations n’affectent pas **SQLMoreResults**.  
  
 Pour plus d’informations, voir [Résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Si une mise à jour, un insérer ou supprimer une déclaration dans un lot d’instructions n’affecte aucune ligne à la source de données, **SQLMoreResults** retourne SQL_SUCCESS. Ceci est différent du cas d’une mise à jour recherchée, d’insérer ou de supprimer la déclaration qui est exécutée par **SQLExecDirect**, **SQLExecute**, ou **SQLParamData**, qui retourne SQL_NO_DATA si elle n’affecte aucune ligne à la source de données. Si une demande appelle **SQLRowCount** pour récupérer le nombre de rangées après qu’un appel à **SQLMoreResults** n’ait affecté aucune ligne, **SQLRowCount** retournera SQL_NO_DATA.  
  
 Pour plus d’informations sur le séquençage valide des fonctions de traitement des résultats, voir [Annexe B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Pour plus d’informations sur SQL_PARAM_DATA_AVAILABLE et les paramètres de sortie en streaming, voir [Les paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="availability-of-row-counts"></a>Disponibilité des comptes de ligne  
 Lorsqu’un lot contient plusieurs relevés consécutifs générateurs de nombres de lignes, il est possible que ces nombres de lignes soient enroulés en un seul nombre de lignes. Par exemple, si un lot comporte cinq énoncés d’insertion, certaines sources de données sont capables de retourner cinq dénombrements individuels de lignes. Certaines autres sources de données ne renvoient qu’un seul nombre de lignes qui représente la somme des cinq rangs individuels.  
  
 Lorsqu’un lot contient une combinaison d’instructions génératrices de résultats et de comptage des lignes, le nombre de lignes peut ou non être disponible du tout. Le comportement du conducteur en ce qui concerne la disponibilité des dénombrements de lignes est énuméré dans le type d’information SQL_BATCH_ROW_COUNT disponible par un appel à **SQLGetInfo**. Supposons, par exemple, que le lot contient un **SELECT**, suivi de deux **INSERT**s et un autre **SELECT**. Ensuite, les cas suivants sont possibles :  
  
-   Les nombres de lignes correspondant aux deux relevés **INSERT** ne sont pas du tout disponibles. Le premier appel à **SQLMoreResults** vous positionnera sur l’ensemble de résultat de la deuxième déclaration **SELECT.**  
  
-   Les nombres de lignes correspondant aux deux relevés **INSERT** sont disponibles individuellement. (Un appel à **SQLGetInfo** ne renvoie pas le SQL_BRC_ROLLED_UP peu pour le type d’information SQL_BATCH_ROW_COUNT.) Le premier appel à **SQLMoreResults** vous positionnera sur le nombre de rangées du premier **INSERT**, et le deuxième appel vous positionnera sur le nombre de rangées du second **INSERT**. Le troisième appel à **SQLMoreResults** vous positionnera sur l’ensemble de résultat de la deuxième déclaration **SELECT.**  
  
-   Les nombres de lignes correspondant aux deux **INSERT** sont enroulés en un seul nombre de lignes disponibles. (Un appel à **SQLGetInfo** renvoie le SQL_BRC_ROLLED_UP peu pour le type d’information SQL_BATCH_ROW_COUNT.) Le premier appel à **SQLMoreResults** vous positionnera sur le nombre de rangées enroulées, et le deuxième appel à **SQLMoreResults** vous positionnera sur l’ensemble de résultat de la deuxième **SELECT**.  
  
 Certains conducteurs rendent les dénombrements de rangées disponibles uniquement pour les lots explicites et non pour les procédures stockées.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Aller chercher une seule rangée ou un bloc de données dans une direction avant-seulement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Aller chercher une partie ou la totalité d’une colonne de données|[Fonction SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
