---
title: Transitions de connexions (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transitioning states [ODBC], connection
- connection transitions [ODBC]
- state transitions [ODBC], connection
ms.assetid: 6b6e1a47-4a52-41c8-bb9e-7ddeae09913e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 225f8517a78f8e9d4d765163649da174d72e490c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284769"
---
# <a name="connection-transitions"></a>Transitions de connexion
Les connexions ODBC ont les états suivants.  
  
|State|Description|  
|-----------|-----------------|  
|C0|Environnement non alloué, connexion non allouée|  
|C1|Environnement alloué, connexion non allouée|  
|C2|Environnement alloué, connexion allouée|  
|C3|La fonction de connexion a besoin de données|  
|C4|Connexion connectée|  
|C5|Connexion connectée, relevé attribué|  
|C6|Connexion connectée, transaction en cours. Il est possible qu’une connexion soit en état C6 sans déclarations allouées sur la connexion. Supposons, par exemple, que la connexion soit en mode de validation manuelle et qu’elle soit en état C4. Si une déclaration est attribuée, exécutée (à partir d’une transaction), puis libérée, la transaction reste active mais il n’y a pas d’instructions sur la connexion.|  
  
 Les tableaux suivants montrent comment chaque fonction ODBC affecte l’état de connexion.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|C0<br /><br /> Pas d’Env.|C1 Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|--------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|C1[1]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(IH) [2]|C2|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(IH) [3]|(IH)|(08003)|(08003)|C5|--[5]|--[5]|  
|(IH) [4]|(IH)|(08003)|(08003)|--[5]|--[5]|--[5]|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DESC.  
  
 [5] Appeler **SQLAllocHandle** avec *OutputHandlePtr* pointant vers une poignée valide surintés qui manipulent sans égard pour le contenu précédent de cette poignée, et pourrait causer des problèmes pour les conducteurs ODBC. Il est incorrect ODBC programmation d’application d’appeler **SQLAllocHandle** deux fois avec la même variable d’application définie pour * \*OutputHandlePtr* sans appeler **SQLFreeHandle** pour libérer la poignée avant de la réaffecter. La suréscription des poignées ODBC d’une manière qui peut entraîner un comportement incohérent ou des erreurs de la part des conducteurs d’ODBC.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C3 [d] C4 [s]|-- [d] C2 [e] C4 [s]|(08002)|(08002)|(08002)|  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--|--[1] C5[2]|  
  
 [1] La connexion était en mode de validation manuelle.  
  
 [2] La connexion était en mode auto-commit.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges, et SQLTables  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--[1] C6[2]|--|  
  
 [1] La connexion était en mode auto-commit, ou la source de données n’a pas commencé une transaction.  
  
 [2] La connexion était en mode de validation manuelle, et la source de données a commencé une transaction.  
  
## <a name="sqlconnect"></a>SQLConnect  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C4|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlcopydesc-sqlgetdescfield-sqlgetdescrec-sqlsetdescfield-and-sqlsetdescrec"></a>SQLCopyDesc, SQLGetDescField, SQLGetDescRec, SQLSetDescField, et SQLSetDescRec  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|--[1]|--|--|  
  
 [1] Dans cet état, les seuls descripteurs disponibles à la demande sont des descripteurs explicitement attribués.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources et SQLDrivers  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|--|--|--|--|--|--|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(08003)|C2|C2|C2|25000|  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C4 s -- n[f]|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|--[3]|--[3]|--[3]|--|--|--[4] ou ([5], [6], et [8]) C4[5] et [7] C5[5], [6], et [9]|  
|(IH) [2]|(IH)|(08003)|(08003)|--|--|C5|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] Parce que la connexion n’est pas dans un état connecté, elle n’est pas affectée par la transaction.  
  
 [4] Le commit ou le recul a échoué sur la connexion. La fonction renvoie SQL_ERROR dans ce cas.  
  
 [5] L’engagement ou le recul a réussi sur la connexion. La fonction renvoie SQL_ERROR si l’engagement ou le recul a échoué sur une autre connexion, ou la fonction retourne SQL_SUCCESS si le commit ou le recul a réussi sur toutes les connexions.  
  
 [6] Il y avait au moins une déclaration allouée sur la connexion.  
  
 [7] Il n’y avait pas de déclarations allouées sur le lien.  
  
 [8] La connexion avait au moins une déclaration pour laquelle il y avait un curseur ouvert, et la source de données préserve les curseurs lorsque les transactions sont engagées ou annulées, selon la question de savoir si *CompletionType* était SQL_COMMIT ou SQL_ROLLBACK). Pour plus d’informations, consultez les attributs SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 [9] Si la connexion avait des relevés pour lesquels il y avait des curseurs ouverts, les curseurs n’ont pas été conservés lorsque la transaction a été commise ou annulée.  
  
## <a name="sqlexecdirect-and-sqlexecute"></a>SQLExecDirect et SQLExecute  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--[1] C6[2] C6[3]|--|  
  
 [1] La connexion était en mode auto-commit, et la déclaration exécutée n’était pas une *spécification* *de curseur* (comme une déclaration SELECT); ou la connexion était en mode de validation manuelle, et la déclaration exécutée n’a pas commencé une transaction.  
  
 [2] La connexion était en mode auto-commit, et la déclaration exécutée était une *spécification* *de curseur* (comme une déclaration SELECT).  
  
 [3] La connexion était en mode de validation manuelle, et la source de données a commencé une transaction.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|C0|(HY010)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(IH) [2]|(IH)|(C1)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(IH) [3]|(IH)|(IH)|(IH)|(IH)|C4[5] --[6]|--[7] C4[5] et [8] C5[6] et [8]|  
|(IH) [4]|(IH)|(IH)|(IH)|--|--|--|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DESC.  
  
 [5] Il n’y avait qu’une seule déclaration allouée sur la connexion.  
  
 [6] Il y avait plusieurs déclarations allouées sur la connexion.  
  
 [7] La connexion était en mode de validation manuelle.  
  
 [8] La connexion était en mode auto-commit.  
  
## <a name="sqlfreestmt"></a>SQLFreeStmt  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|(IH)|(IH)|(IH)|(IH)|--|C5[3] --[4]|  
|(IH) [2]|(IH)|(IH)|(IH)|(IH)|--|--|  
  
 Cette ligne montre les transactions lorsque l’argument *d’Option* est SQL_CLOSE.  
  
 [2] Cette ligne montre les transactions lorsque *l’argument d’option* est SQL_UNBIND ou SQL_RESET_PARAMS.  
  
 [3] La connexion était en mode auto-commit, et aucun curseur n’était ouvert sur n’importe quelle déclaration excepté celle-ci.  
  
 [4] La connexion était en mode de validation manuelle, ou elle était en mode auto-commit et un curseur était ouvert sur au moins une autre déclaration.  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|Ih|Ih|--[1] 08003[2]|HY010|--|--|--|  
  
 [1] *L’argument d’attribut* était SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE ou SQL_ATTR_TRACEFILE, ou une valeur avait été fixée pour l’attribut de connexion.  
  
 [2] *L’argument d’attribut n’était* pas SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE ou SQL_ATTR_TRACEFILE, et une valeur n’avait pas été fixée pour l’attribut de connexion.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField et SQLGetDiagRec  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|--|--|--|--|--|--|  
|(IH) [2]|(IH)|--|--|--|--|--|  
|(IH) [3]|(IH)|(IH)|(IH)|(IH)|--|--|  
|(IH) [4]|(IH)|(IH)|(IH)|--|--|--|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|Ih|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|Ih|Ih|HY010|HY010|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|Ih|Ih|--[1] 08003[2]|08003|--|--|--|  
  
 [1] L’argument *InfoType* était SQL_ODBC_VER.  
  
 [2] L’argument *d’InfoType* n’était pas SQL_ODBC_VER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--[1] C6[2]|--[3] C5[1]|  
  
 [1] La connexion était en mode auto-commit, et l’appel à **SQLMoreResults** n’a pas para parasité le traitement d’un ensemble de résultats d’un cahier des fonctions cursor.  
  
 [2] La connexion était en mode auto-commit, et l’appel à **SQLMoreResults** a para parasité le traitement d’un ensemble de résultats d’un cahier des fonctions cursor.  
  
 [3] La connexion était en mode de validation manuelle.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(08003)|(08003)|--|--|--|  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--[1] C6[2]|--|  
  
 [1] La connexion était en mode auto-commit, ou la source de données n’a pas commencé une transaction.  
  
 [2] La connexion était en mode de validation manuelle, et la source de données a commencé une transaction.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|Ih|Ih|--[1] 08003[2]|HY010|--[3] 08002[4] hy011[5]|--[3] 08002[4] hy011[5]|--[3] et [6] C5[8] 08002[4] HY011[5] ou [7]|  
  
 [1] *L’argument d’attribut n’était* pas SQL_ATTR_TRANSLATE_LIB ou SQL_ATTR_TRANSLATE_OPTION.  
  
 [2] *L’argument d’attribut* était SQL_ATTR_TRANSLATE_LIB ou SQL_ATTR_TRANSLATE_OPTION.  
  
 [3] *L’argument d’attribut n’était* pas SQL_ATTR_ODBC_CURSORS ou SQL_ATTR_PACKET_SIZE.  
  
 [4] *L’argument d’attribut* était SQL_ATTR_ODBC_CURSORS.  
  
 [5] *L’argument d’attribut* était SQL_ATTR_PACKET_SIZE.  
  
 [6] *L’argument d’attribut n’était* pas SQL_ATTR_AUTOCOMMIT, ou *l’argument d’attribut* était SQL_ATTR_AUTOCOMMIT et le réglage de cet attribut n’a pas commis la transaction.  
  
 [7] *L’argument d’attribut* était SQL_ATTR_TXN_ISOLATION.  
  
 [8] *L’argument d’attribut* était SQL_ATTR_AUTOCOMMIT, et le réglage de cet attribut a commis la transaction.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|--|--|(HY010)|--|--|--|  
  
## <a name="all-other-odbc-functions"></a>Toutes les autres fonctions ODBC  
  
|C0<br /><br /> Pas d’Env.|C1<br /><br /> Non alloué|C2<br /><br /> Allocated|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--|--|
