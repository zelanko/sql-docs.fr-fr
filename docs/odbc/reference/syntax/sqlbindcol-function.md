---
title: Fonction SQLBindCol (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBindCol
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBindCol
helpviewer_keywords:
- SQLBindCol function [ODBC]
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90bb1c1aa4dbfa2614f689faa47eb0c41a6cecd6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298739"
---
# <a name="sqlbindcol-function"></a>Fonction SQLBindCol
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLBindCol** lie les tampons de données d’application aux colonnes dans l’ensemble de résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLBindCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *ColumnNumber*  
 [Entrée] Nombre de la colonne de jeu de résultat à lier. Les colonnes sont numérotées dans l’ordre de colonne croissante à partir de 0, où la colonne 0 est la colonne de signet. Si les signets ne sont pas utilisés - c’est-à-dire, l’attribut de l’SQL_ATTR_USE_BOOKMARKS’énoncé est réglé pour SQL_UB_OFF - alors les nombres de colonnes commencent à 1.  
  
 *Targettype*  
 [Entrée] L’identifiant du type de \*données C du tampon *TargetValuePtr.* Lorsqu’il est en train de récupérer des données à partir de la source de données avec **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, ou **SQLSetPos**, le conducteur convertit les données à ce type; lorsqu’il envoie des données à la source de données avec **SQLBulkOperations** ou **SQLSetPos**, le conducteur convertit les données de ce type. Pour une liste de types de données C valides et d’identifiants de type, consultez la section [Types de données C](../../../odbc/reference/appendixes/c-data-types.md) dans l’annexe D : Data Types.  
  
 Si l’argument *de TargetType* est un type de données d’intervalle, l’intervalle par défaut menant la précision (2) et l’intervalle par défaut secondes de précision (6), tel qu’indiqué dans les champs SQL_DESC_DATETIME_INTERVAL_PRECISION et SQL_DESC_PRECISION de l’ARD, respectivement, sont utilisés pour les données. Si l’argument *de TargetType* est SQL_C_NUMERIC, la précision par défaut (définie par le conducteur) et l’échelle par défaut (0), telle qu’elle est définie dans les champs SQL_DESC_PRECISION et SQL_DESC_SCALE de l’ARD, sont utilisées pour les données. Si une précision ou une échelle par défaut n’est pas appropriée, l’application doit définir explicitement le champ descripteur approprié par un appel à **SQLSetDescField** ou **SQLSetDescRec**.  
  
 Vous pouvez également spécifier un type de données C étendu. Pour plus d’informations, voir [C Data Types in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr (en)*  
 [Entrée différée/sortie] Pointeur vers le tampon de données pour se lier à la colonne. **SQLFetch** et **SQLFetchScroll retournent** les données dans ce tampon. **SQLBulkOperations** renvoie des données dans ce tampon lorsque *l’opération* est SQL_FETCH_BY_BOOKMARK; il récupère des données de ce tampon lorsque *l’opération* est SQL_ADD ou SQL_UPDATE_BY_BOOKMARK. **SQLSetPos** retourne des données dans ce tampon lorsque *l’opération* est SQL_REFRESH; il récupère les données de ce tampon lorsque *l’opération* est SQL_UPDATE.  
  
 Si *TargetValuePtr* est un pointeur nul, le pilote débinde le tampon de données pour la colonne. Une application peut délier toutes les colonnes en appelant **SQLFreeStmt** avec l’option SQL_UNBIND. Une application peut délier le tampon de données pour une colonne, mais ont toujours un tampon de longueur / indicateur lié à la colonne, si *l’argument TargetValuePtr* dans l’appel à **SQLBindCol** est un pointeur nul, mais *l’argument StrLen_or_IndPtr* est une valeur valide.  
  
 *BufferLength*  
 [Entrée] Longueur du \*tampon *TargetValuePtr* dans les octets.  
  
 Le pilote utilise *BufferLength* pour éviter \*d’écrire au-delà de la fin du tampon *TargetValuePtr* lorsqu’il renvoie des données à longueur variable, telles que des données de caractère ou binaires. Notez que le conducteur compte le caractère de \*non-résiliation lorsqu’il renvoie les données de caractère à *TargetValuePtr*. \**TargetValuePtr* doit donc contenir de l’espace pour le caractère de non-termination ou le pilote va tronquer les données.  
  
 Lorsque le conducteur retourne des données de longueur fixe, comme un intégrateur ou une structure de date, le conducteur ignore *BufferLength* et suppose que le tampon est assez grand pour contenir les données. Par conséquent, il est important que l’application alloue un tampon suffisamment grand pour les données à durée fixe ou que le pilote écrira au-delà de la fin du tampon.  
  
 **SQLBindCol** retourne SQLSTATE HY090 (longueur de chaîne ou tampon invalide) lorsque *BufferLength* est inférieur à 0, mais pas lorsque *BufferLength* est 0. Toutefois, si *TargetType* spécifie un type de personnage, une application ne doit pas définir *BufferLength* à 0, parce que les pilotes conformes à l’ISO CLI retournent SQLSTATE HY090 (longueur de chaîne ou tampon invalide) dans ce cas.  
  
 *StrLen_or_IndPtr*  
 [Entrée différée/sortie] Pointeur vers le tampon longueur/indicateur pour se lier à la colonne. **SQLFetch** et **SQLFetchScroll** retournent une valeur dans ce tampon. **SQLBulkOperations** récupère une valeur de ce tampon lorsque *l’opération* est SQL_ADD, SQL_UPDATE_BY_BOOKMARK ou SQL_DELETE_BY_BOOKMARK. **SQLBulkOperations** retourne une valeur dans ce tampon lorsque *l’opération* est SQL_FETCH_BY_BOOKMARK. **SQLSetPos** retourne une valeur dans ce tampon lorsque *l’opération* est SQL_REFRESH; il récupère une valeur de ce tampon lorsque *l’opération* est SQL_UPDATE.  
  
 **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, et **SQLSetPos** peuvent retourner les valeurs suivantes dans le tampon longueur/indicateur :  
  
-   La durée des données disponibles pour revenir  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 L’application peut mettre les valeurs suivantes dans le tampon longueur/indicateur pour une utilisation avec **SQLBulkOperations** ou **SQLSetPos**:  
  
-   La durée des données envoyées  
  
-   SQL_NTS  
  
-   SQL_NULL_DATA  
  
-   SQL_DATA_AT_EXEC  
  
-   Le résultat de la macro SQL_LEN_DATA_AT_EXEC  
  
-   SQL_COLUMN_IGNORE  
  
 Si le tampon d’indicateur et le tampon de longueur sont des tampons distincts, le tampon d’indicateur ne peut revenir qu’SQL_NULL_DATA, tandis que le tampon de longueur peut retourner toutes les autres valeurs.  
  
 Pour plus d’informations, voir [SQLBulkOperations Function](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md), [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md), et Using [Length/Indicator Values](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Si *StrLen_or_IndPtr* est un pointeur nul, aucune longueur ou valeur d’indicateur n’est utilisée. Il s’agit d’une erreur lors de l’obtenir des données et les données sont NULL.  
  
 Consultez [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md), si votre application s’exécute sur un système d’exploitation 64 bits.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLBindCol** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLBindCol** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|(DM) *L’argument de La Colonnen comptait* 0, et l’argument *de TargetType* n’était pas SQL_C_BOOKMARK ou SQL_C_VARBOOKMARK.|  
|07009|Indice descripteur invalide|La valeur spécifiée pour l’argument *ColumnNumber* a dépassé le nombre maximum de colonnes dans l’ensemble de résultats.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY003 (HY003)|Type tampon d’application invalide|L’argument *TargetType* n’était ni un type de données valide ni SQL_C_DEFAULT.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque **SQLBindCol** a été appelé.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.<br /><br /> (DM) Le conducteur était un ODBC 2. *x* conducteur, *l’argument de ColumnNumber* a été réglé à 0, et la valeur spécifiée pour l’argument *BufferLength* n’était pas égale à 4.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données ne prend pas en charge la conversion spécifiée par la combinaison de l’argument *TargetType* et du type de données SQL spécifique au conducteur de la colonne correspondante.<br /><br /> *L’argument ColumnNumber* était 0 et le conducteur ne prend pas en charge les signets.<br /><br /> Le conducteur ne prend en charge que L’ODBC 2. *x* et l’argument *TargetType* était l’un des suivants:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> et n’importe lequel des types de données D’intervalle répertoriés dans [les types de données C](../../../odbc/reference/appendixes/c-data-types.md) de l’Annexe D : Types de données.<br /><br /> Le conducteur ne prend en charge les versions ODBC avant 3.50, et l’argument *TargetType* a été SQL_C_GUID.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 **SQLBindCol** est utilisé pour associer ou *lier les* colonnes dans l’ensemble de résultats aux tampons de données et aux tampons de longueur/indicateur dans l’application. Lorsque l’application appelle **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos** pour obtenir des données, le conducteur retourne les données pour les colonnes liées dans les tampons spécifiés; pour plus d’informations, voir [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md). Lorsque l’application appelle **SQLBulkOperations** pour mettre à jour ou insérer une ligne ou **SQLSetPos** pour mettre à jour une ligne, le conducteur récupère les données pour les colonnes liées des tampons spécifiés; pour plus d’informations, voir [SQLBulkOperations Function](../../../odbc/reference/syntax/sqlbulkoperations-function.md) ou [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md). Pour plus d’informations sur la liaison, voir [Résultats de récupération (De base)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 Notez que les colonnes n’ont pas besoin d’être tenus de récupérer des données d’eux. Une application peut également appeler **SQLGetData** pour récupérer des données dans les colonnes. Bien qu’il soit possible de lier certaines colonnes d’affilée et d’appeler **SQLGetData** pour d’autres, cela est soumis à certaines restrictions. Pour plus d’informations, voir [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>Colonnes contraignantes, non contraignantes et rebinding  
 Une colonne peut être liée, non liée ou rebondie à tout moment, même après que les données ont été récupérées à partir de l’ensemble de résultats. La nouvelle liaison prend effet la prochaine fois qu’une fonction qui utilise des fixations est appelée. Supposons, par exemple, qu’une application lie les colonnes dans un ensemble de résultats et appelle **SQLFetch**. Le conducteur retourne les données dans les tampons consolidés. Supposons maintenant que l’application lie les colonnes à un ensemble différent de tampons. Le conducteur ne met pas les données pour la rangée juste-fetched dans les tampons nouvellement liés. Au lieu de cela, il attend jusqu’à ce que **SQLFetch** est appelé à nouveau et place ensuite les données pour la rangée suivante dans les tampons nouvellement liés.  
  
> [!NOTE]  
>  L’attribut d’instruction SQL_ATTR_USE_BOOKMARKS doit toujours être défini avant de lier une colonne à la colonne 0. Ce n’est pas nécessaire, mais est fortement recommandé.  
  
## <a name="binding-columns"></a>Liaison de colonnes  
 Pour lier une colonne, une application appelle **SQLBindCol** et passe le numéro de colonne, le type, l’adresse et la longueur d’un tampon de données, ainsi que l’adresse d’un tampon de longueur/indicateur. Pour plus d’informations sur la façon dont ces adresses sont utilisées, voir « Adresses tampons », plus tard dans cette section. Pour plus d’informations sur les colonnes de liaison, voir [Utiliser SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 L’utilisation de ces tampons est reportée; c’est-à-dire que l’application les lie dans **SQLBindCol,** mais le conducteur y accède à partir d’autres fonctions - à savoir **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**. Il incombe à l’application de s’assurer que les pointeurs spécifiés dans **SQLBindCol** demeurent valides tant que la liaison demeure en vigueur. Si l’application permet à ces pointeurs de devenir invalides - par exemple, elle libère un tampon - et appelle ensuite une fonction qui s’attend à ce qu’ils soient valides, les conséquences ne sont pas définies. Pour plus d’informations, voir [Tampons différés](../../../odbc/reference/develop-app/deferred-buffers.md).  
  
 La liaison reste en vigueur jusqu’à ce qu’elle soit remplacée par une nouvelle liaison, que la colonne ne soit pas liée ou que la déclaration soit libérée.  
  
## <a name="unbinding-columns"></a>Colonnes non contraignantes  
 Pour délier une seule colonne, une application appelle **SQLBindCol** avec *ColumnNumber* réglé sur le nombre de cette colonne et *TargetValuePtr* réglé à un pointeur nul. Si *ColumnNumber* fait référence à une colonne non liée, **SQLBindCol** retourne toujours SQL_SUCCESS.  
  
 Pour délier toutes les colonnes, une application appelle **SQLFreeStmt** avec *fOption* réglé pour SQL_UNBIND. Cela peut également être accompli en plaçant le champ SQL_DESC_COUNT de l’ARD à zéro.  
  
## <a name="rebinding-columns"></a>Colonnes rebinding  
 Une application peut effectuer l’une ou l’autre des deux opérations pour modifier une liaison :  
  
-   Appelez **SQLBindCol** pour spécifier une nouvelle liaison pour une colonne qui est déjà liée. Le conducteur surmene l’ancienne fixation avec la nouvelle.  
  
-   Spécifier une compensation à ajouter à l’adresse tampon qui a été spécifiée par l’appel de liaison à **SQLBindCol**. Pour plus d’informations, voir la section suivante, "Binding Offsets."  
  
## <a name="binding-offsets"></a>Compensations contraignantes  
 Une compensation contraignante est une valeur ajoutée aux adresses des données et des tampons de longueur/indicateur (comme indiqué dans *l’argument TargetValuePtr* et *StrLen_or_IndPtr)* avant qu’elles ne soient déreférées. Lorsque des compensations sont utilisées, les fixations sont un « modèle » de la façon dont les tampons de l’application sont disposés, et l’application peut déplacer ce « modèle » vers différents domaines de mémoire en changeant le décalage. Étant donné que le même décalage est ajouté à chaque adresse dans chaque liaison, les décalages relatifs entre les tampons pour différentes colonnes doivent être les mêmes dans chaque ensemble de tampons. Cela est toujours vrai lorsque la fixation de la ligne est utilisée; l’application doit soigneusement exposer ses tampons pour que cela soit vrai lorsque la liaison de colonne-sage est utilisée.  
  
 L’utilisation d’un décalage de liaison a essentiellement le même effet que la rébination d’une colonne en appelant **SQLBindCol**. La différence est qu’un nouvel appel à **SQLBindCol** spécifie de nouvelles adresses pour le tampon de données et la longueur / indicateur tampon, tandis que l’utilisation d’un décalage de liaison ne change pas les adresses, mais ajoute juste une compensation pour eux. L’application peut spécifier un nouveau décalage quand il le souhaite, et ce décalage est toujours ajouté aux adresses initialement liées. En particulier, si le décalage est réglé à 0 ou si l’attribut de déclaration est réglé à un pointeur nul, le pilote utilise les adresses initialement liées.  
  
 Pour spécifier une compensation contraignante, la demande définit l’attribut SQL_ATTR_ROW_BIND_OFFSET_PTR énoncé à l’adresse d’un tampon SQLINTEGER. Avant que l’application appelle une fonction qui utilise des fixations, il met un décalage dans les octets dans ce tampon. Pour déterminer l’adresse du tampon à utiliser, le conducteur ajoute le décalage à l’adresse de la liaison. La somme de l’adresse et de la compensation doit être une adresse valide, mais l’adresse à laquelle le décalage est ajouté n’a pas à être valide. Pour plus d’informations sur la façon dont les compensations contraignantes sont utilisées, voir « Adresses tampons », plus tard dans cette section.  
  
## <a name="binding-arrays"></a>Arrays de liaison  
 Si la taille de l’acart (la valeur de l’attribut de l’SQL_ATTR_ROW_ARRAY_SIZE) est supérieure à 1, l’application lie des pans de tampons au lieu de tampons uniques. Pour plus d’informations, voir [Block Cursors](../../../odbc/reference/develop-app/block-cursors.md).  
  
 L’application peut lier les tableaux de deux façons :  
  
-   Lier un tableau à chaque colonne. C’est ce qu’on appelle *la liaison de colonne-sage* parce que chaque structure de données (tableau) contient des données pour une seule colonne.  
  
-   Définissez une structure pour conserver les données pour toute une rangée et lier un tableau de ces structures. C’est ce qu’on appelle *la liaison de ligne-sage* parce que chaque structure de données contient les données pour une seule rangée.  
  
 Chaque tableau de tampons doit avoir au moins autant d’éléments que la taille de l’acart.  
  
> [!NOTE]  
>  Une application doit vérifier que l’alignement est valide. Pour plus d’informations sur les considérations d’alignement, voir [Alignement](../../../odbc/reference/develop-app/alignment.md).  
  
## <a name="column-wise-binding"></a>Liaison selon les colonnes  
 Dans la liaison de colonne-sage, l’application lie des données séparées et des tableaux de longueur/indicateur à chaque colonne.  
  
 Pour utiliser la liaison de colonne-sage, l’application définit d’abord l’attribut SQL_ATTR_ROW_BIND_TYPE énoncé à SQL_BIND_BY_COLUMN. (C’est la valeur par défaut.) Pour que chaque colonne soit liée, l’application effectue les étapes suivantes :  
  
1.  Alloue un tableau tampon de données.  
  
2.  Alloue une gamme de tampons de longueur/indicateur.  
  
    > [!NOTE]  
    >  Si l’application écrit directement aux descripteurs lorsque la liaison de la colonne est utilisée, des tableaux distincts peuvent être utilisés pour la longueur et les données d’indicateur.  
  
3.  Appelle **SQLBindCol** avec les arguments suivants:  
  
    -   *TargetType* est le type d’élément unique dans le tableau tampon de données.  
  
    -   *TargetValuePtr* est l’adresse du tableau tampon de données.  
  
    -   *BufferLength* est la taille d’un seul élément dans le tableau tampon de données. *L’argument de BufferLength* est ignoré lorsque les données sont des données à durée fixe.  
  
    -   *StrLen_or_IndPtr* est l’adresse du tableau de longueur/indicateur.  
  
 Pour plus d’informations sur la façon dont ces informations sont utilisées, voir « Adresses tampons », plus tard dans cette section. Pour plus d’informations sur la liaison de colonne-sage, voir [Column-Wise Binding](../../../odbc/reference/develop-app/column-wise-binding.md).  
  
## <a name="row-wise-binding"></a>Liaison selon les lignes  
 Dans la fixation en ligne, l’application définit une structure qui contient des données et des tampons de longueur/indicateur pour chaque colonne à lier.  
  
 Pour utiliser la fixation en ligne, l’application effectue les étapes suivantes :  
  
1.  Définit une structure pour contenir une seule rangée de données (y compris les données et les tampons de longueur/indicateur) et alloue un éventail de ces structures.  
  
    > [!NOTE]  
    >  Si l’application écrit directement aux descripteurs lorsque la liaison en ligne est utilisée, des champs distincts peuvent être utilisés pour la longueur et les données d’indicateurs.  
  
2.  Définit l’attribut SQL_ATTR_ROW_BIND_TYPE énoncé à la taille de la structure qui contient une seule rangée de données ou à la taille d’une instance d’un tampon dans lequel les colonnes de résultats seront liées. La longueur doit inclure de l’espace pour toutes les colonnes liées, et tout rembourrage de la structure ou du tampon, pour s’assurer que lorsque l’adresse d’une colonne liée est incrémentée avec la longueur spécifiée, le résultat indiquera le début de la même colonne dans la rangée suivante. Lors de *l’utilisation de la taille de l’opérateur* dans ANSI C, ce comportement est garanti.  
  
3.  Appelle **SQLBindCol** avec les arguments suivants pour que chaque colonne soit liée :  
  
    -   *TargetType* est le type de membre tampon de données à lié à la colonne.  
  
    -   *TargetValuePtr* est l’adresse du membre tampon de données dans le premier élément de tableau.  
  
    -   *BufferLength* est la taille du membre tampon de données.  
  
    -   *StrLen_or_IndPtr* est l’adresse du membre de la longueur/indicateur à lier.  
  
 Pour plus d’informations sur la façon dont ces informations sont utilisées, voir « Adresses tampons », plus tard dans cette section. Pour plus d’informations sur la liaison de colonne-sage, voir [Row-Wise Binding](../../../odbc/reference/develop-app/row-wise-binding.md).  
  
## <a name="buffer-addresses"></a>Adresses tampon  
 *L’adresse tampon* est l’adresse réelle des données ou de la longueur/indicateur tampon. Le conducteur calcule l’adresse tampon juste avant qu’elle n’écrive aux tampons (par exemple pendant le temps d’aller). Il est calculé à partir de la formule suivante, qui utilise les adresses spécifiées dans les arguments *TargetValuePtr* et *StrLen_or_IndPtr,* la compensation contraignante, et le numéro de ligne:  
  
 *Compensation* + *de liaison d’adresse* liée ((numéro de*rangée* - 1) x *taille d’élément*)  
  
 où les variables de la formule sont définies comme décrites dans le tableau suivant.  
  
|Variable|Description|  
|--------------|-----------------|  
|*Adresse liée*|Pour les tampons de données, l’adresse spécifiée avec l’argument *TargetValuePtr* dans **SQLBindCol**.<br /><br /> Pour les tampons de longueur/indicateur, l’adresse spécifiée avec *l’argument StrLen_or_IndPtr* dans **SQLBindCol**. Pour de plus amples renseignements, consultez la section « Commentaires additionnels » dans la section « Descriptors et SQLBindCol ».<br /><br /> Si l’adresse consolidée est de 0, aucune valeur de données n’est retournée, même si l’adresse calculée par la formule précédente n’est pas zéro.|  
|*Compensation de liaison*|Si la fixation en ligne est utilisée, la valeur stockée à l’adresse spécifiée avec l’attribut SQL_ATTR_ROW_BIND_OFFSET_PTR déclaration.<br /><br /> Si la liaison de la colonne est utilisée ou si la valeur de l’attribut de l’SQL_ATTR_ROW_BIND_OFFSET_PTR’énoncé est un pointeur nul, *binding Offset* est de 0.|  
|*Row Number*|Le numéro à 1 base de la rangée dans le rame. Pour les allers-meur à une seule ligne, qui sont la valeur par défaut, c’est 1.|  
|*Taille de l’élément*|La taille d’un élément dans le tableau lié.<br /><br /> Si la liaison de colonne-sage est utilisée, **c’est la taille de (SQLINTEGER)** pour la longueur/ tampons d’indicateur. Pour les tampons de données, c’est la valeur de l’argument *BufferLength* dans **SQLBindCol** si le type de données est de longueur variable, et la taille du type de données si le type de données est la longueur fixe.<br /><br /> Si la fixation de la ligne est utilisée, c’est la valeur de l’attribut de l’SQL_ATTR_ROW_BIND_TYPE énoncé pour les données et les tampons de longueur/indicateur.|  
  
## <a name="descriptors-and-sqlbindcol"></a>Descripteurs et SQLBindCol  
 Les sections suivantes décrivent comment **SQLBindCol** interagit avec les descripteurs.  
  
> [!CAUTION]  
>  Appeler **SQLBindCol** pour une déclaration peut affecter d’autres déclarations. Cela se produit lorsque l’ARD associé à l’instruction est explicitement attribué et est également associé à d’autres énoncés. Étant donné que **SQLBindCol** modifie le descripteur, les modifications s’appliquent à toutes les déclarations auxquelles ce descripteur est associé. Si ce n’est pas le comportement requis, l’application doit dissocier ce descripteur des autres déclarations avant d’appeler **SQLBindCol**.  
  
## <a name="argument-mappings"></a>Cartographies d’argument  
 Conceptuellement, **SQLBindCol** effectue les étapes suivantes dans l’ordre :  
  
1.  Appelle **SQLGetStmtAttr** pour obtenir la poignée ARD.  
  
2.  Appelle **SQLGetDescField** pour obtenir le champ SQL_DESC_COUNT de ce descripteur, et si la valeur de *l’argument De Lame de colonne* dépasse la valeur de SQL_DESC_COUNT, appelle **SQLSetDescField** pour augmenter la valeur de SQL_DESC_COUNT à *ColumnNumber*.  
  
3.  Appelle **SQLSetDescField** plusieurs fois pour attribuer des valeurs aux champs suivants de l’ARD :  
  
    -   Définit SQL_DESC_TYPE et SQL_DESC_CONCISE_TYPE à la valeur de *TargetType*, sauf que si *TargetType* est l’un des identificateurs concis d’un sous-type de date ou d’intervalle, il définit SQL_DESC_TYPE à SQL_DATETIME ou SQL_INTERVAL, respectivement; définit SQL_DESC_CONCISE_TYPE à l’identifiant concis; et définit SQL_DESC_DATETIME_INTERVAL_CODE au sous-code de date ou d’intervalle correspondant.  
  
    -   Définit une ou plusieurs SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE et SQL_DESC_DATETIME_INTERVAL_PRECISION, le cas échéant pour *TargetType*.  
  
    -   Définit le champ SQL_DESC_OCTET_LENGTH à la valeur de *BufferLength*.  
  
    -   Définit le champ SQL_DESC_DATA_PTR à la valeur de *TargetValue*.  
  
    -   Définit le champ SQL_DESC_INDICATOR_PTR à la valeur de *StrLen_or_Ind*. (Voir le paragraphe suivant.)  
  
    -   Définit le champ SQL_DESC_OCTET_LENGTH_PTR à la valeur de *StrLen_or_Ind*. (Voir le paragraphe suivant.)  
  
 La variable à laquelle *l’argument StrLen_or_Ind* fait référence est utilisée à la fois pour l’information sur les indicateurs et la longueur. Si un aller chercher rencontre une valeur nulle pour la colonne, il stocke SQL_NULL_DATA dans cette variable; autrement, il stocke la longueur des données dans cette variable. Passer un pointeur nul que *StrLen_or_Ind* empêche l’opération aller chercher de retourner la longueur des données, mais rend l’aller chercher échouer si elle rencontre une valeur nulle et n’a aucun moyen de retourner SQL_NULL_DATA.  
  
 Si l’appel à **SQLBindCol** échoue, le contenu des champs descripteur qu’il aurait mis dans l’ARD n’est pas défini et la valeur du champ SQL_DESC_COUNT de l’ARD est inchangée.  
  
## <a name="implicit-resetting-of-count-field"></a>Réinitialisation implicite du champ COUNT  
 **SQLBindCol** ne fixe SQL_DESC_COUNT à la valeur de *l’argument de La Colonnen* que lorsque cela augmenterait la valeur de SQL_DESC_COUNT. Si la valeur de l’argument *TargetValuePtr* est un pointeur nul et que la valeur de *l’argument de La fiche de colonne* est égale à SQL_DESC_COUNT (c’est-à-dire, lorsqu’il ne relie pas la colonne la plus élevée), alors SQL_DESC_COUNT est réglée au nombre de la colonne la plus haute liée restante.  
  
## <a name="cautions-regarding-sql_default"></a>Mises en garde concernant les SQL_DEFAULT  
 Pour récupérer les données de la colonne avec succès, l’application doit déterminer correctement la longueur et le point de départ des données dans le tampon d’application. Lorsque l’application spécifie un *TargetType*explicite, les idées fausses d’application sont facilement détectées. Toutefois, lorsque l’application spécifie un *TargetType* de SQL_DEFAULT, **SQLBindCol** peut être appliqué à une colonne d’un type de données différent de celui prévu par l’application, soit des modifications apportées aux métadonnées, soit en appliquant le code à une autre colonne. Dans ce cas, l’application peut ne pas toujours déterminer le début ou la longueur des données de colonne récupérées. Cela peut entraîner des erreurs de données non déclarées ou des violations de la mémoire.  
  
## <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application exécute une déclaration **SELECT** sur la table des clients pour retourner un ensemble de résultats des numéros d’ID, noms et numéros de téléphone du client, triés par leur nom. Il appelle ensuite **SQLBindCol** pour lier les colonnes de données aux tampons locaux. Enfin, l’application récupère chaque série de données avec **SQLFetch** et imprime le nom, l’identification et le numéro de téléphone de chaque client.  
  
 Pour plus d’exemples de code, voir [SQLBulkOperations Function](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLColumns Function](../../../odbc/reference/syntax/sqlcolumns-function.md), [SQLFetchScroll Function](../../../odbc/reference/syntax/sqlfetchscroll-function.md), et [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp  
// SQLBindCol_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
  
#define UNICODE  
#include <sqlext.h>  
  
#define NAME_LEN 50  
#define PHONE_LEN 60
  
void show_error() {  
   printf("error\n");  
}  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
   SQLWCHAR szName[NAME_LEN], szPhone[PHONE_LEN], sCustID[NAME_LEN];  
   SQLLEN cbName = 0, cbCustID = 0, cbPhone = 0;  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLWCHAR*) L"NorthWind", SQL_NTS, (SQLWCHAR*) NULL, 0, NULL, 0);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {   
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               retcode = SQLExecDirect(hstmt, (SQLWCHAR *) L"SELECT CustomerID, ContactName, Phone FROM CUSTOMERS ORDER BY 2, 1, 3", SQL_NTS);  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
                  // Bind columns 1, 2, and 3  
                  retcode = SQLBindCol(hstmt, 1, SQL_C_WCHAR, &sCustID, 100, &cbCustID);  
                  retcode = SQLBindCol(hstmt, 2, SQL_C_WCHAR, szName, NAME_LEN, &cbName);  
                  retcode = SQLBindCol(hstmt, 3, SQL_C_WCHAR, szPhone, PHONE_LEN, &cbPhone);   
  
                  // Fetch and print each row of data. On an error, display a message and exit.  
                  for (int i=0 ; ; i++) {  
                     retcode = SQLFetch(hstmt);  
                     if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
                        show_error();  
                     if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                     {
                        //replace wprintf with printf
                        //%S with %ls
                        //warning C4477: 'wprintf' : format string '%S' requires an argument of type 'char *'
                        //but variadic argument 2 has type 'SQLWCHAR *'
                        //wprintf(L"%d: %S %S %S\n", i + 1, sCustID, szName, szPhone);  
                        printf("%d: %ls %ls %ls\n", i + 1, sCustID, szName, szPhone);  
                    }    
                     else  
                        break;  
                  }  
               }  
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLCancel(hstmt);  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 Voir aussi, [Échantillon ODBC Program](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Informations de retour sur une colonne dans un ensemble de résultats|[Fonction SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Aller chercher plusieurs rangées de données|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Libérer des tampons de colonne sur la déclaration|[Fonction SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Aller chercher une partie ou la totalité d’une colonne de données|[Fonction SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Retour du nombre de colonnes de jeu de résultats|[Fonction SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
