---
title: Fonction SQLCancel (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCancel
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCancel
helpviewer_keywords:
- SQLCancel function [ODBC]
ms.assetid: ac0b5972-627f-4440-8c5a-0e8da728726d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fcc2afce495a1481692ba1f20162a2df5d9a9458
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301309"
---
# <a name="sqlcancel-function"></a>SQLCancel, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLCancel** annule le traitement sur une déclaration.  
  
 Pour annuler le traitement sur une connexion ou une déclaration, utilisez [SQLCancelHandle Function](../../../odbc/reference/syntax/sqlcancelhandle-function.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLCancel(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLCancel** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLCancel** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) dans l’argument * \*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLCancel** a été appelée.<br /><br /> (DM) Annuler l’opération a échoué parce qu’une opération asynchrone est en cours sur une poignée de connexion qui est associée à *StatementHandle*.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY018 HY018|Serveur a refusé la demande d’annulation|Le serveur a refusé la demande d’annulation.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 **SQLCancel** peut annuler les types de traitement suivants sur une déclaration :  
  
-   A function running asynchronously on the statement.  
  
-   Une fonction sur une déclaration qui a besoin de données.  
  
-   A function running on the statement on another thread.  
  
 À ODBC 2. *x*, si une demande appelle **SQLCancel** lorsqu’aucun traitement n’est effectué sur la déclaration, **SQLCancel** a le même effet que **SQLFreeStmt** avec l’option SQL_CLOSE; ce comportement n’est défini que pour l’exhaustivité et les applications doivent appeler **SQLFreeStmt** ou **SQLCloseCursor** pour fermer les curseurs.  
  
 When **SQLCancel** is called to cancel a function running asynchronously in a statement or a function on a statement that needs data, diagnostic records posted by the function being canceled are cleared, and **SQLCancel** posts its own diagnostic records; lorsque **SQLCancel** est appelé à annuler une fonction en cours d’exécution sur une déclaration sur un autre thread, cependant, il n’efface pas les dossiers diagnostiques de la fonction annulée en cours et ne publie pas ses propres dossiers diagnostiques.  
  
## <a name="canceling-asynchronous-processing"></a>Annulation du traitement asynchrone  
 Après qu’une application appelle une fonction asynchrone, il appelle la fonction à plusieurs reprises pour déterminer si elle a terminé le traitement. Si la fonction est encore en traitement, elle renvoie SQL_STILL_EXECUTING. Si la fonction a terminé le traitement, elle renvoie un code différent.  
  
 Après tout appel à la fonction qui renvoie SQL_STILL_EXECUTING, une application peut appeler **SQLCancel** pour annuler la fonction. Si la demande d’annulation est acceptée, le conducteur retourne SQL_SUCCESS. Ce message n’indique pas que la fonction a été effectivement annulée; il indique que la demande d’annulation a été traitée. Quand ou si la fonction est effectivement annulée est dépendante du conducteur et de la source de données dépendante. L’application doit continuer à appeler la fonction d’origine jusqu’à ce que le code de retour ne soit pas SQL_STILL_EXECUTING. Si la fonction a été annulée avec succès, le code de retour est SQL_ERROR et SQLSTATE HY008 (Opération annulée). Si la fonction a terminé son traitement normal, le code de retour est SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO si la fonction a réussi ou SQL_ERROR et un SQLSTATE autre que HY008 (Opération annulée) si la fonction a échoué.  
  
> [!NOTE]  
>  Dans ODBC 3.5, un appel à **SQLCancel** lorsqu’aucun traitement n’est effectué sur la déclaration n’est pas traité comme **SQLFreeStmt** avec l’option SQL_CLOSE, mais n’a aucun effet du tout. Pour fermer un curseur, une application doit appeler **SQLCloseCursor**, pas **SQLCancel**.  
  
 Pour plus d’informations sur le traitement asynchrone, voir [Asynchrone Execution](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).  
  
## <a name="canceling-functions-that-need-data"></a>Annulation des fonctions qui ont besoin de données  
 Après le retour **de SQLExecute** ou **SQLExecDirect** SQL_NEED_DATA et avant que les données n’ont été envoyées pour tous les paramètres de données à l’exécution, une application peut appeler **SQLCancel** pour annuler l’exécution de la déclaration. Une fois la déclaration annulée, l’application peut à nouveau appeler **SQLExecute** ou **SQLExecDirect.** Pour plus d’informations, voir [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Après le retour **de SQLBulkOperations** ou **SQLSetPos** SQL_NEED_DATA et avant que les données n’ont été envoyées pour toutes les colonnes de données d’exécution, une application peut appeler **SQLCancel** pour annuler l’opération. Une fois l’opération annulée, l’application peut à nouveau appeler **SQLBulkOperations** ou **SQLSetPos;** l’annulation n’affecte pas l’état du curseur ou la position actuelle du curseur. Pour plus d’informations, voir [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md) ou [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="canceling-functions-executing-on-another-thread"></a>Annulation des fonctions exécutant sur un autre thread  
 Dans une application multitâli, l’application peut annuler une fonction qui s’exécute sur un autre thread. Pour annuler la fonction, l’application appelle **SQLCancel** avec la même poignée de déclaration que celle utilisée par la fonction cible, mais sur un thread différent. La façon dont la fonction est annulée dépend du conducteur et du système d’exploitation. As in canceling a function running asynchronously, the return code of the **SQLCancel** indicates only whether the driver processed the request successfully. Seules SQL_SUCCESS ou SQL_ERROR peuvent être retournées; aucune information diagnostique n’est retournée. Si la fonction originale est annulée, elle revient SQL_ERROR et SQLSTATE HY008 (Opération annulée).  
  
 Si une déclaration SQL est exécutée lorsque **SQLCancel** est appelé sur un autre thread pour annuler l’exécution de la déclaration, il est possible pour l’exécution de réussir et de retourner SQL_SUCCESS tandis que l’annulation est également réussie. Dans ce cas, le gestionnaire de conducteur suppose que le curseur ouvert par l’exécution de la déclaration est fermé par l’annulation, de sorte que l’application ne sera pas en mesure d’utiliser le curseur.  
  
 Pour plus d’informations sur le threading, voir [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à un paramètre|[Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Effectuer des opérations d’insertion ou de mise à jour en vrac|[SQLBulkOperations, fonction](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Cancels a function running asynchronously on a connection handle, in addition to the functionality of **SQLCancel**.|[SQLCancelHandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Libérer une poignée de déclaration|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Obtenir un champ d’un dossier diagnostique ou un champ de l’en-tête diagnostique|[Fonction SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
|Obtenir plusieurs champs d’une structure de données diagnostiques|[SQLGetDiagRec, fonction](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
|Retour du paramètre suivant pour envoyer des données pour|[SQLParamData, fonction](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Envoi de données de paramètres au moment de l’exécution|[Fonction SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionnement du curseur dans un aviron, données rafraîchissantes dans l’aviron, ou mise à jour ou suppression des données dans l’ensemble de résultats|[SQLSetPos, fonction](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
