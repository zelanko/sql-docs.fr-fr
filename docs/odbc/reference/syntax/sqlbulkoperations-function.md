---
title: Fonction SQLBulkOperations (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBulkOperations
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBulkOperations
helpviewer_keywords:
- SQLBulkOperations function [ODBC]
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f4f294a6d84856bc3065b599a370bb5658e3ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301329"
---
# <a name="sqlbulkoperations-function"></a>SQLBulkOperations, fonction
**Conformité**  
 Version introduite : ODBC 3.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLBulkOperations** effectue des insertions en vrac et des opérations de signets en vrac, y compris la mise à jour, la suppression et l’utilisation par signet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Opération*  
 [Entrée] Opération pour effectuer :  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Pour plus d’informations, voir "Commentaires".  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLBulkOperations** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLBulkOperations** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
 Pour toutes les SQLSTATEs qui peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_ERROR (à l’exception des SQLSTATes de 01xxx), SQL_SUCCESS_WITH_INFO est retournée si une erreur se produit sur une ou plusieurs rangées, mais pas toutes, d’une opération à plusieurs pousses, et SQL_ERROR est retournée si une erreur se produit sur une opération à une seule rangée.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Truncation droite de données de chaîne|*L’argument de l’opération* était SQL_FETCH_BY_BOOKMARK, et les données de chaîne ou binaire retournées pour une colonne ou des colonnes avec un type de données de SQL_C_CHAR ou SQL_C_BINARY ont abouti à la troncation de caractères nonblank ou de données binaires non-NULL.|  
|01S01|Erreur dans la rangée|*L’argument de l’opération* a été SQL_ADD, et une erreur s’est produite dans une ou plusieurs rangées pendant l’opération, mais au moins une rangée a été ajoutée avec succès. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)<br /><br /> (Cette erreur n’est soulevée que lorsqu’une application fonctionne avec un ODBC 2. *x* conducteur.)|  
|01S07|Troncation fractionnaire|*L’argument de l’opération* était SQL_FETCH_BY_BOOKMARK, le type de données du tampon d’application n’était pas SQL_C_CHAR ou SQL_C_BINARY, et les données retournées aux tampons d’application pour une ou plusieurs colonnes ont été tronquées. (Pour les types de données C numériques, la partie fractionnaire du nombre a été tronquée. Pour le temps, l’humidité du temps et les types de données d’intervalle C qui contiennent un composant de temps, la partie fractionnelle du temps a été tronquée.)<br /><br /> (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|*L’argument de l’opération* était SQL_FETCH_BY_BOOKMARK, et la valeur des données d’une colonne dans l’ensemble de résultats ne pouvait pas être convertie au type de données spécifié par l’argument *de TargetType* dans l’appel à **SQLBindCol**.<br /><br /> *L’argument de l’opération* était SQL_UPDATE_BY_BOOKMARK ou SQL_ADD, et la valeur des données dans les tampons d’application ne pouvait pas être convertie au type de données d’une colonne dans l’ensemble de résultats.|  
|07009|Indice descripteur invalide|*L’argument Opération* a été SQL_ADD, et une colonne a été liée avec un nombre de colonnes supérieure au nombre de colonnes dans l’ensemble de résultat.|  
|21S02|Le degré de tableau dérivé ne correspond pas à la liste des colonnes|*L’argument Opération* a été SQL_UPDATE_BY_BOOKMARK; et aucune colonne n’était updatable parce que toutes les colonnes étaient non liées ou lus seulement, ou la valeur dans la longueur liée / tampon indicateur a été SQL_COLUMN_IGNORE.|  
|22001|Truncation droite de données de chaîne|L’attribution d’un personnage ou d’une valeur binaire à une colonne dans l’ensemble de résultat a entraîné la troncation de caractères ou non nuls (pour les caractères ou octets binaires).|  
|22003|Valeur numérique hors de portée|*L’argument de l’opération* était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et l’attribution d’une valeur numérique à une colonne dans l’ensemble de résultat a fait tronquer l’ensemble (par opposition à la fractionnement) de la partie du nombre.<br /><br /> *L’argument Opération* a été SQL_FETCH_BY_BOOKMARK, et le retour de la valeur numérique pour une ou plusieurs colonnes liées aurait causé une perte de chiffres importants.|  
|22007|Format de date invalide|*L’argument de l’opération* était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et l’affectation d’une date ou d’une valeur de temps à une colonne dans l’ensemble de résultats a fait que l’année, le mois ou le champ de jour étaient hors de portée.<br /><br /> *L’argument Opération* a été SQL_FETCH_BY_BOOKMARK, et le retour de la date ou de la valeur de timestamp pour une ou plusieurs colonnes liées aurait causé l’année, le mois ou le champ de jour pour être hors de portée.|  
|22008|Débordement de champ date/heure|L’argument de *l’opération* était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et l’exécution de l’arithmétique sur les données envoyées à une colonne dans le résultat fixé a abouti à un champ de date (l’année, le mois, le jour, l’heure, la minute ou le deuxième champ) du résultat tombant en dehors de la gamme permise de valeurs pour le champ ou étant invalide sur la base des règles naturelles du calendrier grégorien pour les dates.<br /><br /> L’argument de *l’opération* était SQL_FETCH_BY_BOOKMARK, et l’exécution de l’arithmétique sur les données récupérées à partir du résultat fixé a donné lieu à un champ d’échéance (l’année, le mois, le jour, l’heure, la minute ou le deuxième champ) du résultat qui ne parvenait pas à la plage de valeurs permise pour le terrain ou n’étant pas valide en fonction des règles naturelles du calendrier grégorien pour les dates.|  
|22015|Débordement de champ d’intervalle|*L’argument de l’opération* était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et l’affectation d’un type C numérique ou d’intervalle exact à un type de données SQL d’intervalle a causé une perte de chiffres importants.<br /><br /> *L’argument de l’Opération* était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK; lors de l’attribution à un type SQL d’intervalle, il n’y avait aucune représentation de la valeur du type C dans le type SQL d’intervalle.<br /><br /> *L’argument de l’opération* était SQL_FETCH_BY_BOOKMARK, et l’attribution d’un type SQL numérique ou d’intervalle exact à un type d’intervalle C a causé une perte de chiffres importants dans le champ principal.<br /><br /> *L’argument de l’Opération* était SQL_FETCH_BY_BOOKMARK; lors de l’attribution à un type d’intervalle C, il n’y avait aucune représentation de la valeur du type SQL dans le type d’intervalle C.|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|*L’argument de l’Opération* était SQL_FETCH_BY_BOOKMARK; le type C était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type SQL de la colonne était un type de données de caractère; et la valeur de la colonne n’était pas un littéral valide du type C lié.<br /><br /> *L’argument Opération* était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK; le type SQL était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type C était SQL_C_CHAR; et la valeur de la colonne n’était pas un littéral valide du type SQL lié.|  
|23000|Violation de la contrainte d’intégrité|*L’argument de l’Opération* était SQL_ADD, SQL_DELETE_BY_BOOKMARK ou SQL_UPDATE_BY_BOOKMARK, et une contrainte d’intégrité a été violée.<br /><br /> *L’argument de l’opération* était SQL_ADD, et une colonne qui n’était pas liée est définie comme NON NULL et n’a pas de défaut.<br /><br /> *L’argument de l’opération* était SQL_ADD, la longueur spécifiée dans le tampon *StrLen_or_IndPtr* lié était SQL_COLUMN_IGNORE, et la colonne n’avait pas de valeur par défaut.|  
|24 000|État de curseur non valide|Le *StatementHandle* était dans un état exécuté, mais aucun ensemble de résultat n’a été associé à la *StatementHandle*.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|42000|Erreur de syntaxe ou violation d’accès|Le conducteur n’a pas été en mesure de verrouiller la rangée au besoin pour effectuer l’opération demandée dans *l’argumentation de l’opération.*|  
|44000|Violation de WITH CHECK OPTION|*L’argument de l’opération* était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et l’encart ou la mise à jour a été effectué sur une table vue (ou une table dérivée de la table vue) qui a été créée en spécifiant **AVEC CHECK OPTION**, de telle sorte qu’une ou plusieurs lignes affectées par l’encart ou la mise à jour ne seront plus présentes dans la table vue.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLBulkOperations** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Le *statementhandle* spécifié n’était pas dans un état exécuté. La fonction a été appelée sans appeler **d’abord SQLExecDirect**, **SQLExecute**, ou une fonction de catalogue.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Le conducteur était un ODBC 2. *x* le conducteur et **SQLBulkOperations** ont été appelés pour une *déclaration à la* suite avant que **SQLFetchScroll** ou **SQLFetch** ne soit appelé.<br /><br /> (DM) **SQLBulkOperations** a été appelé après **SQLExtendedFetch** a été appelé sur le *StatementHandle*.|  
|HY011 HY011|L’attribut ne peut pas être défini maintenant|(DM) Le conducteur était un ODBC 2. *x* conducteur, et l’attribut de déclaration SQL_ATTR_ROW_STATUS_PTR a été défini entre les appels à **SQLFetch** ou **SQLFetchScroll** et **SQLBulkOperations**.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|*L’argument de l’Opération* était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK; une valeur de données n’était pas un pointeur nul; le type de données C était SQL_C_BINARY ou SQL_C_CHAR; et la valeur de longueur de la colonne était inférieure à 0, mais n’était pas égale à SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS, ou SQL_NULL_DATA, ou moins ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> La valeur d’un tampon de longueur/indicateur était SQL_DATA_AT_EXEC; le type SQL était soit SQL_LONGVARCHAR, SQL_LONGVARBINARY, soit un type de données spécifique à une source de données longue; et le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était « Y ».<br /><br /> *L’argument de l’opération* était SQL_ADD, l’attribut de la déclaration SQL_ATTR_USE_BOOKMARK a été réglé pour SQL_UB_VARIABLE, et la colonne 0 était liée à un tampon dont la longueur n’était pas égale à la longueur maximale pour le signet de cet ensemble de résultats. (Cette longueur est disponible dans le domaine SQL_DESC_OCTET_LENGTH de l’IRD et peut être obtenue en appelant **SQLDescribeCol**, **SQLColAttribute**, ou **SQLGetDescField**.)|  
|HY092 HY092|Identifiant d’attribut invalide|(DM) La valeur spécifiée pour *l’argument de l’opération* était invalide.<br /><br /> *L’argument de l’Opération* était SQL_ADD, SQL_UPDATE_BY_BOOKMARK ou SQL_DELETE_BY_BOOKMARK, et l’attribut de déclaration SQL_ATTR_CONCURRENCY était réglé pour SQL_CONCUR_READ_ONLY.<br /><br /> *L’argument de l’Opération* était SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK ou SQL_UPDATE_BY_BOOKMARK, et la colonne de signets n’était pas liée ou l’attribut de déclaration SQL_ATTR_USE_BOOKMARKS était réglé pour SQL_UB_OFF.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données ne prend pas en charge l’opération demandée dans *l’argumentation de l’opération.*|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la source de données ne rende l’ensemble de résultats. La période de délai d’attente est fixée par **SQLSetStmtAttr** avec un argument *d’attribut* de SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
  
> [!CAUTION]  
>  Pour obtenir de l’information sur la déclaration selon **SQLBulkOperations** peut être appelé et ce qu’il doit faire pour la compatibilité avec ODBC 2. *x* applications, voir les [curseurs de bloc, les curseurs défilementables et la section compatibilité vers l’arrière](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) dans l’annexe G: Lignes directrices du conducteur pour la compatibilité vers l’arrière.  
  
 Une application utilise **SQLBulkOperations** pour effectuer les opérations suivantes sur la table de base ou la vue qui correspond à la requête actuelle :  
  
-   Ajouter de nouvelles lignes.  
  
-   Mettez à jour un ensemble de lignes où chaque rangée est identifiée par un signet.  
  
-   Supprimer un ensemble de lignes où chaque ligne est identifiée par un signet.  
  
-   Chercher un ensemble de rangées où chaque rangée est identifiée par un signet.  
  
 Après un appel à **SQLBulkOperations**, la position de curseur de bloc est indéfinie. L’application doit appeler **SQLFetchScroll** pour définir la position du curseur. Une demande ne doit appeler **SQLFetchScroll** qu’avec un argument *d’orientation de* SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE ou SQL_FETCH_BOOKMARK. La position du curseur n’est pas définie si la demande appelle **SQLFetch** ou **SQLFetchScroll** avec un argument *d’orientation de* SQL_FETCH_PRIOR, SQL_FETCH_NEXT ou SQL_FETCH_RELATIVE.  
  
 Une colonne peut être ignorée dans les opérations en vrac effectuées par un appel à **SQLBulkOperations** en définissant la longueur de la colonne / tampon d’indicateur spécifié dans l’appel à **SQLBindCol**, pour SQL_COLUMN_IGNORE.  
  
 Il n’est pas nécessaire que l’application définisse l’attribut de l’SQL_ATTR_ROW_OPERATION_PTR lorsqu’elle appelle **SQLBulkOperations** parce que les lignes ne peuvent pas être ignorées lors de l’exécution des opérations en vrac avec cette fonction.  
  
 Le tampon indiqué par l’attribut de déclaration SQL_ATTR_ROWS_FETCHED_PTR contient le nombre de lignes touchées par un appel à **SQLBulkOperations**.  
  
 Lorsque *l’argument de l’opération* est SQL_ADD ou SQL_UPDATE_BY_BOOKMARK et que la liste de sélection des spécifications de requête associée au curseur contient plus d’une référence à la même colonne, il est défini par le conducteur si une erreur est générée ou si le conducteur ignore les références dupliquées et effectue les opérations demandées.  
  
 Pour plus d’informations sur la façon d’utiliser **SQLBulkOperations**, voir [Mise à jour des données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).  
  
## <a name="performing-bulk-inserts"></a>Exécution des inserts en vrac  
 Pour insérer des données avec **SQLBulkOperations**, une application effectue la séquence suivante d’étapes :  
  
1.  Exécute une requête qui renvoie un ensemble de résultats.  
  
2.  Définit l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration au nombre de lignes qu’il veut insérer.  
  
3.  Appelle **SQLBindCol** pour lier les données qu’il veut insérer. Les données sont liées à un tableau avec une taille égale à la valeur de SQL_ATTR_ROW_ARRAY_SIZE.  
  
    > [!NOTE]  
    >  La taille du tableau indiqué par l’attribut de l’SQL_ATTR_ROW_STATUS_PTR énoncé devrait être soit égale à SQL_ATTR_ROW_ARRAY_SIZE ou SQL_ATTR_ROW_STATUS_PTR devrait être un pointeur nul.  
  
4.  Appelle **SQLBulkOperations***(StatementHandle,* SQL_ADD) pour effectuer l’insertion.  
  
5.  Si l’application a défini l’attribut SQL_ATTR_ROW_STATUS_PTR relevé, elle peut inspecter ce tableau pour voir le résultat de l’opération.  
  
 Si une application lie la colonne 0 avant d’appeler **SQLBulkOperations** avec un argument *d’opération* de SQL_ADD, le conducteur mettra à jour la colonne 0 tampons liés avec les valeurs de signets pour la ligne nouvellement insérée. Pour que cela se produise, l’application doit avoir défini l’attribut SQL_ATTR_USE_BOOKMARKS déclaration à SQL_UB_VARIABLE avant d’exécuter la déclaration. (Cela ne fonctionne pas avec un ODBC 2. *x* conducteur.)  
  
 Les données longues peuvent être ajoutées en pièces par SQLBulkOperations, en utilisant des appels vers SQLParamData et SQLPutData. Pour plus d’informations, voir « Fournir des données longues pour les inserts et mises à jour en vrac » plus tard dans cette référence de fonction.  
  
 Il n’est pas nécessaire que l’application appelle **SQLFetch** ou **SQLFetchScroll** avant d’appeler **SQLBulkOperations** (sauf lorsqu’elle va à l’encontre d’un ODBC 2.* x* conducteur; voir [Backward Compatibility and Standards Compliance](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Le comportement est défini par le conducteur si **SQLBulkOperations**, avec un argument *d’opération* de SQL_ADD, est appelé sur un curseur qui contient des colonnes en double. Le conducteur peut retourner un SQLSTATE défini par le conducteur, ajouter les données à la première colonne qui apparaît dans l’ensemble de résultats, ou effectuer d’autres comportements définis par le conducteur.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Effectuer des mises à jour en vrac en utilisant des signets  
 Pour effectuer des mises à jour en vrac en utilisant des signets avec **SQLBulkOperations**, une application effectue les étapes suivantes dans l’ordre:  
  
1.  Définit l’attribut SQL_ATTR_USE_BOOKMARKS déclaration à SQL_UB_VARIABLE.  
  
2.  Exécute une requête qui renvoie un ensemble de résultats.  
  
3.  Définit l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration au nombre de lignes qu’il veut mettre à jour.  
  
4.  Appelle **SQLBindCol** pour lier les données qu’il veut mettre à jour. Les données sont liées à un tableau avec une taille égale à la valeur de SQL_ATTR_ROW_ARRAY_SIZE. Il appelle également **SQLBindCol** pour lier la colonne 0 (la colonne de signet).  
  
5.  Copie les signets pour les lignes qu’il est intéressé à mettre à jour dans le tableau lié à la colonne 0.  
  
6.  Mise à jour des données dans les tampons consolidés.  
  
    > [!NOTE]  
    >  La taille du tableau indiqué par l’attribut de l’SQL_ATTR_ROW_STATUS_PTR énoncé devrait être égale à SQL_ATTR_ROW_ARRAY_SIZE ou SQL_ATTR_ROW_STATUS_PTR devrait être un pointeur nul.  
  
7.  Appels **SQLBulkOperations***(StatementHandle,* SQL_UPDATE_BY_BOOKMARK).  
  
    > [!NOTE]  
    >  Si l’application a défini l’attribut SQL_ATTR_ROW_STATUS_PTR relevé, elle peut inspecter ce tableau pour voir le résultat de l’opération.  
  
8.  En option, les appels **SQLBulkOperations***(StatementHandle*, SQL_FETCH_BY_BOOKMARK) pour récupérer des données dans les tampons d’application liés pour vérifier que la mise à jour s’est produite.  
  
9. Si les données ont été mises à jour, le conducteur modifie la valeur du tableau d’état de la ligne pour que les lignes appropriées SQL_ROW_UPDATED.  
  
 Les mises à jour en vrac effectuées par **SQLBulkOperations** peuvent inclure de longues données en utilisant des appels vers **SQLParamData** et **SQLPutData**. Pour plus d’informations, voir « Fournir des données longues pour les inserts et mises à jour en vrac » plus tard dans cette référence de fonction.  
  
 Si les signets persistent sur les curseurs, l’application n’a pas besoin d’appeler **SQLFetch** ou **SQLFetchScroll** avant de les mettre à jour par signets. Il peut utiliser des signets qu’il a stockés à partir d’un curseur précédent. Si les signets ne persistent pas entre les curseurs, l’application doit appeler **SQLFetch** ou **SQLFetchScroll** pour récupérer les signets.  
  
 Le comportement est défini par le conducteur si **SQLBulkOperations**, avec un argument *d’opération* de SQL_UPDATE_BY_BOOKMARK, est appelé sur un curseur qui contient des colonnes en double. Le conducteur peut retourner un SQLSTATE défini par le conducteur, mettre à jour la première colonne qui apparaît dans l’ensemble de résultats, ou effectuer d’autres comportements définis par le conducteur.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Exécution de fetches en vrac à l’aide de signets  
 Pour effectuer des allers de l’avant en vrac à l’aide de signets avec **SQLBulkOperations**, une application effectue les étapes suivantes dans l’ordre:  
  
1.  Définit l’attribut SQL_ATTR_USE_BOOKMARKS déclaration à SQL_UB_VARIABLE.  
  
2.  Exécute une requête qui renvoie un ensemble de résultats.  
  
3.  Définit l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration au nombre de lignes qu’il veut aller chercher.  
  
4.  Appelle **SQLBindCol** pour lier les données qu’il veut aller chercher. Les données sont liées à un tableau avec une taille égale à la valeur de SQL_ATTR_ROW_ARRAY_SIZE. Il appelle également **SQLBindCol** pour lier la colonne 0 (la colonne de signet).  
  
5.  Copie les signets pour les lignes qu’il est intéressé à aller chercher dans le tableau lié à la colonne 0. (Cela suppose que la demande a déjà obtenu les signets séparément.)  
  
    > [!NOTE]  
    >  La taille du tableau indiqué par l’attribut de l’SQL_ATTR_ROW_STATUS_PTR énoncé devrait être égale à SQL_ATTR_ROW_ARRAY_SIZE ou SQL_ATTR_ROW_STATUS_PTR devrait être un pointeur nul.  
  
6.  Appels **SQLBulkOperations***(StatementHandle,* SQL_FETCH_BY_BOOKMARK).  
  
7.  Si l’application a défini l’attribut SQL_ATTR_ROW_STATUS_PTR relevé, elle peut inspecter ce tableau pour voir le résultat de l’opération.  
  
 Si les signets persistent à travers les curseurs, l’application n’a pas besoin d’appeler **SQLFetch** ou **SQLFetchScroll** avant d’aller chercher par des signets. Il peut utiliser des signets qu’il a stockés à partir d’un curseur précédent. Si les signets ne persistent pas entre les curseurs, l’application doit appeler **SQLFetch** ou **SQLFetchScroll** une fois pour récupérer les signets.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>Exécution de suppressions en vrac à l’aide de signets  
 Pour effectuer des suppressions en vrac à l’aide de signets avec **SQLBulkOperations**, une application effectue les étapes suivantes dans l’ordre:  
  
1.  Définit l’attribut SQL_ATTR_USE_BOOKMARKS déclaration à SQL_UB_VARIABLE.  
  
2.  Exécute une requête qui renvoie un ensemble de résultats.  
  
3.  Définit l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration au nombre de lignes qu’il veut supprimer.  
  
4.  Appelle **SQLBindCol** pour lier la colonne 0 (la colonne de signets).  
  
5.  Copie les signets pour les lignes qu’il est intéressé à supprimer dans le tableau lié à la colonne 0.  
  
    > [!NOTE]  
    >  La taille du tableau indiqué par l’attribut de l’SQL_ATTR_ROW_STATUS_PTR énoncé devrait être égale à SQL_ATTR_ROW_ARRAY_SIZE ou SQL_ATTR_ROW_STATUS_PTR devrait être un pointeur nul.  
  
6.  Appels **SQLBulkOperations***(StatementHandle,* SQL_DELETE_BY_BOOKMARK).  
  
7.  Si l’application a défini l’attribut SQL_ATTR_ROW_STATUS_PTR relevé, elle peut inspecter ce tableau pour voir le résultat de l’opération.  
  
 Si les signets persistent à travers les curseurs, l’application n’a pas à appeler **SQLFetch** ou **SQLFetchScroll** avant de supprimer par des signets. Il peut utiliser des signets qu’il a stockés à partir d’un curseur précédent. Si les signets ne persistent pas entre les curseurs, l’application doit appeler **SQLFetch** ou **SQLFetchScroll** une fois pour récupérer les signets.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>Fournir des données longues pour les inserts et mises à jour en vrac  
 De longues données peuvent être fournies pour les encarts en vrac et les mises à jour effectuées par les appels à **SQLBulkOperations**. Pour insérer ou mettre à jour de longues données, une application effectue les étapes suivantes en plus des étapes décrites dans les sections « Performing Bulk Inserts » et « Performing Bulk Updates Using Bookmarks » plus tôt dans ce sujet.  
  
1.  Lorsqu’il lie les données en utilisant **SQLBindCol**, l’application place une valeur définie par l’application, comme le numéro de colonne, dans le tampon * \*TargetValuePtr* pour les colonnes de données à l’exécution. La valeur peut être utilisée plus tard pour identifier la colonne.  
  
     L’application place le résultat de la SQL_LEN_DATA_AT_EXEC(*longueur)* macro dans le * \*tampon StrLen_or_IndPtr.* Si le type de données SQL de la colonne est SQL_LONGVARBINARY, SQL_LONGVARCHAR ou un type de données longue spécifique à la source de données et que le conducteur renvoie « Y » pour le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo**, la *longueur* est le nombre d’octets de données à envoyer pour le paramètre; autrement, il doit être une valeur non native et est ignoré.  
  
2.  Lorsque **SQLBulkOperations** est appelé, s’il y a des colonnes de données à l’exécution, la fonction renvoie SQL_NEED_DATA et procède à l’étape 3, qui suit. (S’il n’y a pas de colonnes de données à l’exécution, le processus est terminé.)  
  
3.  La demande appelle **SQLParamData** pour récupérer l’adresse du tampon * \*TargetValuePtr* pour la première colonne de données à exécuter à traiter. **SQLParamData** revient SQL_NEED_DATA. L’application récupère la valeur définie * \** par l’application à partir du tampon TargetValuePtr.  
  
    > [!NOTE]  
    >  Bien que les paramètres de données à l’exécution ressemblent à des colonnes de données à l’exécution, la valeur retournée par **SQLParamData** est différente pour chacun.  
  
     Les colonnes de données d’exécution sont des colonnes dans un ensemble de rangées pour lesquelles les données seront envoyées avec **SQLPutData** lorsqu’une ligne est mise à jour ou insérée avec **SQLBulkOperations**. Ils sont liés avec **SQLBindCol**. La valeur retournée par **SQLParamData** est l’adresse de la ligne dans le tampon*TargetValuePtr* qui est en cours de traitement.  
  
4.  L’application appelle **SQLPutData** une ou plusieurs fois pour envoyer des données pour la colonne. Plus d’un appel est nécessaire si toute la valeur de données ne peut pas être retournée dans le * \*tampon TargetValuePtr* spécifié dans **SQLPutData**; plusieurs appels vers **SQLPutData** pour la même colonne ne sont autorisés que lors de l’envoi de données de caractère C à une colonne avec un type de données spécifique à un personnage, binaire ou spécifique à la source de données ou lors de l’envoi de données C binaires à une colonne avec un type de données de caractère, binaire ou spécifique à la source de données.  
  
5.  L’application appelle **SQLParamData** à nouveau pour signaler que toutes les données ont été envoyées pour la colonne.  
  
    -   S’il y a plus de colonnes de données à l’exécution, **SQLParamData** renvoie SQL_NEED_DATA et l’adresse du tampon *TargetValuePtr* pour la prochaine colonne de données à exécution à traiter. L’application reprend les étapes 4 et 5.  
  
    -   S’il n’y a plus de colonnes de données à l’exécution, le processus est terminé. Si la déclaration a été exécutée avec succès, **SQLParamData** renvoie SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO; si l’exécution a échoué, elle renvoie SQL_ERROR. À ce stade, **SQLParamData** peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLBulkOperations**.  
  
 Si l’opération est annulée ou si une erreur se produit dans **SQLParamData** ou **SQLPutData** après le retour **de SQLBulkOperations** SQL_NEED_DATA et avant que les données ne soient envoyées pour toutes les colonnes de données à l’exécution, l’application ne peut appeler que **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**, ou **SQLPutData** pour la déclaration ou la connexion associée à la déclaration. S’il appelle toute autre fonction pour l’instruction ou la connexion associée à l’instruction, la fonction renvoie SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction).  
  
 Si l’application appelle **SQLCancel** alors que le conducteur a encore besoin de données pour les colonnes de données à l’exécution, le conducteur annule l’opération. L’application peut alors appeler **SQLBulkOperations** à nouveau; l’annulation n’affecte pas l’état du curseur ou la position actuelle du curseur.  
  
## <a name="row-status-array"></a>Tableau d’état des lignes  
 Le tableau d’état de la ligne contient des valeurs d’état pour chaque rangée de données dans le rangée après un appel à **SQLBulkOperations**. Le conducteur définit les valeurs de statut dans ce tableau après un appel à **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, ou **SQLBulkOperations**. Ce tableau est d’abord peuplé d’un appel à **SQLBulkOperations** si **SQLFetch** ou **SQLFetchScroll** n’a pas été appelé avant **SQLBulkOperations**. Ce tableau est souligné par l’attribut de l’SQL_ATTR_ROW_STATUS_PTR déclaration. Le nombre d’éléments dans les tableaux d’état de la rangée doit égaler le nombre de lignes dans le rangée (tel que défini par l’attribut de l’SQL_ATTR_ROW_ARRAY_SIZE déclaration). Pour plus d’informations sur ce tableau d’état de la ligne, voir [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Exemple de code  
 L’exemple suivant récupère 10 rangées de données à la fois à partir de la table des clients. Il invite ensuite l’utilisateur à prendre une action. Pour réduire le trafic réseau, l’exemple tampon met à jour, supprime et insère localement dans les tableaux liés, mais à des décalages au-delà des données encastrées. Lorsque l’utilisateur choisit d’envoyer des mises à jour, supprime et insère à la source de données, le code définit la compensation de liaison de manière appropriée et appelle **SQLBulkOperations**. Par souci de simplicité, l’utilisateur ne peut pas tamponner plus de 10 mises à jour, suppressions ou inserts.  
  
```cpp  
// SQLBulkOperations_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include "stdio.h"  
  
#define UPDATE_ROW 100  
#define DELETE_ROW 101  
#define ADD_ROW 102  
#define SEND_TO_DATA_SOURCE 103  
#define UPDATE_OFFSET 10  
#define INSERT_OFFSET 20  
#define DELETE_OFFSET 30  
  
// Define structure for customer data (assume 10 byte maximum bookmark size).  
typedef struct tagCustStruct {  
   SQLCHAR Bookmark[10];  
   SQLINTEGER BookmarkLen;  
   SQLUINTEGER CustomerID;  
   SQLINTEGER CustIDInd;  
   SQLCHAR CompanyName[51];  
   SQLINTEGER NameLenOrInd;  
   SQLCHAR Address[51];  
   SQLINTEGER AddressLenOrInd;  
   SQLCHAR Phone[11];  
   SQLINTEGER PhoneLenOrInd;  
} CustStruct;  
  
// Allocate 40 of these structures. Elements 0-9 are for the current rowset,  
// elements 10-19 are for the buffered updates, elements 20-29 are for  
// the buffered inserts, and elements 30-39 are for the buffered deletes.  
CustStruct CustArray[40];  
SQLUSMALLINT RowStatusArray[10], Action, RowNum, NumUpdates = 0, NumInserts = 0,  
NumDeletes = 0;  
SQLLEN BindOffset = 0;  
SQLRETURN retcode;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLHSTMT hstmt = NULL;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Set the following statement attributes:  
   // SQL_ATTR_CURSOR_TYPE:           Keyset-driven  
   // SQL_ATTR_ROW_BIND_TYPE:         Row-wise  
   // SQL_ATTR_ROW_ARRAY_SIZE:        10  
   // SQL_ATTR_USE_BOOKMARKS:         Use variable-length bookmarks  
   // SQL_ATTR_ROW_STATUS_PTR:        Points to RowStatusArray  
   // SQL_ATTR_ROW_BIND_OFFSET_PTR:   Points to BindOffset  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_KEYSET_DRIVEN, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER)sizeof(CustStruct), 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_USE_BOOKMARKS, (SQLPOINTER)SQL_UB_VARIABLE, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_OFFSET_PTR, &BindOffset, 0);  
  
   // Bind arrays to the bookmark, CustomerID, CompanyName, Address, and Phone columns.  
   retcode = SQLBindCol(hstmt, 0, SQL_C_VARBOOKMARK, CustArray[0].Bookmark, sizeof(CustArray[0].Bookmark), &CustArray[0].BookmarkLen);  
   retcode = SQLBindCol(hstmt, 1, SQL_C_ULONG, &CustArray[0].CustomerID, 0, &CustArray[0].CustIDInd);  
   retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, CustArray[0].CompanyName, sizeof(CustArray[0].CompanyName), &CustArray[0].NameLenOrInd);  
   retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, CustArray[0].Address, sizeof(CustArray[0].Address), &CustArray[0].AddressLenOrInd);  
   retcode = SQLBindCol(hstmt, 4, SQL_C_CHAR, CustArray[0].Phone, sizeof(CustArray[0].Phone), &CustArray[0].PhoneLenOrInd);  
  
   // Execute a statement to retrieve rows from the Customers table.  
   retcode = SQLExecDirect(hstmt, (SQLCHAR*)"SELECT CustomerID, CompanyName, Address, Phone FROM Customers", SQL_NTS);  
  
   // Fetch and display the first 10 rows.  
   retcode = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
   // DisplayCustData(CustArray, 10);  
  
   // Call GetAction to get an action and a row number from the user.  
   // while (GetAction(&Action, &RowNum)) {  
   Action = SQL_FETCH_NEXT;  
   RowNum = 2;  
   switch (Action) {  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmt, Action, RowNum);  
         // DisplayCustData(CustArray, 10);  
         break;  
  
      case UPDATE_ROW:  
         // Check if we have reached the maximum number of buffered updates.  
         if (NumUpdates < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered updates section of CustArray, copy the bookmark of the row  
            // being updated to the same element, and increment the update counter.  
            // Checking to see we have not already buffered an update for this  
            // row not shown.  
            // GetNewCustData(CustArray, UPDATE_OFFSET + NumUpdates);  
            memcpy(CustArray[UPDATE_OFFSET + NumUpdates].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
            CustArray[UPDATE_OFFSET + NumUpdates].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
            NumUpdates++;  
         } else {  
            printf("Buffers full. Send buffered changes to the data source.");  
         }  
         break;  
      case DELETE_ROW:  
         // Check if we have reached the maximum number of buffered deletes.  
         if (NumDeletes < 10) {  
            // Copy the bookmark of the row being deleted to the next available element  
            // of the buffered deletes section of CustArray and increment the delete  
            // counter. Checking to see we have not already buffered an update for  
            // this row not shown.  
            memcpy(CustArray[DELETE_OFFSET + NumDeletes].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
  
            CustArray[DELETE_OFFSET + NumDeletes].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
  
            NumDeletes++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case ADD_ROW:  
         // reached maximum number of buffered inserts?  
         if (NumInserts < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered inserts section of CustArray and increment insert counter.  
            // GetNewCustData(CustArray, INSERT_OFFSET + NumInserts);  
            NumInserts++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case SEND_TO_DATA_SOURCE:  
         // If there are any buffered updates, inserts, or deletes, set the array size  
         // to that number, set the binding offset to use the data in the buffered  
         // update, insert, or delete part of CustArray, and call SQLBulkOperations to  
         // do the updates, inserts, or deletes. Because we will never have more than  
         // 10 updates, inserts, or deletes, we can use the same row status array.  
         if (NumUpdates) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumUpdates, 0);  
            BindOffset = UPDATE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_UPDATE_BY_BOOKMARK);  
            NumUpdates = 0;  
         }  
  
         if (NumInserts) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumInserts, 0);  
            BindOffset = INSERT_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_ADD);  
            NumInserts = 0;  
         }  
  
         if (NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumDeletes, 0);  
            BindOffset = DELETE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_DELETE_BY_BOOKMARK);  
            NumDeletes = 0;  
         }  
  
         // If there were any updates, inserts, or deletes, reset the binding offset  
         // and array size to their original values.  
         if (NumUpdates || NumInserts || NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
            BindOffset = 0;  
         }  
         break;  
   }  
   // }  
  
   // Close the cursor.  
   SQLFreeStmt(hstmt, SQL_CLOSE);  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Obtenir un seul champ d’un descripteur|[Fonction SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Obtenir plusieurs champs d’un descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Mise en place d’un champ unique d’un descripteur|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Réglage de plusieurs champs d’un descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Positionnement du curseur, données rafraîchissantes dans le ramset, ou mise à jour ou suppression des données dans le ramset|[SQLSetPos, fonction](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
