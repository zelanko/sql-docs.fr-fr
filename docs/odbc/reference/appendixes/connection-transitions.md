---
title: Transitions de connexion | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46d480683a2d10f760a02049ab28bc590353fcbf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47619097"
---
# <a name="connection-transitions"></a>Transitions de connexion
Connexions ODBC ont les états suivants.  
  
|État|Description|  
|-----------|-----------------|  
|C0|Environnement non alloué, non alloué de connexion|  
|C1|Environnement alloué, non alloué de connexion|  
|C2|Allouée d’environnement, allouée de connexion|  
|C3|Fonction de la connexion a besoin de données|  
|C4|Connexion connectée|  
|C5|Connecté connexion, allouée d’instruction|  
|C6|Connexion connectée, la transaction en cours. Il est possible pour une connexion est dans un état C6 sans instructions allouées sur la connexion. Par exemple, supposons que la connexion est en mode de validation manuelle et est dans un état C4. Si une instruction est allouée, exécutée (démarrage d’une transaction) et ensuite libérée, la transaction reste active, mais il en existe pas d’instructions sur la connexion.|  
  
 Les tableaux suivants indiquent comment chaque fonction ODBC affecte l’état de connexion.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|C0<br /><br /> Aucun Env.|C1 non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|--------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|C1 [1]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(IH) [2]|C2|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(IH) [3]|(IH)|(08003)|(08003)|C5|--[5]|--[5]|  
|(IH) [4]|(IH)|(08003)|(08003)|--[5]|--[5]|--[5]|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_STMT.  
  
 [4] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DESC.  
  
 [5] appel **SQLAllocHandle** avec *OutputHandlePtr* pointant vers un handle valide remplace ce handle sans tenir compte pour le handle d’ofthat contenu précédent et peut entraîner des problèmes pour les pilotes ODBC. Il s’agit de la programmation d’applications ODBC incorrecte pour appeler **SQLAllocHandle** à deux reprises avec la même variable d’application définie pour  *\*OutputHandlePtr* sans appeler  **SQLFreeHandle** pour libérer le handle avant de réallouer. Remplacement ODBC gère de manière peut entraîner un comportement incohérent ou erreur de la part des pilotes ODBC.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C4 de C3 [d] [s]|--C2 [d] [e] C4 [s]|(08002)|(08002)|(08002)|  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--|--C5 [1] [2]|  
  
 [1] la connexion était en mode de validation manuelle.  
  
 [2] la connexion était en mode de validation automatique.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges et SQLTables  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--C6 [1] [2]|--|  
  
 [1] la connexion était en mode de validation automatique, ou la source de données n’a pas commencé une transaction.  
  
 [2] la connexion était en mode de validation manuelle, et la source de données a commencé une transaction.  
  
## <a name="sqlconnect"></a>SQLConnect  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C4|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlcopydesc-sqlgetdescfield-sqlgetdescrec-sqlsetdescfield-and-sqlsetdescrec"></a>SQLCopyDesc, SQLGetDescField, SQLGetDescRec, SQLSetDescField et SQLSetDescRec  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|--[1]|--|--|  
  
 [1] dans cet état, les descripteurs uniquement disponibles pour l’application sont alloués explicitement les descripteurs.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources et SQLDrivers  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|--|--|--|--|--|--|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(08003)|C2|C2|C2|25000|  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|S C4--n [f]|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|--[3]|--[3]|--[3]|--|--|--[4] ou ([5], [6] et [8]) C4 [5] et [7] C5 [5], [6] et [9]|  
|(IH) [2]|(IH)|(08003)|(08003)|--|--|C5|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DBC.  
  
 [3], car la connexion n’est pas dans un état connecté, il n’affecte pas la transaction.  
  
 [4] de la validation ou de restauration a échoué sur la connexion. La fonction retourne SQL_ERROR dans ce cas.  
  
 [5] le commit ou rollback a réussi sur la connexion. La fonction retourne SQL_ERROR si la validation ou restauration a échoué sur une autre connexion, ou la fonction retourne SQL_SUCCESS, si la validation ou restauration a réussi sur toutes les connexions.  
  
 [6] est survenu au moins une instruction allouée sur la connexion.  
  
 [7] se sont produites aucune instruction allouée sur la connexion.  
  
 [8] la connexion a au moins une instruction pour laquelle il a été un curseur ouvert, et la source de données conserve les curseurs lorsque les transactions sont validées ou annulées, selon le cas (selon que *CompletionType* a été SQL_ VALIDER ou SQL_ROLLBACK). Pour plus d’informations, voir les attributs SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 [9] si la connexion a toutes les instructions pour lequel ont été les curseurs ouverts, les curseurs non préservées lors de la transaction a été validée ou restaurée.  
  
## <a name="sqlexecdirect-and-sqlexecute"></a>SQLExecDirect et SQLExecute  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--C6 DE C6 [1] [2] [3]|--|  
  
 [1] la connexion était en mode de validation automatique, et l’instruction d’exécution n’était pas un *curseur* *spécification* (par exemple, une instruction SELECT) ; ou la connexion a été en mode de validation manuelle, l’instruction exécutée n’a pas commencé une transaction.  
  
 [2] la connexion était en mode de validation automatique, et l’instruction exécutée a été un *curseur* *spécification* (par exemple, une instruction SELECT).  
  
 [3] la connexion était en mode de validation manuelle, et la source de données a commencé une transaction.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|C0|(HY010)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(IH) [2]|(IH)|(C1)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(IH) [3]|(IH)|(IH)|(IH)|(IH)|C4 [5], [6]|--C4 [7] [5] et [8] C5 [6] et [8]|  
|(IH) [4]|(IH)|(IH)|(IH)|--|--|--|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_STMT.  
  
 [4] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DESC.  
  
 [5], il ne était qu’une seule instruction allouée sur la connexion.  
  
 [6] ont été allouées sur la connexion de plusieurs instructions.  
  
 [7] la connexion était en mode de validation manuelle.  
  
 [8] la connexion était en mode de validation automatique.  
  
## <a name="sqlfreestmt"></a>SQLFreeStmt  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|(IH)|(IH)|(IH)|(IH)|--|C5 [3] : [4]|  
|(IH) [2]|(IH)|(IH)|(IH)|(IH)|--|--|  
  
 [1] cette ligne affiche les transactions lorsque la *Option* argument est SQL_CLOSE.  
  
 [2] cette ligne affiche les transactions lorsque la *Option* argument soit SQL_UNBIND SQL_RESET_PARAMS.  
  
 [3] la connexion était en mode de validation automatique, et aucun curseur n’était ouverts sur toutes les instructions à l’exception de celui-ci.  
  
 [4] de la connexion était en mode de validation manuelle, ou il était en mode de validation automatique, et un curseur a été ouvert au moins une autre instruction.  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003[2]|HY010|--|--|--|  
  
 [1] le *attribut* argument a été SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, sql_attr_login_timeout permet de contrôler, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE ou SQL_ATTR_TRACEFILE, ou une valeur a été définie pour l’attribut de connexion.  
  
 [2] le *attribut* argument n’était pas SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, sql_attr_login_timeout permet de contrôler, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE ou SQL_ATTR_TRACEFILE, et une valeur n’a pas été définie pour la connexion attribut.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagRec et SQLGetDiagField  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|--|--|--|--|--|--|  
|(IH) [2]|(IH)|--|--|--|--|--|  
|(IH) [3]|(IH)|(IH)|(IH)|(IH)|--|--|  
|(IH) [4]|(IH)|(IH)|(IH)|--|--|--|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_STMT.  
  
 [4] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|HY010|HY010|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003[2]|08003|--|--|--|  
  
 [1] le *InfoType* SQL_ODBC_VER a été l’argument.  
  
 [2] le *InfoType* argument n’a pas été SQL_ODBC_VER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--C6 [1] [2]|--C5 [3] [1]|  
  
 [1] la connexion a été en mode de validation automatique et l’appel à **SQLMoreResults** n’a pas initialisé le traitement d’un jeu de résultats d’une spécification de curseur.  
  
 [2] de la connexion a été en mode de validation automatique et l’appel à **SQLMoreResults** a initialisé le traitement d’un jeu de résultats d’une spécification de curseur.  
  
 [3] la connexion était en mode de validation manuelle.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(08003)|(08003)|--|--|--|  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--C6 [1] [2]|--|  
  
 [1] la connexion était en mode de validation automatique, ou la source de données n’a pas commencé une transaction.  
  
 [2] la connexion était en mode manuel – commit, et la source de données a commencé une transaction.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003[2]|HY010|--08002 [3] [4] HY011 [5]|--08002 [3] [4] HY011 [5]|--[3] et [6] C5 [8] 08002 [4] HY011 [5] ou [7]|  
  
 [1] le *attribut* argument n’était pas SQL_ATTR_TRANSLATE_LIB ou SQL_ATTR_TRANSLATE_OPTION.  
  
 [2] le *attribut* argument a été SQL_ATTR_TRANSLATE_LIB ou SQL_ATTR_TRANSLATE_OPTION.  
  
 [3] le *attribut* argument n’était pas SQL_ATTR_ODBC_CURSORS ou SQL_ATTR_PACKET_SIZE.  
  
 [4] le *attribut* SQL_ATTR_ODBC_CURSORS a été l’argument.  
  
 [5] le *attribut* argument a été SQL_ATTR_PACKET_SIZE.  
  
 [6] le *attribut* argument n’a pas été SQL_ATTR_AUTOCOMMIT, ou le *attribut* argument était SQL_ATTR_AUTOCOMMIT et si cet attribut n’a pas validé la transaction.  
  
 [7] le *attribut* argument était SQL_ATTR_TXN_ISOLATION.  
  
 [8] le *attribut* argument était SQL_ATTR_AUTOCOMMIT, et si cet attribut a validé la transaction.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|--|--|(HY010)|--|--|--|  
  
## <a name="all-other-odbc-functions"></a>Toutes les autres fonctions ODBC  
  
|C0<br /><br /> Aucun Env.|C1<br /><br /> Non alloué|C2<br /><br /> allouée|C3<br /><br /> Besoin de données|C4<br /><br /> Connecté|C5<br /><br /> .|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--|--|
