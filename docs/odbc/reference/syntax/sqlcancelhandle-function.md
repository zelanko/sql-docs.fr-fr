---
title: Fonction SQLCancelHandle (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
f1_keywords:
- SQLCancelHandle
helpviewer_keywords:
- SQLCancelHandle function [ODBC]
ms.assetid: 16049b5b-22a7-4640-9897-c25dd0f19d21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 059ed283032feb96ca5e6b12520682ccb034752a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299664"
---
# <a name="sqlcancelhandle-function"></a>SQLCancelHandle, fonction
**Conformité**  
 Version introduite: ODBC 3.8  
  
 Conformité aux normes : Aucun  
  
 On s’attend à ce que la plupart des pilotes ODBC 3.8 (et plus tard) mettent en œuvre cette fonction. Si un conducteur ne le fait pas, un appel à **SQLCancelHandle** avec une poignée de connexion dans le paramètre *de poignée* retournera SQL_ERROR avec un SQLSTATE de IM001 et le message «Driver ne prend pas en charge cette fonction» Un appel à **SQLCancelHandle** avec une poignée de déclaration que le paramètre *de poignée* sera cartographié à un appel à **SQLCancel** par le gestionnaire de conducteur et peut être traitée si le conducteur implémente **SQLCancelcel**. Une application peut utiliser **SQLGetFunctions** pour déterminer si un conducteur prend en charge **SQLCancelHandle**.  
  
 **Résumé**  
 **SQLCancelHandle** annule le traitement sur une connexion ou une déclaration. Le Gestionnaire de chauffeur passe en carte à **SQLCancelHandle** à un appel à **SQLCancel** lorsque *HandleType* est SQL_HANDLE_STMT.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLCancelHandle(  
      SQLSMALLINT  HandleType,  
      SQLHANDLE    Handle);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Le type de poignée sur laquelle le traitement du cacel. Les valeurs valides sont SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
 *Handle*  
 [Entrée] La poignée sur laquelle annuler le traitement.  
  
 Si *Handle* n’est pas une poignée valide du type spécifié par *HandleType*, **SQLCancelHandle** retourne SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLCancelHandle** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de poignée de déclaration ou un *HandleType* de SQL_HANDLE_DBC et une *poignée*de poignée de connexion .  
  
 Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLCancelHandle** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) dans l’argument * \*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|Une fonction asynchronement exécutée et liée à la déclaration a été appelée pour l’une des poignées de déclaration associées à la *poignée,* et *HandleType* a été mis à SQL_HANDLE_DBC. La fonction asynchrone était encore en cours d’exécution lorsque **SQLCancelHandle** a été appelé.<br /><br /> (DM) *L’argument de HandleType* était SQL_HANDLE_STMT; une fonction d’exécution asynchrone a été appelée sur la poignée de connexion associée; et la fonction était encore en cours d’exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour l’une des poignées de déclaration associées à la *poignée* et *HandleType* a été mis à SQL_HANDLE_DBC, et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> **SQLBrowseConnect** a été appelé pour *ConnectionHandle*, et retourné SQL_NEED_DATA. Cette fonction a été appelée avant le processus de navigation terminé.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY092 HY092|Identification d’attribut/option invalide|*HandleType* a été mis à SQL_HANDLE_ENV ou SQL_HANDLE_DESC.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé à la *poignée* ne prend pas en charge la fonction.|  
  
 Si **SQLCancelHandle** est appelé avec *HandleType* réglé pour SQL_HANDLE_STMT, il peut retourner n’importe quel SQLSTATE qui peut être retourné par la fonction **SQLCancel**.  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est similaire à **SQLCancel,** mais peut prendre soit une connexion ou une poignée de déclaration comme un paramètre plutôt que seulement une poignée de déclaration. Le Gestionnaire de chauffeur passe en carte à **SQLCancelHandle** à un appel à **SQLCancel** lorsque *HandleType* est SQL_HANDLE_STMT. Cela permet aux applications d’utiliser **SQLCancelHandle** pour annuler les opérations de relevé même si le conducteur ne met pas en œuvre **SQLCancelHandle**.  
  
 Pour plus d’informations sur l’annulation d’une opération de déclaration, voir [SQLCancel Function](../../../odbc/reference/syntax/sqlcancel-function.md).  
  
 S’il n’y a pas d’opérations en cours sur *Handle,* l’appel à **SQLCancelHandle** n’a aucun effet.  
  
 **SQLCancelHandle** sur une poignée de connexion peut annuler les types de traitement suivants :  
  
-   A function running asynchronously on the connection.  
  
-   A function running on the connection handle on another thread.  
  
 When **SQLCancelHandle** is called to cancel a function running asynchronously in a connection, diagnostic records posted by **SQLCancelHandle** are appended to those returned by the operation being canceled; **SQLCancelHandle** does not return diagnostic records, however, when canceling a function running on a connection on another thread.  
  
 L’utilisation **de SQLCancelHandle** pour annuler **SQLEndTran** peut mettre la connexion en état de suspension. Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur la façon d’utiliser **SQLCancelHandle** dans une application qui sera déployée sur un système d’exploitation Windows plus ancien que Windows 7, voir [Compatibilité Matrix](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
#### <a name="canceling-connection-related-asynchronous-processing"></a>Annulation du traitement asynchrone lié à la connexion  
 Si une fonction renvoie SQL_STILL_EXECUTING, une application peut appeler **SQLCancelHandle** pour annuler l’opération. Si la demande d’annulation est acceptée, **SQLCancelHandle** revient SQL_SUCCESS. Cela ne signifie pas que la fonction originale a été annulée; il indique que la demande d’annulation a été traitée. Le conducteur et la source de données déterminent quand ou si l’opération est annulée. L’application doit continuer à appeler la fonction d’origine jusqu’à ce que le code de retour ne soit pas SQL_STILL_EXECUTING. Si la fonction originale a été annulée, le code de retour est SQL_ERROR et SQLSTATE HY008 (Opération annulée). Si la fonction originale a terminé son traitement normal (n’a pas été annulée), le code de retour est SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, ou SQL_ERROR et un SQLSTATE autre que HY008 (Opération annulée), si la fonction originale a échoué.  
  
#### <a name="canceling-functions-executing-on-another-thread"></a>Annulation des fonctions exécutant sur un autre thread  
 Dans une application multitâli, l’application peut annuler une opération qui s’exécute sur un autre thread. Pour annuler l’opération, l’application appelle **SQLCancelHandle** avec la poignée utilisée par la fonction, mais sur un thread différent. Le conducteur et le système d’exploitation déterminent comment l’opération est annulée. Le code de retour **SQLCancelHandle** indique si le conducteur a traité la demande, retournant SQL_SUCCESS ou SQL_ERROR (aucune information diagnostique n’est retournée). Si le traitement de la fonction originale est annulé, la fonction originale renvoie SQL_ERROR et SQLSTATE HY008 (Opération annulée).  
  
 Si une fonction est exécutée lorsque **SQLCancelHandle** est appelé sur un autre thread pour annuler la fonction, il est possible pour la fonction de réussir et de retourner SQL_SUCCESS avant que l’annulation peut prendre effet. Un appel à **SQLCancelHandle** n’a aucun effet si l’opération a été terminée avant **que SQLCancelHandle** ne puisse annuler l’opération.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Canceling a function running asynchronously on a statement handle, canceling a function on a statement that needs data, or canceling a function running on a statement on another thread.|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
