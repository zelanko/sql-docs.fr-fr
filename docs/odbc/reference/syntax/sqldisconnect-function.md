---
title: Fonction SQLDisconnect (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDisconnect
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLDisconnect
helpviewer_keywords:
- SQLDisconnect function [ODBC]
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5ea73919fbe90719d881fb43108ab1934933708
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301149"
---
# <a name="sqldisconnect-function"></a>SQLDisconnect, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLDisconnect** ferme la connexion associée à une poignée de connexion spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDisconnect** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et une *poignée* de *ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLDisconnect** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01002|Erreur de déconnexion|Une erreur s’est produite pendant la déconnexion. Cependant, la déconnexion a réussi. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) La connexion spécifiée dans l’argument *ConnectionHandle* n’était pas ouverte.|  
|25000|État de transaction non valide|Il y avait une transaction en cours sur la connexion spécifiée par l’argument *ConnectionHandle*. La transaction reste active.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *ConnectionHandle*. La fonction a été appelée, et avant qu’il nageoires exécution [SQLCancelHandle Fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelé sur le *ConnectionHandle*. Puis la fonction a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ne fine l’exécution **SQLCancelHandle** a été appelé sur le *ConnectionHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour un *StatementHandle* associé à la *ConnectionHandle* et était toujours en exécution lorsque **SQLDisconnect** a été appelé.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *ConnectionHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour un *StatementHandle* associé à la *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande, et la connexion est toujours active. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *ConnectionHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Si une application appelle **SQLDisconnect** après le retour de **SQLBrowseConnect** SQL_NEED_DATA et avant qu’elle ne retourne un code de retour différent, le conducteur annule le processus de navigation de connexion et renvoie la connexion à un état non connecté.  
  
 Si une application appelle **SQLDisconnect** alors qu’il y a une transaction incomplète associée à la poignée de connexion, le conducteur renvoie SQLSTATE 25000 (État de transaction invalide), ce qui indique que la transaction est inchangée et que la connexion est ouverte. Une transaction incomplète est une transaction qui n’a pas été commise ou annulée avec **SQLEndTran**.  
  
 Si une application appelle **SQLDisconnect** avant d’avoir libéré toutes les instructions associées à la connexion, le conducteur, après s’être déconnecté avec succès de la source de données, libère ces relevés et tous les descripteurs qui ont été explicitement attribués sur la connexion. Toutefois, si une ou plusieurs des déclarations associées à la connexion s’exécutent toujours asynchronement, **SQLDisconnect renvoie** SQL_ERROR avec une valeur SQLSTATE de HY010 (erreur de séquence de fonction). De plus, **SQLDisconnect** libérera toutes les déclarations associées et tous les descripteurs qui ont été explicitement attribués à la connexion, si la connexion est en état de suspension ou si **SQLDisconnect** a été annulé avec succès par **SQLCancelHandle**.  
  
 Pour plus d’informations sur la façon dont une application utilise **SQLDisconnect**, voir [Déconnexion d’une source de données ou d’un pilote](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="disconnecting-from-a-pooled-connection"></a>Déconnecter d’une connexion mise en commun  
 Si la mise en commun des connexions est activée pour un environnement partagé et qu’une application appelle **SQLDisconnect** sur une connexion dans cet environnement, la connexion est retournée au pool de connexion et est toujours disponible pour d’autres composants utilisant le même environnement partagé.  
  
## <a name="code-example"></a>Exemple de code  
 Voir [Sample ODBC Program](../../../odbc/reference/sample-odbc-program.md), [SQLBrowseConnect Function](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), et [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Répartition d’une poignée|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Connexion à une source de données|[Fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Connexion à une source de données à l’aide d’une chaîne de connexion ou d’une boîte de dialogue|[Fonction SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Exécution d’une opération de validation ou de restauration|[Fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Libérer une poignée de connexion|[SQLFreeConnect, fonction](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
