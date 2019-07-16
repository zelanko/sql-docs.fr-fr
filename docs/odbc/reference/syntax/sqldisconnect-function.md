---
title: SQLDisconnect, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDisconnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDisconnect
helpviewer_keywords:
- SQLDisconnect function [ODBC]
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7c99b63800d8b007ed11c21a042edc4f51ff7c92
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003222"
---
# <a name="sqldisconnect-function"></a>SQLDisconnect, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLDisconnect** ferme la connexion associée à un handle de connexion spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *Handle de connexion*  
 [Entrée] Handle de connexion.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDisconnect** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_DBC et un *gérer* de *ConnectionHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLDisconnect** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01002|Erreur de déconnexion|Une erreur s’est produite lors de la déconnexion. Toutefois, la déconnexion a réussi. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) la connexion spécifiée dans l’argument *ConnectionHandle* n’était pas ouverte.|  
|25000|État de transaction non valide|Il a été une transaction en cours sur la connexion spécifiée par l’argument *ConnectionHandle*. La transaction reste active.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *ConnectionHandle*. La fonction a été appelée, et avant qu’elle a fini de l’exécution [sqlcancelhandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelé sur le *ConnectionHandle*. La fonction a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> La fonction a été appelée et avant qu’il l’exécution terminée **SQLCancelHandle** a été appelé sur le *ConnectionHandle* d’un thread différent dans une application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour un *au paramètre StatementHandle* associé à la *ConnectionHandle* et était en cours d’exécution lorsque **SQLDisconnect** a été appelée.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *ConnectionHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour un *au paramètre StatementHandle*  associé à la *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande et la connexion est toujours active. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *ConnectionHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Si une application appelle **SQLDisconnect** après **SQLBrowseConnect** retourne SQL_NEED_DATA et avant de retourner un code de retour, le pilote annule la connexion au processus de navigation et retourne la connexion à un état non connecté.  
  
 Si une application appelle **SQLDisconnect** s’il existe une transaction incomplète associée au handle de connexion, le pilote retourne SQLSTATE 25000 (état de transaction non valide), indiquant que la transaction est inchangée et la connexion est ouverte. Une transaction incomplète est un qui n’a pas été validée ou restaurée avec **SQLEndTran**.  
  
 Si une application appelle **SQLDisconnect** avant qu’il a libéré toutes les instructions associées à la connexion, le pilote, une fois qu’il se déconnecte avec succès à partir de la source de données libère de ces instructions et tous les descripteurs qui ont été alloué de façon explicite sur la connexion. Toutefois, si une ou plusieurs des instructions associées à la connexion sont en cours d’exécution en mode asynchrone, **SQLDisconnect** retourne SQL_ERROR avec la valeur SQLSTATE HY010 (erreur de séquence de fonction). En outre, **SQLDisconnect** permettra de libérer toutes les instructions et tous les descripteurs qui ont été alloués explicitement sur la connexion, si la connexion est dans un état suspendu ou si **SQLDisconnect** a été a été annulé par **SQLCancelHandle**.  
  
 Pour plus d’informations sur la façon dont une application utilise **SQLDisconnect**, consultez [déconnexion d’une Source de données ou le pilote](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="disconnecting-from-a-pooled-connection"></a>Déconnexion d’une connexion regroupée  
 Si le regroupement de connexions est activé pour un environnement partagé et une application appelle **SQLDisconnect** sur une connexion dans cet environnement, la connexion est retournée au pool de connexions et est toujours disponible à d’autres composants à l’aide de le même environnement partagé.  
  
## <a name="code-example"></a>Exemple de code  
 Consultez [exemple de programme ODBC](../../../odbc/reference/sample-odbc-program.md), [fonction SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), et [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Allocation d’un handle|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Connexion à une source de données|[SQLConnect, fonction](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Connexion à une source de données à l’aide d’une boîte de dialogue ou de chaîne de connexion|[SQLDriverConnect, fonction](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|L’exécution d’une opération commit ou rollback|[SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Libération d’un descripteur de connexion|[SQLFreeConnect, fonction](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
