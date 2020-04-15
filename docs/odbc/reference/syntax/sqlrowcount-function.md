---
title: Fonction SQLRowCount (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2cbca03e7c3e381b803196a1bf7bb227ebeea03b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293369"
---
# <a name="sqlrowcount-function"></a>SQLRowCount (fonction)
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLRowCount** renvoie le nombre de lignes touchées par une **mise À JOUR**, **INSERT**, ou **DÉLÉT;** une SQL_ADD, un SQL_UPDATE_BY_BOOKMARK ou SQL_DELETE_BY_BOOKMARK’opération dans **SQLBulkOperations;** ou une SQL_UPDATE ou une SQL_DELETE opération dans **SQLSetPos**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *RowCountPtr RowCountPtr RowCountPtr RowCount*  
 [Sortie] Indique un tampon dans lequel retourner un compte de ligne. Pour **UPDATE**, **INSERT**, et les déclarations **DE DELETE,** pour les opérations SQL_ADD, SQL_UPDATE_BY_BOOKMARK et SQL_DELETE_BY_BOOKMARK dans **SQLBulkOperations**, et pour les opérations SQL_UPDATE ou SQL_DELETE dans **SQLSetPos**, la valeur retournée dans*rowCountPtr* est soit le nombre de lignes touchées par la demande ou -1 si le nombre de lignes touchées n’est pas disponible.  
  
 Lorsque **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos, ou SQLMoreResults** est appelé, le champ SQL_DIAG_ROW_COUNT de la structure de données diagnostiques est réglé sur le nombre de rangées, et le nombre de rangées est mis en cache d’une manière dépendante de la mise en œuvre. **SQLRowCount** retourne la valeur de comptage de la rangée mise en cache. La valeur de comptage de la rangée en cache est valide jusqu’à ce que la poignée de déclaration soit remise à l’état préparé ou attribué, que l’énoncé soit réexaminé ou **que LE SQLCloseCursor** soit appelé. Notez que si une fonction a été appelée depuis que le champ SQL_DIAG_ROW_COUNT a été défini, la valeur retournée par **SQLRowCount** peut être différente de la valeur dans le champ SQL_DIAG_ROW_COUNT parce que le champ SQL_DIAG_ROW_COUNT est réinitialisé à 0 par n’importe quel appel de fonction.  
  
 Pour d’autres déclarations et fonctions, \*le conducteur peut définir la valeur retournée dans *RowCountPtr*. Par exemple, certaines sources de données peuvent être en mesure de retourner le nombre de lignes retournées par une instruction **SELECT** ou une fonction de catalogue avant d’aller chercher les lignes.  
  
> [!NOTE]  
>  De nombreuses sources de données ne peuvent pas retourner le nombre de lignes dans un résultat défini avant de les chercher; pour une interopérabilité maximale, les applications ne doivent pas s’appuyer sur ce comportement.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRowCount** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLRowCount** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLRowCount** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) La fonction a été appelée avant d’appeler **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** pour le *StatementHandle*.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Si la dernière déclaration SQL exécutée sur la poignée de déclaration n’était pas une **mise À JOUR**, **INSERT**, ou **DÉLÉT** déclaration ou si *l’argument de l’opération* dans l’appel précédent à **SQLBulkOperations** n’était pas SQL_ADD, SQL_UPDATE_BY_BOOKMARK, ou SQL_DELETE_BY_BOOKMARK, ou si *l’argument de l’opération* dans l’appel précédent à **SQLSetPos** n’était pas SQL_UPDATE ou SQL_DELETE, la valeur de *' RowCountPtr* est définie par le conducteur. Pour plus d’informations, voir [Déterminer le nombre de lignes touchées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
