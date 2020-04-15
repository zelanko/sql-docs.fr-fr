---
title: Fonction SQLSetPos (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetPos
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetPos
helpviewer_keywords:
- SQLSetPos function [ODBC]
ms.assetid: 80190ee7-ae3b-45e5-92a9-693eb558f322
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a8839f1ae540ac9e5f29e144f7f57fb754e50ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287329"
---
# <a name="sqlsetpos-function"></a>SQLSetPos, fonction
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLSetPos** définit la position du curseur dans un jeu de lignes et permet à une application de actualiser les données dans le rame ou de mettre à jour ou de supprimer des données dans l’ensemble de résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLSetPos(  
      SQLHSTMT        StatementHandle,  
      SQLSETPOSIROW   RowNumber,  
      SQLUSMALLINT    Operation,  
      SQLUSMALLINT    LockType);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *RowNumber*  
 [Entrée] Position de la rangée dans le ramage sur lequel effectuer l’opération spécifiée avec *l’argument de l’opération.* Si *RowNumber* est 0, l’opération s’applique à chaque rangée dans le ramage.  
  
 Pour plus d’informations, voir «Commentaires».  
  
 *Opération*  
 [Entrée] Opération pour effectuer :  
  
 SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE  
  
> [!NOTE]
>  La valeur SQL_ADD pour *l’argument de l’opération* a été amortie pour ODBC *3.x*. Les conducteurs ODBC *3.x* devront prendre en charge SQL_ADD pour la compatibilité vers l’arrière. Cette fonctionnalité a été remplacée par un appel à **SQLBulkOperations** par une *opération* de SQL_ADD. Lorsqu’une application ODBC *3.x* fonctionne avec un conducteur ODBC *2.x,* le Driver Manager passe un appel à **SQLBulkOperations** avec une *opération* de SQL_ADD à **SQLSetPos** avec une *opération* de SQL_ADD.  
  
 Pour plus d’informations, voir "Commentaires".  
  
 *LockType LockType*  
 [Entrée] Précise comment verrouiller la ligne après avoir effectué l’opération spécifiée dans *l’argumentation de l’opération.*  
  
 SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK  
  
 Pour plus d’informations, voir "Commentaires".  
  
 **Retours**  
  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetPos** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLSetPos** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
 Pour toutes les SQLSTATEs qui peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_ERROR (à l’exception des SQLSTATes de 01xxx), SQL_SUCCESS_WITH_INFO est retournée si une erreur se produit sur une ou plusieurs rangées, mais pas toutes, d’une opération à plusieurs pousses, et SQL_ERROR est retournée si une erreur se produit sur une opération à une seule rangée.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01001|Conflit d’opération cursor|*L’argument de l’opération* était SQL_DELETE ou SQL_UPDATE, et aucune rangée ou plus d’une rangée n’a été supprimée ou mise à jour. (Pour plus d’informations sur les mises à jour de plus d’une rangée, voir la description de *l’attribut* SQL_ATTR_SIMULATE_CURSOR dans **SQLSetStmtAttr .)** (Les retours de fonction SQL_SUCCESS_WITH_INFO.)<br /><br /> *L’argument de l’opération* était SQL_DELETE ou SQL_UPDATE, et l’opération a échoué en raison de la concordance optimiste. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Truncation droite de données de chaîne|*L’argument de l’opération* était SQL_REFRESH, et les données de chaîne ou binaire retournées pour une colonne ou des colonnes avec un type de SQL_C_CHAR de données ou SQL_C_BINARY ont abouti à la troncation de caractères nonblank ou de données binaires non-NULL.|  
|01S01|Erreur dans la rangée|*L’argument de RowNumber* était 0, et une erreur s’est produite dans une ou plusieurs rangées lors de l’exécution de l’opération spécifiée avec *l’argument de l’opération.*<br /><br /> (SQL_SUCCESS_WITH_INFO est retournée si une erreur se produit sur une ou plusieurs rangées, mais pas toutes, d’une opération à plusieurs lancers, et SQL_ERROR est retournée si une erreur se produit sur une opération à une seule rangée.)<br /><br /> (Ce SQLSTATE n’est retourné que lorsque **SQLSetPos** est appelé après **SQLExtendedFetch**, si le conducteur est un conducteur ODBC *2.x* et la bibliothèque de curseurs n’est pas utilisé.)|  
|01S07|Troncation fractionnaire|*L’argument de l’opération* était SQL_REFRESH, le type de données du tampon d’application n’était pas SQL_C_CHAR ou SQL_C_BINARY, et les données retournées aux tampons d’application pour une ou plusieurs colonnes ont été tronquées. Pour les types de données numériques, la partie fractionnaire du nombre a été tronquée. Pour le temps, l’humidité du temps et les types de données d’intervalle contenant un composant de temps, la partie fractionnelle du temps a été tronquée.<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|La valeur de données d’une colonne dans l’ensemble de résultat n’a pas pu être convertie au type de données spécifié par *TargetType* dans l’appel à **SQLBindCol**.|  
|07009|Indice descripteur invalide|*L’argument Opération* a été SQL_REFRESH ou SQL_UPDATE, et une colonne a été liée avec un nombre de colonnes supérieure au nombre de colonnes dans l’ensemble de résultat.|  
|21S02|Le degré de tableau dérivé ne correspond pas à la liste des colonnes|*L’argument Opération* était SQL_UPDATE, et aucune colonne n’était updatable parce que toutes les colonnes étaient soit non liées, lues seulement, ou la valeur dans la longueur liée / tampon indicateur a été SQL_COLUMN_IGNORE.|  
|22001|Données de chaîne, troncation droite|*L’argument de l’Opération* était SQL_UPDATE, et l’affectation d’un personnage ou d’une valeur binaire à une colonne a abouti à la troncation de caractères ou d’octets non-noirs (pour les caractères) ou non nuls (pour les caractères ou les octets binaires).|  
|22003|Valeur numérique hors de portée|*L’argument Opération* a été SQL_UPDATE, et l’attribution d’une valeur numérique à une colonne dans l’ensemble de résultat a causé l’ensemble (par opposition à fractionnel) partie du nombre d’être tronqué.<br /><br /> *L’argument Opération* a été SQL_REFRESH, et le retour de la valeur numérique pour une ou plusieurs colonnes liées aurait causé une perte de chiffres importants.|  
|22007|Format de date invalide|*L’argument Opération* a été SQL_UPDATE, et l’affectation d’une date ou une valeur de temps à une colonne dans l’ensemble de résultat a causé l’année, le mois, ou le champ de jour pour être hors de portée.<br /><br /> *L’argument Opération* a été SQL_REFRESH, et le retour de la date ou de la valeur de timestamp pour une ou plusieurs colonnes liées aurait causé l’année, le mois ou le champ de jour pour être hors de portée.|  
|22008|Débordement de champ date/heure|L’argument de *l’opération* était SQL_UPDATE, et l’exécution de l’arithmétique de date sur les données envoyées à une colonne dans le résultat fixé a abouti à un champ de date time (l’année, le mois, le jour, l’heure, la minute, ou le deuxième champ) du résultat étant en dehors de la gamme permise de valeurs pour le champ, ou étant invalide sur la base des règles naturelles du calendrier grégorien pour les dates.<br /><br /> L’argument de *l’opération* était SQL_REFRESH, et l’exécution de l’arithmétique de date sur les données récupérées à partir du résultat fixé a abouti à un champ de date (l’année, le mois, le jour, l’heure, la minute ou le deuxième champ) du résultat étant en dehors de la gamme permise de valeurs pour le champ, ou étant invalide en fonction des règles naturelles du calendrier grégorien pour les dates.|  
|22015|Débordement de champ d’intervalle|*L’argument de l’opération* était SQL_UPDATE, et l’affectation d’un type C numérique ou d’intervalle exact à un type de données SQL d’intervalle a causé une perte de chiffres importants.<br /><br /> *L’argument de l’Opération* était SQL_UPDATE; lors de l’attribution à un type SQL d’intervalle, il n’y avait aucune représentation de la valeur du type C dans le type SQL d’intervalle.<br /><br /> *L’argument de l’opération* était SQL_REFRESH, et l’attribution d’un type SQL numérique ou d’intervalle exact à un type d’intervalle C a causé une perte de chiffres importants dans le champ principal.<br /><br /> *L’argument de l’opération* était SQL_ REFRESH; lors de l’attribution à un type d’intervalle C, il n’y avait aucune représentation de la valeur du type SQL dans le type d’intervalle C.|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|*L’argument de l’Opération* était SQL_REFRESH; le type C était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type SQL de la colonne était un type de données de caractère; et la valeur de la colonne n’était pas un littéral valide du type C lié.<br /><br /> *L’argument Opération* a été SQL_UPDATE; le type SQL était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type C était SQL_C_CHAR; et la valeur de la colonne n’était pas un littéral valide du type SQL lié.|  
|23000|Violation de la contrainte d’intégrité|*L’argument Opération* a été SQL_DELETE ou SQL_UPDATE, et une contrainte d’intégrité a été violée.|  
|24 000|État de curseur non valide|Le *StatementHandle* était dans un état exécuté, mais aucun ensemble de résultat n’a été associé à la *StatementHandle*.<br /><br /> (DM) Un curseur était ouvert sur le *StatementHandle*, mais **SQLFetch** ou **SQLFetchScroll** n’avait pas été appelé.<br /><br /> Un curseur était ouvert sur le *StatementHandle*, et **SQLFetch** ou **SQLFetchScroll** avaient été appelés, mais le curseur a été positionné avant le début de l’ensemble de résultats ou après la fin de l’ensemble de résultats.<br /><br /> *L’argument Opération* a été SQL_DELETE, SQL_REFRESH, ou SQL_UPDATE, et le curseur a été positionné avant le début de l’ensemble de résultat ou après la fin de l’ensemble de résultat.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|42000|Erreur de syntaxe ou violation d’accès|Le conducteur n’a pas été en mesure de verrouiller la rangée au besoin pour effectuer l’opération demandée dans *l’argument Opération*.<br /><br /> Le conducteur n’a pas été en mesure de verrouiller la ligne comme demandé dans l’argument *LockType*.|  
|44000|Violation de WITH CHECK OPTION|*L’argument de l’opération* a été SQL_UPDATE, et la mise à jour a été effectuée sur une table vue ou une table dérivée de la table vue qui a été créée en spécifiant **AVEC CHECK OPTION**, de sorte qu’une ou plusieurs lignes touchées par la mise à jour ne seront plus présentes dans la table vue.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*, puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction SQLSetPos a été appelée.<br /><br /> (DM) Le *statementhandle* spécifié n’était pas dans un état exécuté. La fonction a été appelée sans appeler **d’abord SQLExecDirect**, **SQLExecute**, ou une fonction de catalogue.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Le conducteur était un conducteur ODBC *2.x,* et **SQLSetPos** a été appelé pour un *statementHandle* après **SQLFetch** a été appelé.|  
|HY011 HY011|L’attribut ne peut pas être défini maintenant|(DM) Le conducteur était un conducteur ODBC *2.x;* l’attribut de l’énoncé de SQL_ATTR_ROW_STATUS_PTR a été défini; puis **SQLSetPos** a été appelé avant **SQLFetch**, **SQLFetchScroll**, ou **SQLExtendedFetch** a été appelé.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|*L’argument de l’opération* était SQL_UPDATE, une valeur de données était un pointeur nul, et la valeur de longueur de la colonne n’était pas de 0, SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NULL_DATA, ou inférieure ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> *L’argument de l’Opération* était SQL_UPDATE; une valeur de données n’était pas un pointeur nul; le type de données C était SQL_C_BINARY ou SQL_C_CHAR; et la valeur de longueur de la colonne était inférieure à 0, mais pas égale à SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS, ou SQL_NULL_DATA, ou moins ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> La valeur d’un tampon de longueur/indicateur était SQL_DATA_AT_EXEC; le type SQL était soit SQL_LONGVARCHAR, SQL_LONGVARBINARY, soit un type de données spécifique à une source de données longue; et le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était « Y ».|  
|HY092 HY092|Identifiant d’attribut invalide|(DM) La valeur spécifiée pour *l’argument de l’opération* était invalide.<br /><br /> (DM) La valeur spécifiée pour l’argument *LockType* était invalide.<br /><br /> *L’argument de l’Opération* était SQL_UPDATE ou SQL_DELETE, et l’attribut SQL_ATTR_CONCURRENCY déclaration était SQL_ATTR_CONCUR_READ_ONLY.|  
|HY107|Valeur de la ligne hors de portée|La valeur spécifiée pour l’argument *RowNumber* était supérieure au nombre de lignes dans le ramage.|  
|HY109 HY109|Position de curseur invalide|Le curseur associé au *StatementHandle* a été défini comme avant seulement, de sorte que le curseur ne pouvait pas être placé dans le jeu de ligne. Voir la description de l’attribut SQL_ATTR_CURSOR_TYPE dans **SQLSetStmtAttr**.<br /><br /> *L’argument de l’Opération* était SQL_UPDATE, SQL_DELETE ou SQL_REFRESH, et la querelle identifiée par l’argument *de RowNumber* avait été supprimée ou n’avait pas été récupérée.<br /><br /> (DM) L’argument *de RowNumber* était 0, et *l’argument de l’opération* était SQL_POSITION.<br /><br /> **SQLSetPos** a été appelé après **l’appel de SQLBulkOperations** et avant **que SQLFetchScroll** ou **SQLFetch** ne soit appelé.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données n’appuie pas l’opération demandée dans *l’argument de l’opération* ou l’argument *LockType.*|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtAttr** avec un *attribut* de SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
  
> [!CAUTION]
>  Pour obtenir de l’information sur la déclaration indique que **SQLSetPos** peut être appelé et ce qu’il doit faire pour la compatibilité avec les applications ODBC *2.x,* voir [Block Cursors, Cursors Scrollable, et Compatibilité vers l’arrière](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md).  
  
## <a name="rownumber-argument"></a>RowNumber Argument  
 *L’argument de RowNumber* précise le nombre de rangées dans le rangée sur lequel effectuer l’opération spécifiée par *l’argument de l’opération.* Si *RowNumber* est 0, l’opération s’applique à chaque rangée dans le ramage. *RowNumber* doit être une valeur de 0 au nombre de rangées dans le ramage.  
  
> [!NOTE]  
>  Dans la langue C, les tableaux sont basés sur 0 et l’argument *RowNumber* est basé sur 1. Par exemple, pour mettre à jour la cinquième rangée de l’achambre, une application modifie les tampons encastrés à l’indice de tableau 4, mais spécifie un *RowNumber* de 5.  
  
 Toutes les opérations positionnent le curseur sur la ligne spécifiée par *RowNumber*. Les opérations suivantes nécessitent une position de curseur :  
  
-   Mise à jour et suppression des relevés positionnés.  
  
-   Appels à **SQLGetData**.  
  
-   Appels à **SQLSetPos** avec les options SQL_DELETE, SQL_REFRESH et SQL_UPDATE.  
  
 Par exemple, si *RowNumber* est 2 pour un appel à **SQLSetPos** avec une *opération* de SQL_DELETE, le curseur est positionné sur la deuxième rangée de la rangée et cette rangée est supprimée. L’entrée dans le tableau d’état de la ligne de mise en œuvre (indiquée par l’attribut de l’SQL_ATTR_ROW_STATUS_PTR) pour la deuxième rangée est changée pour SQL_ROW_DELETED.  
  
 Une application peut spécifier une position de curseur lorsqu’elle appelle **SQLSetPos**. En général, il appelle **SQLSetPos** avec l’opération SQL_POSITION ou SQL_REFRESH pour positionner le curseur avant d’exécuter une mise à jour positionnée ou supprimer la déclaration ou d’appeler **SQLGetData**.  
  
## <a name="operation-argument"></a>Opération Argument  
 *L’argument de l’opération* appuie les opérations suivantes. Pour déterminer quelles options sont prises en charge par une source de données, une application appelle **SQLGetInfo** avec le SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 type d’information (selon le type de curseur).  
  
|*Opération*<br /><br /> argument|Opération|  
|------------------------------|---------------|  
|SQL_POSITION|Le conducteur positionne le curseur sur la ligne spécifiée par *RowNumber*.<br /><br /> Le contenu du tableau d’état de la ligne indiqué par l’attribut de déclaration SQL_ATTR_ROW_OPERATION_PTR est ignoré pour *l’opération*SQL_POSITION .|  
|SQL_REFRESH|Le conducteur positionne le curseur sur la ligne spécifiée par *RowNumber* et actualise les données dans les tampons encastrés pour cette rangée. Pour plus d’informations sur la façon dont le conducteur retourne les données dans les tampons rowset, voir les descriptions de ligne-sage et colonne-sage liaison dans **SQLBindCol**.<br /><br /> **SQLSetPos** avec une *opération* de SQL_REFRESH met à jour l’état et le contenu des lignes dans le rame aller chercher actuel. Cela comprend rafraîchir les signets. Étant donné que les données dans les tampons sont actualisées mais non recadrées, les membres de la rangée sont fixes. Ceci est différent de la mise à jour effectuée par un appel à **SQLFetchScroll** avec une *FetchOrientation* de SQL_FETCH_RELATIVE et un *RowNumber* égal à 0, qui refaçonne le jeu de ligne de l’ensemble de résultat afin qu’il puisse afficher des données ajoutées et supprimer les données supprimées si ces opérations sont prises en charge par le conducteur et le curseur.<br /><br /> Un rafraîchissement réussi avec **SQLSetPos** ne changera pas un statut de ligne de SQL_ROW_DELETED. Les lignes supprimées dans le jeu de ligne continueront d’être marquées comme supprimées jusqu’à la prochaine récupération. Les lignes disparaîtront à la prochaine aller chercher si le curseur prend en charge l’emballage (dans lequel un **SQLFetch ou** **SQLFetchScroll ultérieur** ne retourne pas les rangées supprimées).<br /><br /> Les lignes ajoutées n’apparaissent pas lorsqu’un rafraîchissement avec **SQLSetPos** est effectué. Ce comportement est différent de **SQLFetchScroll** avec un *FetchType* de SQL_FETCH_RELATIVE et un *RowNumber* égal à 0, qui rafraîchit également le rame actuel, mais montrera des enregistrements ajoutés ou emballer des enregistrements supprimés si ces opérations sont prises en charge par le curseur.<br /><br /> Un rafraîchissement réussi avec **SQLSetPos** changera un statut de ligne de SQL_ROW_ADDED pour SQL_ROW_SUCCESS (si le tableau d’état de la ligne existe).<br /><br /> Un rafraîchissement réussi avec **SQLSetPos** changera un statut de ligne de SQL_ROW_UPDATED au nouveau statut de la ligne (si le tableau d’état de la ligne existe).<br /><br /> Si une erreur se produit dans une opération **SQLSetPos** sur une rangée, l’état de la rangée est réglé pour SQL_ROW_ERROR (si le tableau d’état de la ligne existe).<br /><br /> Pour un curseur ouvert avec un attribut de déclaration SQL_ATTR_CONCURRENCY de SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES, un rafraîchissement avec **SQLSetPos** pourrait mettre à jour les valeurs de concurrence optimiste utilisées par la source de données pour détecter que la ligne a changé. Si cela se produit, les versions de ligne ou les valeurs utilisées pour s’assurer que la concurrence du curseur sont mises à jour chaque fois que les tampons encastrés sont actualisés à partir du serveur. Cela se produit pour chaque rangée qui est rafraîchie.<br /><br /> Le contenu du tableau d’état de la ligne indiqué par l’attribut de déclaration SQL_ATTR_ROW_OPERATION_PTR est ignoré pour *l’opération*SQL_REFRESH .|  
|SQL_UPDATE|Le conducteur positionne le curseur sur la ligne spécifiée par *RowNumber* et met à jour la ligne de données sous-jacente avec les valeurs dans les tampons rowset (l’argument *TargetValuePtr* dans **SQLBindCol**). Il récupère la longueur des données des tampons de longueur/indicateur *(l’argument StrLen_or_IndPtr* dans **SQLBindCol**). Si la longueur d’une colonne est SQL_COLUMN_IGNORE, la colonne n’est pas mise à jour. Après la mise à jour de la ligne, le conducteur modifie l’élément correspondant du tableau d’état de la ligne pour SQL_ROW_UPDATED ou SQL_ROW_SUCCESS_WITH_INFO (si le tableau d’état de la ligne existe).<br /><br /> Il est défini par le conducteur ce que le comportement est si **SQLSetPos** avec un argument *d’opération* de SQL_UPDATE est appelé sur un curseur qui contient des colonnes en double. Le conducteur peut retourner un SQLSTATE défini par le conducteur, peut mettre à jour la première colonne qui apparaît dans l’ensemble de résultats, ou effectuer d’autres comportements définis par le conducteur.<br /><br /> Le tableau d’opération de ligne indiqué par l’attribut de l’SQL_ATTR_ROW_OPERATION_PTR déclaration peut être utilisé pour indiquer qu’une rangée dans le jeu de rangée actuel doit être ignorée lors d’une mise à jour en vrac. Pour plus d’informations, voir «Status and Operation Arrays» plus tard dans cette référence de fonction.|  
|SQL_DELETE|Le conducteur positionne le curseur sur la ligne spécifiée par *RowNumber* et supprime la ligne de données sous-jacente. Il modifie l’élément correspondant du tableau d’état de la ligne pour SQL_ROW_DELETED. Une fois la ligne supprimée, ce qui suit n’est pas valable pour la ligne : mise à jour et suppression des relevés positionnés, appels à **SQLGetData**et appels à **SQLSetPos** avec *Opération* réglée à autre chose que SQL_POSITION. Pour les conducteurs qui prennent en charge l’emballage, la ligne est supprimée du curseur lorsque de nouvelles données sont récupérées à partir de la source de données.<br /><br /> La question de savoir si la ligne reste visible dépend du type curseur. Par exemple, les lignes supprimées sont visibles par des curseurs statiques et pilotés par des clés, mais invisibles aux curseurs dynamiques.<br /><br /> Le tableau d’opération de ligne indiqué par l’attribut de l’SQL_ATTR_ROW_OPERATION_PTR déclaration peut être utilisé pour indiquer qu’une rangée dans le jeu de ligne actuel doit être ignorée lors d’une suppression en vrac. Pour plus d’informations, voir «Status and Operation Arrays» plus tard dans cette référence de fonction.|  
  
## <a name="locktype-argument"></a>LockType Argument  
 *L’argument LockType* fournit un moyen pour les applications de contrôler la concurrence. Dans la plupart des cas, les sources de données qui prennent en charge les niveaux de concurrence et les transactions ne supporteront que la valeur SQL_LOCK_NO_CHANGE de l’argument *LockType.* *L’argument LockType* n’est généralement utilisé que pour la prise en charge des fichiers.  
  
 *L’argument lockType* spécifie l’état de verrouillage de la rangée après **l’exécution de SQLSetPos.** Si le conducteur n’est pas en mesure de verrouiller la ligne pour effectuer l’opération demandée ou pour satisfaire l’argument *LockType,* il renvoie SQL_ERROR et SQLSTATE 42000 (erreur syntaxe ou violation d’accès).  
  
 Bien que l’argument *de LockType* soit spécifié pour une seule déclaration, le verrou accorde les mêmes privilèges à toutes les déclarations sur le lien. En particulier, un verrou qui est acquis par une déclaration sur une connexion peut être déverrouillé par une déclaration différente sur la même connexion.  
  
 Une ligne verrouillée par **SQLSetPos** reste verrouillée jusqu’à ce que l’application appelle **SQLSetPos** pour la ligne avec *LockType* réglé pour SQL_LOCK_UNLOCK, ou jusqu’à ce que l’application appelle **SQLFreeHandle** pour la déclaration ou **SQLFreeStmt** avec l’option SQL_CLOSE. Pour un conducteur qui prend en charge les transactions, une ligne verrouillée par **SQLSetPos** est déverrouillée lorsque l’application appelle **SQLEndTran** pour valider ou annuler une transaction sur la connexion (si un curseur est fermé lorsqu’une transaction est engagée ou annulée, comme l’indiquent les types d’information SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR retournés par **SQLGetInfo**).  
  
 *L’argument LockType* prend en charge les types de serrures suivants. Pour déterminer quels verrous sont pris en charge par une source de données, une application appelle **SQLGetInfo** avec le SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 type d’information (selon le type de curseur).  
  
|*Argument LockType*|Type de verrou|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|Le conducteur ou la source de données s’assure que la rangée est dans le même état verrouillé ou déverrouillé qu’avant **SQLSetPos** a été appelé. Cette valeur de *LockType* permet aux sources de données qui ne prennent pas en charge le verrouillage explicite au niveau des rangées d’utiliser tout verrouillage requis par les niveaux actuels de concurrence et d’isolement des transactions.|  
|SQL_LOCK_EXCLUSIVE|Le conducteur ou la source de données verrouille la ligne exclusivement. Une déclaration sur une connexion différente ou dans une application différente ne peut pas être utilisée pour acquérir des verrous sur la ligne.|  
|SQL_LOCK_UNLOCK|Le conducteur ou la source de données déverrouille la ligne.|  
  
 Si un conducteur prend en charge SQL_LOCK_EXCLUSIVE mais ne prend pas en charge SQL_LOCK_UNLOCK, une rangée qui est verrouillée restera verrouillée jusqu’à ce que l’un des appels de fonction décrit dans le paragraphe précédent se produise.  
  
 Si un conducteur prend en charge SQL_LOCK_EXCLUSIVE mais ne prend pas en charge SQL_LOCK_UNLOCK, une rangée qui est verrouillée restera verrouillée jusqu’à ce que la demande appelle **SQLFreeHandle** pour la déclaration ou **SQLFreeStmt** avec l’option SQL_CLOSE. Si le conducteur prend en charge les transactions et ferme le curseur lors de l’engagement ou du recul de la transaction, l’application appelle **SQLEndTran**.  
  
 Pour les opérations de mise à jour et de suppression dans **SQLSetPos**, l’application utilise l’argument *LockType* comme suit:  
  
-   Pour garantir qu’une ligne ne change pas après sa récupération, une application appelle **SQLSetPos** avec *Opération* réglée à SQL_REFRESH et *LockType* mis à SQL_LOCK_EXCLUSIVE.  
  
-   Si l’application définit *LockType* à SQL_LOCK_NO_CHANGE, le conducteur garantit qu’une opération de mise à jour ou de suppression ne réussira que si l’application spécifiée SQL_CONCUR_LOCK pour l’attribut SQL_ATTR_CONCURRENCY déclaration.  
  
-   Si l’application spécifie SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES pour l’attribut de l’SQL_ATTR_CONCURRENCY, le conducteur compare les versions ou les valeurs de la ligne et rejette l’opération si la ligne a changé depuis que l’application a récupéré la ligne.  
  
-   Si l’application spécifie SQL_CONCUR_READ_ONLY pour l’attribut de l’SQL_ATTR_CONCURRENCY, le conducteur rejette toute mise à jour ou suppression de l’opération.  
  
 Pour plus d’informations sur l’attribut SQL_ATTR_CONCURRENCY déclaration, voir [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="status-and-operation-arrays"></a>Classement et opérations Arrays  
 Les tableaux d’état et d’opération suivants sont utilisés lors de l’appel **SQLSetPos**:  
  
-   Le tableau d’état de la ligne (comme le souligne le champ SQL_DESC_ARRAY_STATUS_PTR dans l’IRD et l’attribut de l’SQL_ATTR_ROW_STATUS_ARRAY) contient des valeurs de statut pour chaque rangée de données dans le rangée. Le conducteur définit les valeurs de statut dans ce tableau après un appel à **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, ou **SQLSetPos**. Ce tableau est souligné par l’attribut de l’SQL_ATTR_ROW_STATUS_PTR déclaration.  
  
-   Le tableau d’exploitation de la rangée (tel que mentionné par le champ SQL_DESC_ARRAY_STATUS_PTR dans l’ARD et l’attribut de l’énoncé de SQL_ATTR_ROW_OPERATION_ARRAY) contient une valeur pour chaque rangée dans le ramage qui indique si un appel à **SQLSetPos** pour une opération en vrac est ignoré ou effectué. Chaque élément du tableau est réglé sur SQL_ROW_PROCEED (par défaut) ou SQL_ROW_IGNORE. Ce tableau est souligné par l’attribut SQL_ATTR_ROW_OPERATION_PTR déclaration.  
  
 Le nombre d’éléments dans les tableaux d’état et d’exploitation doit égaler le nombre de lignes dans le rangée (tel que défini par l’attribut de l’SQL_ATTR_ROW_ARRAY_SIZE déclaration).  
  
 Pour plus d’informations sur le tableau d’état de la ligne, voir [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md). Pour plus d’informations sur le tableau d’exploitation de la rangée, voir « Ignorer une rangée dans une opération en vrac », plus tard dans cette section.  
  
## <a name="using-sqlsetpos"></a>Utilisation de SQLSetPos  
 Avant qu’une application n’appelle **SQLSetPos**, elle doit effectuer la séquence suivante d’étapes :  
  
1.  Si l’application appelle **SQLSetPos** avec *Opération* réglée pour SQL_UPDATE, appelez **SQLBindCol** (ou **SQLSetDescRec**) pour chaque colonne pour spécifier son type de données et lier les tampons pour les données et la longueur de la colonne.  
  
2.  Si l’application appelle **SQLSetPos** avec *Opération* réglée pour SQL_DELETE ou SQL_UPDATE, appelez **SQLColAttribute** pour vous assurer que les colonnes à supprimer ou à mettre à jour sont updatables.  
  
3.  Appelez **SQLExecDirect**, **SQLExecute**, ou une fonction de catalogue pour créer un ensemble de résultats.  
  
4.  Appelez **SQLFetch** ou **SQLFetchScroll** pour récupérer les données.  
  
 Pour plus d’informations sur l’utilisation **de SQLSetPos**, voir [Mise à jour des données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
## <a name="deleting-data-using-sqlsetpos"></a>Suppression des données à l’aide de SQLSetPos  
 Pour supprimer les données avec **SQLSetPos**, une application appelle **SQLSetPos** avec *RowNumber* réglé sur le nombre de la ligne à supprimer et *Opération* réglée à SQL_DELETE.  
  
 Une fois les données supprimées, le pilote modifie la valeur du tableau d’état de la ligne d’implémentation pour que la ligne appropriée SQL_ROW_DELETED (ou SQL_ROW_ERROR).  
  
## <a name="updating-data-using-sqlsetpos"></a>Mise à jour des données à l’aide de SQLSetPos  
 Une application peut passer la valeur d’une colonne soit dans le tampon de données lié ou avec un ou plusieurs appels à **SQLPutData**. Les colonnes dont les données sont transmises avec **SQLPutData** sont connues sous le nom de *colonnes* *de données à l’exécution.* Ceux-ci sont couramment utilisés pour envoyer des données pour SQL_LONGVARBINARY et SQL_LONGVARCHAR colonnes et peuvent être mélangés avec d’autres colonnes.  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>Pour mettre à jour les données avec SQLSetPos, une application :  
  
1.  Place les valeurs dans les tampons de données et de longueur/indicateur liés à **SQLBindCol**:  
  
    -   Pour les colonnes normales, l’application place la nouvelle valeur de colonne * \** dans le * \*tampon TargetValuePtr* et la longueur de cette valeur dans le tampon StrLen_or_IndPtr. Si la ligne ne doit pas être mise à jour, l’application place SQL_ROW_IGNORE dans l’élément de cette rangée du tableau d’opération de la ligne.  
  
    -   Pour les colonnes de données d’exécution, l’application place une valeur définie par l’application, comme le numéro de colonne, dans le * \*tampon TargetValuePtr.* La valeur peut être utilisée plus tard pour identifier la colonne.  
  
         L’application place le résultat de la SQL_LEN_DATA_AT_EXEC macro de*longueur)* dans le tampon*de StrLen_or_IndPtr.* Si le type de données SQL de la colonne est SQL_LONGVARBINARY, SQL_LONGVARCHAR ou un type de données longue spécifique à la source de données et que le conducteur renvoie « Y » pour le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo**, la *longueur* est le nombre d’octets de données à envoyer pour le paramètre; autrement, il doit être une valeur non négative et est ignoré.  
  
2.  Appels **SQLSetPos** avec *l’argument de l’opération* mis à SQL_UPDATE de mettre à jour la ligne de données.  
  
    -   S’il n’y a pas de colonnes de données à l’exécution, le processus est terminé.  
  
    -   S’il y a des colonnes de données à l’exécution, la fonction renvoie SQL_NEED_DATA et procède à l’étape 3.  
  
3.  Appelle **SQLParamData** pour récupérer l’adresse du tampon * \*TargetValuePtr* pour la première colonne de données à exécuter à traiter. **SQLParamData** revient SQL_NEED_DATA. L’application récupère la valeur définie * \** par l’application à partir du tampon TargetValuePtr.  
  
    > [!NOTE]  
    >  Bien que les paramètres de données d’exécution soient similaires aux colonnes de données à l’exécution, la valeur retournée par **SQLParamData** est différente pour chacune.  
  
    > [!NOTE]  
    >  Les paramètres de données à l’exécution sont des paramètres dans une déclaration SQL pour laquelle les données seront envoyées avec **SQLPutData** lorsque la déclaration sera exécutée avec **SQLExecDirect** ou **SQLExecute**. Ils sont liés à **SQLBindParameter** ou en fixant des descripteurs avec **SQLSetDescRec**. La valeur retournée par **SQLParamData** est une valeur 32 bits transmise à **SQLBindParameter** dans l’argument *De ParameterValuePtr.*  
  
    > [!NOTE]  
    >  Les colonnes de données d’exécution sont des colonnes dans un ensemble de rangées pour lesquelles les données seront envoyées avec **SQLPutData** lorsqu’une ligne sera mise à jour avec **SQLSetPos**. Ils sont liés avec **SQLBindCol**. La valeur retournée par **SQLParamData** est l’adresse de la ligne dans le tampon*TargetValuePtr* qui est en cours de traitement.  
  
4.  Appelle **SQLPutData** une ou plusieurs fois pour envoyer des données pour la colonne. Plus d’un appel est nécessaire si toutes les valeurs de données ne peuvent pas être retournées dans le * \*tampon TargetValuePtr* spécifié dans **SQLPutData**; plusieurs appels vers **SQLPutData** pour la même colonne ne sont autorisés que lors de l’envoi de données de caractère C à une colonne avec un type de données spécifique à un personnage, binaire ou spécifique à la source de données ou lors de l’envoi de données C binaires à une colonne avec un type de données de caractère, binaire ou spécifique à la source de données.  
  
5.  Appelle **SQLParamData** à nouveau pour signaler que toutes les données ont été envoyées pour la colonne.  
  
    -   S’il y a plus de colonnes de données à l’exécution, **SQLParamData** renvoie SQL_NEED_DATA et l’adresse du tampon *TargetValuePtr* pour la prochaine colonne de données à exécution à traiter. L’application reprend les étapes 4 et 5.  
  
    -   S’il n’y a plus de colonnes de données à l’exécution, le processus est terminé. Si la déclaration a été exécutée avec succès, **SQLParamData** renvoie SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO; si l’exécution a échoué, elle renvoie SQL_ERROR. À ce stade, **SQLParamData** peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLSetPos**.  
  
 Si les données ont été mises à jour, le conducteur modifie la valeur du tableau d’état de la ligne de mise en œuvre pour que la ligne appropriée SQL_ROW_UPDATED.  
  
 Si l’opération est annulée ou si une erreur se produit dans **SQLParamData** ou **SQLPutData**, après le retour **de SQLSetPos** SQL_NEED_DATA et avant que les données ne soient envoyées pour toutes les colonnes de données à l’exécution, l’application ne peut appeler que **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**, ou **SQLPutData** pour la déclaration ou la connexion associée à la déclaration. S’il appelle toute autre fonction pour l’instruction ou la connexion associée à l’instruction, la fonction renvoie SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction).  
  
 Si l’application appelle **SQLCancel** alors que le conducteur a encore besoin de données pour les colonnes de données à l’exécution, le conducteur annule l’opération. L’application peut alors appeler **SQLSetPos** à nouveau; l’annulation n’affecte pas l’état du curseur ou la position actuelle du curseur.  
  
 Lorsque la liste SELECT des spécifications de requête associée au curseur contient plus d’une référence à la même colonne, qu’une erreur soit générée ou que le conducteur ignore les références dupliquées et effectue les opérations demandées est définie par le conducteur.  
  
## <a name="performing-bulk-operations"></a>Opérations en vrac performantes  
 Si l’argument *de RowNumber* est 0, le conducteur effectue l’opération spécifiée dans *l’argument de l’opération* pour chaque rangée dans le ramage qui a une valeur de SQL_ROW_PROCEED dans son champ dans le tableau d’opération de ligne indiquée par SQL_ATTR_ROW_OPERATION_PTR attribut de déclaration. Il s’agit d’une valeur valable de l’argument *de RowNumber* en faveur *d’un argument d’opération* de SQL_DELETE, de SQL_REFRESH ou de SQL_UPDATE, mais pas SQL_POSITION. **SQLSetPos** avec une *opération* de SQL_POSITION et un *RowNumber* égal à 0 retournera SQLSTATE HY109 (position de curseur invalide).  
  
 Si une erreur se produit qui se rapporte à l’ensemble de la ligne, comme SQLSTATE HYT00 (Timeout expiré), le conducteur retourne SQL_ERROR et le SQLSTATE approprié. Le contenu des tampons encastrés est indéfini, et la position du curseur est inchangée.  
  
 Si une erreur se produit qui se rapporte à une seule ligne, le conducteur :  
  
-   Définit l’élément de la ligne dans le tableau d’état de la ligne indiqué par l’attribut SQL_ATTR_ROW_STATUS_PTR déclaration à SQL_ROW_ERROR.  
  
-   Affiche une ou plusieurs SQLSTATes supplémentaires pour l’erreur dans la file d’attente d’erreur et définit le champ SQL_DIAG_ROW_NUMBER dans la structure de données diagnostiques.  
  
 Après avoir traité l’erreur ou l’avertissement, si le conducteur effectue l’opération pour les rangées restantes dans la rangée, il retourne SQL_SUCCESS_WITH_INFO. Ainsi, pour chaque rangée qui a retourné une erreur, la file d’attente d’erreur contient zéro ou plus de SQLSTATEs supplémentaires. Si le conducteur arrête l’opération après avoir traité l’erreur ou l’avertissement, il retourne SQL_ERROR.  
  
 Si le conducteur renvoie des avertissements, comme SQLSTATE 01004 (Données tronquées), il renvoie des avertissements qui s’appliquent à l’ensemble de la rangée ou à des rangées inconnues dans le rame avant qu’il ne renvoie les informations d’erreur qui s’appliquent à des lignes spécifiques. Il renvoie des avertissements pour des lignes spécifiques ainsi que toute autre information d’erreur sur ces lignes.  
  
 Si *RowNumber* est égal à 0 et *que l’opération* est SQL_UPDATE, SQL_REFRESH ou SQL_DELETE, le nombre de lignes sur lesquelles **SQLSetPos** fonctionne est indiqué par l’attribut de déclaration SQL_ATTR_ROWS_FETCHED_PTR.  
  
 Si *RowNumber* est égal à 0 et *que l’opération* est SQL_DELETE, SQL_REFRESH ou SQL_UPDATE, la rangée actuelle après l’opération est la même que la rangée actuelle avant l’opération.  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>Ignorer une ligne dans une opération en vrac  
 Le tableau d’opération de la ligne peut être utilisé pour indiquer qu’une rangée dans le rowset actuel doit être ignorée lors d’une opération en vrac à **l’aide de SQLSetPos**. Pour ordonner au conducteur d’ignorer une ou plusieurs lignes au cours d’une opération en vrac, une application doit effectuer les étapes suivantes :  
  
1.  Appelez **SQLSetStmtAttr** pour définir l’attribut de la déclaration SQL_ATTR_ROW_OPERATION_PTR pour indiquer un éventail de SQLUSMALLINTs. Ce champ peut également être défini en appelant **SQLSetDescField** pour définir le champ d’en-tête SQL_DESC_ARRAY_STATUS_PTR de l’ARD, ce qui exige qu’une application obtienne la poignée descripteur.  
  
2.  Définissez chaque élément du tableau d’opération de la ligne à l’une des deux valeurs :  
  
    -   SQL_ROW_IGNORE, pour indiquer que la rangée est exclue pour l’opération en vrac.  
  
    -   SQL_ROW_PROCEED, pour indiquer que la rangée est incluse dans l’opération en vrac. (Il s'agit de la valeur par défaut.)  
  
3.  Appelez **SQLSetPos** pour effectuer l’opération en vrac.  
  
 Les règles suivantes s’appliquent au tableau d’exploitation de la rangée :  
  
-   SQL_ROW_IGNORE et SQL_ROW_PROCEED n’affectent que les opérations en vrac à l’aide de **SQLSetPos** avec une *opération* de SQL_DELETE ou de SQL_UPDATE. Ils n’affectent pas les appels à **SQLSetPos** avec une *opération* de SQL_REFRESH ou de SQL_POSITION.  
  
-   Le pointeur est configuré à null par défaut.  
  
-   Si le pointeur est nul, toutes les lignes sont mises à jour comme si tous les éléments étaient réglés pour SQL_ROW_PROCEED.  
  
-   La mise en place d’un élément à SQL_ROW_PROCEED ne garantit pas que l’opération se fera sur cette rangée particulière. Par exemple, si une certaine rangée dans le rowset a l’état SQL_ROW_ERROR, le conducteur pourrait ne pas être en mesure de mettre à jour cette ligne, peu importe si l’application spécifiée SQL_ROW_PROCEED. Une application doit toujours vérifier le tableau d’état de la ligne pour voir si l’opération a été réussie.  
  
-   SQL_ROW_PROCEED est défini comme 0 dans le fichier d’en-tête. Une application peut parasoriser le tableau d’opération de la ligne à 0 afin de traiter toutes les lignes.  
  
-   Si le numéro d’élément "n" dans le tableau d’opération de ligne est réglé pour SQL_ROW_IGNORE et **SQLSetPos** est appelé pour effectuer une mise à jour en vrac ou supprimer l’opération, la rangée nth dans le rangée reste inchangée après l’appel à **SQLSetPos**.  
  
-   Une application doit automatiquement définir une colonne de lecture uniquement pour SQL_ROW_IGNORE.  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>Ignorer une colonne dans une opération en vrac  
 Pour éviter les diagnostics de traitement inutiles générés par les mises à jour tentées à une ou plusieurs colonnes de lecture seulement, une application peut définir la valeur dans la longueur liée / tampon indicateur à SQL_COLUMN_IGNORE. Pour plus d’informations, voir [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application permet à un utilisateur de parcourir la table ORDERS et de mettre à jour l’état de l’ordre. Le curseur est piloté par des ensembles de clés avec une taille de 20 encastrement et utilise un contrôle de concurrence optimiste comparant les versions de la ligne. Une fois chaque jeu de ligne récupéré, l’application l’imprime et permet à l’utilisateur de sélectionner et de mettre à jour l’état d’une commande. L’application utilise **SQLSetPos** pour positionner le curseur sur la rangée sélectionnée et effectue une mise à jour positionnée de la ligne. (La manipulation des erreurs est omise pour plus de clarté.)  
  
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
  
 Pour plus d’exemples, voir [Mises à jour positionnées et supprimer les déclarations](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) et [mettre à jour les lignes dans le Rowset avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Effectuer des opérations en vrac qui ne se rapportent pas à la position du curseur de bloc|[SQLBulkOperations, fonction](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Obtenir un seul champ d’un descripteur|[Fonction SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Obtenir plusieurs champs d’un descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Mise en place d’un champ unique d’un descripteur|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Réglage de plusieurs champs d’un descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
