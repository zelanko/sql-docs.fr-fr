---
title: Fonction SQLFetchScroll (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFetchScroll
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFetchScroll
helpviewer_keywords:
- SQLFetchScroll function [ODBC]
ms.assetid: c0243667-428c-4dda-ae91-3c307616a1ac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6c65ef71f5c2cb9202ab788cac5e00357674f4a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285879"
---
# <a name="sqlfetchscroll-function"></a>Fonction SQLFetchScroll
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLFetchScroll** récupère le jeu de données spécifiés à partir de l’ensemble de résultats et renvoie les données pour toutes les colonnes liées. Les jeux de lignes peuvent être spécifiés à une position absolue ou relative ou par signet.  
  
 Lorsque vous travaillez avec un conducteur ODBC 2.x, le Driver Manager cartographie cette fonction à **SQLExtendedFetch**. Pour plus d’informations, voir [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLFetchScroll(  
      SQLHSTMT      StatementHandle,  
      SQLSMALLINT   FetchOrientation,  
      SQLLEN        FetchOffset);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Allerorienter*  
 [Entrée]  
  
 Type d’aller chercher:  
  
 SQL_FETCH_NEXT  
  
 SQL_FETCH_PRIOR  
  
 SQL_FETCH_FIRST  
  
 SQL_FETCH_LAST  
  
 SQL_FETCH_ABSOLUTE  
  
 SQL_FETCH_RELATIVE  
  
 SQL_FETCH_BOOKMARK  
  
 Pour plus d’informations, voir "Positionner le curseur" dans la section "Commentaires".  
  
 *AllerOffset (en)*  
 [Entrée]  
  
 Nombre de la rangée à aller chercher. L’interprétation de cet argument dépend de la valeur de l’argument *de FetchOrientation.* Pour plus d’informations, voir "Positionner le curseur" dans la section "Commentaires".  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLFetchScroll** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un HandleType de SQL_HANDLE_STMT et une poignée de StatementHandle. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLFetchScroll** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire. Si une erreur se produit sur une seule colonne, **SQLGetDiagField** peut être appelé avec un DiagIdentificateur de SQL_DIAG_COLUMN_NUMBER pour déterminer la colonne sur lequel l’erreur s’est produite; et **SQLGetDiagField** peut être appelé avec un DiagIdentificateur de SQL_DIAG_ROW_NUMBER pour déterminer la rangée contenant cette colonne.  
  
 Pour toutes les SQLSTATEs qui peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_ERROR (à l’exception des SQLSTATes de 01xxx), SQL_SUCCESS_WITH_INFO est retournée si une erreur se produit sur une ou plusieurs rangées, mais pas toutes, d’une opération à plusieurs pousses, et SQL_ERROR est retournée si une erreur se produit sur une opération à une seule rangée.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Les données de chaîne ou binaires retournées pour une colonne ont abouti à la troncation de caractère non-blank ou de données binaires non-NULL. Si c’était une valeur de chaîne, il était juste-tronqué.|  
|01S01|Erreur dans la rangée|Une erreur s’est produite en allant chercher une ou plusieurs rangées.<br /><br /> (Si ce SQLSTATE est retourné lorsqu’une application ODBC 3 *.x* fonctionne avec un pilote ODBC 2 *.x,* il peut être ignoré.)|  
|01S06|Tentative d’aller chercher avant le jeu de résultat retourné le premier rowset|Le jeu de ligne demandé chevauchait le début de l’ensemble de résultats lorsque FetchOrientation était SQL_FETCH_PRIOR, la position actuelle était au-delà de la première rangée, et le nombre de la rangée actuelle est inférieur ou égal à la taille de l’aviron.<br /><br /> Le jeu de ligne demandé chevauchait le début de l’ensemble de résultats lorsque FetchOrientation était SQL_FETCH_PRIOR, la position actuelle était au-delà de la fin de l’ensemble de résultats, et la taille de l’ensemble de rangées était supérieure à la taille de l’ensemble de résultats.<br /><br /> Le jeu de ligne demandé chevauchait le début de l’ensemble de résultats lorsque FetchOrientation était SQL_FETCH_RELATIVE, FetchOffset était négatif, et la valeur absolue de FetchOffset était inférieure ou égale à la taille de la ligne.<br /><br /> Le jeu de ligne demandé chevauchait le début de l’ensemble de résultat lorsque FetchOrientation était SQL_FETCH_ABSOLUTE, FetchOffset était négatif, et la valeur absolue de FetchOffset était supérieure à la taille de l’ensemble de résultat, mais inférieure ou égale à la taille de la ligne.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S07|Troncation fractionnaire|Les données retournées pour une colonne ont été tronquées. Pour les types de données numériques, la partie fractionnaire du nombre a été tronquée. Pour le temps, l’humidité du temps et les types de données d’intervalle contenant un composant de temps, la partie fractionnelle du temps a été tronquée.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|La valeur de données d’une colonne dans l’ensemble de résultat n’a pas pu être convertie au type de données spécifié par *TargetType* dans **SQLBindCol**.<br /><br /> La colonne 0 était reliée par un type de SQL_C_BOOKMARK de données, et l’attribut de l’SQL_ATTR_USE_BOOKMARKS a été réglé pour SQL_UB_VARIABLE.<br /><br /> La colonne 0 était reliée par un type de SQL_C_VARBOOKMARK de données, et l’attribut de l’SQL_ATTR_USE_BOOKMARKS n’était pas réglé pour SQL_UB_VARIABLE.|  
|07009|Indice descripteur invalide|Le conducteur était un conducteur ODBC 2 *.x* qui ne prend pas en charge **SQLExtendedFetch**, et un numéro de colonne spécifié dans la liaison pour une colonne était 0.<br /><br /> La colonne 0 était liée, et l’attribut de la déclaration SQL_ATTR_USE_BOOKMARKS a été réglé pour SQL_UB_OFF.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|22001|Données de chaîne, droite tronquées|Un signet à longueur variable retourné pour une colonne a été tronqué.|  
|22002|Variable d’indicateur requise mais non fournie|Les données NULL ont été récupérées dans une colonne dont *les StrLen_or_IndPtr* définies par **SQLBindCol** (ou SQL_DESC_INDICATOR_PTR définies par **SQLSetDescField** ou **SQLSetDescRec**) était un pointeur nul.|  
|22003|Valeur numérique hors de portée|Le retour de la valeur numérique (en tant que numérique ou chaîne) pour une ou plusieurs colonnes liées aurait fait tronquer la partie entière (par opposition à fractionnelle) du nombre.<br /><br /> Pour plus d’informations, voir [Convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) à [l’Annexe D : Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Format de date invalide|Une colonne de caractère dans l’ensemble de résultat était liée à une structure de date, d’heure ou de timetamp C, et une valeur dans la colonne était, respectivement, une date, un heure ou un fuseur horaires non valides.|  
|22012|Division par zéro|Une valeur d’une expression arithmétique a été retournée, ce qui a entraîné une division par zéro.|  
|22015|Débordement de champ d’intervalle|L’attribution d’un type SQL numérique ou d’intervalle exact à un type d’intervalle C a causé une perte de chiffres significatifs dans le champ principal.<br /><br /> Lorsque vous adz des données à un type d’intervalle C, il n’y avait aucune représentation de la valeur du type SQL dans le type d’intervalle C.|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|Une colonne de caractère dans l’ensemble de résultat était liée à un tampon de caractère C, et la colonne contenait un caractère pour lequel il n’y avait aucune représentation dans l’ensemble de caractères du tampon.<br /><br /> Le type C était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type SQL de la colonne était un type de données de caractère; et la valeur de la colonne n’était pas un littéral valide du type C lié.|  
|24 000|État de curseur non valide|Le *StatementHandle* était dans un état exécuté, mais aucun ensemble de résultat n’a été associé à la *StatementHandle*.|  
|40001|Échec de la sérialisation|La transaction dans laquelle le montant a été exécuté a été interrompue afin d’éviter l’impasse.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLFetchScroll** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Le *statementhandle* spécifié n’était pas dans un état exécuté. La fonction a été appelée sans appeler **d’abord SQLExecDirect**, **SQLExecute** ou une fonction de catalogue.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) **SQLFetch** a été appelé pour le *StatementHandle* après **SQLExtendedFetch** a été appelé et avant **SQLFreeStmt** avec l’option SQL_CLOSE a été appelé.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|L’attribut de l’SQL_ATTR_USE_BOOKMARK déclaration a été réglé pour SQL_UB_VARIABLE, et la colonne 0 était liée à un tampon dont la longueur n’était pas égale à la longueur maximale pour le signet de cet ensemble de résultats. (Cette longueur est disponible dans le domaine SQL_DESC_OCTET_LENGTH de l’IRD et peut être obtenue en appelant **SQLDescribeCol**, **SQLColAttribute**, ou **SQLGetDescField**.)|  
|HY106|Aller type hors de portée|DM) La valeur spécifiée pour l’argument FetchOrientation était invalide.<br /><br /> (DM) L’argument FetchOrientation était SQL_FETCH_BOOKMARK, et l’attribut de déclaration SQL_ATTR_USE_BOOKMARKS a été fixé à SQL_UB_OFF.<br /><br /> La valeur de l’attribut de la déclaration SQL_ATTR_CURSOR_TYPE était SQL_CURSOR_FORWARD_ONLY, et la valeur de l’argument FetchOrientation n’était pas SQL_FETCH_NEXT.<br /><br /> La valeur de l’attribut de la déclaration SQL_ATTR_CURSOR_SCROLLABLE était SQL_NONSCROLLABLE, et la valeur de l’argument FetchOrientation n’était pas SQL_FETCH_NEXT.|  
|HY107|Valeur de la ligne hors de portée|La valeur spécifiée avec l’attribut de l’SQL_ATTR_CURSOR_TYPE déclaration était SQL_CURSOR_KEYSET_DRIVEN, mais la valeur spécifiée avec l’attribut de l’SQL_ATTR_KEYSET_SIZE déclaration était supérieure à 0 et inférieure à la valeur spécifiée avec l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration.|  
|HY111|Valeur de signet invalide|L’argument FetchOrientation était SQL_FETCH_BOOKMARK, et le signet indiqué par la valeur de l’attribut de la déclaration SQL_ATTR_FETCH_BOOKMARK_PTR n’était pas valide ou était un pointeur nul.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données ne prend pas en charge la conversion spécifiée par la combinaison du *TargetType* dans **SQLBindCol** et le type de données SQL de la colonne correspondante.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats demandé. La période de délai d’attente est fixée par SQLSetStmtAttr, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLFetchScroll** renvoie un jeu de ligne spécifié à partir de l’ensemble de résultats. Les jeux de lignes peuvent être spécifiés par position absolue ou relative ou par signet. **SQLFetchScroll** ne peut être appelé que pendant qu’un ensemble de résultats existe - c’est-à-dire après un appel qui crée un ensemble de résultats et avant que le curseur sur cet ensemble de résultats est fermé. Si des colonnes sont liées, il renvoie les données dans ces colonnes. Si l’application a spécifié un pointeur à un tableau d’état de ligne ou un tampon dans lequel retourner le nombre de rangées récupérées, **SQLFetchScroll** retourne cette information ainsi. Les appels à **SQLFetchScroll** peuvent être mélangés avec des appels à **SQLFetch,** mais ne peuvent pas être mélangés avec des appels à **SQLExtendedFetch**.  
  
 Pour plus d’informations, voir [à l’aide de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md) et à [l’aide de curseurs défilants](../../../odbc/reference/develop-app/using-scrollable-cursors.md).  
  
## <a name="positioning-the-cursor"></a>Positionnement du curseur  
 Lorsque l’ensemble de résultat est créé, le curseur est positionné avant le début de l’ensemble de résultats. **SQLFetchScroll** positionne le curseur de bloc en fonction des valeurs des arguments *FetchOrientation* et *FetchOffset* comme le montre le tableau suivant. Les règles exactes pour déterminer le début du nouvel acart sont indiquées dans la section suivante.  
  
|Allerorienter|Signification|  
|----------------------|-------------|  
|SQL_FETCH_NEXT|Retournez le jeu de ligne suivant. Cela équivaut à appeler **SQLFetch**.<br /><br /> **SQLFetchScroll** ignore la valeur de *FetchOffset*.|  
|SQL_FETCH_PRIOR|Retourner le jeu de ligne précédent.<br /><br /> **SQLFetchScroll** ignore la valeur de *FetchOffset*.|  
|SQL_FETCH_RELATIVE|Retournez le *ramset FetchOffset* dès le début de la rangée actuelle.|  
|SQL_FETCH_ABSOLUTE|Retournez le ram ensemble à partir de la ligne *FetchOffset*.|  
|SQL_FETCH_FIRST|Retournez le premier jeu de ligne dans l’ensemble de résultats.<br /><br /> **SQLFetchScroll** ignore la valeur de *FetchOffset*.|  
|SQL_FETCH_LAST|Retournez le dernier ensemble complet de ligne dans l’ensemble de résultat.<br /><br /> **SQLFetchScroll** ignore la valeur de *FetchOffset*.|  
|SQL_FETCH_BOOKMARK|Retournez les lignes FetchOffset encastrées à partir du signet spécifié par l’attribut SQL_ATTR_FETCH_BOOKMARK_PTR déclaration.|  
  
 Les conducteurs ne sont pas tenus d’appuyer toutes les orientations d’aller chercher; une application appelle **SQLGetInfo** avec un type d’information de SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 (selon le type de curseur) pour déterminer quelles orientations d’aller chercher sont prises en charge par le conducteur. L’application devrait examiner les SQL_CA1_NEXT, les SQL_CA1_RELATIVE, les SQL_CA1_ABSOLUTE et les WQL_CA1_BOOKMARK des bitmasks dans ces types d’information. De plus, si le curseur est avant seulement et que FetchOrientation n’est pas SQL_FETCH_NEXT, **SQLFetchScroll** retourne SQLSTATE HY106 (type Aller de l’avant hors de portée).  
  
 L’attribut SQL_ATTR_ROW_ARRAY_SIZE énoncé précise le nombre de lignes dans le ramage. Si le ramset est récupéré par **SQLFetchScroll** chevauche la fin de l’ensemble de résultats, **SQLFetchScroll** retourne un jeu de ligne partiel. Autrement dit, si S R - 1 est plus grand que L, où S est la ligne de départ de la rangée étant récupéré, R est la taille rowset, et L est la dernière ligne dans l’ensemble de résultat, alors que seuls les premiers L - S 1 rangées de l’acart sont valides. Les autres rangées sont vides et ont un statut de SQL_ROW_NOROW.  
  
 Après le retour **de SQLFetchScroll,** la ligne actuelle est la première rangée de la rangée.  
  
## <a name="cursor-positioning-rules"></a>Règles de positionnement des curseurs  
 Les sections suivantes décrivent les règles exactes pour chaque valeur de FetchOrientation. Ces règles utilisent la notation suivante.  
  
|Notation|Signification|  
|--------------|-------------|  
|*Avant le début*|Le curseur de bloc est positionné avant le début de l’ensemble de résultat. Si la première rangée du nouveau rame est avant le début de l’ensemble de résultats, **SQLFetchScroll** revient SQL_NO_DATA.|  
|*Après la fin*|Le curseur de bloc est positionné après la fin de l’ensemble de résultats. Si la première ligne du nouveau rame est après la fin de l’ensemble de résultats, **SQLFetchScroll** revient SQL_NO_DATA.|  
|*CurrRowsetStart*|Le nombre de la première rangée dans le rowset actuel.|  
|*LastResultRow*|Le nombre de la dernière rangée dans l’ensemble de résultats.|  
|*RowsetSize RowsetSize*|La taille de rowset.|  
|*AllerOffset (en)*|La valeur de l’argument *de FetchOffset.*|  
|*BookmarkRow (en)*|La ligne correspondant au signet spécifié par l’attribut de l’SQL_ATTR_FETCH_BOOKMARK_PTR déclaration.|  
  
## <a name="sql_fetch_next"></a>SQL_FETCH_NEXT  
 Les règles suivantes s’appliquent.  
  
|Condition|Première rangée de rame|  
|---------------|-----------------------------|  
|*Avant le début*|1|  
|*CurrRowsetStart - RowsetSize*[1] * \<- LastResultRow*|*CurrRowsetStart - RowsetSize*[1]|  
|*CurrRowsetStart - RowsetSize*[1]*> LastResultRow*|*Après la fin*|  
|*Après la fin*|*Après la fin*|  
  
 [1] Si la taille de l’acart a été changée depuis l’appel précédent pour aller chercher des rangées, c’est la taille de l’ensemble de rangée qui a été utilisé avec l’appel précédent.  
  
## <a name="sql_fetch_prior"></a>SQL_FETCH_PRIOR  
 Les règles suivantes s’appliquent.  
  
|Condition|Première rangée de rame|  
|---------------|-----------------------------|  
|*Avant le début*|*Avant le début*|  
|*CurrRowsetStart 1*|*Avant le début*|  
|*1 < CurrRowsetStart <- RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*CurrRowsetStart > RowsetSize* <sup>[2]</sup>|*CurrRowsetStart - RowsetSize* <sup>[2]</sup>|  
|*Après la fin et LastResultRow < RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*Après la fin et LastResultRow >- RowsetSize* <sup>[2]</sup>|*LastResultRow - RowsetSize 1* <sup>[2]</sup>|  
  
 **SQLFetchScroll** retourne SQLSTATE 01S06 (Tentative d’aller chercher avant que le jeu de résultat ne renvoie le premier jeu de ligne) et SQL_SUCCESS_WITH_INFO.  
  
 [2] Si la taille de rowset a été changée depuis l’appel précédent pour aller chercher des rangées, c’est la nouvelle taille de rowset.  
  
## <a name="sql_fetch_relative"></a>SQL_FETCH_RELATIVE  
 Les règles suivantes s’appliquent.  
  
|Condition|Première rangée de rame|  
|---------------|-----------------------------|  
|*(Avant le début et FetchOffset > 0) OU (Après la fin et FetchOffset < 0)*|*--*<sup>[1]</sup>|  
|*BeforeStart ET FetchOffset <0*|*Avant le début*|  
|*CurrRowsetStart 1 ET FetchOffset < 0*|*Avant le début*|  
|*CurrRowsetStart > 1 ET CurrRowsetStart - FetchOffset < 1 ET &#124; FetchOffset &#124; > RowsetSize* <sup>[3]</sup>|*Avant le début*|  
|*CurrRowsetStart > 1 ET CurrRowsetStart - FetchOffset < 1 ET &#124; FetchOffset &#124; <- RowsetSize* <sup>[3]</sup>|*1* <sup>[2]</sup>|  
|*1 <' CurrRowsetStart ' FetchOffset \<' LastResultRow*|*CurrRowsetStart - FetchOffset*|  
|*CurrRowsetStart - FetchOffset > LastResultRow*|*Après la fin*|  
|*Après la fin et FetchOffset >0*|*Après la fin*|  
  
 ***SQLFetchScroll*** retourne le même jeu de ligne que s’il était appelé avec FetchOrientation mis à SQL_FETCH_ABSOLUTE. Pour plus d’informations, consultez la section « SQL_FETCH_ABSOLUTE ».  
  
 **SQLFetchScroll** retourne SQLSTATE 01S06 (Tentative d’aller chercher avant que le jeu de résultat ne renvoie le premier jeu de ligne) et SQL_SUCCESS_WITH_INFO.  
  
 [3] Si la taille de rowset a été changée depuis l’appel précédent pour aller chercher des rangées, c’est la nouvelle taille de rowset.  
  
## <a name="sql_fetch_absolute"></a>SQL_FETCH_ABSOLUTE  
 Les règles suivantes s’appliquent.  
  
|Condition|Première rangée de rame|  
|---------------|-----------------------------|  
|*FetchOffset < 0 ET &#124; FetchOffset &#124; <- LastResultRow*|*LastResultRow et FetchOffset 1*|  
|*FetchOffset < 0 ET &#124; FetchOffset &#124; > LastResultRow ET &#124; FetchOffset &#124; > RowsetSize* <sup>[2]</sup>|*Avant le début*|  
|*FetchOffset < 0 ET &#124; FetchOffset &#124; > LastResultRow ET &#124; FetchOffset &#124; <- RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*FetchOffset 0*|*Avant le début*|  
|*1 <' FetchOffset \<' LastResultRow*|*AllerOffset (en)*|  
|*FetchOffset > LastResultRow*|*Après la fin*|  
  
 **SQLFetchScroll** retourne SQLSTATE 01S06 (Tentative d’aller chercher avant que le jeu de résultat ne renvoie le premier jeu de ligne) et SQL_SUCCESS_WITH_INFO.  
  
 [2] Si la taille de rowset a été changée depuis l’appel précédent pour aller chercher des rangées, c’est la nouvelle taille de rowset.  
  
 Un aller chercher absolu effectué contre un curseur dynamique ne peut pas fournir le résultat requis parce que les positions de ligne dans un curseur dynamique sont indéterminées. Une telle opération équivaut à un aller chercher d’abord suivi d’un parent aller chercher; ce n’est pas une opération atomique, comme c’est un aller chercher absolu sur un curseur statique.  
  
## <a name="sql_fetch_first"></a>SQL_FETCH_FIRST  
 Les règles suivantes s’appliquent.  
  
|Condition|Première rangée de rame|  
|---------------|-----------------------------|  
|*Any*|*1*|  
  
## <a name="sql_fetch_last"></a>SQL_FETCH_LAST  
 Les règles suivantes s’appliquent.  
  
|Condition|Première rangée de rame|  
|---------------|-----------------------------|  
|*RowsetSize* <sup>[1]</sup> <- LastResultRow|*LastResultRow - RowsetSize 1* <sup>[1]</sup>|  
|*RowsetSize* <sup>[1]</sup> > LastResultRow|*1*|  
  
 [1] Si la taille de rowset a été changée depuis l’appel précédent pour aller chercher des rangées, c’est la nouvelle taille de rowset.  
  
## <a name="sql_fetch_bookmark"></a>SQL_FETCH_BOOKMARK  
 Les règles suivantes s’appliquent.  
  
|Condition|Première rangée de rame|  
|---------------|-----------------------------|  
|*BookmarkRow - FetchOffset < 1*|*Avant le début*|  
|*1 <' BookmarkRow ' FetchOffset \<' LastResultRow*|*BookmarkRow - FetchOffset*|  
|*BookmarkRow - FetchOffset > LastResultRow*|*Après la fin*|  
  
 Pour plus d’informations sur les signets, voir [Signets (ODBC)](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
## <a name="effect-of-deleted-added-and-error-rows-on-cursor-movement"></a>Effet des lignes supprimées, ajoutées et erronées sur le mouvement cursur  
 Les curseurs statiques et pilotés par les clés détectent parfois les lignes ajoutées à l’ensemble de résultats et suppriment les lignes supprimées de l’ensemble de résultats. En appelant **SQLGetInfo** avec les options de SQL_STATIC_CURSOR_ATTRIBUTES2 et de SQL_KEYSET_CURSOR_ATTRIBUTES2 et en examinant les SQL_CA2_SENSITIVITY_ADDITIONS, SQL_CA2_SENSITIVITY_DELETIONS et SQL_CA2_SENSITIVITY_UPDATES des bitmasks, une application détermine si les curseurs mis en œuvre par un conducteur particulier le font. Pour les conducteurs qui peuvent détecter les lignes supprimées et les supprimer, les paragraphes suivants décrivent les effets de ce comportement. Pour les conducteurs qui peuvent détecter les lignes supprimées mais ne peuvent pas les supprimer, les suppressions n’ont aucun effet sur les mouvements de curseur, et les paragraphes suivants ne s’appliquent pas.  
  
 Si le curseur détecte les lignes ajoutées à l’ensemble de résultats ou supprime les lignes supprimées de l’ensemble de résultats, il apparaît comme s’il ne détecte ces modifications que lorsqu’il récupère des données. Cela comprend le cas où **SQLFetchScroll** est appelé avec FetchOrientation réglé à SQL_FETCH_RELATIVE et FetchOffset réglé à 0 pour réfélérer le même jeu de rangée, mais n’inclut pas le cas lorsque SQLSetPos est appelé avec fOption réglé pour SQL_REFRESH. Dans ce dernier cas, les données des tampons rowset sont actualisées, mais non recadrées, et les lignes supprimées ne sont pas supprimées de l’ensemble de résultats. Ainsi, lorsqu’une ligne est supprimée ou insérée dans l’acart actuel, le curseur ne modifie pas les tampons encastrés. Au lieu de cela, il détecte le changement quand il récupère n’importe quel jeu de ligne qui comprenait précédemment la rangée supprimée ou inclut maintenant la rangée insérée.  
  
 Par exemple :  
  
```cpp  
// Fetch the next rowset.  
SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
// Delete third row of the rowset. Does not modify the rowset buffers.  
SQLSetPos(hstmt, 3, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
// The third row has a status of SQL_ROW_DELETED after this call.  
SQLSetPos(hstmt, 3, SQL_REFRESH, SQL_LOCK_NO_CHANGE);  
// Refetch the same rowset. The third row is removed, replaced by what  
// was previously the fourth row.  
SQLFetchScroll(hstmt, SQL_FETCH_RELATIVE, 0);  
```  
  
 Lorsque **SQLFetchScroll** retourne un nouvel ensemble de rames qui a une position par rapport à la rangée actuelle - c’est-à-dire que FetchOrientation est SQL_FETCH_NEXT, SQL_FETCH_PRIOR ou SQL_FETCH_RELATIVE - elle n’inclut pas de changements à l’encart actuel lors du calcul de la position de départ du nouvel ensemble de rames. Cependant, il comprend des changements en dehors de l’achaillement actuel s’il est capable de les détecter. De plus, lorsque **SQLFetchScroll** retourne un nouveau jeu de ligne qui a une position indépendante de l’ensemble actuel - c’est-à-dire que FetchOrientation est SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE ou SQL_FETCH_BOOKMARK - il inclut tous les changements qu’il est capable de détecter, même s’ils sont dans la rangée actuelle.  
  
 Lorsqu’on détermine si les lignes nouvellement ajoutées sont à l’intérieur ou à l’extérieur de l’ensemble de rangées en cours, un jeu de rangée partiel est considéré comme se terminent à la dernière rangée valide; c’est-à-dire la dernière rangée pour laquelle le statut de ligne n’est pas SQL_ROW_NOROW. Par exemple, supposons que le curseur est capable de détecter les lignes nouvellement ajoutées, le ramset actuel est un jeu de ligne partiel, l’application ajoute de nouvelles lignes, et le curseur ajoute ces lignes à la fin de l’ensemble de résultats. Si l’application appelle **SQLFetchScroll** avec FetchOrientation réglé pour SQL_FETCH_NEXT, **SQLFetchScroll** renvoie le jeu en rangée en commençant par la première nouvelle ligne.  
  
 Supposons, par exemple, que l’ensemble de rangées actuel comprend des rangées 21 à 30, la taille de l’encart est de 10, le curseur enlève les lignes supprimées de l’ensemble de résultats, et le curseur détecte les lignes ajoutées à l’ensemble de résultats. Le tableau suivant montre les lignes **SQLFetchScroll** revient dans diverses situations.  
  
|Modifier|Type d’aller chercher|AllerOffset (en)|Nouveau rowset[1]|  
|------------|----------------|-----------------|---------------------|  
|Supprimer la rangée 21|NEXT|0|31 à 40 ans|  
|Supprimer la rangée 31|NEXT|0|32 à 41 ans|  
|Insérer la ligne entre les rangées 21 et 22|NEXT|0|31 à 40 ans|  
|Insérer la ligne entre les rangées 30 et 31|NEXT|0|Ligne insérée, 31 à 39|  
|Supprimer la rangée 21|PRIOR|0|11 à 20 ans|  
|Supprimer la rangée 20|PRIOR|0|10 à 19 ans|  
|Insérer la ligne entre les rangées 21 et 22|PRIOR|0|11 à 20 ans|  
|Insérer la ligne entre les rangées 20 et 21|PRIOR|0|12 à 20, rangée insérée|  
|Supprimer la rangée 21|RELATIVE|0|22 à 31<sup>[2]</sup>|  
|Supprimer la rangée 21|RELATIVE|1|22 à 31 ans|  
|Insérer la ligne entre les rangées 21 et 22|RELATIVE|0|21, rangée insérée, 22 à 29|  
|Insérer la ligne entre les rangées 21 et 22|RELATIVE|1|22 à 31 ans|  
|Supprimer la rangée 21|ABSOLUTE|21|22 à 31<sup>[2]</sup>|  
|Supprimer la rangée 22|ABSOLUTE|21|21, 23 à 31|  
|Insérer la ligne entre les rangées 21 et 22|ABSOLUTE|22|Ligne insérée, 22 à 29|  
  
 Cette colonne utilise les numéros de ligne avant que les lignes ne soient insérées ou supprimées.  
  
 [2] Dans ce cas, le curseur tente de retourner les rangées commençant par la rangée 21. Parce que la ligne 21 a été supprimée, la première rangée qu’elle renvoie est la rangée 22.  
  
 Les lignes d’erreur (c’est-à-dire les rangées ayant un statut de SQL_ROW_ERROR) n’affectent pas le mouvement des curseurs. Par exemple, si le jeu de ligne actuel commence avec la rangée 11 et que l’état de la rangée 11 est SQL_ROW_ERROR, appeler **SQLFetchScroll** avec FetchOrientation réglé pour SQL_FETCH_RELATIVE et FetchOffset réglé à 5 retours le jeu en rangée commençant par la rangée 16, tout comme il le ferait si le statut pour la rangée 11 a été SQL_SUCCESS.  
  
## <a name="returning-data-in-bound-columns"></a>Retour des données dans les colonnes liées  
 **SQLFetchScroll** renvoie les données dans les colonnes liées de la même manière que **SQLFetch**. Pour plus d’informations, voir "Returning Data in Bound Columns" dans [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Si aucune colonne n’est liée, **SQLFetchScroll** ne retourne pas les données mais déplace le curseur de bloc à la position spécifiée. La question de savoir si les données peuvent être récupérées à partir de colonnes non liées d’un curseur de bloc avec **SQLGetData** dépend du conducteur. Cette capacité est prise en charge si un appel à **SQLGetInfo** renvoie le SQL_GD_BLOCK bit pour le type d’information SQL_GETDATA_EXTENSIONS.  
  
## <a name="buffer-addresses"></a>Adresses tampon  
 **SQLFetchScroll** utilise la même formule pour déterminer l’adresse des données et des tampons de longueur/indicateur que **SQLFetch**. Pour plus d’informations, voir "Buffer Addresses" dans [SQLBindCol Function](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="row-status-array"></a>Tableau d’état des lignes  
 **SQLFetchScroll** établit les valeurs dans le tableau d’état de la ligne de la même manière que SQLFetch. Pour plus d’informations, voir "Row Status Array" dans [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="rows-fetched-buffer"></a>Lignes Fetched Buffer  
 **SQLFetchScroll** retourne le nombre de rangées récupérées dans les rangées récupéré tampon de la même manière que **SQLFetch**. Pour plus d’informations, voir "Rows Fetched Buffer" dans [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Lorsqu’une demande appelle **SQLFetchScroll** dans un conducteur ODBC 3.x, le gestionnaire de conducteur appelle **SQLFetchScroll** au conducteur. Lorsqu’une demande appelle **SQLFetchScroll** dans un conducteur ODBC 2.x, le gestionnaire de conducteur appelle SQLExtendedFetch dans le conducteur. Étant donné que **SQLFetchScroll** et SQLExtendedFetch ont traité des erreurs d’une manière légèrement différente, l’application voit un comportement d’erreur légèrement différent lorsqu’elle appelle **SQLFetchScroll** chez les conducteurs ODBC 2.x et ODBC 3.x.  
  
 **SQLFetchScroll** renvoie les erreurs et les avertissements de la même manière que **SQLFetch;** pour plus d’informations, voir "Traitement des erreurs" dans **SQLFetch**. **SQLExtendedFetch** retourne les erreurs de la même manière que **SQLFetch**, avec les exceptions suivantes:  
  
 Lorsqu’un avertissement se produit qui s’applique à une rangée particulière dans le ramage, SQLExtendedFetch définit l’entrée correspondante dans le tableau d’état de la rangée pour SQL_ROW_SUCCESS, et non SQL_ROW_SUCCESS_WITH_INFO.  
  
 Si des erreurs se produisent dans chaque rangée de la rangée, SQLExtendedFetch retourne SQL_SUCCESS_WITH_INFO, et non SQL_ERROR.  
  
 Dans chaque groupe de dossiers d’état qui s’applique à une rangée individuelle, le premier dossier d’état retourné par SQLExtendedFetch doit contenir SQLSTATE 01S01 (Erreur de ligne); **SQLFetchScroll** ne retourne pas ce SQLSTATE. Si SQLExtendedFetch n’est pas en mesure de retourner d’autres SQLSTATEs, il doit tout de même retourner ce SQLSTATE.  
  
## <a name="sqlfetchscroll-and-optimistic-concurrency"></a>SQLFetchScroll et Concordrency Optimiste  
 Si un curseur utilise une concordance optimiste - c’est-à-dire que l’attribut de l’SQL_ATTR_CONCURRENCY a une valeur de SQL_CONCUR_VALUES ou de SQL_CONCUR_ROWVER - **SQLFetchScroll** met à jour les valeurs de concordance optimistes utilisées par la source de données pour détecter si une ligne a changé. Cela se produit chaque fois que **SQLFetchScroll** récupère un nouveau jeu de rangée, y compris quand il refaçons le jeu de rame actuel. (Il est appelé avec FetchOrientation réglé à SQL_FETCH_RELATIVE et FetchOffset réglé à 0.)  
  
## <a name="sqlfetchscroll-and-odbc-2x-drivers"></a>SQLFetchScroll et ODBC 2.x Pilotes  
 Lorsqu’une application appelle **SQLFetchScroll** dans un conducteur ODBC 2.x, le Driver Manager cartographie cet appel à **SQLExtendedFetch**. Il passe les valeurs suivantes pour les arguments de **SQLExtendedFetch**.  
  
|Argument SQLExtendedFetch|Value|  
|-------------------------------|-----------|  
|StatementHandle (en)|StatementHandle dans **SQLFetchScroll**.|  
|Allerorienter|FetchOrientation dans **SQLFetchScroll**.|  
|AllerOffset (en)|Si FetchOrientation n’est pas SQL_FETCH_BOOKMARK, la valeur de l’argument FetchOffset dans **SQLFetchScroll** est utilisée.<br /><br /> Si FetchOrientation est SQL_FETCH_BOOKMARK, la valeur stockée à l’adresse spécifiée par l’attribut de l’SQL_ATTR_FETCH_BOOKMARK_PTR’indication est utilisée.|  
|RowCountPtr RowCountPtr RowCountPtr RowCount|L’adresse spécifiée par l’attribut SQL_ATTR_ROWS_FETCHED_PTR déclaration.|  
|RowStatusArray RowStatusArray|L’adresse spécifiée par l’attribut SQL_ATTR_ROW_STATUS_PTR déclaration.|  
  
 Pour plus d’informations, voir [Block Cursors, Scrollable Cursors et Compatibility backward](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Appendix G: Driver Guidelines for Backward Compatibility.  
  
## <a name="descriptors-and-sqlfetchscroll"></a>Descripteurs et SQLFetchScroll  
 **SQLFetchScroll** interagit avec les descripteurs de la même manière que **SQLFetch**. Pour plus d’informations, consultez la section « Descriptors et SQLFetchScroll » dans [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Exemple de code  
 Voir [Column-Wise Binding](../../../odbc/reference/develop-app/column-wise-binding.md), [Row-Wise Binding](../../../odbc/reference/develop-app/row-wise-binding.md), [Positioned Update and Delete Statements](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md), et Mise à jour des lignes dans le [Rowset avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Exécution d’opérations d’insertion, de mise à jour ou de suppression en vrac|[SQLBulkOperations, fonction](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Informations de retour sur une colonne dans un ensemble de résultats|[Fonction SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Aller chercher une seule rangée ou un bloc de données dans une direction avant-seulement|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Fermeture du curseur sur la déclaration|[Fonction SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Retour du nombre de colonnes de jeu de résultats|[Fonction SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionnement du curseur, données rafraîchissantes dans l’aviron, ou mise à jour ou suppression des données dans l’ensemble de résultats|[SQLSetPos, fonction](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
