---
title: Sqlcancelhandle, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f572e9e76f77b0c535cd57ff4ed6cd091aec0f5
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537572"
---
# <a name="sqlcancelhandle-function"></a>SQLCancelHandle, fonction
**Conformité**  
 Version introduite : ODBC 3.8  
  
 Conformité aux normes : None  
  
 Il est probable que la plupart des pilotes ODBC de 3,8 (et versions ultérieures) implémente cette fonction. Si un pilote n’effectue pas le cas, un appel à **SQLCancelHandle** avec une connexion gérer dans le *gérer* paramètre retourne SQL_ERROR avec SQLSTATE de IM001 et le message « pilote ne prend pas en charge cette fonction '' un appel pour **SQLCancelHandle** avec une instruction gérer en tant que le *gérer* paramètre sera mappé à un appel à **SQLCancel** par le Gestionnaire de pilotes et peuvent être traitées si le pilote implémente **SQLCancel**. Une application peut utiliser **SQLGetFunctions** pour déterminer si un pilote prend en charge **SQLCancelHandle**.  
  
 **Résumé**  
 **SQLCancelHandle** annule le traitement sur une connexion ou une instruction. Le Gestionnaire de pilotes est mappé à un appel à **SQLCancelHandle** à un appel à **SQLCancel** lorsque *HandleType* est SQL_HANDLE_STMT.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLCancelHandle(  
      SQLSMALLINT  HandleType,  
      SQLHANDLE    Handle);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Le type du handle sur lequel cacel traitement. Les valeurs valides sont SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
 *Handle*  
 [Entrée] Handle sur lesquels annuler le traitement.  
  
 Si *gérer* n’est pas un handle valide du type spécifié par *HandleType*, **SQLCancelHandle** retourne SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLCancelHandle** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une instruction gèrent *gérer* ou un *HandleType* de SQL_HANDLE_DBC et un handle de connexion *gérer*.  
  
 Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLCancelHandle** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) dans l’argument  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|Une fonction de façon asynchrone en cours d’exécution, lié à une instruction a été appelée pour l’une des descripteurs d’instruction associés à la *gérer*, et *HandleType* a pour valeur SQL_HANDLE_DBC. La fonction asynchrone était en cours d’exécution lorsque **SQLCancelHandle** a été appelée.<br /><br /> (DM) le *HandleType* argument était SQL_HANDLE_STMT ; une fonction d’exécution asynchrone a été appelée sur le handle de connexion associés ; et la fonction s’exécute toujours quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelée pour l’une des descripteurs d’instruction associés à la *gérer* et *HandleType* a été défini sur SQL_HANDLE_DBC et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> **SQLBrowseConnect** a été appelé pour *ConnectionHandle*et retourné SQL_NEED_DATA. Cette fonction a été appelée avant la fin du processus navigation.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY092|Identificateur d’option/attribut non valide|*HandleType* a été défini à SQL_HANDLE_ENV ou SQL_HANDLE_DESC.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *gérer* ne prend pas en charge la fonction.|  
  
 Si **SQLCancelHandle** est appelée avec *HandleType* défini à SQL_HANDLE_STMT, elle peut retourner n’importe quel SQLSTATE qui peut être retournée par la fonction **SQLCancel**.  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est similaire à **SQLCancel** mais peut prendre le handle d’une connexion ou une instruction comme un paramètre au lieu d’un descripteur d’instruction. Le Gestionnaire de pilotes est mappé à un appel à **SQLCancelHandle** à un appel à **SQLCancel** lorsque *HandleType* est SQL_HANDLE_STMT. Cela permet aux applications d’utiliser **SQLCancelHandle** d’annuler des opérations de l’instruction même si le pilote n’implémente pas **SQLCancelHandle**.  
  
 Pour plus d’informations sur l’annulation d’une opération de l’instruction, consultez [sqlcancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md).  
  
 S’il en existe aucune opération en cours d’exécution sur *gérer* l’appel à **SQLCancelHandle** n’a aucun effet.  
  
 **SQLCancelHandle** sur une connexion handle peut annuler les types de traitement suivants :  
  
-   Une fonction en cours d’exécution en mode asynchrone sur la connexion.  
  
-   Une fonction en cours d’exécution sur le handle de connexion sur un autre thread.  
  
 Lorsque **SQLCancelHandle** est appelé pour annuler une fonction en cours d’exécution en mode asynchrone dans une connexion, les enregistrements de diagnostic publiés par **SQLCancelHandle** sont ajoutées à celles retournées par l’opération en cours annulée ; **SQLCancelHandle** ne retourne pas les enregistrements de diagnostic, toutefois, lors de l’annulation d’une fonction en cours d’exécution sur une connexion sur un autre thread.  
  
 À l’aide de **SQLCancelHandle** Annuler **SQLEndTran** peut placer la connexion dans un état suspendu. Pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation **SQLCancelHandle** dans une application qui sera déployée sur un système d’exploitation Windows antérieurs à Windows 7, consultez [matrice de compatibilité](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
#### <a name="canceling-connection-related-asynchronous-processing"></a>L’annulation liées à la connexion de traitement asynchrone  
 Si une fonction retourne SQL_STILL_EXECUTING, une application peut appeler **SQLCancelHandle** pour annuler l’opération. Si la demande d’annulation a réussi, **SQLCancelHandle** retourne SQL_SUCCESS. Cela ne signifie pas que la fonction d’origine a été annulée ; Il indique que la demande d’annulation a été traitée. Le pilote et la source de données déterminent quand ou si l’opération est annulée. L’application doit continuer à appeler la fonction d’origine jusqu'à ce que le code de retour n’est pas SQL_STILL_EXECUTING. Si la fonction d’origine a été annulée, le code de retour est SQL_ERROR et SQLSTATE HY008 (opération annulée). Si la fonction d’origine effectué son traitement normal (pas annulée), le code de retour est SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, ou SQL_ERROR et un SQLSTATE autre que HY008 (opération annulée), en cas d’échec de la fonction d’origine.  
  
#### <a name="canceling-functions-executing-on-another-thread"></a>Annulation de l’exécution sur un autre Thread de fonctions  
 Dans une application multithread, l’application peut annuler une opération qui s’exécute sur un autre thread. Pour annuler l’opération, l’application appelle **SQLCancelHandle** avec le handle utilisé par la fonction, mais sur un thread différent. Le pilote et le système d’exploitation déterminent comment l’opération est annulée. Le **SQLCancelHandle** renvoyer le code indique si le pilote traité la demande en renvoyant SQL_SUCCESS ou SQL_ERROR (aucune information de diagnostic n’est retournée). Si le traitement sur la fonction d’origine est annulé, la fonction d’origine retourne SQL_ERROR et SQLSTATE HY008 (opération annulée).  
  
 Si une fonction est exécutée lorsque **SQLCancelHandle** est appelée sur un autre thread pour annuler la fonction, il est possible pour la fonction de réussir et retourne SQL_SUCCESS avant l’annulation prenne effet. Un appel à **SQLCancelHandle** n’a aucun effet si l’opération terminée avant **SQLCancelHandle** a été en mesure d’annuler l’opération.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Annulation d’une fonction s’exécutant de façon asynchrone sur un descripteur d’instruction, l’annulation d’une fonction sur une instruction qui a besoin de données ou de l’annulation d’une fonction en cours d’exécution sur une instruction sur un autre thread.|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
