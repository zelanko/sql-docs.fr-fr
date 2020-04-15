---
title: Transitions de déclarations Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transitioning states [ODBC], statement
- state transitions [ODBC], statement
- statement transitions [ODBC]
ms.assetid: 3d70e0e3-fe83-4b4d-beac-42c82495a05b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55f82e275bfd5bff12544b35a1370cdb31495320
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302850"
---
# <a name="statement-transitions"></a>Transitions d’instruction
Les déclarations de l’ODBC ont les états suivants.  
  
|State|Description|  
|-----------|-----------------|  
|S0|Déclaration non allouée. (L’état de connexion doit être C4, C5 ou C6. Pour plus d’informations, voir [Transitions de connexion](../../../odbc/reference/appendixes/connection-transitions.md).)|  
|S1|Déclaration allouée.|  
|S2|Déclaration préparée. Aucun ensemble de résultats ne sera créé.|  
|S3|Déclaration préparée. Un ensemble de résultats (peut-être vide) sera créé.|  
|S4|Déclaration exécutée et aucun ensemble de résultats n’a été créé.|  
|S5|L’énoncé exécuté et un ensemble de résultats (peut-être vide) ont été créés. Le curseur est ouvert et positionné avant la première rangée de l’ensemble de résultats.|  
|S6|Curseur positionné avec **SQLFetch** ou **SQLFetchScroll**.|  
|S7|Curseur positionné avec **SQLExtendedFetch**.|  
|S8|La fonction a besoin de données. **SQLParamData** n’a pas été appelé.|  
|S9|La fonction a besoin de données. **SQLPutData n’a** pas été appelé.|  
|S10|La fonction a besoin de données. **SQLPutData** a été appelé.|  
|S11|Toujours en train de s’exécuter. Une déclaration est laissée dans cet état après une fonction qui est exécutée asynchronement retourne SQL_STILL_EXECUTING. Une déclaration est temporairement dans cet état tandis que toute fonction qui accepte une poignée de déclaration est l’exécution. Résidence temporaire dans l’état S11 n’est pas indiqué dans les tables d’état, sauf la table d’état pour **SQLCancel**. Alors qu’une déclaration est temporairement dans l’état S11, la fonction peut être annulée en appelant **SQLCancel** à partir d’un autre thread.|  
|S12|Exécution asynchrone annulée. Dans S12, une application doit appeler la fonction annulée jusqu’à ce qu’elle retourne une valeur autre que SQL_STILL_EXECUTING. La fonction n’a été annulée avec succès que si la fonction retourne SQL_ERROR et SQLSTATE HY008 (Opération annulée). S’il renvoie une autre valeur, comme SQL_SUCCESS, l’opération d’annulation a échoué et la fonction exécutée normalement.|  
  
 Les États S2 et S3 sont connus sous le nom d’États préparés, états S5 à S7 comme états curseurs, États S8 à S10 comme états de données de besoin, et les états S11 et S12 comme les états asynchrones. Dans chacun de ces groupes, les transitions ne sont indiquées séparément que lorsqu’elles sont différentes pour chaque État du groupe; dans la plupart des cas, les transitions pour chaque État dans chaque groupe sont les mêmes.  
  
 Les tableaux suivants montrent comment chaque fonction ODBC affecte l’état de déclaration.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1], [5], [6]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[2], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|S1[3]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[4], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DESC.  
  
 [5] Appeler **SQLAllocHandle** avec *OutputHandlePtr* pointant vers une poignée valide surintés qui manipulent sans égard pour le contenu précédent à cette poignée et pourrait causer des problèmes pour les conducteurs ODBC. Il est incorrect ODBC programmation d’application d’appeler **SQLAllocHandle** deux fois avec la même variable d’application définie pour * \*OutputHandlePtr* sans appeler **SQLFreeHandle** pour libérer la poignée avant de la réaffecter. La suréscription des poignées ODBC d’une manière qui pourrait entraîner un comportement ou des erreurs incohérents de la part des conducteurs d’ODBC.  
  
## <a name="sqlbindcol"></a>SQLBindCol  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbindparameter"></a>SQLBindParameter  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbrowseconnect-sqlconnect-and-sqldriverconnect"></a>SQLBrowseConnect, SQLConnect et SQLDriverConnect  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|08002|08002|08002|08002|08002|08002|08002|  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations (SQLBulkOperations)  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|HY010|24 000|Voir la table suivante|HY010|NS [c] HY010 o|  
  
## <a name="sqlbulkoperations-cursor-states"></a>SQLBulkOperations (États Cursor)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|-- [s] S8 [d] S11 [x]|-- [s] S8 [d] S11 [x]|HY010|  
  
## <a name="sqlcancel"></a>SQLCancel  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|--|--|--|--|S1[1] S2 [nr] et [2] S3 [r]et [2] S5[3] et [5] S6 ([3] ou [4]) et [6] S7[4] et [7]|Voir la table suivante|  
  
 **SQLExecDirect** est retourné SQL_NEED_DATA.  
  
 [2] **SQLExecute** retourné SQL_NEED_DATA.  
  
 [3] **SQLBulkOperations** retourné SQL_NEED_DATA.  
  
 [4] **SQLSetPos** retourné SQL_NEED_DATA.  
  
 [5] **SQLFetch**, **SQLFetchScroll**, ou **SQLExtendedFetch** n’avait pas été appelé.  
  
 [6] **SQLFetch** ou **SQLFetchScroll** avait été appelé.  
  
 [7] **SQLExtendedFetch** avait été appelé.  
  
## <a name="sqlcancel-asynchronous-states"></a>SQLCancel (États asynchrones)  
  
|S11<br /><br /> Toujours en cours d’exécution|S12<br /><br /> Asynch annulé|  
|-----------------------------|-----------------------------|  
|NS[1] S12[2]|S12|  
  
 [1] La déclaration était temporairement dans l’état S11 pendant qu’une fonction était exécutée. **SQLCancel** a été appelé à partir d’un thread différent.  
  
 [2] La déclaration était dans l’état S11 parce qu’une fonction appelée asynchronement retourné SQL_STILL_EXECUTING.  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|24 000|24 000|24 000|S1 [np] S3 [p]|HY010|HY010|  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|Voir la table suivante|24 000|-- [s] S11 [x]|HY010|NS [c] HY010 o|  
  
## <a name="sqlcolattribute-prepared-states"></a>SQLColAttribute (États préparés)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|--[1] 07005[2]|-- [s] S11 x|  
  
 [1] *FieldIdentifier* a été SQL_DESC_COUNT.  
  
 [2] *FieldIdentifier n’était* pas SQL_DESC_COUNT.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges, et SQLTables  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S5 [s] S11 [x]|S1 [e] S5 [s] S11 [x]|S1 [e] et [1] S5 [s] et [1] S11 [x] et [1] 24000[2]|Voir la table suivante|HY010|NS [c] HY010 o|  
  
 [1] Le résultat actuel est le dernier ou le seul résultat, ou il n’y a pas de résultats actuels. Pour plus d’informations sur les résultats multiples, voir [résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] Le résultat actuel n’est pas le dernier résultat.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables-cursor-states"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges, et SQLTables (Cursor States)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24 000|24000[1]|24 000|  
  
 [1] Cette erreur est retournée par le gestionnaire du conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc (SQLCopyDesc)  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH[1]|--|--|--|--|HY010|NS [c] et [3] HY010 [o] ou [4]|  
|IH[2]|HY010|Voir la table suivante|24 000|-- [s] S11 x|HY010|NS [c] et [3] HY010 [o] ou [4]|  
  
 Cette ligne montre les transitions lorsque l’argument *sourceDescHandle* était un ARD, APD, ou IPD.  
  
 Cette ligne montre les transitions lorsque l’argument *de SourceDescHandle* était un IRD.  
  
 [3] Les arguments *sourceDescHandle* et *TargetDescHandle* étaient les mêmes que dans la fonction **SQLCopyDesc** qui fonctionne asynchronement.  
  
 [4] Soit l’argument *SourceDescHandle* ou l’argument *De TargetDescHandle* (ou les deux) étaient différents de ceux de la fonction **SQLCopyDesc** qui fonctionne asynchronement.  
  
## <a name="sqlcopydesc-prepared-states"></a>SQLCopyDesc (États préparés)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|24000[1]|-- [s] S11 [x]|  
  
 [1] Cette ligne montre les transitions lorsque l’argument *SourceDescHandle* était un IRD.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources et SQLDrivers  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqldescribecol"></a>SQLDescribeCol  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|Voir la table suivante|24 000|-- [s] S11 [x]|HY010|NS [c] HY010 o|  
  
## <a name="sqldescribecol-prepared-states"></a>SQLDescribeCol (États préparés)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|07005|-- [s] S11 [x]|  
  
## <a name="sqldescribeparam"></a>SQLDescribeParam  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|-- [s] S11 [x]|HY010|HY010|HY010|NS [c] HY010 [o]|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|S0[1]|S0[1]|S0[1]|S0[1]|(HY010)|(HY010)|  
  
 [1] Appeler **SQLDisconnect** libère toutes les déclarations associées à la connexion. En outre, cela renvoie l’état de connexion à C2; l’état de connexion doit être C4 avant que l’état de déclaration soit S0.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--[2] ou [3] S1[1]|--[3] S1 [np] et ([1] ou [2]) S1 [p] et [1] S2 [p] et [2]|--[3] S1 [np] et ([1] ou [2]) S1 [p] et [1] S3 [p] et [2]|(HY010)|(HY010)|  
  
 [1] *L’argument de CompletionType* est SQL_COMMIT et **SQLGetInfo** renvoie SQL_CB_DELETE pour le type d’information SQL_CURSOR_COMMIT_BEHAVIOR, ou l’argument *de CompletionType* est SQL_ROLLBACK et **SQLGetInfo** retourne SQL_CB_DELETE pour le type d’information SQL_CURSOR_ROLLBACK_BEHAVIOR.  
  
 [2] *L’argument de CompletionType* est SQL_COMMIT et **SQLGetInfo** renvoie SQL_CB_CLOSE pour le type d’information SQL_CURSOR_COMMIT_BEHAVIOR, ou l’argument *de CompletionType* est SQL_ROLLBACK et **SQLGetInfo** retourne SQL_CB_CLOSE pour le type d’information SQL_CURSOR_ROLLBACK_BEHAVIOR.  
  
 [3] *L’argument de CompletionType* est SQL_COMMIT et **SQLGetInfo** renvoie SQL_CB_PRESERVE pour le type d’information SQL_CURSOR_COMMIT_BEHAVIOR, ou l’argument *de CompletionType* est SQL_ROLLBACK et **SQLGetInfo** retourne SQL_CB_PRESERVE pour le type d’information SQL_CURSOR_ROLLBACK_BEHAVIOR.  
  
## <a name="sqlexecdirect"></a>SQLExecDirect  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S4 [s] et [nr] S5 [s] et [r] S8 [d] S11 [x]|-- [e] et [1] S1 [e] et [2] S4 [s] et [nr] S5 [s] et [r] S8 [d] S11 [x]|-- [e], [1], et [3] S1 [e], [2], et [3] S4 [s], [nr], et [3] S5 [s], [r], et [3] S8 [d] et [3] S11 [x] et [3] 24000 [4]|Voir la table suivante|HY010|NS [c] HY010 [o]|  
  
 [1] L’erreur a été retournée par le gestionnaire de conducteur.  
  
 [2] L’erreur n’a pas été retournée par le gestionnaire de conducteur.  
  
 [3] Le résultat actuel est le dernier ou le seul résultat, ou il n’y a pas de résultats actuels. Pour plus d’informations sur les résultats multiples, voir [résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] Le résultat actuel n’est pas le dernier résultat.  
  
## <a name="sqlexecdirect-cursor-states"></a>SQLExecDirect (États Cursor)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24 000|24000 [1]|24 000|  
  
 [1] Cette erreur est retournée par le gestionnaire de conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA, et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.  
  
## <a name="sqlexecute"></a>SQLExecute  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|Voir la table suivante|S2 [e], p, et [1] S4 [s], [p], [nr], et [1] S5 [s], [p], [r], et [1] S8 [d], [p], et [1] S11 [x], [p], et [1] 24000 [p] et [2] HY010 [np]|Voir la table des états curseur|HY010|NS [c] HY010 [o]|  
  
 [1] Le résultat actuel est le dernier ou le seul résultat, ou il n’y a pas de résultats actuels. Pour plus d’informations sur les résultats multiples, voir [résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] Le résultat actuel n’est pas le dernier résultat.  
  
## <a name="sqlexecute-prepared-states"></a>SQLExecute (États préparés)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|S4 [s] S8 [d] S11 [x]|S5 [s] S8 [d] S11 [x]|  
  
## <a name="sqlexecute-cursor-states"></a>SQLExecute (États Cursor)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000 [p] HY010 [np]|24000 [p], [1] HY010 [np]|24000 [p] HY010 [np]|  
  
 [1] Cette erreur est retournée par le gestionnaire de conducteur si **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_NO_DATA, et est retourné par le conducteur si **SQLFetch** ou **SQLFetchScroll** est retourné SQL_NO_DATA.  
  
## <a name="sqlextendedfetch"></a>SQLExtendedFetch  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|S1010|S1010|24 000|Voir la table suivante|S1010|NS [c] S1010 [o]|  
  
## <a name="sqlextendedfetch-cursor-states"></a>SQLExtendedFetch (États-Unis)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S7 [s] ou [nf] S11 [x]|S1010|-- [s] ou [nf] S11 [x]|  
  
## <a name="sqlfetch-and-sqlfetchscroll"></a>SQLFetch et SQLFetchScroll  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|HY010|24 000|Voir la table suivante|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlfetch-and-sqlfetchscroll-cursor-states"></a>SQLFetch et SQLFetchScroll (États Cursor)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S6 [s] ou [nf] S11 [x]|-- [s] ou [nf] S11 [x]|HY010|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|-- [1]|HY010|HY010|HY010|HY010|HY010|HY010|  
|IH [2]|S0|S0|S0|S0|HY010|HY010|  
|-- [3]|--|--|--|--|--|--|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV ou SQL_HANDLE_DBC.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DESC et le descripteur a été explicitement attribué.  
  
## <a name="sqlfreestmt"></a>SQLFreeStmt  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH [1]|--|--|S1 [np] S2 [p]|S1 [np] S3 [p]|HY010|HY010|  
|IH [2]|--|--|--|--|HY010|HY010|  
  
 Cette ligne montre les transitions quand *Option* était SQL_CLOSE.  
  
 Cette ligne montre les transitions lorsque *Option* était SQL_UNBIND ou SQL_RESET_PARAMS. Si l’argument *d’Option* a été SQL_DROP et que le conducteur sous-jacent est un conducteur ODBC 3 *.x,* le gestionnaire de conducteur en fait un appel à **SQLFreeHandle** avec *HandleType* prêt à SQL_HANDLE_STMT. Pour plus d’informations, consultez le tableau de transition de [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetcursorname"></a>SQLGetCursorName  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|--|--|--|--|HY010|HY010|  
  
## <a name="sqlgetdata"></a>SQLGetData  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|HY010|24 000|Voir la table suivante|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlgetdata-cursor-states"></a>SQLGetData (États Cursor)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24 000|-- [s] ou [nf] S11 [x] 24000 [b] HY109 [i]|-- [s] ou [nf] S11 [x] 24000 [b] HY109 [i]|  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField et SQLGetDescRec  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|-- [1] ou [2] HY010 [3]|Voir la table suivante|-- [1] ou [2] 24000 [3]|-- [1], [2], ou [3] S11 [3] et [x]|HY010|NS [c] ou [4] HY010 [o] et [5]|  
  
 [1] *L’argument de DescriptorHandle* était un APD ou ARD.  
  
 [2] *L’argument de DescriptorHandle* était un IPD.  
  
 [3] *L’argument de DescriptorHandle* était un IRD.  
  
 [4] *L’argument de DescriptorHandle* était le même que l’argument *de DescriptorHandle* dans la fonction **SQLGetDescField** ou **SQLGetDescRec** qui fonctionne asynchronement.  
  
 [5] *L’argument de DescriptorHandle* était différent de *l’argument de DescriptorHandle* dans la fonction **SQLGetDescField** ou **SQLGetDescRec** qui fonctionne asynchronement.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec-prepared-states"></a>SQLGetDescField et SQLGetDescRec (États préparés)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|--[1], [2], ou [3] S11[2] et [x]|--[1], [2], ou [3] S11 [x]|  
  
 [1] *L’argument de DescriptorHandle* était un APD ou ARD.  
  
 [2] *L’argument de DescriptorHandle* était un IPD.  
  
 [3] *L’argument de DescriptorHandle* était un IRD. Notez que ces fonctions reviennent toujours SQL_NO_DATA dans l’état S2 lorsque *DescriptorHandle* était un IRD.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField et SQLGetDiagRec  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--|--|--|  
|IH[2]|--[3]|--[3]|--|--|--[3]|--[3]|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV, SQL_HANDLE_DBC ou SQL_HANDLE_DESC.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT.  
  
 [3] **SQLGetDiagField** retourne toujours une erreur dans cet état lorsque *DiagIdentifier* est SQL_DIAG_ROW_COUNT.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|--[1] 24000[2]|--[1] 24000[2]|--[1] 24000[2]|Voir la table suivante|HY010|HY010|  
  
 [1] L’attribut de déclaration n’était pas SQL_ATTR_ROW_NUMBER.  
  
 [2] L’attribut de déclaration était SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlgetstmtattr-cursor-states"></a>SQLGetStmtAttr (États Cursor)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--[1] 24000[2]|--[1] ou ([v] et [2]) 24000 [b] et [2] HY109 [i] et [2]|-- [i] ou ([v] et [2]) 24000 [b] et [2] HY109[1] et [2]|  
  
 [1] *L’argument d’attribut n’était* pas SQL_ATTR_ROW_NUMBER.  
  
 [2] *L’argument d’attribut* était SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|--[1]|--[1]|-- [s] et [2] S1 [nf], [np], et [4] S2 [nf], [p], et [4] S5 [s] et [3] S11 [x]|S1 [nf], [np], et [4] S3 [nf], [p] et [4] S4 [s] et [2] S5 [s] et [3] S11 [x]|HY010|NS [c] HY010 [o]|  
  
 [1] La fonction retourne toujours SQL_NO_DATA dans cet état.  
  
 [2] Le résultat suivant est un décompte des lignes.  
  
 [3] Le prochain résultat est un ensemble de résultats.  
  
 [4] Le résultat actuel est le dernier résultat.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlnumparams"></a>SQLNumParams  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|-- [s] S11 [x]|-- [s] S11 [x]|-- [s] S11 [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlnumresultcols"></a>SQLNumResultCols  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|-- [s] S11 [x]|-- [s] S11 [x]|-- [s] S11 [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata"></a>SQLParamData  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|HY010|HY010|HY010|Voir la table suivante|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata-need-data-states"></a>SQLParamData (États de données des besoins)  
  
|S8<br /><br /> Besoin de données|S9<br /><br /> Doit mettre|S10<br /><br /> Peut mettre|  
|----------------------|---------------------|---------------------|  
|S1 [e] et [1] S2 [e], [nr], et [2] S3 [e], [r], et [2] S5 [e] et [4] S6 [e] et [5] S7 [e] et [3] S9 [d] S11 [x]|HY010|S1 [e] et [1] S2 [n], [nr], et [2] S3 [e], [r], et [2] S4 [s], [nr], et ([1] ou [2]) S5 [s], [r], et ([1] ou [2]) S5 ([s] ou [e]) et [4] S6 ([s] ou [e]) et [5] S7 ([s] ou [e]) et [3] S9 [d] S11 [x]|  
  
 **SQLExecDirect** est retourné SQL_NEED_DATA.  
  
 [2] **SQLExecute** retourné SQL_NEED_DATA.  
  
 [3] **SQLSetPos** avait été appelé de l’état S7 et retourné SQL_NEED_DATA.  
  
 [4] **SQLBulkOperations** avait été appelé de l’état S5 et retourné SQL_NEED_DATA.  
  
 [5] **SQLSetPos** ou **SQLBulkOperations** avaient été appelés de l’état S6 et retourné SQL_NEED_DATA.  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S2 [s] et [nr] S3 [s] et [r] S11 [x]|-- [s] ou ([e] et [1]) S1 [e] et [2] S11 [x]|S1 [e] et [3] S2 [s], [nr], et [3] S3 [s], [r], et [3] S11 [x] et [3] 24000[4]|Voir la table suivante|HY010|NS [c] HY010 [o]|  
  
 [1] La préparation échoue pour une raison autre que la validation de la déclaration (le SQLSTATE était HY009 [valeur de l’argument invalide] ou HY090 [longueur de chaîne ou tampon invalide]).  
  
 [2] La préparation échoue en validant la déclaration (le SQLSTATE n’était pas HY009 [valeur d’argument invalide] ou HY090 [longueur de chaîne ou tampon invalide]).  
  
 [3] Le résultat actuel est le dernier ou le seul résultat, ou il n’y a pas de résultats actuels. Pour plus d’informations sur les résultats multiples, voir [résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] Le résultat actuel n’est pas le dernier résultat.  
  
## <a name="sqlprepare-cursor-states"></a>SQLPrepare (États Cursor)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24 000|24 000|24 000|  
  
## <a name="sqlputdata"></a>SQLPutData  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|HY010|HY010|HY010|Voir la table suivante|NS [c] HY010 [o]|  
  
## <a name="sqlputdata-need-data-states"></a>SQLPutData (États de données des besoins)  
  
|S8<br /><br /> Besoin de données|S9<br /><br /> Doit mettre|S10<br /><br /> Peut mettre|  
|----------------------|---------------------|---------------------|  
|HY010|S1 [e] et [1] S2 [e], [nr], et [2] S3 [e], [r], et [2] S5 [e] et [4] S6 [e] et [5] S7 [e] et [3] S10 [s] S11 [x]|-- [s] S1 [e] et [1] S2 [e], [nr], et [2] S3 [e], [r], et [2] S5 [e] et [4] S6 [e] et [5] S7 [e] et [3] S11 [x] HY011[6]|  
  
 **SQLExecDirect** est retourné SQL_NEED_DATA.  
  
 [2] **SQLExecute** retourné SQL_NEED_DATA.  
  
 [3] **SQLSetPos** avait été appelé de l’état S7 et retourné SQL_NEED_DATA.  
  
 [4] **SQLBulkOperations** avait été appelé de l’état S5 et retourné SQL_NEED_DATA.  
  
 [5] **SQLSetPos** ou **SQLBulkOperations** avaient été appelés de l’état S6 et retourné SQL_NEED_DATA.  
  
 [6] Un ou plusieurs appels à **SQLPutData** pour un seul paramètre retourné SQL_SUCCESS, puis un appel à **SQLPutData** a été faite pour le même paramètre avec *StrLen_or_Ind* réglé pour SQL_NULL_DATA.  
  
## <a name="sqlrowcount"></a>SQLRowCount  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|(HY010)|--|--|(HY010)|(HY010)|  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--[2] 24000[3]|HY010|HY010|  
  
 Cette ligne montre les transitions lorsque *l’attribut* était un attribut de connexion. Pour les transitions lorsque *l’attribut* était un attribut de déclaration, voir le tableau de transition de l’instruction pour **SQLSetStmtAttr**.  
  
 [2] *L’argument d’attribut n’était* pas SQL_ATTR_CURRENT_CATALOG.  
  
 [3] *L’argument d’attribut* était SQL_ATTR_CURRENT_CATALOG.  
  
## <a name="sqlsetcursorname"></a>SQLSetCursorName  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|--|--|24 000|24 000|HY010|HY010|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField et SQLSetDescRec  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH[1]|--|--|--|--|HY010|HY010|  
  
 Cette ligne montre des transitions où *l’argument de DescriptorHandle* est un ARD, APD, IPD, ou (pour **SQLSetDescField**) un IRD lorsque *l’argument FieldIdentifier* est SQL_DESC_ARRAY_STATUS_PTR ou SQL_DESC_ROWS_PROCESSED_PTR. C’est une erreur d’appeler **SQLSetDescField** pour un IRD lorsque *FieldIdentifier* est toute autre valeur.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|HY011 HY011|HY011 HY011|HY011 HY011|HY011 HY011|Y011 (en)|HY01 (HY01)|HY011 HY011|  
  
## <a name="sqlsetpos"></a>SQLSetPos  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|HY010|HY010|24 000|Voir la table suivante|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlsetpos-cursor-states"></a>SQLSetPos (États Cursor)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24 000|-- [s] S8 [d] S11 [x] 24000 [b] HY109 [i]|-- [s] S8 [d] S11 [x] 24000 [b] HY109 [i]|  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> Allocated|S2-S3<br /><br /> Prepared|S4<br /><br /> Exécuté|S5-S7<br /><br /> Curseur|S8-S10<br /><br /> Besoin de données|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|Ih|--|--[1] HY011[2]|--[1] 24000[2]|--[1] 24000[2]|HY010 [np] ou [1] HY011 [p] et [2]|HY010 [np] ou [1] HY011 [p] et [2]|  
  
 [1] *L’argument d’attribut n’était* pas SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE ou SQL_ATTR_CURSOR_SENSITIVITY.  
  
 [2] *L’argument d’attribut* était SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE, ou SQL_ATTR_CURSOR_SENSITIVITY.
