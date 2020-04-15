---
title: Fonction SQLExtendedFetch (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExtendedFetch
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLExtendedFetch
helpviewer_keywords:
- SQLExtendedFetch function [ODBC]
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dc832e5a20b1d3c0a1ad63b3e2a070563de2b46d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285979"
---
# <a name="sqlextendedfetch-function"></a>SQLExtendedFetch, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: Deprecated  
  
 **Résumé**  
 **SQLExtendedFetch** récupère le jeu de données spécifiés à partir de l’ensemble de résultats et renvoie les données pour toutes les colonnes liées. Les jeux de lignes peuvent être spécifiés à une position absolue ou relative ou par signet.  
  
> [!NOTE]
>  Dans ODBC 3 *.x*, **SQLExtendedFetch** a été remplacé par **SQLFetchScroll**. Les applications ODBC 3 *.x* ne doivent pas appeler **SQLExtendedFetch;** au lieu de cela, ils devraient appeler **SQLFetchScroll**. Le gestionnaire de chauffeur cartographie **SQLFetchScroll** à **SQLExtendedFetch** lorsqu’il travaille avec un conducteur ODBC 2 *.x.* Les conducteurs de 3 *.x* D’ODBC devraient prendre en charge **SQLExtendedFetch** s’ils veulent travailler avec des applications ODBC 2 *.x* qui l’appellent. Pour plus d’informations, voir " Commentaires " et [Cursesors de bloc, Curseurs défilants et Compatibilité vers l’arrière](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) dans l’annexe G : Lignes directrices de pilote pour la compatibilité vers l’arrière.  
  
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
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Allerorienter*  
 [Entrée] Type d’aller chercher. C’est la même chose que *FetchOrientation* dans **SQLFetchScroll**.  
  
 *AllerOffset (en)*  
 [Entrée] Nombre de la rangée à aller chercher. C’est la même chose que *FetchOffset* dans **SQLFetchScroll**, à une exception près. Lorsque *FetchOrientation* est SQL_FETCH_BOOKMARK, *FetchOffset* est un signet fixe, et non un décalage à partir d’un signet. En d’autres termes, **SQLExtendedFetch** récupère le signet de cet argument, et non l’attribut SQL_ATTR_FETCH_BOOKMARK_PTR déclaration. Il ne prend pas en charge les signets à longueur variable et ne prend pas en charge la récupération d’un acart à un décalage (autre que 0) à partir d’un signet.  
  
 *RowCountPtr RowCountPtr RowCountPtr RowCount*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre de lignes effectivement récupéré. Ce tampon est utilisé de la même manière que le tampon spécifié par l’attribut SQL_ATTR_ROWS_FETCHED_PTR déclaration. Ce tampon n’est utilisé que par **SQLExtendedFetch**. Il n’est pas utilisé par **SQLFetch** ou **SQLFetchScroll**.  
  
 *RowStatusArray RowStatusArray*  
 [Sortie] Pointeur vers un tableau dans lequel retourner le statut de chaque rangée. Ce tableau est utilisé de la même manière que le tableau spécifié par l’attribut SQL_ATTR_ROW_STATUS_PTR déclaration.  
  
 Cependant, l’adresse de ce tableau n’est pas stockée dans le champ SQL_DESC_STATUS_ARRAY_PTR dans l’IRD. De plus, ce tableau n’est utilisé que par **SQLExtendedFetch** et par **SQLBulkOperations** avec une *opération* de SQL_ADD ou **SQLSetPos** lorsqu’il est appelé d’après **SQLExtendedFetch**. Il n’est pas utilisé par **SQLFetch** ou **SQLFetchScroll**, et il n’est pas utilisé par **SQLBulkOperations** ou **SQLSetPos** quand ils sont appelés après **SQLFetch** ou **SQLFetchScroll**. Il n’est pas non plus utilisé lorsque **SQLBulkOperations** avec une *opération* de SQL_ADD est appelé avant toute fonction d’aller chercher est appelé. En d’autres termes, il n’est utilisé que dans l’état de déclaration S7. Il n’est pas utilisé dans les états de déclaration S5 ou S6. Pour plus d’informations, voir [Transitions d’énoncés](../../../odbc/reference/appendixes/statement-transitions.md) à l’annexe B : Tableaux de transition d’État ODBC.  
  
 Les demandes doivent fournir un pointeur valide dans l’argument *RowStatusArray;* sinon, le comportement de **SQLExtendedFetch** et le comportement des appels à **SQLBulkOperations** ou **SQLSetPos** après qu’un curseur a été positionné par **SQLExtendedFetch** sont indéfinis.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLExtendedFetch** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLError**. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLExtendedFetch** et explique chacune dans le contexte de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire. Si une erreur se produit sur une seule colonne, **SQLGetDiagField** peut être appelé avec un *DiagIdentificateur* de SQL_DIAG_COLUMN_NUMBER pour déterminer la colonne sur lequel l’erreur s’est produite; et **SQLGetDiagField** peut être appelé avec un *DiagIdentificateur* de SQL_DIAG_ROW_NUMBER pour déterminer la rangée contenant cette colonne.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Les données de chaîne ou binaires retournées pour une colonne ont abouti à la troncation de caractère non-blank ou de données binaires non-NULL. Si c’était une valeur de chaîne, il était juste-tronqué. S’il s’agissait d’une valeur numérique, la fraction du nombre a été tronquée.  (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S01|Erreur dans la rangée|Une erreur s’est produite en allant chercher une ou plusieurs rangées. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S06|Tentative d’aller chercher avant le jeu de résultat retourné le premier rowset|Le jeu de ligne demandé chevauchait le début de l’ensemble de résultats lorsque la position actuelle était au-delà de la première rangée, et soit *FetchOrientation* a été SQL_PRIOR ou *FetchOrientation* a été SQL_RELATIVE avec un *FetchOffset* négatif dont la valeur absolue était inférieure ou égale à la SQL_ROWSET_SIZE actuelle. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S07|Troncation fractionnaire|Les données retournées pour une colonne ont été tronquées. Pour les types de données numériques, la partie fractionnaire du nombre a été tronquée. Pour le temps, l’humidité du temps et les types de données d’intervalle contenant un composant de temps, la partie fractionnelle du temps a été tronquée.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|Une valeur de données n’a pas pu être convertie au type de données C spécifié par *TargetType* dans **SQLBindCol**.|  
|07009|Indice descripteur invalide|La colonne 0 était reliée à **SQLBindCol**, et l’attribut de déclaration SQL_ATTR_USE_BOOKMARKS a été réglé pour SQL_UB_OFF.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|22002|Variable d’indicateur requise mais non fournie|Les données de NULL ont été récupérées dans une colonne dont *le StrLen_or_IndPtr* établi par **SQLBindCol** était un pointeur nul.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|22003|Valeur numérique hors de portée|Le retour de la valeur numérique (en tant que numérique ou chaîne) pour une ou plusieurs colonnes aurait fait tronquer la partie entière (par opposition à fractionnelle) du nombre.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)<br /><br /> Pour plus d’informations, consultez [Les lignes directrices pour les types d’intervalle et de données numériques](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md) à l’annexe D : Types de données.|  
|22007|Format de date invalide|Une colonne de caractère dans l’ensemble de résultat était liée à une structure de date, d’heure ou de timetamp C, et une valeur dans la colonne était, respectivement, une date, un heure ou un fuseur horaires non valides.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|22012|Division par zéro|Une valeur d’une expression arithmétique a été retournée, ce qui a entraîné une division par zéro.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|22015|Débordement de champ d’intervalle|L’attribution d’un type SQL numérique ou d’intervalle exact à un type d’intervalle C a causé une perte de chiffres significatifs dans le champ principal.<br /><br /> Lorsque vous adz des données à un type d’intervalle C, il n’y avait aucune représentation de la valeur du type SQL dans le type d’intervalle C.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|Le type C était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type SQL de la colonne était un type de données de caractère; et la valeur de la colonne n’était pas un littéral valide du type C lié.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|24 000|État de curseur non valide|Le *StatementHandle* était dans un état exécuté, mais aucun ensemble de résultat n’a été associé à la *StatementHandle*.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLError** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*, puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLExtendedFetch** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Le *statementhandle* spécifié n’était pas dans un état exécuté. La fonction a été appelée sans appeler **d’abord SQLExecDirect**, **SQLExecute**, ou une fonction de catalogue.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) **SQLExtendedFetch** a été appelé pour le *StatementHandle* après **SQLFetch** ou **SQLFetchScroll** a été appelé et avant **SQLFreeStmt** a été appelé avec l’option SQL_CLOSE.<br /><br /> (DM) **SQLBulkOperations** a été appelé pour une déclaration avant **SQLFetch**, **SQLFetchScroll**, ou **SQLExtendedFetch** a été appelé, puis **SQLExtendedFetch** a été appelé avant **SQLFreeStmt** a été appelé avec l’option SQL_CLOSE.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY106|Aller type hors de portée|(DM) La valeur spécifiée pour l’argument *FetchOrientation était invalide.* (Voir "Commentaires.")<br /><br /> L’argument *FetchOrientation* était SQL_FETCH_BOOKMARK, et l’attribut de déclaration SQL_ATTR_USE_BOOKMARKS a été mis à SQL_UB_OFF.<br /><br /> La valeur de l’option de déclaration SQL_CURSOR_TYPE était SQL_CURSOR_FORWARD_ONLY, et la valeur de l’argument *FetchOrientation* n’était pas SQL_FETCH_NEXT.<br /><br /> L’argument *FetchOrientation* était SQL_FETCH_RESUME.|  
|HY107|Valeur de la ligne hors de portée|La valeur spécifiée avec l’option SQL_CURSOR_TYPE énoncé était SQL_CURSOR_KEYSET_DRIVEN, mais la valeur spécifiée avec l’attribut de l’SQL_KEYSET_SIZE énoncé était supérieure à 0 et inférieure à la valeur spécifiée avec l’attribut SQL_ROWSET_SIZE déclaration.|  
|HY111|Valeur de signet invalide|L’argument *FetchOrientation* était SQL_FETCH_BOOKMARK, et le signet spécifié dans l’argument *de FetchOffset* n’était pas valide.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données ne prend pas en charge le type d’aller chercher spécifié.<br /><br /> Le conducteur ou la source de données ne prend pas en charge la conversion spécifiée par la combinaison du *TargetType* dans **SQLBindCol** et le type de données SQL de la colonne correspondante. Cette erreur ne s’applique que lorsque le type de données SQL de la colonne a été cartographié à un type de données SQL spécifique au conducteur.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtOption**, SQL_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Le comportement de **SQLExtendedFetch** est identique à celui de **SQLFetchScroll**, à quelques exceptions près :  
  
-   **SQLExtendedFetch** et **SQLFetchScroll** utilisent différentes méthodes pour retourner le nombre de rangées récupérées. **SQLExtendedFetch** retourne le nombre de rangées récupérées dans * \*RowCountPtr;* **SQLFetchScroll** renvoie le nombre de rangées récupérées directement à la mémoire tampon indiquée par SQL_ATTR_ROWS_FETCHED_PTR. Pour plus d’informations, voir l’argument *RowCountPtr.*  
  
-   **SQLExtendedFetch** et **SQLFetchScroll** retournent le statut de chaque rangée dans différents tableaux. Pour plus d’informations, voir l’argument *RowStatusArray.*  
  
-   **SQLExtendedFetch** et **SQLFetchScroll** utilisent différentes méthodes pour récupérer le signet lorsque *FetchOrientation* est SQL_FETCH_BOOKMARK. **SQLExtendedFetch** ne prend pas en charge les signets à longueur variable ni les ramets allant chercher des rames à un décalage autre que 0 à partir d’un signet. Pour plus d’informations, voir l’argument *de FetchOffset.*  
  
-   **SQLExtendedFetch** et **SQLFetchScroll** utilisent différentes tailles de ramset. **SQLExtendedFetch** utilise la valeur de l’attribut de l’SQL_ROWSET_SIZE déclaration, et **SQLFetchScroll** utilise la valeur de l’attribut de l’SQL_ATTR_ROW_ARRAY_SIZE déclaration.  
  
-   **SQLExtendedFetch** a une sémantique de traitement d’erreur légèrement différente de **SQLFetchScroll**. Pour plus d’informations, voir « Traitement des erreurs » dans la section « Commentaires » de [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
-   **SQLExtendedFetch** n’appuie pas les compensations contraignantes (l’attribut SQL_ATTR_ROW_BIND_OFFSET_PTR déclaration).  
  
-   Les appels à **SQLExtendedFetch** ne peuvent pas être mélangés avec des appels à **SQLFetch** ou **SQLFetchScroll**, et si **SQLBulkOperations** est appelé avant toute fonction d’aller chercher est appelé, **SQLExtendedFetch** ne peut pas être appelé jusqu’à ce que le curseur est fermé et rouvert. **C’est-à-dire, SQLExtendedFetch** ne peut être appelé que dans l’état de déclaration S7. Pour plus d’informations, voir [Transitions d’énoncés](../../../odbc/reference/appendixes/statement-transitions.md) à l’annexe B : Tableaux de transition d’État ODBC.  
  
 Lorsqu’une application appelle **SQLFetchScroll** alors qu’elle utilise un conducteur ODBC 2 *.x,* le Driver Manager cartographie cet appel à **SQLExtendedFetch**. Pour plus d’informations, voir "SQLFetchScroll et ODBC 2 *.x* Drivers" dans [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 Dans ODBC 2 *.x*, **SQLExtendedFetch** a été appelé à aller chercher plusieurs rangées et **SQLFetch** a été appelé à aller chercher une seule rangée. Dans ODBC 3 *.x*, d’autre part, **SQLFetch** peut être appelé à aller chercher plusieurs rangées.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Exécution d’opérations d’insertion, de mise à jour ou de suppression en vrac|[SQLBulkOperations, fonction](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Informations de retour sur une colonne dans un ensemble de résultats|[Fonction SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Retour du nombre de colonnes de jeu de résultats|[Fonction SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionnement du curseur, données rafraîchissantes dans l’aviron, ou mise à jour ou suppression des données dans l’ensemble de résultats|[SQLSetPos, fonction](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
