---
title: Fonction SQLDescribeCol (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeCol
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeCol
helpviewer_keywords:
- SQLDescribeCol function [ODBC]
ms.assetid: eddef353-83f3-4a3c-8f24-f9ed888890a4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c727f6b36930b0d2ad0d5a61592b83bcd4995426
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301169"
---
# <a name="sqldescribecol-function"></a>Fonction SQLDescribeCol
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLDescribeCol** renvoie le descripteur de résultat - nom de colonne, type, taille de colonne, chiffres décimaux, et nullabilité - pour une colonne dans l’ensemble de résultat. Cette information est également disponible dans les domaines de l’IRD.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLDescribeCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLCHAR *      ColumnName,  
      SQLSMALLINT    BufferLength,  
      SQLSMALLINT *  NameLengthPtr,  
      SQLSMALLINT *  DataTypePtr,  
      SQLULEN *      ColumnSizePtr,  
      SQLSMALLINT *  DecimalDigitsPtr,  
      SQLSMALLINT *  NullablePtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *ColumnNumber*  
 [Entrée] Nombre de données de résultat de colonne, commandées séquentiellement dans l’ordre croissant de colonne, à partir de 1. *L’argument de ColumnNumber* peut également être réglé à 0 pour décrire la colonne de signet.  
  
 *ColumnName*  
 [Sortie] Pointeur vers un tampon annulé dans lequel retourner le nom de colonne. Cette valeur est lue à partir du champ SQL_DESC_NAME de l’IRD. Si la colonne n’est pas nommée ou si le nom de la colonne ne peut pas être déterminé, le conducteur renvoie une chaîne vide.  
  
 Si *ColumnName* est NULL, *NameLengthPtr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *ColumnName*.  
  
 *BufferLength*  
 [Entrée] Longueur du tampon *' ColumnName',* en caractères.  
  
 *NomLengthPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total de \*caractères (à l’exclusion de la résiliation nulle) disponible pour revenir dans *ColumnName*. Si le nombre de caractères disponibles pour revenir est supérieur ou \*égal à *BufferLength*, le nom de colonne dans *ColumnName* est tronqué à *BufferLength* moins la longueur d’un caractère de non-terminaison.  
  
 *DataTypePtr (en)*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le type de données SQL de la colonne. Cette valeur est lue à partir du champ SQL_DESC_CONCISE_TYPE de l’IRD. Il s’agira de l’une des valeurs de [SQL Data Types,](../../../odbc/reference/appendixes/sql-data-types.md)ou d’un type de données SQL spécifique au conducteur. Si le type de données ne peut pas être déterminé, le conducteur retourne SQL_UNKNOWN_TYPE.  
  
 À ODBC 3. *x*, SQL_TYPE_DATE, SQL_TYPE_TIME ou SQL_TYPE_TIMESTAMP est retourné dans * \*DataTypePtr* pour les données de date, d’heure ou d’humidité du temps, respectivement; à ODBC 2. *x*, SQL_DATE, SQL_TIME, ou SQL_TIMESTAMP est retourné. Le gestionnaire de conducteur effectue les cartes requises lorsqu’un ODBC 2. *x* application fonctionne avec un ODBC 3. *x* conducteur ou lorsqu’un ODBC 3. *x* application fonctionne avec un ODBC 2. *x* conducteur.  
  
 Lorsque *ColumnNumber* est égal à 0 (pour une colonne de signets), SQL_BINARY est retourné dans * \*DataTypePtr* pour les signets à longueur variable. (SQL_INTEGER est retourné si les signets sont utilisés par un ODBC 3. *x* application fonctionnant avec un ODBC 2. *x* conducteur ou par un ODBC 2. *x* application fonctionnant avec un ODBC 3. *x* conducteur.)  
  
 Pour plus d’informations sur ces types de données, consultez [sqL Data Types](../../../odbc/reference/appendixes/sql-data-types.md) dans l’annexe D : Data Types. Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur.  
  
 *ColumnSizePtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la taille (en caractères) de la colonne sur la source de données. Si la taille de la colonne ne peut pas être déterminée, le conducteur retourne 0. Pour plus d’informations sur la taille de la colonne, voir [La taille de la colonne, les chiffres décimaux, la longueur d’octet de transfert et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe D : Types de données.  
  
 *DécimaleDigitsPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre de chiffres décimaux de la colonne sur la source de données. Si le nombre de chiffres décimaux ne peut pas être déterminé ou ne s’applique pas, le conducteur retourne 0. Pour plus d’informations sur les chiffres décimaux, voir [La taille de colonne, les chiffres décimaux, la longueur d’octet de transfert et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe D : Data Types.  
  
 *NullablePtr (nullablePtr)*  
 [Sortie] Pointeur vers un tampon dans lequel retourner une valeur qui indique si la colonne permet des valeurs NULL. Cette valeur est lue à partir du champ SQL_DESC_NULLABLE de l’IRD. Les valeurs possibles sont les suivantes :  
  
 SQL_NO_NULLS : La colonne n’autorise pas les valeurs NULL.  
  
 SQL_NULLABLE : La colonne permet des valeurs NULL.  
  
 SQL_NULLABLE_UNKNOWN : Le conducteur ne peut pas déterminer si la colonne permet des valeurs NULL.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDescribeCol** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLDescribeCol** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \*tampon *ColumnName* n’était pas assez grand pour retourner le nom de colonne entière, de sorte que le nom de colonne a été tronqué. La longueur du nom de colonne fausse est retournée dans*nameLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07005|Déclaration préparée et non *une spécification curseur*|La déclaration associée à la *DéclarationHandle* n’a pas retourné un ensemble de résultats. Il n’y avait pas de colonnes à décrire.|  
|07009|Indice descripteur invalide|(DM) La valeur spécifiée pour l’argument *ColumnNumber* était égale à 0, et l’option de déclaration SQL_ATTR_USE_BOOKMARKS était SQL_UB_OFF.<br /><br /> La valeur spécifiée pour l’argument *ColumnNumber* était supérieure au nombre de colonnes dans l’ensemble de résultats.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Échec de l’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque **SQLDescribeCol** a été appelé.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) La fonction a été appelée avant d’appeler **SQLPrepare**, **SQLExecute**, ou une fonction de catalogue sur la poignée de déclaration.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
 **SQLDescribeCol** peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLPrepare** ou **SQLExecute** lorsqu’il est appelé après **SQLPrepare** et avant **SQLExecute**, selon le moment où la source de données évalue la déclaration SQL associée à la poignée de déclaration.  
  
 Pour des raisons de rendement, une demande ne doit pas appeler **SQLDescribeCol** avant d’exécuter une déclaration.  
  
## <a name="comments"></a>Commentaires  
 Une application appelle généralement **SQLDescribeCol** après un appel à **SQLPrepare** et avant ou après l’appel associé à **SQLExecute**. Une application peut également appeler **SQLDescribeCol** après un appel à **SQLExecDirect**. Pour plus d’informations, voir [Métadonnées Result Set](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLDescribeCol** récupère le nom, le type et la longueur de la colonne générés par une déclaration **SELECT.** Si la colonne est une expression,*' ColumnName* est soit une chaîne vide ou un nom défini par le conducteur.  
  
> [!NOTE]  
>  ODBC prend en charge SQL_NULLABLE_UNKNOWN comme une extension, même si la spécification Open Group et SQL Access Group Call Interface n’indique pas l’option pour **SQLDescribeCol**.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Informations de retour sur une colonne dans un ensemble de résultats|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Aller chercher plusieurs rangées de données|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Retour du nombre de colonnes de jeu de résultats|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Préparation d’une déclaration pour l’exécution|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
