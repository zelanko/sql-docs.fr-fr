---
title: Fonction SQLGetData (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetData
helpviewer_keywords:
- SQLGetData function [ODBC]
ms.assetid: e3c1356a-5db7-4186-85fd-8b74633317e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac11505b8e47dae8df53af27c64a7ee6372b3f28
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285505"
---
# <a name="sqlgetdata-function"></a>Fonction SQLGetData
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetData** récupère des données pour une seule colonne dans l’ensemble de résultat ou pour un seul paramètre après le retour **de SQLParamData** SQL_PARAM_DATA_AVAILABLE. Il peut être appelé plusieurs fois pour récupérer des données à durée variable dans les pièces.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetData(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   Col_or_Param_Num,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_IndPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Col_or_Param_Num*  
 [Entrée] Pour la récupération des données de colonne, c’est le nombre de la colonne pour laquelle retourner les données. Les colonnes de jeu de résultat sont numérotées dans l’ordre de colonne croissant à partir de 1. La colonne de signets est la colonne numéro 0; cela ne peut être spécifié que si des signets sont activés.  
  
 Pour la récupération des données de paramètres, c’est l’ordinaire du paramètre, qui commence à 1.  
  
 *Targettype*  
 [Entrée] Le type d’identifiant du type de données C du tampon*TargetValuePtr.* Pour une liste de types de données C valides et d’identifiants de type, consultez la section [Types de données C](../../../odbc/reference/appendixes/c-data-types.md) dans l’annexe D : Data Types.  
  
 Si *TargetType* est SQL_ARD_TYPE, le conducteur utilise l’identifiant de type spécifié dans le champ SQL_DESC_CONCISE_TYPE de l’ARD. Si *TargetType* est SQL_APD_TYPE, **SQLGetData** utilisera le même type de données C qui a été spécifié dans **SQLBindParameter**. Dans le cas contraire, le type de données C spécifié dans **SQLGetData** remplace le type de données C spécifié dans **SQLBindParameter**. S’il est SQL_C_DEFAULT, le conducteur sélectionne le type de données C par défaut en fonction du type de données SQL de la source.  
  
 Vous pouvez également spécifier un type de données C étendu. Pour plus d’informations, voir [C Data Types in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr (en)*  
 [Sortie] Pointeur vers le tampon dans lequel retourner les données.  
  
 *TargetValuePtr* ne peut pas être NULL.  
  
 *BufferLength*  
 [Entrée] Longueur du tampon*TargetValuePtr* dans les octets.  
  
 Le pilote utilise *BufferLength* pour éviter \*d’écrire au-delà de la fin du tampon *TargetValuePtr* lors du retour des données à longueur variable, telles que les données de caractère ou binaires. Notez que le conducteur compte le caractère \*de non-termination lors du retour des données de caractère à *TargetValuePtr*. **TargetValuePtr* doit donc contenir de l’espace pour le caractère de non-termination, ou le conducteur tronque les données.  
  
 Lorsque le conducteur retourne des données de longueur fixe, comme un intégrateur ou une structure de date, le conducteur ignore *BufferLength* et suppose que le tampon est assez grand pour contenir les données. Il est donc important que l’application alloue un tampon suffisamment grand pour les données à durée fixe ou que le conducteur écrira au-delà de la fin du tampon.  
  
 **SQLGetData** retourne SQLSTATE HY090 (longueur de chaîne ou tampon invalide) lorsque *BufferLength* est inférieur à 0, mais pas lorsque *BufferLength* est 0.  
  
 *StrLen_or_IndPtr*  
 [Sortie] Pointeur vers le tampon dans lequel retourner la longueur ou la valeur de l’indicateur. S’il s’agit d’un pointeur nul, aucune longueur ou valeur d’indicateur n’est retournée. Cela renvoie une erreur lorsque les données récupérées sont NULL.  
  
 **SQLGetData** peut retourner les valeurs suivantes dans le tampon longueur/indicateur :  
  
-   La durée des données disponibles pour revenir  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Pour plus d’informations, voir [Utilisation de la longueur/indicateurs valeurs](../../../odbc/reference/develop-app/using-length-and-indicator-values.md) et des «commentaires» dans ce sujet.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetData** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLGetData** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Toutes les données de la colonne spécifiée, *Col_or_Param_Num,* ne pouvaient pas être récupérées en un seul appel à la fonction. SQL_NO_TOTAL ou la longueur des données restantes dans la colonne spécifiée avant l’appel \*actuel à **SQLGetData** est retournée en *StrLen_or_IndPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)<br /><br /> Pour plus d’informations sur l’utilisation de plusieurs appels à **SQLGetData** pour une seule colonne, voir "Commentaires".|  
|01S07|Troncation fractionnaire|Les données retournées pour une ou plusieurs colonnes ont été tronquées. Pour les types de données numériques, la partie fractionnaire du nombre a été tronquée. Pour le temps, l’humidité du temps et les types de données d’intervalle contenant un composant de temps, la partie fractionnelle du temps a été tronquée.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|La valeur de données d’une colonne dans l’ensemble de résultat ne peut pas être convertie au type de données C spécifié par l’argument *TargetType*.|  
|07009|Indice descripteur invalide|La valeur spécifiée pour l’argument *Col_or_Param_Num* était de 0, et l’attribut de déclaration SQL_ATTR_USE_BOOKMARKS a été réglé pour SQL_UB_OFF.<br /><br /> La valeur spécifiée pour l’argument *Col_or_Param_Num* était supérieure au nombre de colonnes dans l’ensemble de résultats.<br /><br /> La *valeur Col_or_Param_Num* n’était pas égale à l’ordinaire du paramètre disponible.<br /><br /> (DM) La colonne spécifiée était liée. Cette description ne s’applique pas aux conducteurs qui retournent le SQL_GD_BOUND le bitmask pour l’option SQL_GETDATA_EXTENSIONS dans **SQLGetInfo**.<br /><br /> (DM) Le nombre de colonne spécifiée était inférieur ou égal au nombre de colonnes les plus hautes. Cette description ne s’applique pas aux conducteurs qui retournent le SQL_GD_ANY_COLUMN le bitmask pour l’option SQL_GETDATA_EXTENSIONS dans **SQLGetInfo**.<br /><br /> (DM) L’application a déjà appelé **SQLGetData** pour la rangée actuelle; le nombre de colonne spécifié dans l’appel en cours était inférieur au numéro de la colonne spécifiée dans l’appel précédent; et le conducteur ne retourne pas le SQL_GD_ANY_ORDER le bitmask pour l’option SQL_GETDATA_EXTENSIONS dans **SQLGetInfo**.<br /><br /> (DM) L’argument *de TargetType* était SQL_ARD_TYPE, et *le* Col_or_Param_Num dossier descripteur dans l’ARD a échoué à la vérification de cohérence.<br /><br /> (DM) L’argument *de TargetType* était SQL_ARD_TYPE, et la valeur dans le domaine SQL_DESC_COUNT de l’ARD était inférieure à *l’argument Col_or_Param_Num.*|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|22002|Variable d’indicateur requise mais non fournie|*StrLen_or_IndPtr* était un pointeur nul et les données NULL ont été récupérées.|  
|22003|Valeur numérique hors de portée|Le retour de la valeur numérique (en tant que numérique ou chaîne) pour la colonne aurait fait tronquer la partie entière (par opposition à fractionnement) du nombre.<br /><br /> Pour plus d’informations, voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Format de date invalide|La colonne de caractère dans l’ensemble de résultat était liée à une date, heure ou structure de timetamp C, et la valeur dans la colonne était une date, un heure ou un fuseur horaires non valides, respectivement. Pour plus d’informations, voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22012|Division par zéro|Une valeur d’une expression arithmétique qui a abouti à la division par zéro a été retournée.|  
|22015|Débordement de champ d’intervalle|L’attribution d’un type SQL numérique ou d’intervalle exact à un type d’intervalle C a causé une perte de chiffres significatifs dans le champ principal.<br /><br /> Lorsque vous revenez les données à un type d’intervalle C, il n’y avait aucune représentation de la valeur du type SQL dans le type d’intervalle C.|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|Une colonne de caractère dans l’ensemble de résultat a été retournée à un tampon de caractère C, et la colonne contenait un caractère pour lequel il n’y avait aucune représentation dans l’ensemble de caractères du tampon.<br /><br /> Le type C était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type SQL de la colonne était un type de données de caractère; et la valeur de la colonne n’était pas un littéral valide du type C lié.|  
|24 000|État de curseur non valide|(DM) La fonction a été appelée sans appeler d’abord **SQLFetch** ou **SQLFetchScroll** pour positionner le curseur sur la rangée de données requises.<br /><br /> (DM) Le *StatementHandle* était dans un état exécuté, mais aucun ensemble de résultats n’a été associé à la *DéclarationHandle*.<br /><br /> Un curseur était ouvert sur le *StatementHandle* et **SQLFetch** ou **SQLFetchScroll** avaient été appelés, mais le curseur a été positionné avant le début de l’ensemble de résultats ou après la fin de l’ensemble de résultats.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le tampon *MessageText* décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY003 (HY003)|Type de programme hors de portée|(DM) L’argument *TargetType* n’était pas un type de données valide, SQL_C_DEFAULT, SQL_ARD_TYPE (en cas de récupération des données de colonne), ou SQL_APD_TYPE (en cas de récupération des données de paramètres).<br /><br /> (DM) *L’argument Col_or_Param_Num* était 0, et l’argument *TargetType* n’était pas SQL_C_BOOKMARK pour un signet fixe ou SQL_C_VARBOOKMARK pour un signet à longueur variable.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*, puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli, puis la fonction a été appelée à nouveau sur le *StatementHandle*.|  
|HY009|Utilisation invalide du pointeur nul|(DM) L’argument *TargetValuePtr* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Le *statementhandle* spécifié n’était pas dans un état exécuté. La fonction a été appelée sans appeler **d’abord SQLExecDirect**, **SQLExecute** ou une fonction de catalogue.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLGetData** a été appelée.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Le *StatementHandle* était dans un état exécuté, mais aucun ensemble de résultats n’a été associé à la *DéclarationHandle*.<br /><br /> Un appel à **SQLExeceute**, **SQLExecDirect**, ou **SQLMoreResults** retourné SQL_PARAM_DATA_AVAILABLE, mais **SQLGetData** a été appelé, au lieu de **SQLParamData**.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.<br /><br /> La valeur spécifiée pour l’argument *BufferLength* était inférieure à 4, *l’argument Col_or_Param_Num* a été réglé à 0, et le conducteur était un conducteur ODBC 2 *.x.*|  
|HY109 HY109|Position de curseur invalide|Le curseur a été positionné (par **SQLSetPos**, **SQLFetch**, **SQLFetchScroll**, ou **SQLBulkOperations**) sur une rangée qui avait été supprimée ou ne pouvait pas être récupérée.<br /><br /> Le curseur était un curseur avant-seulement, et la taille de rowset était supérieure à un.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données ne prend pas en charge l’utilisation de **SQLGetData** avec plusieurs lignes dans **SQLFetchScroll**. Cette description ne s’applique pas aux conducteurs qui retournent le SQL_GD_BLOCK le bitmask pour l’option SQL_GETDATA_EXTENSIONS dans **SQLGetInfo**.<br /><br /> Le conducteur ou la source de données ne prend pas en charge la conversion spécifiée par la combinaison de l’argument *TargetType* et du type de données SQL de la colonne correspondante. Cette erreur ne s’applique que lorsque le type de données SQL de la colonne a été cartographié à un type de données SQL spécifique au conducteur.<br /><br /> Le conducteur ne prend en charge que ODBC 2 *.x*, et l’argument *TargetType* était l’un des suivants:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> et n’importe lequel des types de données D’intervalle répertoriés dans [les types de données C](../../../odbc/reference/appendixes/c-data-types.md) de l’Annexe D : Types de données.<br /><br /> Le conducteur ne prend en charge les versions ODBC avant 3.50, et l’argument *TargetType* a été SQL_C_GUID.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur correspondant à la *DéclarationHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLGetData** renvoie les données dans une colonne spécifiée. **SQLGetData** ne peut être appelé qu’après qu’une ou plusieurs rangées ont été récupérées à partir du résultat établi par **SQLFetch**, **SQLFetchScroll**, ou **SQLExtendedFetch**. Si les données à durée variable sont trop grandes pour être retournées en un seul appel à **SQLGetData** (en raison d’une limitation de l’application), **SQLGetData** peut les récupérer en pièces détachées. Il est possible de lier certaines colonnes d’affilée et d’appeler **SQLGetData** pour d’autres, bien que cela soit soumis à certaines restrictions. Pour plus d’informations, voir [Getting Long Data](../../../odbc/reference/develop-app/getting-long-data.md).  
  
 Pour plus d’informations sur l’utilisation **de SQLGetData** avec paramètres de sortie en streaming, voir [Paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-sqlgetdata"></a>Utilisation de SQLGetData  
 Si le conducteur ne prend pas en charge les extensions de **SQLGetData**, la fonction ne peut retourner les données que pour les colonnes non liées avec un nombre supérieur à celui de la dernière colonne liée. De plus, dans une rangée de données, la valeur de *l’argument Col_or_Param_Num* dans chaque appel à **SQLGetData** doit être supérieure ou égale à la valeur de *Col_or_Param_Num* dans l’appel précédent; c’est-à-dire que les données doivent être récupérées dans l’ordre croissant du nombre de colonnes. Enfin, si aucune extension n’est supportée, **SQLGetData** ne peut pas être appelé si la taille de la ligne est supérieure à 1.  
  
 Les conducteurs peuvent assouplir l’une de ces restrictions. Pour déterminer quelles restrictions un conducteur se détend, une application appelle **SQLGetInfo** avec l’une des options de SQL_GETDATA_EXTENSIONS suivantes :  
  
-   SQL_GD_OUTPUT_PARAMS - **SQLGetData** peut être appelé à retourner les valeurs de paramètres de sortie. Pour plus d’informations, voir [Paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_GD_ANY_COLUMN. Si cette option est retournée, **SQLGetData** peut être appelé pour n’importe quelle colonne non liée, y compris celles avant la dernière colonne liée.  
  
-   SQL_GD_ANY_ORDER. Si cette option est retournée, **SQLGetData** peut être appelé pour des colonnes non liées dans n’importe quel ordre.  
  
-   SQL_GD_BLOCK. Si cette option est retournée par **SQLGetInfo** pour la SQL_GETDATA_EXTENSIONS InfoType, le conducteur prend en charge les appels à **SQLGetData** lorsque la taille de l’aviron est supérieure à 1 et que l’application peut appeler **SQLSetPos** avec la SQL_POSITION option de positionner le curseur sur la ligne correcte avant d’appeler **SQLGetData.**  
  
-   SQL_GD_BOUND. Si cette option est retournée, **SQLGetData** peut être appelé pour les colonnes liées ainsi que les colonnes non liées.  
  
 Il y a deux exceptions à ces restrictions et la capacité d’un conducteur à les assouplir. Tout d’abord, **SQLGetData** ne devrait jamais être appelé pour un curseur avant seulement lorsque la taille de l’aviron est supérieure à 1. Deuxièmement, si un conducteur prend en charge les signets, il doit toujours prendre en charge la possibilité d’appeler **SQLGetData** pour la colonne 0, même s’il ne permet pas aux applications d’appeler **SQLGetData** pour d’autres colonnes avant la dernière colonne liée. (Lorsqu’une application travaille avec un conducteur ODBC 2 *.x,* **SQLGetData** retournera avec succès un signet lorsqu’il est appelé avec *Col_or_Param_Num* égal à 0 après un appel à **SQLFetch**, parce que **SQLFetch** est cartographié par l’ODBC 3 *.x* Driver Manager à **SQLExtendedFetch** avec une *FetchOrientation* de SQL_FETCH_NEXT, et **SQLGetData** avec un *Col_or_Param_Num* de 0 est cartographié par l’ODBC 3 *.x* Driver Manager à **SQLGetStmtOption** avec une *fOption* de SQL_GET_BOOKMARK.)  
  
 **SQLGetData** ne peut pas être utilisé pour récupérer le signet d’une rangée juste insérée en appelant **SQLBulkOperations** avec l’option SQL_ADD, parce que le curseur n’est pas positionné sur la rangée. Une application peut récupérer le signet d’une telle ligne en liant la colonne 0 avant d’appeler **SQLBulkOperations** avec SQL_ADD, auquel cas **SQLBulkOperations** retourne le signet dans le tampon lié. **SQLFetchScroll** peut alors être appelé avec SQL_FETCH_BOOKMARK pour repositionner le curseur sur cette rangée.  
  
 Si l’argument *de TargetType* est un type de données d’intervalle, l’intervalle par défaut menant la précision (2) et l’intervalle par défaut secondes de précision (6), tel qu’indiqué dans les champs SQL_DESC_DATETIME_INTERVAL_PRECISION et SQL_DESC_PRECISION de l’ARD, respectivement, sont utilisés pour les données. Si l’argument *de TargetType* est un type de données SQL_C_NUMERIC, la précision par défaut (définie par le conducteur) et l’échelle par défaut (0), telle qu’elle est définie dans les champs SQL_DESC_PRECISION et SQL_DESC_SCALE de l’ARD, sont utilisées pour les données. Si une précision ou une échelle par défaut n’est pas appropriée, l’application doit définir explicitement le champ descripteur approprié par un appel à **SQLSetDescField** ou **SQLSetDescRec**. Il peut définir le champ SQL_DESC_CONCISE_TYPE pour SQL_C_NUMERIC et appeler **SQLGetData** avec un argument *TargetType* de SQL_ARD_TYPE, ce qui entraînera la précision et les valeurs d’échelle dans les champs descripteur à utiliser.  
  
> [!NOTE]
>  Dans ODBC 2 *.x*, les applications fixent *TargetType* pour SQL_C_DATE, SQL_C_TIME ou \*SQL_C_TIMESTAMP pour indiquer que *TargetValuePtr* est une structure de date, d’heure ou d’arrêt. Dans ODBC 3 *.x*, les applications fixent *TargetType* à SQL_C_TYPE_DATE, SQL_C_TYPE_TIME ou SQL_C_TYPE_TIMESTAMP. Le Driver Manager effectue des cartes appropriées si nécessaire, en fonction de l’application et de la version du conducteur.  
  
## <a name="retrieving-variable-length-data-in-parts"></a>Récupération des données variables dans les pièces  
 **SQLGetData** peut être utilisé pour récupérer des données d’une colonne qui contient des données à durée variable dans les pièces - c’est-à-dire lorsque l’identifiant du type de données SQL de la colonne est SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_WCHAR, SQL_WVARCHAR, SQL_WLONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY, ou un identifiant spécifique au conducteur pour un type à longueur variable.  
  
 Pour récupérer les données d’une colonne en pièces, l’application appelle **SQLGetData** plusieurs fois consécutive pour la même colonne. À chaque appel, **SQLGetData** renvoie la partie suivante des données. Il appartient à l’application de remonter les pièces, en prenant soin de supprimer le caractère de non-terminaison des parties intermédiaires des données de caractère. S’il y a plus de données à retourner ou pas assez de tampon a été alloué pour le caractère de fin, **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (Données tronquées). Lorsqu’il renvoie la dernière partie des données, **SQLGetData** retourne SQL_SUCCESS. Ni SQL_NO_TOTAL ni zéro ne peuvent être retournés sur le dernier appel valide pour récupérer les données d’une colonne, car l’application n’aurait alors aucun moyen de savoir quelle quantité de données dans le tampon d’application est valide. Si **SQLGetData** est appelé après cela, il revient SQL_NO_DATA. Pour plus d’informations, voir la section suivante, "Récupérer des données avec SQLGetData."  
  
 Les signets de longueur variable peuvent être retournés en pièces par **SQLGetData**. Comme pour d’autres données, un appel à **SQLGetData** pour retourner les signets à longueur variable dans les pièces retournera SQLSTATE 01004 (données de cordes, droite tronquée) et SQL_SUCCESS_WITH_INFO quand il y a plus de données à retourner. C’est différent du cas où un signet à longueur variable est tronqué par un appel à **SQLFetch** ou **SQLFetchScroll**, qui revient SQL_ERROR et SQLSTATE 22001 (données de cordes, à droite tronquées).  
  
 **SQLGetData** ne peut pas être utilisé pour retourner les données à durée fixe dans les pièces. Si **SQLGetData** est appelé plus d’une fois dans une rangée pour une colonne contenant des données de longueur fixe, il retourne SQL_NO_DATA pour tous les appels après le premier.  
  
## <a name="retrieving-streamed-output-parameters"></a>Récupération des paramètres de sortie en continu  
 Si un pilote prend en charge les paramètres de sortie en continu, une application peut appeler **SQLGetData** avec un petit tampon plusieurs fois pour récupérer une grande valeur de paramètre. Pour plus d’informations sur le paramètre de sortie en streaming, voir [Paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="retrieving-data-with-sqlgetdata"></a>Récupération des données avec SQLGetData  
 Pour retourner les données de la colonne spécifiée, **SQLGetData** effectue la séquence suivante d’étapes :  
  
1.  Retourne SQL_NO_DATA s’il a déjà retourné toutes les données pour la colonne.  
  
2.  Définit \* *StrLen_or_IndPtr* pour SQL_NULL_DATA si les données sont NULL. Si les données sont NULL et *StrLen_or_IndPtr* était un pointeur nul, **SQLGetData** retourne SQLSTATE 22002 (variable d’indicateur requise mais non fournie).  
  
     Si les données de la colonne ne sont pas NULL, **SQLGetData** procède à l’étape 3.  
  
3.  Si l’attribut de l’SQL_ATTR_MAX_LENGTH déclaration est réglé à une valeur non zéro, si la colonne contient des données de caractère ou binaires, et si **SQLGetData** n’a pas été précédemment appelé pour la colonne, les données sont tronquées à SQL_ATTR_MAX_LENGTH octets.  
  
    > [!NOTE]  
    >  L’attribut de l’SQL_ATTR_MAX_LENGTH’énoncé vise à réduire le trafic réseau. Il est généralement implémenté par la source de données, ce qui tronque les données avant de les retourner sur l’ensemble du réseau. Les conducteurs et les sources de données ne sont pas tenus de l’appuyer. Par conséquent, pour garantir que les données sont tronquées à une taille particulière, une application devrait allouer un tampon de cette taille et spécifier la taille de l’argument *BufferLength.*  
  
4.  Convertit les données au type spécifié dans *TargetType*. Les données sont données la précision par défaut et l’échelle pour ce type de données. Si *TargetType* est SQL_ARD_TYPE, le type de données dans le champ SQL_DESC_CONCISE_TYPE de l’ARD est utilisé. Si *TargetType* est SQL_ARD_TYPE, les données sont données la précision et l’échelle dans les champs SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION et SQL_DESC_SCALE de l’ARD, selon le type de données dans le champ SQL_DESC_CONCISE_TYPE. Si une précision ou une échelle par défaut n’est pas appropriée, l’application doit définir explicitement le champ descripteur approprié par un appel à **SQLSetDescField** ou **SQLSetDescRec**.  
  
5.  Si les données ont été converties en un type de données à durée variable, comme le caractère ou **binaire, SQLGetData** vérifie si la longueur des données dépasse *BufferLength*. Si la longueur des données de caractère (y compris le caractère de résiliation nulle) dépasse *BufferLength*, **SQLGetData** tronque les données à *BufferLength* moins la longueur d’un caractère de résiliation nulle. Il met ensuite fin aux données. Si la longueur des données binaires dépasse la longueur du tampon de données, **SQLGetData** la tronque aux octets *de BufferLength.*  
  
     Si le tampon de données fourni est trop petit pour conserver le caractère de résiliation nulle, **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004.  
  
     **SQLGetData** n’tronque jamais les données converties en types de données à durée fixe; il suppose toujours que la longueur de*TargetValuePtr* est la taille du type de données.  
  
6.  Place les données converties (et éventuellement \*tronquées) dans *TargetValuePtr*. Notez que **SQLGetData** ne peut pas retourner les données hors de la ligne.  
  
7.  Place la longueur des \*données dans *StrLen_or_IndPtr*. Si *StrLen_or_IndPtr* était un pointeur nul, **SQLGetData** ne retourne pas la longueur.  
  
    -   Pour les données de caractère ou binaires, c’est la longueur des données après la conversion et avant la troncation due à *BufferLength*. Si le conducteur ne peut pas déterminer la longueur des données après la conversion, comme c’est parfois le cas avec de longues données, il renvoie SQL_SUCCESS_WITH_INFO et fixe la longueur à SQL_NO_TOTAL. (Le dernier appel à **SQLGetData** doit toujours retourner la longueur des données, pas zéro ou SQL_NO_TOTAL.) Si les données ont été tronquées en raison de l’attribut de l’SQL_ATTR_MAX_LENGTH déclaration, la valeur de cet attribut - par opposition à la longueur réelle - est placée dans \* *StrLen_or_IndPtr*. C’est parce que cet attribut est conçu pour tronquer les données sur le serveur avant la conversion, de sorte que le pilote n’a aucun moyen de comprendre quelle est la longueur réelle. Lorsque **SQLGetData** est appelé plusieurs fois de suite pour la même colonne, c’est la longueur des données disponibles au début de l’appel en cours; c’est-à-dire que la longueur diminue à chaque appel subséquent.  
  
    -   Pour tous les autres types de données, c’est la longueur des données après la conversion; c’est-à-dire que c’est la taille du type auquel les données ont été converties.  
  
8.  Si les données sont tronquées sans perte d’importance lors de la conversion (par exemple, le nombre réel 1.234 est tronqué lorsqu’il est converti à l’intégrateur 1) ou parce que *BufferLength* est trop petit (par exemple, la chaîne "abcdef" est placé dans un tampon de 4 byte), **SQLGetData** retourne SQLSTATE 01004 (Données tronquées) et SQL_SUCCESS_WITH_INFO. Si les données sont tronquées sans perte d’importance en raison de l’attribut de la déclaration SQL_ATTR_MAX_LENGTH, **SQLGetData** retourne SQL_SUCCESS et ne retourne pas SQLSTATE 01004 (Données tronquées).  
  
 Le contenu du tampon de données consolidé (si **SQLGetData** est appelé sur une colonne liée) et le tampon longueur/indicateur ne sont pas définis si **SQLGetData** ne retourne pas SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO.  
  
 Les appels successifs à **SQLGetData** récupéreront les données de la dernière colonne demandée; les compensations antérieures deviennent invalides. Par exemple, lorsque la séquence suivante est exécutée :  
  
```cpp  
SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)  
```  
  
 le deuxième appel à SQLGetData (icol-n) récupère les données dès le début de la colonne n. Toute compensation dans les données en raison d’appels antérieurs à **SQLGetData** pour la colonne n’est plus valide.  
  
## <a name="descriptors-and-sqlgetdata"></a>Descripteurs et SQLGetData  
 **SQLGetData** n’interagit directement avec aucun champ descripteur.  
  
 Si *TargetType* est SQL_ARD_TYPE, le type de données dans le champ SQL_DESC_CONCISE_TYPE de l’ARD est utilisé. Si *TargetType* est SQL_ARD_TYPE ou SQL_C_DEFAULT, les données sont données la précision et l’échelle dans les champs SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION et SQL_DESC_SCALE de l’ARD, selon le type de données dans le champ SQL_DESC_CONCISE_TYPE.  
  
## <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application exécute une déclaration **SELECT** pour retourner un ensemble de résultats des identifiants, des noms et des numéros de téléphone du client triés par nom, pièce d’identité et numéro de téléphone. Pour chaque rangée de données, il appelle **SQLFetch** pour positionner le curseur à la rangée suivante. Il appelle **SQLGetData** pour récupérer les données récupérées; les tampons pour les données et le nombre retourné d’octets sont spécifiés dans l’appel à **SQLGetData**. Enfin, il imprime le nom, l’identité et le numéro de téléphone de chaque employé.  
  
```cpp  
#define NAME_LEN 50  
#define PHONE_LEN 50  
  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   sCustID, cbName, cbAge, cbBirthday;  
SQLRETURN    retcode;  
SQLHSTMT     hstmt;  
  
retcode = SQLExecDirect(hstmt,  
   "SELECT CUSTID, NAME, PHONE FROM CUSTOMERS ORDER BY 2, 1, 3",  
   SQL_NTS);  
  
if (retcode == SQL_SUCCESS) {  
   while (TRUE) {  
      retcode = SQLFetch(hstmt);  
      if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO) {  
         show_error();  
      }  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
         /* Get data for columns 1, 2, and 3 */  
  
         SQLGetData(hstmt, 1, SQL_C_ULONG, &sCustID, 0, &cbCustID);  
         SQLGetData(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
         SQLGetData(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN,  
            &cbPhone);  
  
         /* Print the row of data */  
  
         fprintf(out, "%-5d %-*s %*s", sCustID, NAME_LEN-1, szName,   
            PHONE_LEN-1, szPhone);  
      } else {  
         break;  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Affectation de stockage pour une colonne dans un ensemble de résultats|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Effectuer des opérations en vrac qui ne se rapportent pas à la position du curseur de bloc|[SQLBulkOperations (SQLBulkOperations)](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Annulation du traitement des relevés|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Aller chercher une seule série de données ou un bloc de données dans une direction avant-seulement|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Envoi de données de paramètres au moment de l’exécution|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionnement du curseur, données rafraîchissantes dans le ramset, ou mise à jour ou suppression des données dans le ramset|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
