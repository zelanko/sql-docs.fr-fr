---
title: Transitions d’instruction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df4a73890841b4a72dbffa0d5a5ae934bf618f16
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649840"
---
# <a name="statement-transitions"></a>Transitions d’instruction
Instructions ODBC ont les états suivants.  
  
|État|Description|  
|-----------|-----------------|  
|S0|Instruction non allouée. (L’état de connexion doit être C4, C5 ou C6. Pour plus d’informations, consultez [connexion Transitions](../../../odbc/reference/appendixes/connection-transitions.md).)|  
|S1|Instruction allouée.|  
|S2|Instruction préparée. Aucun jeu de résultats n’est créé.|  
|S3|Instruction préparée. Un jeu de résultats (éventuellement vide) est créé.|  
|S4|Instruction d’exécution et aucun jeu de résultats a été créé.|  
|S5|Instruction d’exécution et un jeu de résultats (éventuellement vide) a été créé. Le curseur est ouvert et positionné avant la première ligne du jeu de résultats.|  
|S6|Curseur positionné avec **SQLFetch** ou **SQLFetchScroll**.|  
|S7|Curseur positionné avec **SQLExtendedFetch**.|  
|S8|Fonction a besoin de données. **SQLParamData** n’a pas été appelée.|  
|S9|Fonction a besoin de données. **SQLPutData** n’a pas été appelée.|  
|S10|Fonction a besoin de données. **SQLPutData** a été appelée.|  
|S11|En cours d’exécution. Une instruction reste dans cet état après qu’une fonction qui est exécutée de façon asynchrone retourne SQL_STILL_EXECUTING. Une instruction est temporairement dans cet état lors de n’importe quelle fonction qui accepte qu'un descripteur d’instruction est en cours d’exécution. Séjour dans un état S11 n’est pas affiché dans les tables d’état à l’exception de la table d’état pour **SQLCancel**. Pendant qu’une instruction est temporairement en état S11, la fonction peut être annulée en appelant **SQLCancel** à partir d’un autre thread.|  
|S12|Exécution asynchrone annulée. Dans S12, une application doit appeler la fonction a été annulée jusqu'à ce qu’elle retourne une valeur différente de SQL_STILL_EXECUTING. La fonction a été annulée avec succès uniquement si la fonction retourne SQL_ERROR et SQLSTATE HY008 (opération annulée). Si elle renvoie une autre valeur, tels que SQL_SUCCESS, l’opération d’annulation a échoué et la fonction exécutée normalement.|  
  
 États de S5 via S7 États S2 et S3 sont appelés les États préparées, comme le curseur États, États S8 via S10 en tant que les États de données nécessaire et les États asynchrones aux États S11 et S12. Dans chacun de ces groupes, les transitions sont affichées séparément uniquement lorsqu’ils sont différents pour chaque état du groupe. dans la plupart des cas, les transitions pour chaque état dans chacun un groupe sont les mêmes.  
  
 Les tableaux suivants indiquent comment chaque fonction ODBC affecte l’état de l’instruction.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1], [5], [6]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[2], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|S1 [3]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[4], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_STMT.  
  
 [4] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DESC.  
  
 [5] appel **SQLAllocHandle** avec *OutputHandlePtr* pointant vers un handle valide remplace ce handle sans tenir compte pour le contenu précédent pour qui gérer et peut entraîner des problèmes pour les pilotes ODBC. Il s’agit de la programmation d’applications ODBC incorrecte pour appeler **SQLAllocHandle** à deux reprises avec la même variable d’application définie pour  *\*OutputHandlePtr* sans appeler  **SQLFreeHandle** pour libérer le handle avant de réallouer. Remplacement ODBC gère de manière peut entraîner un comportement incohérent ou erreur de la part des pilotes ODBC.  
  
## <a name="sqlbindcol"></a>SQLBindCol  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbindparameter"></a>SQLBindParameter  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbrowseconnect-sqlconnect-and-sqldriverconnect"></a>SQLBrowseConnect, SQLConnect et SQLDriverConnect  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|08002|08002|08002|08002|08002|08002|08002|  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24000|Consultez le tableau suivant|HY010|O de HY010 NS [c]|  
  
## <a name="sqlbulkoperations-cursor-states"></a>SQLBulkOperations (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--S8 [s] [d] S11 [x]|--S8 [s] [d] S11 [x]|HY010|  
  
## <a name="sqlcancel"></a>SQLCancel  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|S1 [1] S2 [nr] et [2] S3 [r] et S5 [2] [3] et [5] S6 ([3] ou [4]) et [6] S7 [4] et [7]|Consultez le tableau suivant|  
  
 [1] **SQLExecDirect** retourné SQL_NEED_DATA.  
  
 [2] **SQLExecute** retourné SQL_NEED_DATA.  
  
 [3] **SQLBulkOperations** retourné SQL_NEED_DATA.  
  
 [4] **SQLSetPos** retourné SQL_NEED_DATA.  
  
 [5] **SQLFetch**, **SQLFetchScroll**, ou **SQLExtendedFetch** n’avait pas été appelée.  
  
 [6] **SQLFetch** ou **SQLFetchScroll** avait été appelée.  
  
 [7] **SQLExtendedFetch** avait été appelée.  
  
## <a name="sqlcancel-asynchronous-states"></a>SQLCancel (États asynchrones)  
  
|S11<br /><br /> En cours d’exécution|S12<br /><br /> Asynchrone annulée|  
|-----------------------------|-----------------------------|  
|S12 DE NS [1] [2]|S12|  
  
 [1] l’instruction a été temporairement dans un état S11 pendant une fonction s’exécutait. **SQLCancel** a été appelée à partir d’un thread différent.  
  
 [2] l’instruction a été dans un état S11, car une fonction appelée de façon asynchrone retourné SQL_STILL_EXECUTING.  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|24000|24000|24000|S1 [np] S3 [p]|HY010|HY010|  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|Consultez le tableau suivant|24000|--S11 [s] [x]|HY010|O de HY010 NS [c]|  
  
## <a name="sqlcolattribute-prepared-states"></a>SQLColAttribute (États préparées)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|--[1] 07005[2]|--S11 [s] x|  
  
 [1] *FieldIdentifier* a été SQL_DESC_COUNT.  
  
 [2] *FieldIdentifier* n’était pas SQL_DESC_COUNT.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges et SQLTables  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S5 [s] S11 [x]|S1 [e] S5 [s] S11 [x]|S1 [e] et [1] S5 [s] et [1] S11 [x] et [1] 24000 [2]|Consultez le tableau suivant|HY010|O de HY010 NS [c]|  
  
 [1] le résultat actuel est la dernière ou un seul résultat, ou aucun résultat actuel. Pour plus d’informations sur plusieurs résultats, consultez [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] le résultat actuel n’est pas le dernier résultat.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables-cursor-states"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges et SQLTables (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000[1]|24000|  
  
 [1] Cette erreur est retournée par le Gestionnaire de pilotes si **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_NO_DATA et est retourné par le pilote si **SQLFetch** ou **SQLFetchScroll** a retourné SQL_NO_DATA.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH [1]|--|--|--|--|HY010|NS [c] et [3] HY010 [o] ou [4]|  
|IH [2]|HY010|Consultez le tableau suivant|24000|--S11 [s] x|HY010|NS [c] et [3] HY010 [o] ou [4]|  
  
 [1] cette ligne affiche les transitions quand le *SourceDescHandle* argument était un ARD, APD ou IPD.  
  
 [2] cette ligne affiche les transitions quand le *SourceDescHandle* argument était un IRD.  
  
 [3] le *SourceDescHandle* et *TargetDescHandle* arguments étaient les mêmes que dans le **SQLCopyDesc** fonction qui s’exécute de façon asynchrone.  
  
 [4] soit le *SourceDescHandle* argument ou *TargetDescHandle* argument (ou les deux) ont été différentes de celle de la **SQLCopyDesc** fonction qui est en cours d’exécution de façon asynchrone.  
  
## <a name="sqlcopydesc-prepared-states"></a>SQLCopyDesc (États préparées)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|24000[1]|--S11 [s] [x]|  
  
 [1] Cette ligne affiche les transitions quand le *SourceDescHandle* argument était un IRD.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources et SQLDrivers  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqldescribecol"></a>SQLDescribeCol  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|Consultez le tableau suivant|24000|--S11 [s] [x]|HY010|O de HY010 NS [c]|  
  
## <a name="sqldescribecol-prepared-states"></a>SQLDescribeCol (États préparées)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|07005|--S11 [s] [x]|  
  
## <a name="sqldescribeparam"></a>SQLDescribeParam  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|--S11 [s] [x]|HY010|HY010|HY010|NS [c] HY010 [o]|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|S0 [1]|S0 [1]|S0 [1]|S0 [1]|(HY010)|(HY010)|  
  
 [1] appel **SQLDisconnect** libère toutes les instructions associées à la connexion. En outre, il retourne l’état de la connexion à C2 ; l’état de connexion doit être C4 avant que l’état de l’instruction est S0.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--[2] ou [3] S1 [1]|--S1 [3] [np] et ([1] ou [2]) S1 [p] et [1] S2 [p] et [2]|--S1 [3] [np] et ([1] ou [2]) S1 [p] et [1] S3 [p] et [2]|(HY010)|(HY010)|  
  
 [1] le *CompletionType* argument est active et **SQLGetInfo** retourne SQL_CB_DELETE SQL_CURSOR_COMMIT_BEHAVIOR type d’informations, ou le *CompletionType*argument est SQL_ROLLBACK et **SQLGetInfo** retourne SQL_CB_DELETE SQL_CURSOR_ROLLBACK_BEHAVIOR type d’informations.  
  
 [2] le *CompletionType* argument est active et **SQLGetInfo** retourne SQL_CB_CLOSE SQL_CURSOR_COMMIT_BEHAVIOR type d’informations, ou le *CompletionType*argument est SQL_ROLLBACK et **SQLGetInfo** retourne SQL_CB_CLOSE SQL_CURSOR_ROLLBACK_BEHAVIOR type d’informations.  
  
 [3] le *CompletionType* argument est active et **SQLGetInfo** retourne SQL_CB_PRESERVE SQL_CURSOR_COMMIT_BEHAVIOR type d’informations, ou le *CompletionType*argument est SQL_ROLLBACK et **SQLGetInfo** retourne SQL_CB_PRESERVE SQL_CURSOR_ROLLBACK_BEHAVIOR type d’informations.  
  
## <a name="sqlexecdirect"></a>SQLExecDirect  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S4 [s] et [nr] S5 [s] et [r] S8 [d] S11 [x]|--[e] et [1] S1 [e] et S4 [2] [s] et [nr] S5 [s] et [r] S8 [d] S11 [x]|--[e], [1] et [3] S1 [e], [2] et [3] S4 [s], [nr,] et [3] S5 [s], [r] et S8 [3] [d] et [3] S11 [x] et [3] 24000 [4]|Consultez le tableau suivant|HY010|NS [c] HY010 [o]|  
  
 [1] l’erreur a été renvoyée par le Gestionnaire de pilotes.  
  
 [2] l’erreur n’a pas a été renvoyée par le Gestionnaire de pilotes.  
  
 [3] le résultat actuel est la dernière ou un seul résultat, ou aucun résultat actuel. Pour plus d’informations sur plusieurs résultats, consultez [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] le résultat actuel n’est pas le dernier résultat.  
  
## <a name="sqlexecdirect-cursor-states"></a>SQLExecDirect (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000 [1]|24000|  
  
 [1] Cette erreur est retournée par le Gestionnaire de pilotes si **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_NO_DATA et est retourné par le pilote si **SQLFetch** ou  **SQLFetchScroll** a retourné SQL_NO_DATA.  
  
## <a name="sqlexecute"></a>SQLExecute  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|Consultez le tableau suivant|S2 [e], p et S4 [1] [s], [p], [nr,] et [1] S5 [s], [p], [r] et [1] S8 [d] [p] et [1] S11 [x], [p] et [1] 24000 [p] et [2] HY010 [np]|Consultez le tableau d’états de curseur|HY010|NS [c] HY010 [o]|  
  
 [1] le résultat actuel est la dernière ou un seul résultat, ou aucun résultat actuel. Pour plus d’informations sur plusieurs résultats, consultez [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] le résultat actuel n’est pas le dernier résultat.  
  
## <a name="sqlexecute-prepared-states"></a>SQLExecute (États préparées)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|S4 [s] S8 [d] S11 [x]|S5 [s] S8 [d] S11 [x]|  
  
## <a name="sqlexecute-cursor-states"></a>SQLExecute (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000 HY010 [p] [np]|24000 [p], [1] HY010 [np]|24000 HY010 [p] [np]|  
  
 [1] Cette erreur est retournée par le Gestionnaire de pilotes si **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_NO_DATA et est retourné par le pilote si **SQLFetch** ou  **SQLFetchScroll** a retourné SQL_NO_DATA.  
  
## <a name="sqlextendedfetch"></a>SQLExtendedFetch  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|S1010|S1010|24000|Consultez le tableau suivant|S1010|NS [c] S1010 [o]|  
  
## <a name="sqlextendedfetch-cursor-states"></a>SQLExtendedFetch (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S7 [s] ou [nf] S11 [x]|S1010|--[s] ou [nf] S11 [x]|  
  
## <a name="sqlfetch-and-sqlfetchscroll"></a>SQLFetch et SQLFetchScroll  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24000|Consultez le tableau suivant|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlfetch-and-sqlfetchscroll-cursor-states"></a>SQLFetch et SQLFetchScroll (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S6 [s] ou [nf] S11 [x]|--[s] ou [nf] S11 [x]|HY010|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|-- [1]|HY010|HY010|HY010|HY010|HY010|HY010|  
|IH [2]|S0|S0|S0|S0|HY010|HY010|  
|-- [3]|--|--|--|--|--|--|  
  
 [1] cette ligne affiche les transitions quand *HandleType* était SQL_HANDLE_ENV ou SQL_HANDLE_DBC.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_STMT.  
  
 [3] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DESC et le descripteur a été explicitement affectée.  
  
## <a name="sqlfreestmt"></a>SQLFreeStmt  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH [1]|--|--|S1 [np] S2 [p]|S1 [np] S3 [p]|HY010|HY010|  
|IH [2]|--|--|--|--|HY010|HY010|  
  
 [1] cette ligne affiche les transitions quand *Option* a été SQL_CLOSE.  
  
 [2] cette ligne affiche les transitions quand *Option* était SQL_UNBIND ou SQL_RESET_PARAMS. Si le *Option* SQL_DROP a été l’argument et le pilote sous-jacent est un ODBC 3 *.x* pilote, le Gestionnaire de pilotes effectue un mappage à un appel à **SQLFreeHandle** avec  *HandleType* défini à SQL_HANDLE_STMT. Pour plus d’informations, consultez le tableau de transition pour [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetcursorname"></a>SQLGetCursorName  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlgetdata"></a>SQLGetData  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24000|Consultez le tableau suivant|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlgetdata-cursor-states"></a>SQLGetData (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|--[s] ou [nf] S11 [24000 [b] HY109 x] [i]|--[s] ou [nf] S11 [24000 [b] HY109 x] [i]|  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField et SQLGetDescRec  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--[1] ou [2] HY010 [3]|Consultez le tableau suivant|--[1] ou 24000 [2] [3]|--[1], [2] ou [3] S11 [3] et [x]|HY010|NS [c] ou [4] HY010 [o] et [5]|  
  
 [1] le *DescriptorHandle* argument était un APD ou le ARD.  
  
 [2] le *DescriptorHandle* argument était un IPD.  
  
 [3] le *DescriptorHandle* argument était un IRD.  
  
 [4] le *DescriptorHandle* argument était identique à la *DescriptorHandle* argument dans le **SQLGetDescField** ou **SQLGetDescRec** fonction qui s’exécute de façon asynchrone.  
  
 [5] le *DescriptorHandle* argument est différent de celle du *DescriptorHandle* argument dans le **SQLGetDescField** ou **SQLGetDescRec**fonction qui s’exécute de façon asynchrone.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec-prepared-states"></a>SQLGetDescField et SQLGetDescRec (États préparées)  
  
|S2<br /><br /> Aucun résultat|S3<br /><br /> Résultats|  
|-----------------------|--------------------|  
|--[1], [2] ou [3] S11 [2] et [x]|--[1], [2] ou [3] S11 [x]|  
  
 [1] le *DescriptorHandle* argument était un APD ou le ARD.  
  
 [2] le *DescriptorHandle* argument était un IPD.  
  
 [3] le *DescriptorHandle* argument était un IRD. Notez que ces fonctions retournent toujours SQL_NO_DATA dans un état S2 lorsque *DescriptorHandle* a été un IRD.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagRec et SQLGetDiagField  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--|--|--|  
|IH [2]|--[3]|--[3]|--|--|--[3]|--[3]|  
  
 [1] cette ligne affiche les transitions quand *HandleType* était SQL_HANDLE_ENV, SQL_HANDLE_DBC ou SQL_HANDLE_DESC.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_STMT.  
  
 [3] **SQLGetDiagField** toujours retourne une erreur dans cet état lorsque *DiagIdentifier* est SQL_DIAG_ROW_COUNT.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--[1] 24000[2]|--[1] 24000[2]|--[1] 24000[2]|Consultez le tableau suivant|HY010|HY010|  
  
 [1] l’attribut d’instruction n’a pas été SQL_ATTR_ROW_NUMBER.  
  
 [2] l’attribut d’instruction a été SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlgetstmtattr-cursor-states"></a>SQLGetStmtAttr (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--[1] 24000[2]|--[1] ou ([v] et [2]) 24000 [b] et [2] HY109 [i] et [2]|--[i] ou ([v] et [2]) 24000 [b] et [2] HY109 [1] et [2]|  
  
 [1] le *attribut* argument n’a pas été SQL_ATTR_ROW_NUMBER.  
  
 [2] le *attribut* SQL_ATTR_ROW_NUMBER a été l’argument.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|--[1]|--[1]|--[s] et [2] S1 [nf], [np,] et [4] S2 [nf], [p] et [4] S5 [s] et [3] S11 [x]|S1 [nf], [np,] et [4] S3 [nf], [p] et [4] S4 [s] et [2] S5 [s] et [3] S11 [x]|HY010|NS [c] HY010 [o]|  
  
 [1] la fonction retourne toujours SQL_NO_DATA dans cet état.  
  
 [2] le résultat suivant est un nombre de lignes.  
  
 [3] le résultat suivant est un jeu de résultats.  
  
 [4] le résultat actuel est le dernier résultat.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlnumparams"></a>SQLNumParams  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|--S11 [s] [x]|--S11 [s] [x]|--S11 [s] [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlnumresultcols"></a>SQLNumResultCols  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|--S11 [s] [x]|--S11 [s] [x]|--S11 [s] [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata"></a>SQLParamData  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|HY010|HY010|Consultez le tableau suivant|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata-need-data-states"></a>SQLParamData (nécessité des États de données)  
  
|S8<br /><br /> Besoin de données|S9<br /><br /> Instaurer|S10<br /><br /> Peut placer|  
|----------------------|---------------------|---------------------|  
|S1 [e] et S2 [1] [e], [nr] et S3 [2] [e], [r] et [2] S5 [e] et [4] S6 [e] et [5] S7 [e] et [3] S9 [d] S11 [x]|HY010|S1 [e] et S2 [1] [e], [nr] et S3 [2] [e], [r] et [2] S4 [s], [nr], et ([1] ou [2]) S5 [s], [r], et ([1] ou [2]) S5 ([s] ou [e]) et [4] S6 ([s] ou [e]) et [5] S7 ([s] ou [e]) et S9 [3] [d] S11 [x]|  
  
 [1] **SQLExecDirect** retourné SQL_NEED_DATA.  
  
 [2] **SQLExecute** retourné SQL_NEED_DATA.  
  
 [3] **SQLSetPos** avait été appelée à partir de l’état S7 et retourné SQL_NEED_DATA.  
  
 [4] **SQLBulkOperations** avait été appelée à partir de l’état S5 et retourné SQL_NEED_DATA.  
  
 [5] **SQLSetPos** ou **SQLBulkOperations** avait été appelée à partir de l’état S6 et retourné SQL_NEED_DATA.  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S2 [s] et [nr] S3 [s] et [r] S11 [x]|--[s] ou ([e] et [1]) S1 [e] et [2] S11 [x]|S1 [e] et [3] S2 [s], [nr,] et [3] S3 [s], [r] et [3] S11 [x] et [3] 24000 [4]|Consultez le tableau suivant|HY010|NS [c] HY010 [o]|  
  
 [1] la préparation échoue pour une raison autre que la validation de l’instruction (la valeur SQLSTATE a été HY009 [valeur d’argument non valide] ou HY090 [longueur de chaîne ou de la mémoire tampon non valide]).  
  
 [2] la préparation échoue lors de la validation de l’instruction (la variable SQLSTATE n’a pas été HY009 [valeur d’argument non valide] ou HY090 [longueur de chaîne ou de la mémoire tampon non valide]).  
  
 [3] le résultat actuel est la dernière ou un seul résultat, ou aucun résultat actuel. Pour plus d’informations sur plusieurs résultats, consultez [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] le résultat actuel n’est pas le dernier résultat.  
  
## <a name="sqlprepare-cursor-states"></a>SQLPrepare (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000|24000|  
  
## <a name="sqlputdata"></a>SQLPutData  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|HY010|HY010|Consultez le tableau suivant|NS [c] HY010 [o]|  
  
## <a name="sqlputdata-need-data-states"></a>SQLPutData (nécessité des États de données)  
  
|S8<br /><br /> Besoin de données|S9<br /><br /> Instaurer|S10<br /><br /> Peut placer|  
|----------------------|---------------------|---------------------|  
|HY010|S1 [e] et S2 [1] [e], [nr] et S3 [2] [e], [r] et [2] S5 [e] et [4] S6 [e] et [5] S7 [e] et [3] S10 [s] S11 [x]|--S1 [s] [e] et [1] S2 [e], [nr] et S3 [2] [e], [r] et [2] S5 [e] et [4] S6 [e] et [5] S7 [e] et [3] S11 [x] HY011 [6]|  
  
 [1] **SQLExecDirect** retourné SQL_NEED_DATA.  
  
 [2] **SQLExecute** retourné SQL_NEED_DATA.  
  
 [3] **SQLSetPos** avait été appelée à partir de l’état S7 et retourné SQL_NEED_DATA.  
  
 [4] **SQLBulkOperations** avait été appelée à partir de l’état S5 et retourné SQL_NEED_DATA.  
  
 [5] **SQLSetPos** ou **SQLBulkOperations** avait été appelée à partir de l’état S6 et retourné SQL_NEED_DATA.  
  
 [6] un ou plusieurs appels à **SQLPutData** pour un seul paramètre retourné SQL_SUCCESS, puis sur un appel à **SQLPutData** a été effectuée pour le même paramètre avec *StrLen_or_Ind* définie avec la valeur SQL_NULL_DATA.  
  
## <a name="sqlrowcount"></a>SQLRowCount  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|(HY010)|--|--|(HY010)|(HY010)|  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--[2] 24000[3]|HY010|HY010|  
  
 [1] cette ligne affiche les transitions quand *attribut* a un attribut de connexion. Pour les transitions quand *attribut* était une instruction d’attribut, consultez le tableau de transition d’instruction pour **SQLSetStmtAttr**.  
  
 [2] le *attribut* argument n’a pas été SQL_ATTR_CURRENT_CATALOG.  
  
 [3] le *attribut* argument était SQL_ATTR_CURRENT_CATALOG.  
  
## <a name="sqlsetcursorname"></a>SQLSetCursorName  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|24000|24000|HY010|HY010|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField et SQLSetDescRec  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH [1]|--|--|--|--|HY010|HY010|  
  
 [1] cette ligne affiche les transitions où le *DescriptorHandle* argument est un ARD, APD IPD, ou (pour **SQLSetDescField**) un IRD lorsque le *FieldIdentifier* argument est SQL_ DESC_ARRAY_STATUS_PTR ou SQL_DESC_ROWS_PROCESSED_PTR. C’est une erreur d’appeler **SQLSetDescField** pour un IRD lorsque *FieldIdentifier* est une autre valeur.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|HY011|HY011|HY011|HY011|Y011|HY01|HY011|  
  
## <a name="sqlsetpos"></a>SQLSetPos  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24000|Consultez le tableau suivant|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlsetpos-cursor-states"></a>SQLSetPos (États de curseur)  
  
|S5<br /><br /> Ouvert|S6<br /><br /> SQLFetch ou SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|--[s] S8 [d] S11 [24000 [b] HY109 x] [i]|--[s] S8 [d] S11 [24000 [b] HY109 x] [i]|  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
  
|S0<br /><br /> Non alloué|S1<br /><br /> allouée|S2, S3<br /><br /> Prepared|S4<br /><br /> Exécutée|S5 – S7<br /><br /> Curseur|S8 – S10<br /><br /> Besoin de données|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--HY011 [1] [2]|--[1] 24000[2]|--[1] 24000[2]|HY010 [np] ou [1] HY011 [p] et [2]|HY010 [np] ou [1] HY011 [p] et [2]|  
  
 [1] le *attribut* argument n’était pas SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE et SQL_ATTR_CURSOR_SENSITIVITY.  
  
 [2] le *attribut* argument était SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE et SQL_ATTR_CURSOR_SENSITIVITY.
