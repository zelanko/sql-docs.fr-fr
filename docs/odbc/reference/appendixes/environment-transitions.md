---
title: Transitions d’environnement | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ed2bbf40ac333db34d3920b2ed2ec688c344bfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188996"
---
# <a name="environment-transitions"></a>Transitions d’environnement
Environnements de ODBC ont trois états suivants.  
  
|État|Description|  
|-----------|-----------------|  
|E0|Environnement non alloué|  
|E1|Environnement alloué, non alloué de connexion|  
|E2|Allouée d’environnement, allouée de connexion|  
  
 Les tableaux suivants indiquent comment chaque fonction ODBC affecte l’état de l’environnement.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0<br /><br /> Non alloué|E1<br /><br /> allouée|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|E1[1]|--[4]|--[4]|  
|(IH)[2]|E2[5]<br />(HY010)[6]|--[4]|  
|(IH)[3]|(IH)|--[4]|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] cette ligne affiche les transitions quand *HandleType* était SQL_HANDLE_STMT ou SQL_HANDLE_DESC.  
  
 [4] appel **SQLAllocHandle** avec *OutputHandlePtr* pointant vers un handle valide remplace ce descripteur. Cela peut être une erreur de programmation d’application.  
  
 [5] l’attribut d’environnement SQL_ATTR_ODBC_VERSION avait été défini sur l’environnement.  
  
 [6] l’attribut d’environnement SQL_ATTR_ODBC_VERSION n’a pas été défini sur l’environnement.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources et SQLDrivers  
  
|E0<br /><br /> Non alloué|E1<br /><br /> allouée|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|--[1]<br />(HY010)[2]|  
  
 [1] l’attribut d’environnement SQL_ATTR_ODBC_VERSION avait été défini sur l’environnement.  
  
 [2] l’attribut d’environnement SQL_ATTR_ODBC_VERSION n’a pas été défini sur l’environnement.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Non alloué|E1<br /><br /> allouée|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|--[3]<br />(HY010)[4]|--[3]<br />(HY010)[4]|  
|(IH)[2]|(IH)|--|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] l’attribut d’environnement SQL_ATTR_ODBC_VERSION avait été défini sur l’environnement.  
  
 [4] l’attribut d’environnement SQL_ATTR_ODBC_VERSION n’a pas été défini sur l’environnement.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Non alloué|E1<br /><br /> allouée|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|E0|(HY010)|  
|(IH)[2]|(IH)|--[4]<br />E1[5]|  
|(IH)[3]|(IH)|--|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DBC.  
  
 [3] cette ligne affiche les transitions quand *HandleType* était SQL_HANDLE_STMT ou SQL_HANDLE_DESC.  
  
 [4] se sont produites autres handles de connexion alloué.  
  
 [5] le handle de connexion spécifié dans *gérer* a été le handle de connexion alloué uniquement.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagRec et SQLGetDiagField  
  
|E0<br /><br /> Non alloué|E1<br /><br /> allouée|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|--|--|  
|(IH)[2]|(IH)|--|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_ENV.  
  
 [2] cette ligne affiche les transitions quand *HandleType* était SQL_HANDLE_DBC, SQL_HANDLE_STMT ou SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> Non alloué|E1<br /><br /> allouée|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|--|  
  
 [1] l’attribut d’environnement SQL_ATTR_ODBC_VERSION avait été défini sur l’environnement.  
  
 [2] l’attribut d’environnement SQL_ATTR_ODBC_VERSION n’a pas été défini sur l’environnement.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Non alloué|E1<br /><br /> allouée|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|(HY011)|  
  
 [1] l’attribut d’environnement SQL_ATTR_ODBC_VERSION avait été défini sur l’environnement.  
  
 [2] le *attribut* argument n’a pas été SQL_ATTR_ODBC_VERSION et l’attribut d’environnement SQL_ATTR_ODBC_VERSION n’avait pas été définie sur l’environnement.  
  
## <a name="all-other-odbc-functions"></a>Toutes les autres fonctions ODBC  
  
|E0<br /><br /> Non alloué|E1<br /><br /> allouée|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|(IH)|--|
