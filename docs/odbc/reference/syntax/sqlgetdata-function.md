---
title: Fonction SQLGetData | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70ee26274d101d1b18b00c83a89bd0c946da6742
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855813"
---
# <a name="sqlgetdata-function"></a>Fonction SQLGetData
**Conformité**  
 Version introduite : La mise en conformité des normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLGetData** récupère les données pour une seule colonne du jeu de résultats ou pour un seul paramètre après **SQLParamData** retourne SQL_PARAM_DATA_AVAILABLE. Elle peut être appelée plusieurs fois pour récupérer des données de longueur variable dans les parties.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLGetData(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   Col_or_Param_Num,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_IndPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *Au paramètre StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
 *Col_or_Param_Num*  
 [Entrée] Pour récupérer des données de la colonne, il est le numéro de la colonne pour laquelle retourner des données. Colonnes de jeu de résultats sont numérotées dans l’ordre croissant des colonnes en commençant à 1. La colonne de signet est le numéro de colonne 0 ; Cela peut être spécifié uniquement si les signets sont activés.  
  
 Pour récupérer les données de paramètre, il est l’ordinal du paramètre, qui commence à 1.  
  
 *TargetType*  
 [Entrée] L’identificateur de type du type de données C de la **TargetValuePtr* mémoire tampon. Pour obtenir la liste des types de données C valides et les identificateurs de type, consultez la [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md) section annexe d : Types de données.  
  
 Si *TargetType* est SQL_ARD_TYPE, le pilotes utilise l’identificateur de type spécifié dans le champ SQL_DESC_CONCISE_TYPE de la ARD. Si *TargetType* est SQL_APD_TYPE, **SQLGetData** utilisera le même type de données C qui a été spécifié dans **SQLBindParameter**. Sinon, le type de données C est spécifié dans **SQLGetData** remplace le type de données C spécifié dans **SQLBindParameter**. Si elle est SQL_C_DEFAULT, le pilote sélectionne le type de données C par défaut en fonction du type de données SQL de la source.  
  
 Vous pouvez également spécifier un type de données C étendu. Pour plus d’informations, consultez [des Types de données C dans ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr*  
 [Sortie] Pointeur vers la mémoire tampon dans lequel retourner les données.  
  
 *TargetValuePtr* ne peut pas être NULL.  
  
 *BufferLength*  
 [Entrée] Longueur de la **TargetValuePtr* mémoire tampon en octets.  
  
 Le pilote utilise *BufferLength* pour éviter d’écrire au-delà de la fin de la \* *TargetValuePtr* lors du renvoi des données de longueur variable, telles que les données binaires ou caractères de la mémoire tampon. Notez que le pilote compte le caractère null de terminaison lors du renvoi des données de type caractère à \* *TargetValuePtr*. **TargetValuePtr* doivent par conséquent contenir l’espace pour le caractère null, ou le pilote va tronquer les données.  
  
 Lorsque le pilote retourne les données de longueur fixe, comme un entier ou une structure de date, le pilote ignore *BufferLength* et suppose que la mémoire tampon est suffisamment grande pour contenir les données. Il est donc important de l’application pour allouer un tampon assez grand pour les données de longueur fixe ou le pilote écrira au-delà de la fin de la mémoire tampon.  
  
 **SQLGetData** retourne SQLSTATE HY090 (longueur de chaîne ou de mémoire tampon non valide) lorsque *BufferLength* est inférieure à 0 mais pas lors de la *BufferLength* est 0.  
  
 *StrLen_or_IndPtr*  
 [Sortie] Pointeur vers la mémoire tampon dans lequel retourner la valeur de longueur ou d’un indicateur. S’il s’agit d’un pointeur null, aucune valeur de longueur ou indicateur est retournée. Elle renvoie une erreur lorsque les données en cours d’extraction sont NULL.  
  
 **SQLGetData** peut retourner les valeurs suivantes dans la mémoire tampon de longueur / d’indicateur :  
  
-   La longueur des données available retourner  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Pour plus d’informations, consultez [à l’aide des valeurs de longueur / d’indicateur](../../../odbc/reference/develop-app/using-length-and-indicator-values.md) et « Commentaires » dans cette rubrique.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetData** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLGetData** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|Toutes les données pour la colonne spécifiée, *Col_or_Param_Num*, puissent être récupérées dans un seul appel à la fonction. SQL_NO_TOTAL ou la longueur des données restantes dans la colonne spécifiée avant l’appel actuel à **SQLGetData** est retourné dans \* *StrLen_or_IndPtr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)<br /><br /> Pour plus d’informations sur l’utilisation de plusieurs appels à **SQLGetData** pour une seule colonne, consultez « Commentaires ».|  
|01 S 07|Troncation fractionnelle|Les données retournées pour une ou plusieurs colonnes ont été tronquées. Types de données numériques, la partie fractionnaire du nombre ont été tronquée. Pour heure, timestamp et les types de données interval contenant un composant au moment, la partie fractionnaire du temps a été tronquée.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation de l’attribut de type de données restreint|La valeur de données d’une colonne dans le jeu de résultats ne peut pas être convertie au type de données C spécifié par l’argument *TargetType*.|  
|07009|Index de descripteur non valide|La valeur spécifiée pour l’argument *Col_or_Param_Num* était égale à 0, et l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS était définie sur SQL_UB_OFF.<br /><br /> La valeur spécifiée pour l’argument *Col_or_Param_Num* a été supérieur au nombre de colonnes dans le jeu de résultats.<br /><br /> Le *Col_or_Param_Num* valeur n’est pas égale à la position ordinale du paramètre qui est disponible.<br /><br /> (DM) la colonne spécifiée a été liée. Cette description ne s’applique pas aux pilotes qui retournent SQL_GD_BOUND masque de bits pour l’option SQL_GETDATA_EXTENSIONS dans **SQLGetInfo**.<br /><br /> (DM) le nombre de la colonne spécifiée était inférieur ou égal au nombre de la colonne dépendante la plus élevée. Cette description ne s’applique pas aux pilotes qui retournent SQL_GD_ANY_COLUMN masque de bits pour l’option SQL_GETDATA_EXTENSIONS dans **SQLGetInfo**.<br /><br /> (DM) l’application a déjà appelé **SQLGetData** pour la ligne actuelle ; le nombre de la colonne spécifiée dans l’appel actuel est inférieur au nombre de la colonne spécifiée dans l’appel précédent ; et le pilote ne retourne pas le SQL_ Masque de bits GD_ANY_ORDER pour l’option SQL_GETDATA_EXTENSIONS dans **SQLGetInfo**.<br /><br /> (DM) le *TargetType* SQL_ARD_TYPE, a été l’argument et le *Col_or_Param_Num* Échec de l’enregistrement de descripteur dans la ARD la vérification de cohérence.<br /><br /> (DM) le *TargetType* argument était SQL_ARD_TYPE, et la valeur dans le champ SQL_DESC_COUNT de la ARD était inférieure à la *Col_or_Param_Num* argument.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|22002|Variable indicateur requise mais non fournie|*StrLen_or_IndPtr* était un pointeur null et les données de valeur NULL a été récupérées.|  
|22003|Valeur numérique hors limites|Retourner la valeur numérique (comme numérique ou chaîne) pour la colonne aurait entraîné la partie entière (par opposition à fractionnaire) du nombre à tronquer.<br /><br /> Pour plus d’informations, consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Format datetime non valide|La colonne de type caractère dans le jeu de résultats a été liée à une date, heure ou timestamp structure C, et la valeur dans la colonne a une date non valide, une heure ou un horodatage, respectivement. Pour plus d’informations, consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22012|Division par zéro|Une valeur à partir d’une expression arithmétique a entraîné de division par zéro a été retournée.|  
|22015|Dépassement du champ Intervalle|Affectation d’une valeur numérique exacte ou d’intervalle de type SQL à un type d’intervalle C a provoqué une perte de chiffres significatifs dans le champ Début.<br /><br /> Lors du renvoi des données à un type d’intervalle C, il n’a aucune représentation de la valeur du type SQL dans le type d’intervalle C.|  
|22018|Valeur de caractère non valide pour la spécification de la casse|Une colonne de type caractère dans le jeu de résultats a été retournée dans une mémoire tampon de caractères C, et la colonne contenue un caractère pour lesquels il n’existe aucune représentation sous forme de jeu de caractères de la mémoire tampon.<br /><br /> Le type C était une valeur numérique exact ou approximatif, une valeur datetime ou un type de données d’intervalle ; le type SQL de la colonne a un type de données caractère ; et la valeur dans la colonne n’est pas un littéral valid du type C lié.|  
|24000|État de curseur non valide|(DM) la fonction a été appelée sans préalablement appeler **SQLFetch** ou **SQLFetchScroll** pour positionner le curseur sur la ligne de données requis.<br /><br /> (DM) le *au paramètre StatementHandle* était dans un état exécuté, mais aucun jeu de résultats a été associé le *au paramètre StatementHandle*.<br /><br /> Un curseur a été ouvert sur le *au paramètre StatementHandle* et **SQLFetch** ou **SQLFetchScroll** avait été appelée, mais le curseur est positionné avant le début du jeu de résultats ou après le fin du jeu de résultats.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le *MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY003|Type de programme hors limites|(DM) l’argument *TargetType* n’était pas un type de données valide, SQL_C_DEFAULT, SQL_ARD_TYPE (en cas de récupération des données de la colonne) ou SQL_APD_TYPE (en cas de récupération des données de paramètre).<br /><br /> (DM) l’argument *Col_or_Param_Num* était 0 et l’argument *TargetType* n’était pas SQL_C_BOOKMARK pour un signet de longueur fixe ou un SQL_C_VARBOOKMARK d’un signet de longueur variable.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*, puis la fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un une application multithread, puis la fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.|  
|HY009|Utilisation non valide de pointeur null|(DM) l’argument *TargetValuePtr* était un pointeur null.|  
|HY010|Erreur de séquence de fonction|(DM) spécifié *au paramètre StatementHandle* n’était pas dans un état d’exécution. La fonction a été appelée sans préalablement appeler **SQLExecDirect**, **SQLExecute** ou une fonction de catalogue.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLGetData** fonction a été appelée.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) le *au paramètre StatementHandle* était dans un état exécuté, mais aucun jeu de résultats a été associé le *au paramètre StatementHandle*.<br /><br /> Un appel à **SQLExeceute**, **SQLExecDirect**, ou **SQLMoreResults** retourné SQL_PARAM_DATA_AVAILABLE, mais **SQLGetData** a été appelée , au lieu de **SQLParamData**.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.<br /><br /> La valeur spécifiée pour l’argument *BufferLength* était inférieure à 4, le *Col_or_Param_Num* argument a été défini sur 0, et le pilote a été un ODBC 2 *.x* pilote.|  
|HY109|Position de curseur non valide|Le curseur a été positionné (par **SQLSetPos**, **SQLFetch**, **SQLFetchScroll**, ou **SQLBulkOperations**) sur une ligne qui a été supprimée ou ne peut pas être récupérés.<br /><br /> Le curseur a été un curseur avant uniquement, et la taille de l’ensemble de lignes a été supérieure à un.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|La source de données ou le pilote ne prend pas en charge l’utilisation de **SQLGetData** avec plusieurs lignes dans **SQLFetchScroll**. Cette description ne s’applique pas aux pilotes qui retournent SQL_GD_BLOCK masque de bits pour l’option SQL_GETDATA_EXTENSIONS dans **SQLGetInfo**.<br /><br /> La source de données ou le pilote ne prend pas en charge la conversion spécifiée par la combinaison de la *TargetType* argument et le type de données SQL de la colonne correspondante. Cette erreur s’applique uniquement lorsque le type de données SQL de la colonne a été mappé à un type de données spécifiques au pilote SQL.<br /><br /> Le pilote prend en charge uniquement ODBC 2 *.x*et l’argument *TargetType* était une des opérations suivantes :<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> et les types de données d’intervalle C répertoriés dans [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md) annexe d : Types de données.<br /><br /> Le pilote prend uniquement en charge les versions ODBC avant 3,50 et l’argument *TargetType* a été SQL_C_GUID.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le pilote correspondant à la *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 **SQLGetData** renvoie les données dans une colonne spécifiée. **SQLGetData** peut être appelée uniquement après une ou plusieurs lignes qui ont été extraites du jeu de résultats **SQLFetch**, **SQLFetchScroll**, ou **SQLExtendedFetch**. Si les données de longueur variable sont trop grandes pour être retourné dans un seul appel à **SQLGetData** (en raison d’une limitation de l’application), **SQLGetData** retrouver dans les parties. Il est possible de lier des colonnes dans une ligne et l’appel **SQLGetData** pour d’autres, bien que cela soit soumis à certaines restrictions. Pour plus d’informations, consultez [bien les données de type Long](../../../odbc/reference/develop-app/getting-long-data.md).  
  
 Pour plus d’informations sur l’utilisation de **SQLGetData** avec des paramètres de sortie diffusées en continu, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-sqlgetdata"></a>À l’aide de SQLGetData  
 Si le pilote ne prend pas en charge les extensions à **SQLGetData**, la fonction peut retourner uniquement les données des colonnes indépendantes avec un nombre supérieur à celui de la dernière colonne dépendante. En outre, au sein d’une ligne de données, la valeur de la *Col_or_Param_Num* argument dans chaque appel à **SQLGetData** doit être supérieure ou égale à la valeur de *Col_or_Param_Num*dans l’appel précédent ; Autrement dit, les données doivent être récupérées dans l’ordre de numéro de colonne croissant. Enfin, si aucune extension n’est pris en charge, **SQLGetData** ne peut pas être appelée si la taille de l’ensemble de lignes est supérieure à 1.  
  
 Pilotes peuvent se détendre ces restrictions. Pour déterminer quelles restrictions assouplit un pilote, une application appelle **SQLGetInfo** avec une des options SQL_GETDATA_EXTENSIONS suivantes :  
  
-   SQL_GD_OUTPUT_PARAMS = **SQLGetData** peut être appelée pour retourner des valeurs de paramètre de sortie. Pour plus d’informations, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_GD_ANY_COLUMN. Si cette option est retournée, **SQLGetData** peut être appelée pour toute colonne indépendante, y compris celles avant la dernière colonne dépendante.  
  
-   SQL_GD_ANY_ORDER. Si cette option est retournée, **SQLGetData** peut être appelée pour les colonnes indépendantes dans n’importe quel ordre.  
  
-   SQL_GD_BLOCK. Si cette option est retournée par **SQLGetInfo** pour l’InfoType SQL_GETDATA_EXTENSIONS, le pilote prend en charge les appels à **SQLGetData** lorsque la taille de l’ensemble de lignes est supérieure à 1 et l’application peut appeler **SQLSetPos** avec l’option SQL_POSITION pour positionner le curseur sur la ligne appropriée avant d’appeler **SQLGetData.**  
  
-   SQL_GD_BOUND. Si cette option est retournée, **SQLGetData** peut être appelée pour les colonnes liées, ainsi que pour les colonnes indépendantes.  
  
 Il existe deux exceptions à ces restrictions et la capacité d’un pilote d’assouplir les. Tout d’abord, **SQLGetData** ne doit jamais être appelée pour un curseur avant uniquement lorsque la taille de l’ensemble de lignes est supérieure à 1. En second lieu, si un pilote prend en charge les signets, il doit toujours prendre en charge la possibilité d’appeler **SQLGetData** pour la colonne 0, même s’il n’autorise pas les applications d’appeler **SQLGetData** pour les autres colonnes avant le dernier colonne dépendante. (Quand une application ne fonctionne pas avec un ODBC 2 *.x* pilote, **SQLGetData** retournera avec succès un signet lorsqu’elle est appelée avec *Col_or_Param_Num* égale à 0 après un appel à **SQLFetch**, car **SQLFetch** est mappé par le ODBC 3 *.x* Gestionnaire de pilotes à **SQLExtendedFetch** avec un  *FetchOrientation* de SQL_FETCH_NEXT, et **SQLGetData** avec un *Col_or_Param_Num* 0 est mappé par le ODBC 3 *.x* Gestionnaire de pilotes à **SQLGetStmtOption** avec un *fOption* de SQL_GET_BOOKMARK.)  
  
 **SQLGetData** ne peut pas être utilisé pour récupérer le signet pour une ligne qui vient d’être insérée en appelant **SQLBulkOperations** avec l’option SQL_ADD, étant donné que le curseur n’est pas positionné sur la ligne. Une application peut récupérer le signet pour une ligne en liant la colonne 0 avant d’appeler **SQLBulkOperations** avec SQL_ADD, auquel cas **SQLBulkOperations** retourne le signet dans la mémoire tampon liée. **SQLFetchScroll** peut ensuite être appelée avec SQL_FETCH_BOOKMARK pour repositionner le curseur sur cette ligne.  
  
 Si le *TargetType* argument est un type de données d’intervalle, la précision de début d’intervalle par défaut (2) et la précision de secondes d’intervalle par défaut (6), comme défini dans les champs SQL_DESC_DATETIME_INTERVAL_PRECISION et SQL_DESC_PRECISION de le ARD, respectivement, sont utilisés pour les données. Si le *TargetType* argument est un type de données SQL_C_NUMERIC, la précision par défaut (définies par le pilote) et par défaut de la mise à l’échelle (0), comme défini dans les champs SQL_DESC_PRECISION et SQL_DESC_SCALE de la ARD, sont utilisé pour les données. Si la mise à l’échelle ni précision par défaut ne c'est-à-dire pas, l’application doit définir explicitement le champ de descripteur approprié par un appel à **SQLSetDescField** ou **SQLSetDescRec**. Il peut définir le champ SQL_DESC_CONCISE_TYPE à SQL_C_NUMERIC et appelez **SQLGetData** avec un *TargetType* argument de SQL_ARD_TYPE, ce qui provoque les valeurs de précision et l’échelle dans les champs de descripteur à utiliser.  
  
> [!NOTE]  
>  Dans ODBC 2 *.x*, ensemble d’applications *TargetType* SQL_C_DATE, SQL_C_TIME ou SQL_C_TIMESTAMP pour indiquer que \* *TargetValuePtr* est une date, time, ou structure d’horodateur. Dans ODBC 3 *.x*, ensemble d’applications *TargetType* SQL_C_TYPE_DATE, SQL_C_TYPE_TIME ou SQL_C_TYPE_TIMESTAMP. Le Gestionnaire de pilotes rend les mappages appropriés si nécessaire, en sur la version de l’application et le pilote.  
  
## <a name="retrieving-variable-length-data-in-parts"></a>Récupération de données de longueur Variable en parties  
 **SQLGetData** peut être utilisé pour récupérer des données à partir d’une colonne qui contient les données de longueur variable dans les parties, autrement dit, lorsque l’identificateur du type de données SQL de la colonne est SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_WCHAR, SQL_WVARCHAR, SQL_ WLONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY ou un identificateur propre au pilote pour un type de longueur variable.  
  
 Pour récupérer des données à partir d’une colonne dans les parties, l’application appelle **SQLGetData** plusieurs fois de suite pour la même colonne. À chaque appel, **SQLGetData** retourne la partie suivante de données. C’est à l’application pour réassembler les parties, en prenant soin de supprimer le caractère null de terminaison à partir de parties intermédiaires des données de caractères. S’il existe plus de données à retourner ou pas suffisamment de tampon a été allouée pour le caractère de fin, **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (données tronquées). Lorsqu’elle retourne la dernière partie des données, **SQLGetData** retourne SQL_SUCCESS. Ni SQL_NO_TOTAL ni égal à zéro peut être renvoyé sur le dernier appel valid pour récupérer des données à partir d’une colonne, parce que l’application puis n’aurait aucun moyen de savoir la quantité des données dans la mémoire tampon d’application est valide. Si **SQLGetData** est appelé après cela, il retourne SQL_NO_DATA. Pour plus d’informations, consultez la section suivante, « Récupération des données avec SQLGetData ».  
  
 Signets de longueur variable peuvent être retournées dans les parties en **SQLGetData**. Comme avec d’autres données, un appel à **SQLGetData** pour retourner des signets de longueur variable dans les parties retourne SQLSTATE 01004 (chaîne de données tronquée à droite) et SQL_SUCCESS_WITH_INFO en plus de données à retourner. Cela n’est pas le cas lorsqu’un signet de longueur variable tronqué par un appel à **SQLFetch** ou **SQLFetchScroll**, qui retourne SQL_ERROR et SQLSTATE 22001 (données chaîne tronquée à droite).  
  
 **SQLGetData** ne peut pas être utilisée pour retourner des données de longueur fixe dans les parties. Si **SQLGetData** est appelée plusieurs fois dans une ligne pour une colonne contenant des données de longueur fixe, il retourne SQL_NO_DATA pour tous les appels après le premier.  
  
## <a name="retrieving-streamed-output-parameters"></a>Récupération des paramètres de sortie diffusées en continu  
 Si un pilote prend en charge les paramètres de sortie diffusées en continu, une application peut appeler **SQLGetData** avec une petite mémoire tampon autant de fois pour récupérer une valeur de paramètre élevée. Pour plus d’informations sur le paramètre de sortie diffusées en continu, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="retrieving-data-with-sqlgetdata"></a>Récupération des données avec SQLGetData  
 Pour retourner des données pour la colonne spécifiée, **SQLGetData** effectue la séquence d’étapes suivante :  
  
1.  Retourne SQL_NO_DATA s’il a déjà retourné toutes les données pour la colonne.  
  
2.  Jeux \* *StrLen_or_IndPtr* avec la valeur SQL_NULL_DATA si les données sont NULL. Si les données sont NULL et *StrLen_or_IndPtr* était un pointeur null, **SQLGetData** retourne SQLSTATE 22002 (variable indicateur requise mais non fournie).  
  
     Si les données pour la colonne ne sont pas NULL, **SQLGetData** se poursuit à l’étape 3.  
  
3.  Si l’attribut d’instruction SQL_ATTR_MAX_LENGTH est défini sur une valeur différente de zéro, si la colonne contient des données binaires ou caractères et si **SQLGetData** n’a pas été précédemment appelé pour la colonne, les données sont tronquées à SQL_ATTR_MAX_LENGTH octets.  
  
    > [!NOTE]  
    >  L’attribut d’instruction SQL_ATTR_MAX_LENGTH vise à réduire le trafic réseau. Il est généralement implémenté par la source de données, ce qui tronque les données avant de les retourner sur le réseau. Pilotes et les sources de données ne sont pas requis sa prise en charge. Par conséquent, pour garantir que les données sont tronquées à une taille particulière, une application doit allouer un tampon de cette taille et spécifiez la taille dans le *BufferLength* argument.  
  
4.  Convertit les données au type spécifié dans *TargetType*. Les données étant données la précision par défaut et l’échelle pour ce type de données. Si *TargetType* est SQL_ARD_TYPE, les données de type dans le champ SQL_DESC_CONCISE_TYPE de la ARD est utilisé. Si *TargetType* est SQL_ARD_TYPE, les données dans le SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION, reçoit la précision et l’échelle et les champs SQL_DESC_SCALE de la ARD, en fonction des données type dans le SQL_DESC_CONCISE Champ _Type. Si la mise à l’échelle ni précision par défaut ne c'est-à-dire pas, l’application doit définir explicitement le champ de descripteur approprié par un appel à **SQLSetDescField** ou **SQLSetDescRec**.  
  
5.  Si les données a été converties en un type de données de longueur variable, comme le caractère ou binaire, **SQLGetData** vérifie si la longueur des données dépasse *BufferLength*. Si la longueur des données de caractères (y compris le caractère null de terminaison) dépasse *BufferLength*, **SQLGetData** tronque les données à *BufferLength* moins la longueur d’un caractère du caractère nul de terminaison. Il null-termine ensuite les données. Si la longueur des données binaires dépasse la longueur de la mémoire tampon de données, **SQLGetData** tronque à *BufferLength* octets.  
  
     Si la mémoire tampon de données fourni est trop petit pour contenir le caractère null, **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004.  
  
     **SQLGetData** jamais tronque les données converties en données de longueur fixe types ; il suppose toujours que la longueur de **TargetValuePtr* est la taille du type de données.  
  
6.  Place les données converties (et éventuellement tronquées) dans \* *TargetValuePtr*. Notez que **SQLGetData** ne peut pas retourner des données hors ligne.  
  
7.  Place la longueur des données dans \* *StrLen_or_IndPtr*. Si *StrLen_or_IndPtr* était un pointeur null, **SQLGetData** ne retourne pas la longueur.  
  
    -   Pour les données binaires ou caractères, il s’agit la longueur des données après la conversion et avant la troncation en raison *BufferLength*. Si le pilote ne peut pas déterminer la longueur des données après la conversion, comme c’est parfois le cas avec les données de type long, il retourne SQL_SUCCESS_WITH_INFO et définit la longueur de SQL_NO_TOTAL. (Le dernier appel à **SQLGetData** doit toujours retourner la longueur des données, pas zéro ou SQL_NO_TOTAL.) Si les données ont été tronquées en raison de l’instruction SQL_ATTR_MAX_LENGTH attribut, la valeur de cet attribut, par opposition à la longueur réelle, est placé dans \* *StrLen_or_IndPtr*. Il s’agit, car cet attribut est conçu pour tronquer des données sur le serveur avant la conversion, le pilote n’a aucun moyen de déterminer quelles la longueur réelle est. Lorsque **SQLGetData** est appelée plusieurs fois de suite pour la même colonne, il s’agit de la longueur des données disponibles au début de l’appel actuel ; autrement dit, la longueur diminue avec chaque appel suivant.  
  
    -   Pour tous les autres types de données, il s’agit la longueur des données après la conversion ; Autrement dit, il est la taille du type auquel les données ont été converties.  
  
8.  Si les données sont tronquées sans perte de précision lors de la conversion (par exemple, le nombre réel au chiffre inférieur 1,234 est tronqué lorsque converti à l’entier 1) ou parce que *BufferLength* est trop petite (par exemple, la chaîne « abcdef » est placée dans un tampon de 4 octets), **SQLGetData** retourne SQLSTATE 01004 (données tronquées) et SQL_SUCCESS_WITH_INFO. Si les données sont tronquées sans perte de précision en raison de l’attribut d’instruction SQL_ATTR_MAX_LENGTH, **SQLGetData** retourne SQL_SUCCESS et ne retourne pas de SQLSTATE 01004 (données tronquées).  
  
 Le contenu de la mémoire tampon de données liées (si **SQLGetData** est appelée sur une colonne dépendante) et la mémoire tampon de longueur / d’indicateur ne sont pas définis si **SQLGetData** ne renvoie pas SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO.  
  
 Les appels successifs à **SQLGetData** récupérera les données à partir de la dernière colonne demandée ; décalages préalables deviennent non valides. Par exemple, lorsque la séquence suivante est exécutée :  
  
```  
SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)  
```  
  
 le deuxième appel à SQLGetData(icol=n) récupère des données à partir du début de la colonne n. Un décalage quelconque dans les données en raison d’appels antérieurs à **SQLGetData** pour la colonne n’est plus valide.  
  
## <a name="descriptors-and-sqlgetdata"></a>Descripteurs et SQLGetData  
 **SQLGetData** n’interagit pas directement avec les champs de descripteur.  
  
 Si *TargetType* est SQL_ARD_TYPE, les données de type dans le champ SQL_DESC_CONCISE_TYPE de la ARD est utilisé. Si *TargetType* est SQL_ARD_TYPE ou SQL_C_DEFAULT, les données dans le SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION, reçoit la précision et l’échelle et SQL_DESC_SCALE des champs de la ARD, en fonction des données type dans le champ SQL_DESC_CONCISE_TYPE.  
  
## <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application exécute un **sélectionnez** instruction pour retourner un jeu de résultats du client ID, les noms et triés par nom, ID et numéro de téléphone de numéros de téléphone. Pour chaque ligne de données, il appelle **SQLFetch** pour positionner le curseur à la ligne suivante. Il appelle **SQLGetData** pour récupérer les données extraites ; les mémoires tampons pour les données et le nombre d’octets retourné sont spécifiés dans l’appel à **SQLGetData**. Enfin, il imprime le nom de chaque employé, ID et numéro de téléphone.  
  
```  
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
|Assignation du stockage pour une colonne dans un jeu de résultats|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Exécution d’opérations en bloc qui ne sont pas liées à la position du curseur de bloc|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|L’exécution d’une instruction SQL|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécuter une instruction SQL préparée|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|L’extraction d’une seule ligne de données ou un bloc de données dans une direction avant uniquement|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Envoi de données de paramètre au moment de l’exécution|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionnement du curseur, l’actualisation des données dans l’ensemble de lignes, ou la mise à jour ou suppression de données dans l’ensemble de lignes|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Récupération des paramètres de sortie à l’aide de SQLGetData ](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
