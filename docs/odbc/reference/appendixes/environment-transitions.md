---
title: Transitions en milieu de l’environnement (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment transitions [ODBC]
- transitioning states [ODBC], environment
- state transitions [ODBC], environment
ms.assetid: 9d11b1ab-f4c8-48ca-9812-8c04303f939d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebfb5475d24d5fc70c4cb46a666b2573066565a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283299"
---
# <a name="environment-transitions"></a>Transitions d’environnement
Les environnements ODBC ont les trois états suivants.  
  
|State|Description|  
|-----------|-----------------|  
|E0 (E0)|Environnement non alloué|  
|E1|Environnement alloué, connexion non allouée|  
|E2|Environnement alloué, connexion allouée|  
  
 Les tableaux suivants montrent comment chaque fonction ODBC affecte l’état de l’environnement.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|E1[1]|--[4]|--[4]|  
|(IH) [2]|E2[5]<br />(HY010) [6]|--[4]|  
|(IH) [3]|(IH)|--[4]|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT ou SQL_HANDLE_DESC.  
  
 [4] Appeler **SQLAllocHandle** avec *OutputHandlePtr* pointant vers une poignée valide surélevés qui manipulent. Il peut s’agir d’une erreur de programmation d’applications.  
  
 [5] L’attribut SQL_ATTR_ODBC_VERSION environnement avait été fixé sur l’environnement.  
  
 [6] L’attribut SQL_ATTR_ODBC_VERSION environnement n’avait pas été fixé sur l’environnement.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources et SQLDrivers  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|--[1]<br />(HY010) [2]|  
  
 [1] L’attribut SQL_ATTR_ODBC_VERSION environnement avait été fixé sur l’environnement.  
  
 [2] L’attribut SQL_ATTR_ODBC_VERSION environnement n’avait pas été fixé sur l’environnement.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|--[3]<br />(HY010) [4]|--[3]<br />(HY010) [4]|  
|(IH) [2]|(IH)|--|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] L’attribut SQL_ATTR_ODBC_VERSION environnement avait été fixé sur l’environnement.  
  
 [4] L’attribut SQL_ATTR_ODBC_VERSION environnement n’avait pas été fixé sur l’environnement.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|E0 (E0)|(HY010)|  
|(IH) [2]|(IH)|--[4]<br />E1[5]|  
|(IH) [3]|(IH)|--|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT ou SQL_HANDLE_DESC.  
  
 [4] Il y avait d’autres poignées de connexion allouées.  
  
 [5] La poignée de connexion spécifiée dans *Handle* était la seule poignée de connexion allouée.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField et SQLGetDiagRec  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|--|--|  
|(IH) [2]|(IH)|--|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_ENV.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DBC, SQL_HANDLE_STMT ou SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|--|  
  
 [1] L’attribut SQL_ATTR_ODBC_VERSION environnement avait été fixé sur l’environnement.  
  
 [2] L’attribut SQL_ATTR_ODBC_VERSION environnement n’avait pas été fixé sur l’environnement.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|(HY011)|  
  
 [1] L’attribut SQL_ATTR_ODBC_VERSION environnement avait été fixé sur l’environnement.  
  
 [2] *L’argument de l’attribut* n’était pas SQL_ATTR_ODBC_VERSION, et l’attribut SQL_ATTR_ODBC_VERSION environnement n’avait pas été fixé sur l’environnement.  
  
## <a name="all-other-odbc-functions"></a>Toutes les autres fonctions ODBC  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|(IH)|--|
