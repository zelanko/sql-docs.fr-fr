---
title: SQLSetPos, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetPos
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetPos
helpviewer_keywords:
- SQLSetPos function [ODBC]
ms.assetid: 80190ee7-ae3b-45e5-92a9-693eb558f322
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63bca42adcdfc83d1bdb96361680d0c70c9a031c
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793129"
---
# <a name="sqlsetpos-function"></a>SQLSetPos, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ODBC  
  
 **Résumé**  
 **SQLSetPos** définit la position du curseur dans un ensemble de lignes et permet à une application pour actualiser les données dans l’ensemble de lignes ou mettre à jour ou supprimer des données dans le jeu de résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLSetPos(  
      SQLHSTMT        StatementHandle,  
      SQLSETPOSIROW   RowNumber,  
      SQLUSMALLINT    Operation,  
      SQLUSMALLINT    LockType);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
 *RowNumber*  
 [Entrée] Position de la ligne dans l’ensemble de lignes sur lequel effectuer l’opération spécifiée avec le *opération* argument. Si *RowNumber* est 0, l’opération s’applique à chaque ligne dans l’ensemble de lignes.  
  
 Pour plus d’informations, consultez « Commentaires ».  
  
 *Opération*  
 [Entrée] Opération à effectuer :  
  
 SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE  
  
> [!NOTE]
>  La valeur SQL_ADD pour la *opération* argument a été déconseillé pour ODBC *3.x*. ODBC *3.x* pilotes doivent prendre en charge SQL_ADD pour la compatibilité descendante. Cette fonctionnalité a été remplacée par un appel à **SQLBulkOperations** avec un *opération* de SQL_ADD. Lorsqu’une application ODBC *3.x* application fonctionne avec une application ODBC *2.x* pilote, le Gestionnaire de pilotes est mappé à un appel à **SQLBulkOperations** avec un *opération*de SQL_ADD à **SQLSetPos** avec un *opération* de SQL_ADD.  
  
 Pour plus d’informations, consultez « Commentaires ».  
  
 *LockType*  
 [Entrée] Spécifie la façon de verrouiller la ligne après avoir effectué l’opération spécifiée dans le *opération* argument.  
  
 SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK  
  
 Pour plus d’informations, consultez « Commentaires ».  
  
 **Retourne**  
  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetPos** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLSetPos** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
 Pour toutes ces SQLSTATEs qui peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_ERROR (sauf 01xxx SQLSTATE) SQL_SUCCESS_WITH_INFO est retourné si une erreur se produit sur un ou plus, mais pas toutes, les lignes d’une opération de plusieurs ligne, SQL_ERROR est retournée si une erreur se produit sur un opération de ligne unique.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01001|Conflit d’opération de curseur|Le *opération* argument était SQL_DELETE ou SQL_UPDATE, et aucune ligne ou plusieurs lignes ont été supprimés ou mis à jour. (Pour plus d’informations sur les mises à jour de plusieurs lignes, consultez la description de la SQL_ATTR_SIMULATE_CURSOR *attribut* dans **SQLSetStmtAttr**.) (La fonction retourne SQL_SUCCESS_WITH_INFO.)<br /><br /> Le *opération* argument était SQL_DELETE ou SQL_UPDATE, et l’opération a échoué en raison de l’accès concurrentiel optimiste. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Chaîne de données tronquée à droite|Le *opération* argument était SQL_REFRESH, et données de chaîne ou binaire retournées pour une ou plusieurs colonnes avec un type de données SQL_C_CHAR ou SQL_C_BINARY a entraîné la troncation des caractères non vides ou non NULL des données binaires.|  
|01S01|Erreur de ligne|Le *RowNumber* argument était égale à 0, et une erreur s’est produite dans une ou plusieurs lignes lors de l’exécution de l’opération spécifiée avec le *opération* argument.<br /><br /> (SQL_SUCCESS_WITH_INFO est retourné si une erreur se produit sur un ou plus, mais pas toutes, les lignes d’une opération de plusieurs ligne, SQL_ERROR est retournée si une erreur se produit sur une opération de ligne unique.)<br /><br /> (Cet SQLSTATE est renvoyé uniquement lorsque **SQLSetPos** est appelée après **SQLExtendedFetch**, si le pilote est une application ODBC *2.x* pilote et la bibliothèque de curseurs n’est pas utilisé.)|  
|01S07|Troncation fractionnelle|Le *opération* argument était SQL_REFRESH, le type de données de la mémoire tampon d’application n’était pas SQL_C_CHAR ou SQL_C_BINARY, et les données retournées dans les mémoires tampons d’application pour une ou plusieurs colonnes ont été tronquées. Types de données numériques, la partie fractionnaire du nombre ont été tronquée. Pour heure, timestamp et les types de données interval contenant un composant au moment, la partie fractionnaire du temps a été tronquée.<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation de l’attribut de type de données restreint|La valeur de données d’une colonne dans le jeu de résultats n’a pas pu être convertie au type de données spécifié par *TargetType* dans l’appel à **SQLBindCol**.|  
|07009|Index de descripteur non valide|L’argument *opération* était SQL_REFRESH ou SQL_UPDATE, et une colonne a été liée avec un numéro de colonne supérieur au nombre de colonnes dans le jeu de résultats.|  
|21S02|Degré de la table dérivée ne correspond pas à la liste des colonnes|L’argument *opération* était SQL_UPDATE, et aucune colonne ont été être mise à jour, car toutes les colonnes ont été soit indépendant, en lecture seule, ou la valeur dans la mémoire tampon de longueur / d’indicateur lié était SQL_COLUMN_IGNORE.|  
|22001|Données String, troncation à droite|Le *opération* argument était SQL_UPDATE, et l’attribution d’un caractère ou d’une valeur binaire à une colonne a entraîné la troncation de non vide (pour les caractères) ou de caractères non-null (pour les binaires) ou d’octets.|  
|22003|Valeur numérique hors limites|L’argument *opération* a été SQL_UPDATE, et l’attribution d’une valeur numérique à une colonne dans le jeu de résultats a provoqué la partie entière (par opposition à fractionnaire) du nombre à tronquer.<br /><br /> L’argument *opération* a été SQL_REFRESH et retourner la valeur numérique pour un ou plusieurs colonnes dépendantes entraîneraient une perte de chiffres significatifs.|  
|22007|Format datetime non valide|L’argument *opération* était SQL_UPDATE, et l’attribution d’une valeur de date ou timestamp à une colonne dans le jeu de résultats a provoqué l’année, mois ou champ jour hors plage.<br /><br /> L’argument *opération* a été SQL_REFRESH et retourner la valeur de date ou timestamp pour une ou plusieurs colonnes dépendantes aurait entraîné l’année, mois ou champ jour hors plage.|  
|22008|Dépassement du champ date/heure|Le *opération* argument était SQL_UPDATE, et les performances des calculs arithmétiques sur les données envoyées à une colonne du jeu de résultats de la date/heure a entraîné dans un champ d’horodatage (l’année, mois, jour, heure, minute ou second champ) du résultat en cours en dehors de la plage autorisée de valeurs pour le champ ou n’est pas valide après des règles naturelles du calendrier grégorien de dates/heures.<br /><br /> Le *opération* argument était SQL_REFRESH, et les performances des calculs arithmétiques sur les données récupérées à partir de l’ensemble de résultats de la date/heure a entraîné dans un champ d’horodatage (l’année, mois, jour, heure, minute ou second champ) du résultat en cours en dehors de la plage autorisée de valeurs pour le champ ou n’est pas valide après des règles naturelles du calendrier grégorien de dates/heures.|  
|22015|Dépassement du champ Intervalle|Le *opération* argument était SQL_UPDATE, et l’assignation d’une valeur numérique exacte ou le type d’intervalle C à un type de données SQL de l’intervalle a entraîné une perte de chiffres significatifs.<br /><br /> Le *opération* argument était SQL_UPDATE ; lorsque vous attribuez à un intervalle de type SQL, il a été aucune représentation de la valeur du type C dans l’intervalle de type SQL.<br /><br /> Le *opération* argument était SQL_REFRESH et affectation d’une valeur numérique exacte ou d’intervalle de type SQL à un type d’intervalle C a provoqué une perte de chiffres significatifs dans le champ Début.<br /><br /> Le *opération* argument était SQL_ actualiser ; lorsque vous attribuez à un type d’intervalle C, il n’a aucune représentation de la valeur du type SQL dans le type d’intervalle C.|  
|22018|Valeur de caractère non valide pour la spécification de la casse|Le *opération* argument était SQL_REFRESH ; le type C était une valeur numérique exact ou approximatif, une valeur datetime ou un type de données d’intervalle ; le type SQL de la colonne a un type de données caractère ; et la valeur dans la colonne n’est pas un littéral valid de la type de limite C.<br /><br /> L’argument *opération* a été SQL_UPDATE ; le type SQL était une valeur numérique exact ou approximatif, une valeur datetime ou un type de données d’intervalle ; le type C a été SQL_C_CHAR ; et la valeur dans la colonne n’est pas un littéral valid du type SQL dépendant.|  
|23000|Violation de contrainte d’intégrité|L’argument *opération* était SQL_DELETE ou SQL_UPDATE, et une contrainte d’intégrité a été violée.|  
|24000|État de curseur non valide|Le *au paramètre StatementHandle* était dans un état exécuté, mais aucun jeu de résultats a été associé le *au paramètre StatementHandle*.<br /><br /> (DM) un curseur a été ouvert sur le *au paramètre StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelée.<br /><br /> Un curseur a été ouvert sur le *au paramètre StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avait été appelée, mais le curseur est positionné avant le début du jeu de résultats ou après la fin du jeu de résultats.<br /><br /> L’argument *opération* était SQL_DELETE, SQL_REFRESH ou SQL_UPDATE, et le curseur est positionné avant le début du jeu de résultats ou après la fin du jeu de résultats.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|42000|Syntaxe ou violation d’accès|Le pilote n’a pas pu verrouiller la ligne en fonction des besoins pour effectuer l’opération demandée dans l’argument *opération*.<br /><br /> Le pilote n’a pas pu verrouiller la ligne comme demandé dans l’argument *LockType*.|  
|44000|Violation de WITH CHECK OPTION|Le *opération* argument était SQL_UPDATE et la mise à jour a été effectuée sur une table affichée ou une table dérivée à partir de la table affichée qui a été créée en spécifiant **WITH CHECK OPTION**, de sorte qu’une ou plusieurs lignes affecté par la mise à jour ne pourra plus être présent dans la table affichée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*, puis la fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque la fonction SQLSetPos a été appelée.<br /><br /> (DM) spécifié *au paramètre StatementHandle* n’était pas dans un état d’exécution. La fonction a été appelée sans préalablement appeler **SQLExecDirect**, **SQLExecute**, ou une fonction de catalogue.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) le pilote a été une ODBC *2.x* pilote, et **SQLSetPos** a été appelé pour un *au paramètre StatementHandle* après **SQLFetch** a été appelée.|  
|HY011|Attribut ne peut pas être défini maintenant|(DM) le pilote a été une ODBC *2.x* pilote ; le SQL_ATTR_ROW_STATUS_PTR attribut d’instruction a été défini ; puis **SQLSetPos** a été appelé avant **SQLFetch**,  **SQLFetchScroll**, ou **SQLExtendedFetch** a été appelée.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|Le *opération* argument était SQL_UPDATE, une valeur de données était un pointeur null, et la valeur de longueur de colonne n’était pas 0, SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NULL_DATA, ou inférieure ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Le *opération* argument était SQL_UPDATE ; une valeur de données n’était pas un pointeur null ; le type de données C a été SQL_C_BINARY ou SQL_C_CHAR ; et la valeur de longueur de colonne était inférieure à 0 mais pas égale à SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE , SQL_NTS ou SQL_NULL_DATA, ou inférieure ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> La valeur dans une mémoire tampon de longueur / d’indicateur était SQL_DATA_AT_EXEC ; le type SQL a été SQL_LONGVARCHAR, SQL_LONGVARBINARY ou un type de données spécifiques à la source de données de type long ; et le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** a été « Y ».|  
|HY092|Identificateur d’attribut non valide|(DM) la valeur spécifiée pour le *opération* argument n’est pas valide.<br /><br /> (DM) la valeur spécifiée pour le *LockType* argument n’est pas valide.<br /><br /> Le *opération* argument était SQL_UPDATE ou SQL_DELETE et l’attribut d’instruction SQL_ATTR_CONCURRENCY était SQL_ATTR_CONCUR_READ_ONLY.|  
|HY107|Valeur de ligne hors limites|La valeur spécifiée pour l’argument *RowNumber* était supérieur au nombre de lignes dans l’ensemble de lignes.|  
|HY109|Position de curseur non valide|Le curseur associé à la *au paramètre StatementHandle* a été défini en tant que type avant uniquement, donc le curseur n’a pas pu être positionné dans l’ensemble de lignes. Consultez la description de l’attribut SQL_ATTR_CURSOR_TYPE dans **SQLSetStmtAttr**.<br /><br /> Le *opération* argument était SQL_UPDATE, SQL_DELETE ou SQL_REFRESH, et la ligne identifiée par le *RowNumber* argument a été supprimé ou n’a pas été extraites.<br /><br /> (DM) le *RowNumber* argument était égale à 0 et le *opération* SQL_POSITION a été l’argument.<br /><br /> **SQLSetPos** a été appelée après **SQLBulkOperations** a été appelée et avant **SQLFetchScroll** ou **SQLFetch** a été appelée.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|La pilote ou source de données ne prend pas en charge l’opération demandée dans le *opération* argument ou *LockType* argument.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant que la source de données a retourné le jeu de résultats. Le délai d’expiration est défini via **SQLSetStmtAttr** avec un *attribut* de SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
  
> [!CAUTION]
>  Pour plus d’informations sur l’instruction stipule que **SQLSetPos** peut être appelée et ce qu’il doit faire pour assurer la compatibilité avec ODBC *2.x* applications, consultez [curseurs de bloc, curseurs avec défilement, et Compatibilité descendante](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md).  
  
## <a name="rownumber-argument"></a>Argument RowNumber  
 Le *RowNumber* argument spécifie le numéro de la ligne dans l’ensemble de lignes sur lequel effectuer l’opération spécifiée par le *opération* argument. Si *RowNumber* est 0, l’opération s’applique à chaque ligne dans l’ensemble de lignes. *RowNumber* doit être une valeur entre 0 et le nombre de lignes dans l’ensemble de lignes.  
  
> [!NOTE]  
>  Dans le langage C, les tableaux sont basés sur 0 et le *RowNumber* argument est de base 1. Par exemple, pour mettre à jour de la cinquième ligne du jeu de lignes, une application modifie les mémoires tampons d’ensemble de lignes à l’index de tableau 4, mais spécifie un *RowNumber* 5.  
  
 Toutes les opérations de positionner le curseur sur la ligne spécifiée par *RowNumber*. Les opérations suivantes nécessitent une position de curseur :  
  
-   Positionné de mise à jour et supprimer des instructions.  
  
-   Les appels à **SQLGetData**.  
  
-   Les appels à **SQLSetPos** avec les options SQL_DELETE et SQL_REFRESH SQL_UPDATE.  
  
 Par exemple, si *RowNumber* est 2 pour un appel à **SQLSetPos** avec un *opération* de SQL_DELETE, le curseur est positionné sur la deuxième ligne de l’ensemble de lignes et de cette ligne est supprimée. L’entrée dans l’implémentation ligne tableau d’état (vers lequel pointus l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR) pour la deuxième ligne est modifiée pour SQL_ROW_DELETED.  
  
 Une application peut spécifier une position de curseur lorsqu’il appelle **SQLSetPos**. En règle générale, il appelle **SQLSetPos** avec l’opération SQL_POSITION ou SQL_REFRESH pour positionner le curseur avant d’exécuter un positionnées mises à jour ou supprimer l’instruction ou l’appel **SQLGetData**.  
  
## <a name="operation-argument"></a>Argument de l’opération  
 Le *opération* argument prend en charge les opérations suivantes. Pour déterminer quelles options sont prises en charge par une source de données, une application appelle **SQLGetInfo** avec le SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_ Type d’informations CURSOR_ATTRIBUTES1 (selon le type du curseur).  
  
|*Opération*<br /><br /> argument|Opération|  
|------------------------------|---------------|  
|SQL_POSITION|Le pilote positionne le curseur sur la ligne spécifiée par *RowNumber*.<br /><br /> Le contenu du tableau d’état de ligne vers laquelle pointé l’attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR est ignoré pour les SQL_POSITION *opération*.|  
|SQL_REFRESH|Le pilote positionne le curseur sur la ligne spécifiée par *RowNumber* et actualise les données dans les mémoires tampons d’ensemble de lignes pour cette ligne. Pour plus d’informations sur la façon dont le pilote retourne des données dans les mémoires tampons d’ensemble de lignes, consultez les descriptions de la liaison selon les lignes et colonnes dans **SQLBindCol**.<br /><br /> **SQLSetPos** avec un *opération* de SQL_REFRESH met à jour l’état et le contenu des lignes au sein de l’ensemble de lignes extraite en cours. Cela inclut l’actualisation des signets. Étant donné que les données dans les mémoires tampons sont actualisées, mais pas à nouveau extraites, l’appartenance dans l’ensemble de lignes est fixe. Cela est différent de l’actualisation effectuée par un appel à **SQLFetchScroll** avec un *FetchOrientation* de SQL_FETCH_RELATIVE et un *RowNumber* égal à 0, ce qui réextrait l’ensemble de lignes du jeu de résultats afin qu’il peut afficher les données ajoutées et supprimer les données supprimées si ces opérations sont prises en charge par le pilote et le curseur.<br /><br /> Mise à jour avec **SQLSetPos** ne changera pas un état de ligne de SQL_ROW_DELETED. Les lignes supprimées dans l’ensemble de lignes continueront à être marquée comme supprimée jusqu'à l’extraction suivante. Les lignes disparaissent à l’extraction suivante si le curseur prend en charge la compression (dans lequel une ultérieure **SQLFetch** ou **SQLFetchScroll** ne retourne pas de lignes supprimées).<br /><br /> Ajouter des lignes n’apparaissent pas lorsqu’une actualisation avec **SQLSetPos** est effectuée. Ce comportement est différent de **SQLFetchScroll** avec un *FetchType* de SQL_FETCH_RELATIVE et un *RowNumber* égal à 0, ce qui actualise également l’ensemble de lignes en cours mais ne afficher les enregistrements ajoutés ou pack enregistrements supprimés si ces opérations sont prises en charge par le curseur.<br /><br /> Mise à jour avec **SQLSetPos** passe un état de ligne de SQL_ROW_ADDED SQL_ROW_SUCCESS (si le tableau d’état de ligne existe).<br /><br /> Mise à jour avec **SQLSetPos** devient un état de ligne de SQL_ROW_UPDATED nouveau statut de la ligne (si le tableau d’état de ligne existe).<br /><br /> Si une erreur se produit dans un **SQLSetPos** opération sur une ligne, l’état de ligne est défini sur SQL_ROW_ERROR (si le tableau d’état de ligne existe).<br /><br /> Pour un curseur ouvert avec un attribut d’instruction SQL_ATTR_CONCURRENCY de SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES, une actualisation avec **SQLSetPos** peut de mettre à jour les valeurs de l’accès concurrentiel optimiste utilisés par la source de données pour détecter que le ligne a été modifiée. Si cela se produit, les versions de ligne ou les valeurs utilisées pour garantir l’accès concurrentiel au curseur sont mis à jour chaque fois que les tampons de l’ensemble de lignes sont actualisés à partir du serveur. Cela se produit pour chaque ligne qui est actualisé.<br /><br /> Le contenu du tableau d’état de ligne vers laquelle pointé l’attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR est ignoré pour les SQL_REFRESH *opération*.|  
|SQL_UPDATE|Le pilote positionne le curseur sur la ligne spécifiée par *RowNumber* et met à jour la ligne sous-jacente de données avec les valeurs dans les mémoires tampons d’ensemble de lignes (le *TargetValuePtr* argument dans  **SQLBindCol**). Il récupère les longueurs des données dans les mémoires tampons de longueur / d’indicateur (le *StrLen_or_IndPtr* argument dans **SQLBindCol**). Si la longueur de n’importe quelle colonne est SQL_COLUMN_IGNORE, la colonne n’est pas mis à jour. Après la mise à jour la ligne, le pilote devient l’élément correspondant du tableau d’état de ligne SQL_ROW_UPDATED ou SQL_ROW_SUCCESS_WITH_INFO (si le tableau d’état de ligne existe).<br /><br /> Elle est définie par le pilote le comportement si **SQLSetPos** avec un *opération* argument de SQL_UPDATE est appelée sur un curseur qui contient les colonnes en double. Le pilote peut retourner une valeur SQLSTATE définie par le pilote, peuvent mettre à jour de la première colonne qui s’affiche dans le jeu de résultats ou effectuer d’autres comportements définis par le pilote.<br /><br /> Le tableau d’opération de ligne vers laquelle pointé l’attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR peut être utilisé pour indiquer qu’une ligne dans l’ensemble de lignes en cours doit être ignorée pendant une mise à jour en bloc. Pour plus d’informations, consultez « Tableaux d’opération et de statut » plus loin dans cette référence de fonction.|  
|SQL_DELETE|Le pilote positionne le curseur sur la ligne spécifiée par *RowNumber* et supprime la ligne de données sous-jacente. Il modifie l’élément correspondant du tableau d’état de ligne pour SQL_ROW_DELETED. Une fois que la ligne a été supprimée, les éléments suivants ne sont pas valides pour la ligne : positionné mise à jour et supprimer des instructions, les appels à **SQLGetData**et les appels à **SQLSetPos** avec *opération* une valeur à l’exception SQL_POSITION. Pour les pilotes qui prennent en charge la compression, la ligne est supprimée à partir du curseur lorsque de nouvelles données sont récupérées à partir de la source de données.<br /><br /> Si la ligne reste visible varie selon le type de curseur. Par exemple, les lignes supprimées sont visibles aux curseurs statiques et pilotés par jeu de clés, mais invisibles pour les curseurs dynamiques.<br /><br /> Le tableau d’opération de ligne vers laquelle pointé l’attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR peut être utilisé pour indiquer qu’une ligne dans l’ensemble de lignes en cours doit être ignorée pendant une suppression en bloc. Pour plus d’informations, consultez « Tableaux d’opération et de statut » plus loin dans cette référence de fonction.|  
  
## <a name="locktype-argument"></a>LockType Argument  
 Le *LockType* argument fournit un moyen aux applications de contrôle d’accès concurrentiel. Dans la plupart des cas, les sources de données qui prennent en charge les niveaux d’accès concurrentiel et les transactions prendra en charge uniquement la valeur SQL_LOCK_NO_CHANGE de la *LockType* argument. Le *LockType* argument est généralement utilisé uniquement pour la prise en charge basée sur le fichier.  
  
 Le *LockType* argument spécifie l’état de verrouillage de la ligne après **SQLSetPos** a été exécutée. Si le pilote est impossible de verrouiller la ligne pour effectuer l’opération demandée ou pour respecter la *LockType* argument, elle retourne SQL_ERROR et SQLSTATE 42000 (syntaxe ou violation d’accès).  
  
 Bien que le *LockType* arguments sont spécifiés pour une seule instruction, le verrou accorde les privilèges de mêmes pour toutes les instructions sur la connexion. En particulier, un verrou est acquis par une seule instruction sur une connexion peut être déverrouillé par une autre instruction sur la même connexion.  
  
 Une ligne verrouillée via **SQLSetPos** reste verrouillé jusqu'à ce que l’application appelle **SQLSetPos** pour la ligne avec *LockType* défini sur SQL_LOCK_UNLOCK, ou jusqu'à ce que l’application appels **SQLFreeHandle** pour l’instruction ou **SQLFreeStmt** avec l’option SQL_CLOSE. Pour un pilote qui prend en charge des transactions, une ligne verrouillée via **SQLSetPos** est déverrouillé lorsque l’application appelle **SQLEndTran** pour valider ou restaurer une transaction sur la connexion (si un curseur est fermé. Lorsqu’une transaction est validée ou restaurée, comme indiqué par les types d’informations SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR retournés par **SQLGetInfo**).  
  
 Le *LockType* argument prend en charge les types suivants de verrous. Pour déterminer quels verrous sont pris en charge par une source de données, une application appelle **SQLGetInfo** avec le SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_ Type d’informations CURSOR_ATTRIBUTES1 (selon le type du curseur).  
  
|*LockType* argument|Type de verrou|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|La pilote ou source de données garantit que la ligne est dans le même état verrouillé ou déverrouillé, telle qu’elle était avant **SQLSetPos** a été appelée. Cette valeur de *LockType* permet à des sources de données qui ne gèrent pas le verrouillage au niveau des lignes explicite pour utiliser le verrouillage est requis par les niveaux d’isolation d’accès concurrentiel et la transaction actuelles.|  
|SQL_LOCK_EXCLUSIVE|La source de données ou de pilote verrouille exclusivement la ligne. Une instruction sur une autre connexion ou dans une autre application ne peut pas être utilisée pour acquérir des verrous sur la ligne.|  
|SQL_LOCK_UNLOCK|La source de données ou de pilote déverrouille la ligne.|  
  
 Si un pilote prend en charge de SQL_LOCK_EXCLUSIVE mais ne prend pas en charge SQL_LOCK_UNLOCK, une ligne est verrouillée reste verrouillée jusqu'à ce qu’un des appels de fonction décrits dans le paragraphe précédent se produit.  
  
 Si un pilote prend en charge de SQL_LOCK_EXCLUSIVE mais ne prend pas en charge SQL_LOCK_UNLOCK, une ligne est verrouillée restera verrouillée jusqu'à ce que l’application appelle **SQLFreeHandle** pour l’instruction ou **SQLFreeStmt** avec l’option SQL_CLOSE. Si le pilote prend en charge des transactions et ferme le curseur sur validation ou la restauration de la transaction, l’application appelle **SQLEndTran**.  
  
 Pour les opérations update et delete dans **SQLSetPos**, l’application utilise le *LockType* argument comme suit :  
  
-   Pour garantir qu’une ligne ne change pas après qu’il est récupéré, une application appelle **SQLSetPos** avec *opération* défini sur SQL_REFRESH et *LockType* SQL_LOCK_ la valeur EXCLUSIF.  
  
-   Si l’application définit *LockType* à SQL_LOCK_NO_CHANGE, le pilote garantit qu’une opération update ou delete réussit uniquement si l’application a spécifié pour l’attribut d’instruction SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK.  
  
-   Si l’application spécifie SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES pour l’attribut d’instruction SQL_ATTR_CONCURRENCY, le pilote compare les versions de ligne ou de valeurs et rejette l’opération si la ligne a changé depuis l’application extrait une ligne.  
  
-   Si l’application spécifie la valeur SQL_CONCUR_READ_ONLY pour l’attribut d’instruction SQL_ATTR_CONCURRENCY, le pilote rejette toute mise à jour ou l’opération de suppression.  
  
 Pour plus d’informations sur l’attribut d’instruction SQL_ATTR_CONCURRENCY, consultez [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="status-and-operation-arrays"></a>État et les tableaux de l’opération  
 Les tableaux suivants de l’état et l’opération sont utilisés lors de l’appel **SQLSetPos**:  
  
-   Le tableau d’état de ligne (comme il est désigné par le champ SQL_DESC_ARRAY_STATUS_PTR dans le descripteur IRD et l’attribut d’instruction SQL_ATTR_ROW_STATUS_ARRAY) contient des valeurs d’état pour chaque ligne de données dans l’ensemble de lignes. Le pilote définit les valeurs d’état dans ce tableau après un appel à **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, ou **SQLSetPos** . Ce tableau est indiqué par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR.  
  
-   Le tableau d’opération de ligne (comme il est désigné par le champ SQL_DESC_ARRAY_STATUS_PTR le ARD et l’attribut d’instruction SQL_ATTR_ROW_OPERATION_ARRAY) contient une valeur pour chaque ligne dans l’ensemble de lignes qui indique si un appel à **SQLSetPos**pour une opération en bloc est ignorée ou effectuée. Chaque élément dans le tableau est défini sur SQL_ROW_PROCEED (la valeur par défaut) ou SQL_ROW_IGNORE. Ce tableau est indiqué par l’attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR.  
  
 Le nombre d’éléments dans les tableaux d’état et l’opération doit égal au nombre de lignes dans l’ensemble de lignes (comme défini par l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE).  
  
 Pour plus d’informations sur le tableau d’état de ligne, consultez [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md). Pour plus d’informations sur le tableau d’opération de ligne, consultez « En ignorant une ligne dans une opération en bloc, » plus loin dans cette section.  
  
## <a name="using-sqlsetpos"></a>À l’aide de SQLSetPos  
 Avant d’une application appelle **SQLSetPos**, il doit exécuter la séquence d’étapes suivante :  
  
1.  Si l’application appelle **SQLSetPos** avec *opération* SQL_UPDATE, appel de la valeur **SQLBindCol** (ou **SQLSetDescRec**) pour chaque colonne pour spécifier son type de données et lier les mémoires tampons de données et la longueur de la colonne.  
  
2.  Si l’application appelle **SQLSetPos** avec *opération* défini sur SQL_DELETE ou SQL_UPDATE, appel **SQLColAttribute** pour vous assurer que les colonnes à être supprimé ou mis à jour sont modifiables.  
  
3.  Appelez **SQLExecDirect**, **SQLExecute**, ou une fonction de catalogue pour créer un jeu de résultats.  
  
4.  Appelez **SQLFetch** ou **SQLFetchScroll** pour récupérer les données.  
  
 Pour plus d’informations sur l’utilisation de **SQLSetPos**, consultez [la mise à jour des données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
## <a name="deleting-data-using-sqlsetpos"></a>Suppression des données à l’aide de SQLSetPos  
 Pour supprimer des données avec **SQLSetPos**, une application appelle **SQLSetPos** avec *RowNumber* défini sur le nombre de la ligne à supprimer et *opération*défini sur SQL_DELETE.  
  
 Une fois que les données ont été supprimées, le pilote modifie la valeur dans le tableau d’état de ligne mise en œuvre pour la ligne appropriée à SQL_ROW_DELETED (ou SQL_ROW_ERROR).  
  
## <a name="updating-data-using-sqlsetpos"></a>La mise à jour des données à l’aide de SQLSetPos  
 Une application peut passer la valeur d’une colonne dans la mémoire tampon de données liées ou avec un ou plusieurs appels à **SQLPutData**. Les colonnes dont les données sont passées avec **SQLPutData** sont appelés *data-at-execution* *colonnes*. Celles-ci sont couramment utilisés pour envoyer des données pour les colonnes SQL_LONGVARBINARY et SQL_LONGVARCHAR et peuvent être combinés avec d’autres colonnes.  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>Pour mettre à jour des données avec SQLSetPos, une application :  
  
1.  Place les valeurs dans les mémoires tampons de données et de longueur / d’indicateur lié avec **SQLBindCol**:  
  
    -   Pour les colonnes normales, l’application place la nouvelle valeur de colonne dans la  *\*TargetValuePtr* mémoire tampon et la longueur de cette valeur dans le  *\*StrLen_or_IndPtr* mémoire tampon. Si la ligne ne doit pas être mis à jour, l’application place SQL_ROW_IGNORE dans l’élément de cette ligne du tableau d’opération de ligne.  
  
    -   Pour les colonnes de données en cours d’exécution, l’application place une valeur définie par l’application, comme le numéro de colonne, dans le  *\*TargetValuePtr* mémoire tampon. La valeur peut être utilisée ultérieurement pour identifier la colonne.  
  
         L’application place le résultat de la SQL_LEN_DATA_AT_EXEC (*longueur*) macro dans le **StrLen_or_IndPtr* mémoire tampon. Si le type de données SQL de la colonne est SQL_LONGVARBINARY, SQL_LONGVARCHAR ou un type de données spécifiques à la source de données de type long et que le pilote retourne « Y » pour le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo**, *longueur*  est le nombre d’octets de données à envoyer pour le paramètre ; sinon, il doit être une valeur non négative et est ignoré.  
  
2.  Appels **SQLSetPos** avec la *opération* argument valeur SQL_UPDATE pour mettre à jour de la ligne de données.  
  
    -   S’il n’y a aucune colonne de données en cours d’exécution, le processus est terminé.  
  
    -   S’il existe des colonnes de données en cours d’exécution, la fonction retourne SQL_NEED_DATA et se poursuit à l’étape 3.  
  
3.  Appels **SQLParamData** pour récupérer l’adresse de la  *\*TargetValuePtr* mémoire tampon pour la première colonne de data-at-execution à traiter. **SQLParamData** retourne SQL_NEED_DATA. L’application récupère la valeur définie par l’application à partir de la  *\*TargetValuePtr* mémoire tampon.  
  
    > [!NOTE]  
    >  Bien que les paramètres de data-at-execution sont similaires aux colonnes de données en cours d’exécution, la valeur retournée par **SQLParamData** est différent pour chacun.  
  
    > [!NOTE]  
    >  Paramètres de Data-at-execution sont des paramètres dans une instruction SQL pour laquelle les données sont envoyées avec **SQLPutData** lorsque l’instruction est exécutée avec **SQLExecDirect** ou **SQLExecute**. Elles sont liées avec **SQLBindParameter** ou en définissant des descripteurs avec **SQLSetDescRec**. La valeur retournée par **SQLParamData** est une valeur 32 bits passée à **SQLBindParameter** dans le *ParameterValuePtr* argument.  
  
    > [!NOTE]  
    >  Colonnes de Data-at-execution sont des colonnes dans un ensemble de lignes pour lequel les données sont envoyées avec **SQLPutData** quand une ligne est mise à jour avec **SQLSetPos**. Elles sont liées avec **SQLBindCol**. La valeur retournée par **SQLParamData** est l’adresse de la ligne dans le **TargetValuePtr* mémoire tampon qui est en cours de traitement.  
  
4.  Appels **SQLPutData** une ou plusieurs fois pour envoyer des données pour la colonne. Plusieurs appels n’est nécessaire si toutes les valeurs de données ne peut pas être retournés dans le  *\*TargetValuePtr* mémoire tampon spécifiée dans **SQLPutData**; appels multiples à **SQLPutData** pour la même colonne sont autorisées uniquement lors de l’envoi des données de caractères C à une colonne avec un type de données de spécifique à la source de données, binaire ou caractère ou lors de l’envoi des données binaires de C à une colonne avec un caractère, binaire, ou le type de données spécifique à la source de données.  
  
5.  Appels **SQLParamData** pour signaler que toutes les données a été envoyé pour la colonne.  
  
    -   S’il existe plus de colonnes de data-at-execution **SQLParamData** retourne SQL_NEED_DATA et l’adresse de la *TargetValuePtr* mémoire tampon pour la colonne data-at-execution suivante à traiter. L’application répète les étapes 4 et 5.  
  
    -   S’il n’y a pas d’autres colonnes de data-at-execution, le processus est terminé. Si l’instruction a été exécutée avec succès, **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO ; si l’exécution a échoué, elle retourne SQL_ERROR. À ce stade, **SQLParamData** peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLSetPos**.  
  
 Si les données a été mis à jour, le pilote modifie la valeur dans le tableau d’état de ligne mise en œuvre pour la ligne appropriée à SQL_ROW_UPDATED.  
  
 Si l’opération est annulée ou une erreur se produit dans **SQLParamData** ou **SQLPutData**, après **SQLSetPos** retourne SQL_NEED_DATA et avant l’envoi de données pour tous les colonnes de données en cours d’exécution, l’application peut appeler uniquement **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions** , **SQLParamData**, ou **SQLPutData** pour l’instruction ou la connexion associée à l’instruction. Si elle appelle une autre fonction pour l’instruction ou la connexion associée à l’instruction, la fonction retourne SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction).  
  
 Si l’application appelle **SQLCancel** tandis que le pilote a toujours besoin de données pour les colonnes de données en cours d’exécution, le pilote annule l’opération. L’application peut ensuite appeler **SQLSetPos** nouveau ; annulation n’affecte pas l’état de curseur ou la position actuelle du curseur.  
  
 Lorsque la liste de sélection de la spécification de requête associée au curseur contient plusieurs références à la même colonne, si une erreur est générée ou le pilote ignore les références en double et effectue les opérations demandées est définie par le pilote.  
  
## <a name="performing-bulk-operations"></a>Exécution d’opérations en bloc  
 Si le *RowNumber* argument est 0, le pilote effectue l’opération spécifiée dans le *opération* argument pour chaque ligne dans l’ensemble de lignes qui a une valeur de SQL_ROW_PROCEED dans son champ de l’opération de ligne tableau vers lequel pointe attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR. Il s’agit d’une valeur valide de la *RowNumber* argument pour un *opération* argument de SQL_DELETE, SQL_REFRESH, ou SQL_UPDATE, mais pas SQL_POSITION. **SQLSetPos** avec un *opération* de SQL_POSITION et un *RowNumber* égal à 0 retourne SQLSTATE HY109 (position de curseur non valide).  
  
 Si une erreur produit, qui se rapporte à l’ensemble de lignes, telles que SQLSTATE HYT00 (délai d’attente expiré), le pilote retourne SQL_ERROR et le SQLSTATE approprié. Le contenu des mémoires tampons ensemble de lignes n’est pas défini, et la position du curseur est inchangée.  
  
 Si une erreur produit, qui rapporte à une seule ligne, le pilote :  
  
-   Définit l’élément de la ligne dans le tableau d’état de ligne vers laquelle pointé l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR à SQL_ROW_ERROR.  
  
-   Publie un ou plusieurs SQLSTATE supplémentaires pour l’erreur dans la file d’attente de l’erreur et définit le champ SQL_DIAG_ROW_NUMBER dans la structure de données de diagnostic.  
  
 Une fois qu’il a traité l’erreur ou l’avertissement, si le pilote termine l’opération pour les lignes restantes dans l’ensemble de lignes, il retourne SQL_SUCCESS_WITH_INFO. Par conséquent, pour chaque ligne qui a renvoyé une erreur, la file d’attente de l’erreur contient zéro ou plusieurs SQLSTATE supplémentaires. Si le pilote arrête l’opération après avoir traité l’erreur ou l’avertissement, elle retourne SQL_ERROR.  
  
 Si le pilote retourne tous les avertissements, tels que SQLSTATE 01004 (données tronquées), elle retourne des avertissements qui s’appliquent à l’ensemble de lignes ou à des lignes inconnus dans l’ensemble de lignes avant de retourner les informations d’erreur qui s’applique à des lignes spécifiques. Elle retourne des avertissements pour des lignes spécifiques, ainsi que d’autres informations d’erreur sur les lignes.  
  
 Si *RowNumber* est égal à 0 et *opération* est SQL_UPDATE, SQL_REFRESH ou SQL_DELETE, le nombre de lignes qui **SQLSetPos** opère sur pointe vers la sorte Attribut d’instruction _FETCHED_PTR.  
  
 Si *RowNumber* est égal à 0 et *opération* soit SQL_DELETE, SQL_REFRESH, SQL_UPDATE, la ligne actuelle après l’opération est identique à la ligne actuelle avant l’opération.  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>Ignorer une ligne dans une opération en bloc  
 Le tableau d’opération de ligne peut être utilisé pour indiquer qu’une ligne dans l’ensemble de lignes en cours doit être ignorée pendant une opération en bloc à l’aide **SQLSetPos**. Pour indiquer au pilote d’ignorer une ou plusieurs lignes lors d’une opération en bloc, une application doit effectuer les étapes suivantes :  
  
1.  Appelez **SQLSetStmtAttr** pour définir l’attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR pour pointer vers un tableau de SQLUSMALLINTs. Ce champ peut également être défini en appelant **SQLSetDescField** pour définir le champ d’en-tête SQL_DESC_ARRAY_STATUS_PTR de ARD, ce qui nécessite qu’une application obtient le handle du descripteur.  
  
2.  Définissez chaque élément du tableau d’opération de ligne à une des deux valeurs :  
  
    -   SQL_ROW_IGNORE, pour indiquer que la ligne est exclue pour l’opération en bloc.  
  
    -   SQL_ROW_PROCEED, pour indiquer que la ligne est incluse dans l’opération en bloc. (Il s'agit de la valeur par défaut.)  
  
3.  Appelez **SQLSetPos** pour effectuer l’opération en bloc.  
  
 Les règles suivantes s’appliquent dans le tableau d’opération de ligne :  
  
-   SQL_ROW_IGNORE et SQL_ROW_PROCEED affectent uniquement les opérations en bloc à l’aide de **SQLSetPos** avec un *opération* de SQL_DELETE ou SQL_UPDATE. Elles n’affectent pas les appels à **SQLSetPos** avec un *opération* de SQL_REFRESH ou SQL_POSITION.  
  
-   Le pointeur est défini sur null par défaut.  
  
-   Si le pointeur est null, toutes les lignes sont mises à jour comme si tous les éléments ont été définies à SQL_ROW_PROCEED.  
  
-   Définition d’un élément à SQL_ROW_PROCEED ne garantit pas que l’opération se produit sur cette ligne particulière. Par exemple, si une ligne de l’ensemble de lignes a l’état SQL_ROW_ERROR, le pilote peut-être pas en mesure de mettre à jour cette ligne, quel que soit l’application a spécifié que SQL_ROW_PROCEED. Une application doit toujours vérifier le tableau d’état de ligne pour voir si l’opération a réussi.  
  
-   SQL_ROW_PROCEED est définie comme 0 dans le fichier d’en-tête. Une application peut initialiser le tableau d’opération de ligne 0 afin de traiter toutes les lignes.  
  
-   Si le numéro d’élément « n » dans le tableau d’opération de ligne est défini sur SQL_ROW_IGNORE et **SQLSetPos** est appelée pour effectuer une mise à jour en bloc ou de supprimer l’opération, l’énième ligne dans l’ensemble de lignes reste inchangé après l’appel à **SQLSetPos**.  
  
-   Une application doit automatiquement la valeur est une colonne en lecture seule SQL_ROW_IGNORE.  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>Ignorer une colonne dans une opération en bloc  
 Pour éviter un traitement inutile les diagnostics générés par les mises à jour a été lancées pour une ou plusieurs colonnes en lecture seule, une application peut définir la valeur dans la mémoire tampon de longueur / d’indicateur lié à SQL_COLUMN_IGNORE. Pour plus d’informations, consultez [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application permet à un utilisateur de parcourir la table ORDERS et de mettre à jour d’état de la commande. Le curseur est commandé par keyset avec une taille d’ensemble de lignes de 20 et utilise le contrôle d’accès concurrentiel optimiste comparaison des versions de ligne. Une fois que chaque ensemble de lignes est extraites, l’application imprime et permet à l’utilisateur sélectionner et mettre à jour l’état d’une commande. L’application utilise **SQLSetPos** pour positionner le curseur sur la ligne sélectionnée et effectue une mise à jour positionnée de la ligne. (La gestion des erreurs sont omises par souci de clarté).  
  
```cpp  
#define ROWS 20  
#define STATUS_LEN 6  
  
SQLCHAR        szStatus[ROWS][STATUS_LEN], szReply[3];  
SQLINTEGER     cbStatus[ROWS], cbOrderID;  
SQLUSMALLINT   rgfRowStatus[ROWS];  
SQLUINTEGER    sOrderID, crow = ROWS, irow;  
SQLHSTMT       hstmtS, hstmtU;  
  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CONCURRENCY, (SQLPOINTER) SQL_CONCUR_ROWVER, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER) SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_STATUS_PTR, (SQLPOINTER) rgfRowStatus, 0);  
SQLSetCursorName(hstmtS, "C1", SQL_NTS);  
SQLExecDirect(hstmtS, "SELECT ORDERID, STATUS FROM ORDERS ", SQL_NTS);  
  
SQLBindCol(hstmtS, 1, SQL_C_ULONG, &sOrderID, 0, &cbOrderID);  
SQLBindCol(hstmtS, 2, SQL_C_CHAR, szStatus, STATUS_LEN, &cbStatus);  
  
while ((retcode == SQLFetchScroll(hstmtS, SQL_FETCH_NEXT, 0)) != SQL_ERROR) {  
   if (retcode == SQL_NO_DATA_FOUND)  
      break;  
   for (irow = 0; irow < crow; irow++) {  
      if (rgfRowStatus[irow] != SQL_ROW_DELETED)  
         printf("%2d %5d %*s\n", irow+1, sOrderID, NAME_LEN-1, szStatus[irow]);  
   }  
   while (TRUE) {  
      printf("\nRow number to update?");  
      gets_s(szReply, 3);  
      irow = atoi(szReply);  
      if (irow > 0 && irow <= crow) {  
         printf("\nNew status?");  
         gets_s(szStatus[irow-1], (ROWS * STATUS_LEN));  
         SQLSetPos(hstmtS, irow, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
         SQLPrepare(hstmtU,  
          "UPDATE ORDERS SET STATUS=? WHERE CURRENT OF C1", SQL_NTS);  
         SQLBindParameter(hstmtU, 1, SQL_PARAM_INPUT,  
            SQL_C_CHAR, SQL_CHAR,  
            STATUS_LEN, 0, szStatus[irow], 0, NULL);  
         SQLExecute(hstmtU);  
      } else if (irow == 0) {  
         break;  
      }  
   }  
}  
```  
  
 Pour plus d’exemples, consultez [positionné instructions Update et Delete](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) et [la mise à jour des lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à une colonne dans un jeu de résultats|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Exécution d’opérations en bloc qui ne sont pas liées à la position du curseur de bloc|[SQLBulkOperations, fonction](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll, fonction](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Obtention d’un champ unique d’un descripteur|[SQLGetDescField, fonction](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Obtention de plusieurs champs d’un descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Définition d’un champ unique d’un descripteur|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Définition de plusieurs champs d’un descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Définition d’un attribut d’instruction|[SQLSetStmtAttr, fonction](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
