---
title: Fonction SQLSetConnectInfo (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectInfo function [ODBC]
ms.assetid: 0782a1c3-c5d1-499b-a8ba-134162db9990
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b575e0d09f87ad21e1190b8081b6604349a98263
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301850"
---
# <a name="sqlsetconnectinfo-function"></a>SQLSetConnectInfo, fonction
**Conformité**  
 Version introduite: ODBC 3.81 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLSetConnectInfo** est utilisé pour définir la source de données, l’identifiant d’utilisateur et le mot de passe dans le jeton d’information de connexion pour l’appel [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) d’une application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN  SQLSetConnectInfo(  
                SQLHDBC_INFO_TOKEN   TokenHandle,  
                WCHAR *              ServerName,  
                SQLSMALLINT          NameLength1,  
                WCHAR *              UserName,  
                SQLSMALLINT          NameLength2,  
                WCHAR *              Authentication,  
                SQLSMALLINT          NameLength3 );  
```  
  
## <a name="arguments"></a>Arguments  
 *Coup de jeton*  
 [Entrée] Poignée symbolique.  
  
 *Servername*  
 [Entrée] Nom de source de données. Les données peuvent être localisées sur le même ordinateur que le programme, ou sur un autre ordinateur quelque part sur un réseau. Pour plus d’informations sur la façon dont une application choisit une source de données, voir [Choisir une source de données ou un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Entrée] Longueur de*ServerName* en caractères.  
  
 *nom d'utilisateur*  
 [Entrée] Identifiant utilisateur.  
  
 *NomLength2*  
 [Entrée] Longueur de*l’UserName* en caractères.  
  
 *Authentification*  
 [Entrée] Chaîne d’authentification (généralement le mot de passe).  
  
 *NomLength3*  
 [Entrée] Longueur de*l’authentification* en caractères.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Idem pour [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) pour les erreurs de validation des entrées, sauf que le gestionnaire de pilote utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et une **poignée** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 Chaque fois qu’un pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le gestionnaire de pilote renvoie l’erreur à l’application (dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) ou [SQLDriverConnect).](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Chaque fois qu’un pilote retourne SQL_SUCCESS_WITH_INFO, le gestionnaire de conducteur obtiendra les informations diagnostiques de *hDbcInfoToken*, et retournera SQL_SUCCESS_WITH_INFO à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Les applications ne doivent pas appeler cette fonction directement. Un conducteur ODBC qui prend en charge la mise en commun des connexions consciente du conducteur doit mettre en œuvre cette fonction.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Mise en commun des connexions conscientes du conducteur](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
