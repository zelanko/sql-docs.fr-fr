---
title: SQLEndTran, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLEndTran
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLEndTran
helpviewer_keywords:
- SQLEndTran function [ODBC]
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16b4bcfec2640c0dbd55d43be9df2391ed1f66c0
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538036"
---
# <a name="sqlendtran-function"></a>Fonction SQLEndTran
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLEndTran** demande une opération commit ou rollback pour toutes les opérations actives sur toutes les instructions associées à une connexion. **SQLEndTran** peut également demander qu’une instruction commit ou rollback opération pour toutes les connexions associées à un environnement.  
  
> [!NOTE]  
>  Pour plus d’informations sur quelles le Gestionnaire de pilotes mappe cette fonction lorsqu’un ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote, consultez [mappage des fonctions de remplacement pour une compatibilité descendante des Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Identificateur de type de handle. Contient deux SQL_HANDLE_ENV (si *gérer* est un handle d’environnement) ou SQL_HANDLE_DBC (si *gérer* est un handle de connexion).  
  
 *Handle*  
 [Entrée] Le handle du type indiqué par *HandleType*, qui indique la portée de la transaction. Pour plus d’informations, consultez « Commentaires ».  
  
 *CompletionType*  
 [Entrée] L’une des deux valeurs suivantes :  
  
 SQL_COMMIT SQL_ROLLBACK  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLEndTran** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec le bon *HandleType*et *gérer*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLEndTran** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) le *HandleType* a été SQL_HANDLE_DBC et le *gérer* n’était pas dans un état connecté.|  
|08007|Échec de la connexion au cours de la transaction|Le *HandleType* a été SQL_HANDLE_DBC et associé à la connexion le *gérer* a échoué pendant l’exécution de la fonction, et il ne peut pas être déterminé si demandé  **VALIDER** ou **ROLLBACK** s’est produite avant la défaillance.|  
|25S01|État de transaction inconnu|Un ou plusieurs de ces connexions dans *gérer* n’a pas pu terminer la transaction avec le résultat spécifié, et le résultat est inconnu.|  
|25S02|Transaction est toujours active|Le pilote n’a pas pu garantit que tout le travail dans la transaction globale pu être effectué de manière atomique, et la transaction est toujours active.|  
|25S03|Restauration de transaction|Le pilote n’était pas en mesure de garantir que tout le travail dans la transaction globale pu être effectué de manière atomique et fonctionnent tous de la transaction active dans *gérer* a été restaurée.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40002|Violation de contrainte d’intégrité|Le *CompletionType* était active, et la validation des modifications a provoqué la violation de contrainte d’intégrité. Par conséquent, la transaction a été annulée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*szMessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *ConnectionHandle*. La fonction a été appelée et avant qu’il l’exécution terminée [sqlcancelhandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelé sur le *ConnectionHandle*. La fonction a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> La fonction a été appelée et avant qu’il l’exécution terminée **SQLCancelHandle** a été appelé sur le *ConnectionHandle* d’un thread différent dans une application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour un descripteur d’instruction associé à la *ConnectionHandle* et était en cours d’exécution lorsque **SQLEndTran** a été appelée.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *ConnectionHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelée pour un descripteur d’instruction associé avec le *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *gérer* avec *HandleType* ayant pour valeur SQL_HANDLE_DBC et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelée pour l’une des descripteurs d’instruction associés *gérer* et SQL_PARAM_DATA_AVAILABLE retournée. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.|  
|HY012|Code d’opération de transaction non valide|(DM) la valeur spécifiée pour l’argument *CompletionType* a été ni SQL_COMMIT ou SQL_ROLLBACK.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY092|Identificateur d’option/attribut non valide|(DM) la valeur spécifiée pour l’argument *HandleType* n’était ni SQL_HANDLE_ENV ni SQL_HANDLE_DBC.|  
|HY115|SQLEndTran n’est pas autorisée pour un environnement qui contient une connexion avec l’exécution asynchrone (fonction)|(DM) *HandleType* ne peut pas être défini à SQL_HANDLE_ENV si l’exécution asynchrone de fonctions de la connexion est activée pour une connexion dans l’environnement.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, reportez-vous à la section Remarques de cette rubrique.|  
|HYC00|Fonctionnalité optionnelle non implémentée|La source de données ou le pilote ne prend pas en charge la **ROLLBACK** opération.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *ConnectionHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Pour une application ODBC 3. *x* pilote, si *HandleType* est SQL_HANDLE_ENV et *gérer* est un handle d’environnement valide, puis appelle le Gestionnaire de pilotes **SQLEndTran**dans chaque pilote associé à l’environnement. Le *gérer* argument pour l’appel à un pilote sera le handle d’environnement du pilote. Pour une application ODBC 2. *x* pilote, si *HandleType* est SQL_HANDLE_ENV et *gérer* est un handle d’environnement valide, et il existe plusieurs connexions dans un état connecté dans l’environnement, puis appelle le Gestionnaire de pilotes **SQLTransact** dans le pilote une fois pour chaque connexion dans un état connecté dans cet environnement. Le *gérer* argument dans chaque appel sera le handle de la connexion. Dans les deux cas, le pilote tente de valider ou restaurer des transactions, selon la valeur de *CompletionType*, sur toutes les connexions qui se trouvent dans un état connecté sur cet environnement. Les connexions qui ne sont pas actives n’affectent pas la transaction.  
  
> [!NOTE]  
>  **SQLEndTran** ne peut pas être utilisé pour valider ou restaurer les transactions sur un environnement partagé. SQLSTATE HY092 (identificateur d’option/attribut non valide) est renvoyée si **SQLEndTran** est appelée avec *gérer* la valeur est soit le handle d’un environnement partagé ou le handle d’une connexion sur un partage environnement.  
  
 Le Gestionnaire de pilotes retourne SQL_SUCCESS uniquement si elle reçoit SQL_SUCCESS pour chaque connexion. Si le Gestionnaire de pilotes reçoit SQL_ERROR sur une ou plusieurs connexions, il retourne SQL_ERROR à l’application, et les informations de diagnostic sont placées dans la structure de données de diagnostic de l’environnement. Pour déterminer les connexions ou la connexion a échoué pendant l’opération commit ou rollback, l’application peut appeler **SQLGetDiagRec** pour chaque connexion.  
  
> [!NOTE]  
>  Le Gestionnaire de pilotes ne simule pas une transaction globale dans toutes les connexions et par conséquent n’utilise pas de protocoles de validation en deux phases.  
  
 Si *CompletionType* est active, **SQLEndTran** émet une requête de validation pour toutes les opérations actives sur n’importe quelle instruction associée à une connexion affectée. Si *CompletionType* est SQL_ROLLBACK, **SQLEndTran** émet une requête de restauration pour toutes les opérations actives sur n’importe quelle instruction associée à une connexion affectée. Si aucune transaction n’est active, **SQLEndTran** retourne SQL_SUCCESS, sans aucune incidence sur toutes les sources de données. Pour plus d’informations, consultez [engagement et propagée les Transactions](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md).  
  
 Si le pilote est en mode de validation manuelle (en appelant **SQLSetConnectAttr** avec le SQL_ATTR_AUTOCOMMIT attribut SQL_AUTOCOMMIT_OFF), une nouvelle transaction est démarrée implicitement quand une instruction SQL qui peut être contenue dans un transaction est exécutée sur la source de données actuelle. Pour plus d’informations, consultez [Mode Commit](../../../odbc/reference/develop-app/commit-mode.md).  
  
 Pour déterminer les conséquences des opérations de transaction sur les curseurs, une application appelle **SQLGetInfo** avec les options SQL_CURSOR_ROLLBACK_BEHAVIOR et SQL_CURSOR_COMMIT_BEHAVIOR. Pour plus d’informations, consultez les paragraphes suivants et consultez également [effet des Transactions sur les curseurs et les instructions préparées](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
 Si la valeur SQL_CURSOR_ROLLBACK_BEHAVIOR ou SQL_CURSOR_COMMIT_BEHAVIOR est égale à SQL_CB_DELETE, **SQLEndTran** ferme et supprime tous les curseurs ouverts sur toutes les instructions associées à la connexion et ignore tous les résultats en attente. **SQLEndTran** laisse n’importe quelle instruction présente dans un état alloué (annulé) ; l’application peut le réutiliser pour les demandes suivantes de SQL ou vous pouvez appeler **SQLFreeStmt** ou **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT pour libérer les.  
  
 Si la valeur SQL_CURSOR_ROLLBACK_BEHAVIOR ou SQL_CURSOR_COMMIT_BEHAVIOR est égale à SQL_CB_CLOSE, **SQLEndTran** ferme tous les curseurs ouverts sur toutes les instructions associées à la connexion. **SQLEndTran** laisse n’importe quelle instruction présente dans un état préparé ; l’application peut appeler **SQLExecute** pour une instruction associée à la connexion sans préalablement appeler **SQLPrepare**.  
  
 Si la valeur SQL_CURSOR_ROLLBACK_BEHAVIOR ou SQL_CURSOR_COMMIT_BEHAVIOR est égale à SQL_CB_PRESERVE, **SQLEndTran** n’affecte pas les curseurs ouverts associés à la connexion. Les curseurs restent à la ligne sur laquelle il pointe avant l’appel à **SQLEndTran**.  
  
 Pour les pilotes et sources de données qui prennent en charge des transactions, en appelant **SQLEndTran** avec SQL_COMMIT ou SQL_ROLLBACK quand aucune transaction n’est active retourne SQL_SUCCESS (indiquant qu’il n’existe aucune tâche à être validée ou restaurée) et n’a aucun effet sur la source de données.  
  
 Lorsqu’un pilote est en mode de validation automatique, le Gestionnaire de pilotes n’appelle pas **SQLEndTran** dans le pilote. **SQLEndTran** toujours retourne SQL_SUCCESS, indépendamment de si elle est appelée avec un *CompletionType* de SQL_COMMIT ou SQL_ROLLBACK.  
  
 Pilotes ou sources de données qui ne prennent pas en charge les transactions (**SQLGetInfo** *option* SQL_TXN_CAPABLE est SQL_TC_NONE) sont en fait toujours en mode autocommit et par conséquent retournent toujours SQL_SUCCESS pour **SQLEndTran** déterminant si elles sont appelées avec un *CompletionType* de SQL_COMMIT ou SQL_ROLLBACK. Ces pilotes et les sources de données ne pas réellement restaurer les transactions lors de la demande.  
  
## <a name="suspended-state"></a>État suspendu  
 Dans les gestionnaires de pilote qui ont été publié avant Windows 7, une transaction était active si **SQLEndTran** renvoyé SQL_ERROR à partir du pilote. Toutefois, il était possible que la transaction avait été validée avec succès sur le serveur, mais le pilote sur le client n’avait pas été notifié (par exemple, car une erreur réseau s’est produite). Ce qui ne permet la connexion dans un état incorrect. À partir de Windows 7, lorsque **SQLEndTran** retourne SQL_ERROR, la connexion peut être dans un état suspendu. Dans un état suspendu, il est possible d’appeler des fonctions en lecture seule. Finalement, l’application doit appeler **SQLDisconnect** sur une connexion interrompue pour libérer les ressources.  
  
 Si toutes les conditions suivantes sont remplies, la connexion est placée dans un état suspendu :  
  
-   Le pilote retourne SQL_ERROR à partir de **SQLEndTran**.  
  
-   Le pilote est ODBC 3.8, ou version ultérieure.  
  
-   La version de l’application est 3.8 ou ultérieur ; ou l’application de 2.x ou 3.x ODBC recompilée correctement annule le **SQLEndTran** fonctionner à travers **SQLCancelHandle**.  
  
-   Le pilote n’a pas retourné un des messages suivants, qui confirmer que la transaction n’a pas terminé :  
  
    -   25S03 : Restauration de transaction  
  
    -   40001: Échec de la sérialisation  
  
    -   40002: contrainte d’intégrité  
  
    -   HYC00 : Fonctionnalité optionnelle non implémentée  
  
 Si **SQLEndTran** a été appelée sur un environnement handle et une de ses connexions remplies les conditions ci-dessus, toutes les connexions se connectant au même pilote seront placées dans l’état suspendu.  
  
 Une fois une application appelle **SQLDisconnect** sur une connexion interrompue, la connexion peut être utilisée pour vous reconnecter à une autre source de données ou de la même source de données.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Annulation d’une fonction s’exécutant de façon asynchrone sur un handle de connexion.|[SQLCancelHandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Retour d’informations sur un pilote ou d’une source de données|[SQLGetInfo, fonction](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Libération d’un descripteur|[SQLFreeHandle, fonction](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Libération d’un descripteur d’instruction|[SQLFreeStmt, fonction](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
