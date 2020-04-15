---
title: Fonction SQLSetDriverConnectInfo (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDriverConnectInfo function [ODBC]
ms.assetid: bfd4dfc2-fbca-4ef3-81e5-2706f2389256
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10336475e39598161126c13771ad822de0d5f7d8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298797"
---
# <a name="sqlsetdriverconnectinfo-function"></a>SQLSetDriverConnectInfo, fonction
**Conformité**  
 Version introduite: ODBC 3.81 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLSetDriverConnectInfo** est utilisé pour définir la chaîne de connexion dans le jeton d’information de connexion pour l’appel **SQLDriverConnect** d’une application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>Arguments  
 *Coup de jeton*  
 [Entrée] Poignée symbolique.  
  
 *InConnectionString*  
 [Entrée] Une chaîne de connexion complète (voir la syntaxe dans "Comments" dans [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)), une chaîne de connexion partielle, ou une chaîne vide.  
  
 *StringLength1 (en)*  
 [Entrée] Longueur de*InConnectionString*, en caractères si la chaîne est Unicode, ou octets si la chaîne est ANSI ou DBCS.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Tout comme [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) lié à toute erreur de validation d’entrée, sauf que le gestionnaire de pilote utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et une **poignée** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 Chaque fois qu’un pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le gestionnaire de pilote renvoie l’erreur à l’application (dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) ou [SQLDriverConnect).](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Chaque fois qu’un pilote retourne SQL_SUCCESS_WITH_INFO, le gestionnaire de conducteur obtiendra les informations diagnostiques de *hDbcInfoToken*, et retournera SQL_SUCCESS_WITH_INFO à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Les applications ne doivent pas appeler cette fonction directement. Un conducteur ODBC qui prend en charge la mise en commun des connexions consciente du conducteur doit mettre en œuvre cette fonction.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Mise en commun des connexions conscientes du conducteur](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
