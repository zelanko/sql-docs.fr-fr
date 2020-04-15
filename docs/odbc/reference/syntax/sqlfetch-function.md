---
title: Fonction SQLFetch (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFetch
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFetch
helpviewer_keywords:
- SQLFetch function [ODBC]
ms.assetid: 6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc7e2da6996d8d6b2ee66befdc90794efec5617b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285969"
---
# <a name="sqlfetch-function"></a>SQLFetch, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLFetch** récupère la ligne suivante de données de l’ensemble de résultats et renvoie les données pour toutes les colonnes liées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLFetch(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLFetch** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant [LA fonction SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) avec un *handleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLFetch** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire. Si une erreur se produit sur une seule colonne, [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) peut être appelé avec un *DiagIdentificateur* de SQL_DIAG_COLUMN_NUMBER pour déterminer la colonne sur lequel l’erreur s’est produite; et **SQLGetDiagField** peut être appelé avec un *DiagIdentificateur* de SQL_DIAG_ROW_NUMBER pour déterminer la ligne qui contient cette colonne.  
  
 Pour toutes les SQLSTATEs qui peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_ERROR (à l’exception des SQLSTATes de 01xxx), SQL_SUCCESS_WITH_INFO est retournée si une erreur se produit sur une ou plusieurs rangées, mais pas toutes, d’une opération à plusieurs pousses, et SQL_ERROR est retournée si une erreur se produit sur une opération à une seule rangée.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Les données de chaîne ou binaires retournées pour une colonne ont abouti à la troncation de caractère non-blank ou de données binaires non-NULL. Si c’était une valeur de chaîne, il était juste-tronqué.|  
|01S01|Erreur dans la rangée|Une erreur s’est produite en allant chercher une ou plusieurs rangées.<br /><br /> (Si ce SQLSTATE est retourné lorsqu’une application ODBC 3 *.x* fonctionne avec un pilote ODBC 2 *.x,* il peut être ignoré.)|  
|01S07|Troncation fractionnaire|Les données retournées pour une colonne ont été tronquées. Pour les types de données numériques, la partie fractionnaire du nombre a été tronquée. Pour le temps, l’humidité du temps et les types de données d’intervalle qui contiennent un composant de temps, la partie fractionnelle du temps a été tronquée.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|La valeur de données d’une colonne dans l’ensemble de résultat n’a pas pu être convertie au type de données spécifié par *TargetType* dans **SQLBindCol**.<br /><br /> La colonne 0 était reliée par un type de SQL_C_BOOKMARK de données, et l’attribut de l’SQL_ATTR_USE_BOOKMARKS a été réglé pour SQL_UB_VARIABLE.<br /><br /> La colonne 0 était reliée par un type de SQL_C_VARBOOKMARK de données, et l’attribut de l’SQL_ATTR_USE_BOOKMARKS n’était pas réglé pour SQL_UB_VARIABLE.|  
|07009|Indice descripteur invalide|Le conducteur était un conducteur ODBC 2 *.x* qui ne prend pas en charge **SQLExtendedFetch**, et un numéro de colonne spécifié dans la liaison pour une colonne était 0.<br /><br /> La colonne 0 était liée, et l’attribut de la déclaration SQL_ATTR_USE_BOOKMARKS a été réglé pour SQL_UB_OFF.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|22001|Données de chaîne, droite tronquées|Un signet à longueur variable retourné pour une colonne a été tronqué.|  
|22002|Variable d’indicateur requise mais non fournie|Les données NULL ont été récupérées dans une colonne dont *les StrLen_or_IndPtr* définies par **SQLBindCol** (ou SQL_DESC_INDICATOR_PTR définies par **SQLSetDescField** ou **SQLSetDescRec**) était un pointeur nul.|  
|22003|Valeur numérique hors de portée|Le retour de la valeur numérique en tant que numérique ou chaîne pour une ou plusieurs colonnes liées aurait fait tronquer la partie entière (par opposition à fractionnelle) du nombre.<br /><br /> Pour plus d’informations, voir [Convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) dans l’annexe D : Data Types.|  
|22007|Format de date invalide|Une colonne de caractère dans l’ensemble de résultat était liée à une structure de date, d’heure ou de timetamp C, et une valeur dans la colonne était, respectivement, une date, un heure ou un fuseur horaires non valides.|  
|22012|Division par zéro|Une valeur d’une expression arithmétique a été retournée, ce qui a entraîné une division par zéro.|  
|22015|Débordement de champ d’intervalle|L’attribution d’un type SQL numérique ou d’intervalle exact à un type d’intervalle C a causé une perte de chiffres significatifs dans le champ principal.<br /><br /> Lorsque vous adz des données à un type d’intervalle C, il n’y avait aucune représentation de la valeur du type SQL dans le type d’intervalle C.|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|Une colonne de caractère dans l’ensemble de résultat était liée à un tampon de caractère C, et la colonne contenait un caractère pour lequel il n’y avait aucune représentation dans l’ensemble de caractères du tampon.<br /><br /> Le type C était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type SQL de la colonne était un type de données de caractère; et la valeur de la colonne n’était pas un littéral valide du type C lié.|  
|24 000|État de curseur non valide|Le *StatementHandle* était dans un état exécuté, mais aucun ensemble de résultat n’a été associé à la *StatementHandle*.|  
|40001|Échec de la sérialisation|La transaction dans laquelle le montant a été exécuté a été interrompue afin d’éviter l’impasse.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction **SQLFetch** a été appelée, et avant qu’elle ne termine son exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Ensuite, la fonction **SQLFetch** a été appelée à nouveau sur le *StatementHandle*.<br /><br /> Ou, la fonction **SQLFetch** a été appelée, et avant qu’il ne termine l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLFetch** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Le *statementhandle* spécifié n’était pas dans un état exécuté. La fonction a été appelée sans appeler **d’abord SQLExecDirect**, **SQLExecute** ou une fonction de catalogue.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) **SQLFetch** a été appelé pour le *StatementHandle* après **SQLExtendedFetch** a été appelé et avant **SQLFreeStmt** avec l’option SQL_CLOSE a été appelé.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|L’attribut de l’SQL_ATTR_USE_BOOKMARK déclaration a été réglé pour SQL_UB_VARIABLE, et la colonne 0 était liée à un tampon dont la longueur n’était pas égale à la longueur maximale pour le signet de cet ensemble de résultats. (Cette longueur est disponible dans le domaine SQL_DESC_OCTET_LENGTH de l’IRD et peut être obtenue en appelant **SQLDescribeCol**, **SQLColAttribute**, ou **SQLGetDescField**.)|  
|HY107|Valeur de la ligne hors de portée|La valeur spécifiée avec l’attribut de l’SQL_ATTR_CURSOR_TYPE déclaration était SQL_CURSOR_KEYSET_DRIVEN, mais la valeur spécifiée avec l’attribut de l’SQL_ATTR_KEYSET_SIZE déclaration était supérieure à 0 et inférieure à la valeur spécifiée avec l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données ne prend pas en charge la conversion spécifiée par la combinaison du *TargetType* dans **SQLBindCol** et le type de données SQL de la colonne correspondante.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats demandé. La période de délai d’attente est fixée par SQLSetStmtAttr, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLFetch** renvoie le jeu de ligne suivant dans l’ensemble de résultats. Il ne peut être appelé que pendant qu’un ensemble de résultat existe: c’est-à-dire, après un appel qui crée un ensemble de résultat et avant que le curseur sur cet ensemble de résultat est fermé. Si des colonnes sont liées, il renvoie les données dans ces colonnes. Si l’application a spécifié un pointeur à un tableau d’état de ligne ou un tampon dans lequel retourner le nombre de rangées récupérées, **SQLFetch** renvoie également cette information. Les appels à **SQLFetch** peuvent être mélangés avec des appels à **SQLFetchScroll,** mais ne peuvent pas être mélangés avec des appels à **SQLExtendedFetch**. Pour plus d’informations, voir [Fetching a Row of Data](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 Si une application ODBC 3 *.x* fonctionne avec un conducteur ODBC 2 *.x,* le gestionnaire de conducteur cartes **SQLFetch** appelle **à SQLExtendedFetch** pour un ODBC 2 *.x* pilote qui prend en charge **SQLExtendedFetch**. Si le conducteur de l’ODBC 2 *.x* ne prend pas en charge **SQLExtendedFetch**, le gestionnaire de conducteur passe en charge les appels **SQLFetch** à **SQLFetch** dans le conducteur ODBC 2.x, qui ne peut aller chercher qu’une seule rangée.*.x*  
  
 Pour plus d’informations, voir [Block Cursors, Scrollable Cursors et Compatibility backward](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Appendix G: Driver Guidelines for Backward Compatibility.  
  
## <a name="positioning-the-cursor"></a>Positionnement du curseur  
 Lorsque l’ensemble de résultat est créé, le curseur est positionné avant le début de l’ensemble de résultats. **SQLFetch** récupère le jeu de ligne suivant. Il est équivalent à appeler **SQLFetchScroll** avec *FetchOrientation* mis à SQL_FETCH_NEXT. Pour plus d’informations sur les curseurs, voir [Cursors](../../../odbc/reference/develop-app/cursors.md) et [Block Cursors](../../../odbc/reference/develop-app/block-cursors.md).  
  
 L’attribut SQL_ATTR_ROW_ARRAY_SIZE énoncé précise le nombre de lignes dans le ramage. Si le ramon récupéré par **SQLFetch** chevauche la fin de l’ensemble de résultats, **SQLFetch** renvoie un jeu de ligne partiel. Autrement dit, si S R - 1 est plus grand que L, où S est la ligne de départ de la rangée étant récupéré, R est la taille rowset, et L est la dernière ligne dans l’ensemble de résultat, alors que seuls les premiers L - S 1 rangées de l’acart sont valides. Les autres rangées sont vides et ont un statut de SQL_ROW_NOROW.  
  
 Après le retour **de SQLFetch,** la ligne actuelle est la première rangée de la rangée.  
  
 Les règles énumérées dans le tableau suivant décrivent le positionnement du curseur après un appel à **SQLFetch**, en fonction des conditions énumérées dans le deuxième tableau de cette section.  
  
|Condition|Première rangée de rame|  
|---------------|-----------------------------|  
|Avant le début|1|  
|*CurrRowsetStart* \< =  *LastResultRow - RowsetSize*[1]|*CurrRowsetStart* + *RowsetSize*[2]|  
|*CurrRowsetStart* > *LastResultRow - RowsetSize*[1]|Après la fin|  
|Après la fin|Après la fin|  
  
 [1] Si la taille de rowset est changée entre les fetches, c’est la taille de rowset qui a été employée avec l’aller chercher précédent.  
  
 [2] Si la taille de rowset est changée entre les fetches, c’est la taille de rowset qui a été employée avec le nouveau fetch.  
  
|Notation|Signification|  
|--------------|-------------|  
|Avant le début|Le curseur de bloc est positionné avant le début de l’ensemble de résultat. Si la première rangée du nouveau rame est avant le début de l’ensemble de résultats, **SQLFetch** revient SQL_NO_DATA.|  
|Après la fin|Le curseur de bloc est positionné après la fin de l’ensemble de résultats. Si la première ligne du nouveau rame est après la fin de l’ensemble de résultats, **SQLFetch** revient SQL_NO_DATA.|  
|*CurrRowsetStart*|Le nombre de la première rangée dans le rowset actuel.|  
|*LastResultRow*|Le nombre de la dernière rangée dans l’ensemble de résultats.|  
|*RowsetSize RowsetSize*|La taille de rowset.|  
  
 Supposons, par exemple, qu’un ensemble de résultats comporte 100 lignes et que la taille de l’assaillis est de 5. Le tableau suivant montre le code de rame et de retour retourné par **SQLFetch** pour différentes positions de départ.  
  
|Ligne actuelle|Code de retour|Nouveau ramé|des rangées récupérées|  
|--------------------|-----------------|----------------|------------------------|  
|Avant le début|SQL_SUCCESS|1 à 5|5|  
|1 à 5|SQL_SUCCESS|6 à 10 ans|5|  
|52 à 56 ans|SQL_SUCCESS|57 à 61 ans|5|  
|91 à 95 ans|SQL_SUCCESS|96 à 100 ans|5|  
|93 à 97 ans|SQL_SUCCESS|98 à 100. Les rangées 4 et 5 du tableau d’état de la rangée sont réglées pour SQL_ROW_NOROW.|3|  
|96 à 100 ans|SQL_NO_DATA|Aucun.|0|  
|99 à 100 ans|SQL_NO_DATA|Aucun.|0|  
|Après la fin|SQL_NO_DATA|Aucun.|0|  
  
## <a name="returning-data-in-bound-columns"></a>Retour des données dans les colonnes liées  
 Comme **SQLFetch** renvoie chaque rangée, il met les données pour chaque colonne liée dans le tampon lié à cette colonne. Si aucune colonne n’est liée, **SQLFetch** ne renvoie aucune donnée mais déplace le curseur de bloc vers l’avant. Les données peuvent encore être récupérées à l’aide **de SQLGetData**. Si le curseur est un curseur multirow (c’est-à-dire, le SQL_ATTR_ROW_ARRAY_SIZE est supérieur à 1), **SQLGetData** ne peut être appelé que si SQL_GD_BLOCK est retourné lorsque **SQLGetInfo** est appelé avec un *InfoType* de SQL_GETDATA_EXTENSIONS. (Pour plus d’informations, voir [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).)  
  
 Pour chaque colonne reliée d’affilée, **SQLFetch** fait ce qui suit :  
  
1.  Définit le tampon longueur/indicateur pour SQL_NULL_DATA et passe à la colonne suivante si les données sont NULL. Si les données sont NULL et qu’aucun tampon de longueur/indicateur n’a été lié, **SQLFetch** renvoie SQLSTATE 22002 (variable d’indicateur requise mais non fournie) pour la ligne et se poursuit à la rangée suivante. Pour obtenir de l’information sur la façon de déterminer l’adresse du tampon de longueur/indicateur, voir « Adresses tampons » dans [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
     Si les données de la colonne ne sont pas NULL, **SQLFetch** procède à l’étape 2.  
  
2.  Si l’attribut de l’SQL_ATTR_MAX_LENGTH déclaration est réglé à une valeur non zéro et que la colonne contient des données de caractère ou binaires, les données sont tronquées pour SQL_ATTR_MAX_LENGTH octets.  
  
    > [!NOTE]  
    >  L’attribut de l’SQL_ATTR_MAX_LENGTH’énoncé vise à réduire le trafic réseau. Il est généralement mis en œuvre par la source de données, ce qui tronque les données avant de les retourner sur le réseau. Les conducteurs et les sources de données ne sont pas tenus de l’appuyer. Par conséquent, pour garantir que les données sont tronquées à une taille particulière, une application devrait allouer un tampon de cette taille et spécifier la taille de l’argument *cbValueMax* dans **SQLBindCol**.  
  
3.  Convertit les données au type spécifié par *TargetType* dans **SQLBindCol**.  
  
4.  Si les données ont été converties en un type de données à durée variable, comme le caractère ou **binaire, SQLFetch** vérifie si la longueur des données dépasse la longueur du tampon de données. Si la longueur des données de caractère (y compris le caractère de résiliation nulle) dépasse la longueur du tampon de données, **SQLFetch** tronque les données à la longueur du tampon de données moins la longueur d’un caractère de résiliation nulle. Il met ensuite fin aux données. Si la longueur des données binaires dépasse la longueur du tampon de données, **SQLFetch** la tronque jusqu’à la longueur du tampon de données. La longueur du tampon de données est spécifiée avec *BufferLength* dans **SQLBindCol**.  
  
     **SQLFetch n’tronque** jamais les données converties en types de données à durée fixe; il suppose toujours que la longueur du tampon de données est la taille du type de données.  
  
5.  Place les données converties (et peut-être tronquées) dans le tampon de données. Pour plus d’informations sur la façon de déterminer l’adresse du tampon de données, voir "Buffer Addresses" dans [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
6.  Place la longueur des données dans le tampon longueur/indicateur. Si le pointeur d’indicateur et le pointeur de longueur ont tous deux été réglés vers le même tampon (comme le fait un appel à **SQLBindCol),** la longueur est écrite dans le tampon pour les données valides et SQL_NULL_DATA est écrit dans le tampon pour les données NULL. Si aucun tampon de longueur/indicateur n’a été lié, **SQLFetch** ne retourne pas la longueur.  
  
    -   Pour les données de caractère ou binaires, c’est la longueur des données après la conversion et avant la troncation en raison de la mémoire tampon de données étant trop petite. Si le conducteur ne peut pas déterminer la longueur des données après la conversion, comme c’est parfois le cas avec de longues données, il définit la longueur à SQL_NO_TOTAL. Si les données ont été tronquées en raison de l’attribut de l’SQL_ATTR_MAX_LENGTH énoncé, la valeur de cet attribut est mise dans le tampon longueur/indicateur au lieu de la longueur réelle . C’est parce que cet attribut est conçu pour tronquer les données sur le serveur avant la conversion, de sorte que le pilote n’a aucun moyen de comprendre quelle est la longueur réelle.  
  
    -   Pour tous les autres types de données, c’est la longueur des données après la conversion; c’est-à-dire que c’est la taille du type auquel les données ont été converties.  
  
     Pour obtenir de l’information sur la façon de déterminer l’adresse du tampon de longueur/indicateur, voir « Adresses tampons » dans [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
7.  Si les données sont tronquées lors de la conversion sans perte de chiffres significatifs (par exemple, le nombre réel 1.234 est tronqué à l’intégrant 1 une fois converti), **SQLFetch** retourne SQLSTATE 01S07 (tronc fractionnel) et SQL_SUCCESS_WITH_INFO. Si les données sont tronquées parce que la longueur du tampon de données est trop petite (par exemple, la chaîne "abcdef" est mise dans un tampon de 4-byte), **SQLFetch** retourne SQLSTATE 01004 (Data tronqué) et SQL_SUCCESS_WITH_INFO. Si les données sont tronquées en raison de l’attribut de l’SQL_ATTR_MAX_LENGTH déclaration, **SQLFetch** renvoie SQL_SUCCESS et ne renvoie pas SQLSTATE 01S07 (tronc fractionnel) ou SQLSTATE 01004 (Data tronqué). Si les données sont tronquées lors de la conversion avec une perte de chiffres significatifs (par exemple, si une valeur SQL_INTEGER supérieure à 100 000 ont été converties en SQL_C_TINYINT), **SQLFetch** retourne SQLSTATE 22003 (valeur numérique hors de portée) et SQL_ERROR (si la taille de l’aviron est de 1) ou SQL_SUCCESS_WITH_INFO (si la taille de la ligne est supérieure à 1).  
  
 Le contenu du tampon de données consolidé et le tampon longueur/indicateur ne sont pas définis si **SQLFetch** ou **SQLFetchScroll** ne retournent pas SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO.  
  
## <a name="row-status-array"></a>Tableau d’état des lignes  
 Le tableau d’état de la ligne est utilisé pour retourner l’état de chaque rangée dans le ramage. L’adresse de ce tableau est spécifiée avec l’attribut SQL_ATTR_ROW_STATUS_PTR déclaration. Le tableau est attribué par l’application et doit avoir autant d’éléments que spécifiés par l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration. Ses valeurs sont fixées par **SQLFetch**, **SQLFetchScroll**, et **SQLBulkOperations** ou **SQLSetPos** (sauf lorsqu’ils ont été appelés après que le curseur a été positionné par **SQLExtendedFetch**). Si la valeur de l’attribut de l’SQL_ATTR_ROW_STATUS_PTR’énoncé est un pointeur nul, ces fonctions ne retournent pas le statut de la ligne.  
  
 Le contenu du tampon de l’état de la rangée n’est pas défini si **SQLFetch** ou **SQLFetchScroll** ne retourne pas SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO.  
  
 Les valeurs suivantes sont retournées dans le tableau d’état de la ligne.  
  
|Valeur du tableau d’état de ligne|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|La ligne a été récupérée avec succès et n’a pas changé depuis qu’il a été récupéré pour la dernière fois de cet ensemble de résultats.|  
|SQL_ROW_SUCCESS_WITH_INFO|La ligne a été récupérée avec succès et n’a pas changé depuis qu’il a été récupéré pour la dernière fois de cet ensemble de résultats. Cependant, un avertissement a été retourné au sujet de la rangée.|  
|SQL_ROW_ERROR|Une erreur s’est produite en allant chercher la rangée.|  
|SQL_ROW_UPDATED[1],[2], et [3]|La ligne a été récupérée avec succès et a changé depuis qu’il a été récupéré pour la dernière fois de cet ensemble de résultats. Si la ligne est récupérée à nouveau à partir de cet ensemble de résultat ou est rafraîchie par **SQLSetPos**, le statut est changé pour le nouveau statut de la ligne.|  
|SQL_ROW_DELETED[3]|La ligne a été supprimée depuis qu’il a été récupéré pour la dernière fois à partir de cet ensemble de résultats.|  
|SQL_ROW_ADDED[4]|La rangée a été insérée par **SQLBulkOperations**. Si la ligne est récupérée à nouveau à partir de cet ensemble de résultat ou est rafraîchie par **SQLSetPos**, son statut est SQL_ROW_SUCCESS.|  
|SQL_ROW_NOROW|Le jeu de ligne chevauchait la fin de l’ensemble de résultats, et aucune ligne n’a été retournée qui correspondait à cet élément du tableau d’état de la ligne.|  
  
 [1] Pour les curseurs keyset, mixtes et dynamiques, si une valeur clé est mise à jour, la rangée de données est considérée comme ayant été supprimée et une nouvelle ligne ajoutée.  
  
 [2] Certains conducteurs ne peuvent pas détecter les mises à jour des données et ne peuvent donc pas retourner cette valeur. Pour déterminer si un conducteur peut détecter les mises à jour des lignes recadrées, une application appelle **SQLGetInfo** avec l’option SQL_ROW_UPDATES.  
  
 [3] **SQLFetch** ne peut retourner cette valeur que lorsqu’elle est mélangée avec des appels à **SQLFetchScroll**. C’est parce que **SQLFetch** avance à travers l’ensemble de résultats et quand il est utilisé exclusivement, ne refetch aucune ligne. Étant donné qu’aucune ligne n’est refoûtée, **SQLFetch** ne détecte pas les changements qui ont été apportés aux rangées précédemment récupérées. Toutefois, si **SQLFetchScroll** positionne le curseur avant que les rangées précédemment récupérées et **SQLFetch** soient utilisées pour aller chercher ces rangées, **SQLFetch** peut détecter tout changement à ces lignes.  
  
 [4] Retourné par SQLBulkOperations seulement. Non réglé par **SQLFetch** ou **SQLFetchScroll**.  
  
### <a name="rows-fetched-buffer"></a>Lignes Fetched Buffer  
 Le tampon récupéré par les rangées est utilisé pour retourner le nombre de rangées récupérées, y compris les rangées pour lesquelles aucune donnée n’a été retournée parce qu’une erreur s’est produite pendant qu’elles étaient récupérées. En d’autres termes, c’est le nombre de lignes pour lesquelles la valeur dans le tableau d’état de la ligne n’est pas SQL_ROW_NOROW. L’adresse de ce tampon est spécifiée avec l’attribut SQL_ATTR_ROWS_FETCHED_PTR déclaration. Le tampon est attribué par l’application. Il est fixé par **SQLFetch** et **SQLFetchScroll**. Si la valeur de l’attribut de l’SQL_ATTR_ROWS_FETCHED_PTR’énoncé est un pointeur nul, ces fonctions ne renvoient pas le nombre de lignes récupérées. Pour déterminer le nombre de la ligne actuelle dans l’ensemble de résultats, une application peut appeler **SQLGetStmtAttr** avec l’attribut SQL_ATTR_ROW_NUMBER.  
  
 Le contenu des rangées récupérées tampon sont indéfinis si **SQLFetch** ou **SQLFetchScroll** ne retourne pas SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, sauf lorsque SQL_NO_DATA est retourné, auquel cas la valeur dans les rangées tampon récupéré est fixé à 0.  
  
### <a name="error-handling"></a>Gestion des erreurs  
 Les erreurs et les avertissements peuvent s’appliquer à des lignes individuelles ou à l’ensemble de la fonction. Pour plus d’informations sur les [dossiers diagnostiques,](../../../odbc/reference/develop-app/diagnostics.md) voir Diagnostics et [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
#### <a name="errors-and-warnings-on-the-entire-function"></a>Erreurs et avertissements sur l’ensemble de la fonction  
 Si une erreur s’applique à l’ensemble de la fonction, comme SQLSTATE HYT00 (Timeout expired) ou SQLSTATE 24000 (État de curseur invalide), **SQLFetch** retourne SQL_ERROR et le SQLSTATE applicable. Le contenu des tampons encastrés est indéfini et la position du curseur est inchangée.  
  
 Si un avertissement s’applique à l’ensemble de la fonction, **SQLFetch** retourne SQL_SUCCESS_WITH_INFO et le SQLSTATE applicable. Les registres d’état pour les avertissements qui s’appliquent à l’ensemble de la fonction sont retournés avant les registres d’état qui s’appliquent aux rangées individuelles.  
  
#### <a name="errors-and-warnings-in-individual-rows"></a>Erreurs et avertissements dans les rangées individuelles  
 Si une erreur (comme SQLSTATE 22012 (Division par zéro)) ou un avertissement (comme SQLSTATE 01004 (Data tronqué)) s’applique à une seule rangée, **SQLFetch**fait ce qui suit :  
  
-   Définit l’élément correspondant du tableau d’état de la ligne pour SQL_ROW_ERROR pour les erreurs ou SQL_ROW_SUCCESS_WITH_INFO pour les avertissements.  
  
-   Ajoute des enregistrements d’état nuls ou plus qui contiennent SQLSTATEs pour l’erreur ou l’avertissement.  
  
-   Définit les champs de nombre de rangées et de colonnes dans les registres d’état. Si **SQLFetch** ne peut pas déterminer un numéro de ligne ou de colonne, il définit ce nombre à SQL_ROW_NUMBER_UNKNOWN ou SQL_COLUMN_NUMBER_UNKNOWN, respectivement. Si l’enregistrement d’état ne s’applique pas à une colonne particulière, **SQLFetch** définit le numéro de colonne à SQL_NO_COLUMN_NUMBER.  
  
 **SQLFetch** continue d’aller chercher des rangées jusqu’à ce qu’il ait récupéré toutes les rangées dans le ramage. Il renvoie SQL_SUCCESS_WITH_INFO à moins qu’une erreur ne se produise dans chaque rangée de l’aviron (sans compter les lignes avec le statut SQL_ROW_NOROW), auquel cas il retourne SQL_ERROR. En particulier, si la taille de l’aviron est de 1 et qu’une erreur se produit dans cette rangée, **SQLFetch** renvoie SQL_ERROR.  
  
 **SQLFetch** retourne les registres d’état dans l’ordre de numéro de rangée. Autrement dit, il retourne tous les enregistrements d’état pour les rangées inconnues (le cas échéant); ensuite, il retourne tous les enregistrements d’état pour la première rangée (le cas échéant), puis il retourne tous les enregistrements d’état pour la deuxième rangée (le cas échéant), et ainsi de suite. Les registres d’état de chaque rangée sont commandés conformément aux règles normales pour commander les dossiers d’état; pour plus d’informations, voir "Sequence of Status Records" dans [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
### <a name="descriptors-and-sqlfetch"></a>Descripteurs et SQLFetch  
 Les sections suivantes décrivent comment **SQLFetch** interagit avec les descripteurs.  
  
#### <a name="argument-mappings"></a>Cartographies d’argument  
 Le conducteur ne fixe aucun champ descripteur sur la base des arguments de **SQLFetch**.  
  
#### <a name="other-descriptor-fields"></a>Autres champs descripteur  
 Les champs descripteur suivants sont utilisés par **SQLFetch**.  
  
|Champ de descripteur|Desc.|Champ dans|Définir à travers|  
|----------------------|-----------|--------------|-----------------|  
|SQL_DESC_ARRAY_SIZE|Ard|en-tête|attribut de déclaration SQL_ATTR_ROW_ARRAY_SIZE|  
|SQL_DESC_ARRAY_STATUS_PTR|Ird|en-tête|attribut de déclaration SQL_ATTR_ROW_STATUS_PTR|  
|SQL_DESC_BIND_OFFSET_PTR|Ard|en-tête|attribut de déclaration SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_DESC_BIND_TYPE|Ard|en-tête|attribut de déclaration SQL_ATTR_ROW_BIND_TYPE|  
|SQL_DESC_COUNT|Ard|en-tête|*Argument de La Colonnenbre* de **SQLBindCol**|  
|SQL_DESC_DATA_PTR|Ard|enregistrements|*TargetValuePtr* argument de **SQLBindCol**|  
|SQL_DESC_INDICATOR_PTR|Ard|enregistrements|*StrLen_or_IndPtr* argument dans **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH|Ard|enregistrements|*Argument de BufferLength* dans **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH_PTR|Ard|enregistrements|*StrLen_or_IndPtr* argument dans **SQLBindCol**|  
|SQL_DESC_ROWS_PROCESSED_PTR|Ird|en-tête|attribut de déclaration SQL_ATTR_ROWS_FETCHED_PTR|  
|SQL_DESC_TYPE|Ard|enregistrements|*Argument de TargetType* dans **SQLBindCol**|  
  
 Tous les champs descripteur peuvent également être réglés par **SQLSetDescField**.  
  
#### <a name="separate-length-and-indicator-buffers"></a>Lignes tampons de longueur et d’indicateurs séparées  
 Les applications peuvent lier un seul tampon ou deux tampons distincts qui peuvent être utilisés pour contenir la longueur et les valeurs des indicateurs. Lorsqu’une demande appelle **SQLBindCol**, le conducteur fixe les champs SQL_DESC_OCTET_LENGTH_PTR et SQL_DESC_INDICATOR_PTR de l’ARD à la même adresse, qui est transmise dans *l’argument StrLen_or_IndPtr.* Lorsqu’une application appelle **SQLSetDescField** ou **SQLSetDescRec,** elle peut définir ces deux champs à des adresses différentes.  
  
 **SQLFetch** détermine si l’application a spécifié des tampons de longueur et d’indicateur distincts. Dans ce cas, lorsque les données ne sont pas NULL, **SQLFetch** définit le tampon indicateur à 0 et retourne la longueur dans le tampon de longueur. Lorsque les données sont NULL, **SQLFetch** définit le tampon indicateur pour SQL_NULL_DATA et ne modifie pas le tampon de longueur.  
  
### <a name="code-example"></a>Exemple de code  
 Voir [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md), et [SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md).  
  
### <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Informations de retour sur une colonne dans un ensemble de résultats|[Fonction SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Fermeture du curseur sur la déclaration|[Fonction SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Aller chercher une partie ou la totalité d’une colonne de données|[Fonction SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Retour du nombre de colonnes de jeu de résultats|[Fonction SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Préparation d’une déclaration pour l’exécution|[Fonction SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
