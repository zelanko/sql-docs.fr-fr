---
title: Fonction SQLEndTran (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLEndTran
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLEndTran
helpviewer_keywords:
- SQLEndTran function [ODBC]
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cce7792e52fce4984f3da41e11d79c34b6b79e53
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302740"
---
# <a name="sqlendtran-function"></a>Fonction SQLEndTran
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLEndTran** demande une opération de validation ou de restauration pour toutes les opérations actives sur toutes les déclarations associées à une connexion. **SQLEndTran** peut également demander qu’une opération de validation ou de restauration soit effectuée pour toutes les connexions associées à un environnement.  
  
> [!NOTE]  
>  Pour plus d’informations sur ce que le Driver Manager cartographie cette fonction à quand un ODBC 3. *x* application fonctionne avec un ODBC 2. *x* pilote, voir [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Identifiant de type de poignée. Contient soit SQL_HANDLE_ENV (si *poignée* est une poignée d’environnement) ou SQL_HANDLE_DBC (si *Handle* est une poignée de connexion).  
  
 *Handle*  
 [Entrée] La poignée, du type indiqué par *HandleType*, indiquant la portée de la transaction. Voir "Commentaires" pour plus d’informations.  
  
 *AchèvementType*  
 [Entrée] L’une des deux valeurs suivantes :  
  
 SQL_COMMIT SQL_ROLLBACK  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLEndTran** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec le *HandleType* et *la poignée*appropriés . Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLEndTran** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) Le *HandleType* était SQL_HANDLE_DBC, et la *poignée* n’était pas dans un état connecté.|  
|08007|Défaillance de connexion pendant la transaction|Le *HandleType* a été SQL_HANDLE_DBC, et la connexion associée à la *poignée* a échoué pendant l’exécution de la fonction, et il n’est pas possible de déterminer si le **COMMIT** demandé ou **ROLLBACK** s’est produit avant la défaillance.|  
|25S01|État de transaction inconnu|Une ou plusieurs des connexions dans *Handle* n’ont pas terminé la transaction avec le résultat spécifié, et le résultat est inconnu.|  
|25S02|La transaction est toujours active|Le conducteur n’a pas été en mesure de garantir que tous les travaux de la transaction mondiale pourraient être achevés atomiquement, et la transaction est toujours active.|  
|25S03|La transaction est annulée|Le conducteur n’a pas été en mesure de garantir que tous les travaux de la transaction mondiale pouvaient être achevés atomiquement, et tous les travaux de la transaction active dans *Handle* ont été annulés.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40002|Violation de la contrainte d’intégrité|Le *Point d’achèvement* a été SQL_COMMIT, et l’engagement de changements a causé une violation de la contrainte d’intégrité. Par conséquent, la transaction a été annulée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \*tampon szMessageText décrit l’erreur* et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *ConnectionHandle*. La fonction a été appelée, et avant qu’il ne fina l’exécution [DE SQLCancelHandle Function](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelé sur le *ConnectionHandle*. Puis la fonction a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ne fine l’exécution **SQLCancelHandle** a été appelé sur le *ConnectionHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour une poignée de déclaration associée à la *ConnectionHandle* et était toujours en exécution lorsque **SQLEndTran** a été appelé.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *ConnectionHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour une poignée de déclaration associée à la *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celui-ci) a été appelé pour la *poignée* avec *HandleType* mis à SQL_HANDLE_DBC et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour l’une des poignées de déclaration associées à *Handle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY012|Code d’opération de transaction invalide|(DM) La valeur spécifiée pour l’argument *CompletionType* n’était ni SQL_COMMIT ni SQL_ROLLBACK.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY092 HY092|Identification d’attribut/option invalide|(DM) La valeur spécifiée pour l’argument *HandleType* n’était ni SQL_HANDLE_ENV ni SQL_HANDLE_DBC.|  
|HY115|SQLEndTran n’est pas autorisé pour un environnement qui contient une connexion avec l’exécution de la fonction asynchrone activée|(DM) *HandleType* ne peut pas être configuré pour SQL_HANDLE_ENV si l’exécution asynchrone des fonctions de connexion est activée pour une connexion dans l’environnement.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, se référer à la section Commentaires de ce sujet.|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données ne prend pas en charge l’opération **ROLLBACK.**|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *ConnectionHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Pour un ODBC 3. *x* conducteur, si *HandleType* est SQL_HANDLE_ENV et *que la poignée* est une poignée d’environnement valide, alors le gestionnaire de conducteur appellera **SQLEndTran** dans chaque conducteur associé à l’environnement. *L’argument de poignée* pour l’appel à un conducteur sera la poignée de l’environnement du conducteur. Pour un ODBC 2. *x* conducteur, si *HandleType* est SQL_HANDLE_ENV et *poignée* est une poignée d’environnement valide, et il ya plusieurs connexions dans un état connecté dans cet environnement, puis le gestionnaire de conducteur appellera **SQLTransact** dans le conducteur une fois pour chaque connexion dans un état connecté dans cet environnement. *L’argument de poignée* dans chaque appel sera la poignée de la connexion. Dans les deux cas, le conducteur tentera de commettre ou de faire reculer les transactions, en fonction de la valeur de *CompletionType*, sur toutes les connexions qui sont dans un état connecté sur cet environnement. Les connexions qui ne sont pas actives n’affectent pas la transaction.  
  
> [!NOTE]  
>  **SQLEndTran** ne peut pas être utilisé pour engager ou annuler les transactions sur un environnement partagé. SQLSTATE HY092 (identification d’attribut/option invalide) sera retourné si **SQLEndTran** est appelé avec *Handle* réglé à la poignée d’un environnement partagé ou à la poignée d’une connexion sur un environnement partagé.  
  
 Le gestionnaire de conducteur ne retournera SQL_SUCCESS que s’il reçoit SQL_SUCCESS pour chaque connexion. Si le gestionnaire de conducteur reçoit SQL_ERROR sur une ou plusieurs connexions, il retourne SQL_ERROR à l’application, et l’information diagnostique est placée dans la structure de données diagnostiques de l’environnement. Pour déterminer quelle connexion ou connexion a échoué pendant l’opération de validation ou de restauration, l’application peut appeler **SQLGetDiagRec** pour chaque connexion.  
  
> [!NOTE]  
>  Le Gestionnaire de pilote ne simule pas une transaction globale sur toutes les connexions et n’utilise donc pas de protocoles de validation en deux phases.  
  
 Si *CompletionType* est SQL_COMMIT, **SQLEndTran** émet une demande de validation pour toutes les opérations actives sur toute déclaration associée à une connexion affectée. Si *CompletionType* est SQL_ROLLBACK, **SQLEndTran** émet une demande de restauration pour toutes les opérations actives sur toute déclaration associée à une connexion affectée. Si aucune transaction n’est active, **SQLEndTran** retourne SQL_SUCCESS sans effet sur aucune source de données. Pour plus d’informations, voir [Committing et Rolling Back Transactions](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md).  
  
 Si le conducteur est en mode de validation manuelle (en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_AUTOCOMMIT défini à SQL_AUTOCOMMIT_OFF), une nouvelle transaction est implicitement lancée lorsqu’une déclaration SQL qui peut être contenue dans une transaction est exécutée contre la source de données actuelle. Pour plus d’informations, voir [Mode Commit](../../../odbc/reference/develop-app/commit-mode.md).  
  
 Pour déterminer comment les opérations de transaction affectent les curseurs, une application appelle **SQLGetInfo** avec les options SQL_CURSOR_ROLLBACK_BEHAVIOR et SQL_CURSOR_COMMIT_BEHAVIOR. Pour plus d’informations, voir les paragraphes suivants et voir [effet des transactions sur les curseurs et les déclarations préparées](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
 Si la valeur SQL_CURSOR_ROLLBACK_BEHAVIOR ou SQL_CURSOR_COMMIT_BEHAVIOR équivaut à SQL_CB_DELETE, **SQLEndTran** ferme et supprime tous les curseurs ouverts sur toutes les instructions associées à la connexion et rejette tous les résultats en attente. **SQLEndTran** laisse toute déclaration présente dans un état attribué (non préparé); l’application peut les réutiliser pour les demandes SQL ultérieures ou peut appeler **SQLFreeStmt** ou **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT pour les traiter.  
  
 Si la valeur SQL_CURSOR_ROLLBACK_BEHAVIOR ou SQL_CURSOR_COMMIT_BEHAVIOR équivaut à SQL_CB_CLOSE, **SQLEndTran** ferme tous les curseurs ouverts sur toutes les déclarations associées à la connexion. **SQLEndTran** laisse toute déclaration présente dans un état préparé; l’application peut appeler **SQLExecute** pour une déclaration associée à la connexion sans d’abord appeler **SQLPrepare**.  
  
 Si la valeur SQL_CURSOR_ROLLBACK_BEHAVIOR ou SQL_CURSOR_COMMIT_BEHAVIOR équivaut à SQL_CB_PRESERVE, **SQLEndTran** n’affecte pas les curseurs ouverts associés à la connexion. Les curseurs restent à la rangée qu’ils ont pointée avant l’appel à **SQLEndTran**.  
  
 Pour les conducteurs et les sources de données qui prennent en charge les transactions, appeler **SQLEndTran** avec SQL_COMMIT ou SQL_ROLLBACK lorsqu’aucune transaction n’est une transaction SQL_SUCCESS (ce qui indique qu’il n’y a pas de travail à engager ou à revenir en arrière) et n’a aucun effet sur la source de données.  
  
 Lorsqu’un conducteur est en mode autocommit, le gestionnaire de conducteur n’appelle pas **SQLEndTran** dans le conducteur. **SQLEndTran** retourne toujours SQL_SUCCESS peu importe s’il est appelé avec un *completionType* de SQL_COMMIT ou SQL_ROLLBACK.  
  
 Les conducteurs ou les sources de données qui ne prennent pas en charge les transactions *(option* **SQLGetInfo** SQL_TXN_CAPABLE est SQL_TC_NONE) sont effectivement toujours en mode autocommit et reviennent donc toujours SQL_SUCCESS pour **SQLEndTran,** qu’ils soient ou non appelés avec un *completionType* de SQL_COMMIT ou SQL_ROLLBACK. Ces conducteurs et sources de données ne font pas reculer les transactions lorsqu’on leur demande de le faire.  
  
## <a name="suspended-state"></a>État suspendu  
 Dans Driver Managers qui ont été libérés avant Windows 7, une transaction était active si **SQLEndTran** revenait SQL_ERROR du conducteur. Toutefois, il était possible que la transaction ait été validée avec succès sur le serveur, mais le conducteur du client n’avait pas été avisé (par exemple, parce qu’une erreur de réseau s’était produite). Cela laisserait la connexion dans un mauvais état. En commençant par Windows 7, lorsque **SQLEndTran** revient SQL_ERROR, la connexion peut être dans un état suspendu. Dans un état suspendu, il est possible d’appeler des fonctions de lecture seulement. Éventuellement, l’application devrait appeler **SQLDisconnect** sur une connexion suspendue pour libérer des ressources.  
  
 Si toutes les conditions suivantes sont vraies, la connexion sera mise en suspension :  
  
-   Le conducteur retourne SQL_ERROR de **SQLEndTran**.  
  
-   Le conducteur est la version 3.8 d’ODBC, ou plus tard.  
  
-   La version d’application est 3.8 ou plus tard; ou l’application 2.x ou 3.x de l’ODBC 2.x ou 3.x recomposée avec succès annule la fonction **SQLEndTran** par **SQLCancelHandle**.  
  
-   Le conducteur n’a pas retourné l’un des messages suivants, qui confirment que la transaction n’a pas été conclue :  
  
    -   25S03 : La transaction est annulée  
  
    -   40001: Échec de la sérialisation  
  
    -   40002 : Contrainte d’intégrité  
  
    -   HYC00 : Fonctionnalité facultative non implémentée  
  
 Si **SQLEndTran** a été appelé sur une poignée d’environnement et l’une de ses connexions remplies les conditions ci-dessus, toutes les connexions se connectant au même conducteur seront mis dans l’état suspendu.  
  
 Après qu’une application appelle **SQLDisconnect** sur une connexion suspendue, la connexion peut être utilisée pour se reconnecter à une autre source de données ou à la même source de données.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Annulation d’une fonction fonction fonction fonctionnant asynchronement sur une poignée de connexion.|[SQLCancelHandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Retour d’informations sur un conducteur ou une source de données|[Fonction SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Libérer une poignée|[Fonction SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Libérer une poignée de déclaration|[Fonction SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
