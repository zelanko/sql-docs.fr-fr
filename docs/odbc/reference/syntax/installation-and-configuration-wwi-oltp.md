---
title: Sqlsetdriverconnectinfo, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c344315764eac32e2e63663f07b7f797571a0e6
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204688"
---
# <a name="sqlsetdriverconnectinfo-function"></a>SQLSetDriverConnectInfo, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3,81 ODBC : ODBC  
  
 **Résumé**  
 **SQLSetDriverConnectInfo** sert à définir la chaîne de connexion dans le jeton d’informations de connexion pour l’application **SQLDriverConnect** appeler.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>Arguments  
 *TokenHandle*  
 [Entrée] Handle de jeton.  
  
 *InConnectionString*  
 [Entrée] Une chaîne de connexion complète (consultez la syntaxe dans « Commentaires » dans [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)), une chaîne de connexion partielle ou une chaîne vide.  
  
 *StringLength1*  
 [Entrée] Longueur de **InConnectionString*, en caractères, si la chaîne est Unicode ou octets si la chaîne ANSI ou DBCS.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Identique à [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) liés à toute erreur de validation d’entrée, à ceci près que le Gestionnaire de pilotes utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et un **gérer** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 Chaque fois qu’un pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le Gestionnaire de pilotes retourne l’erreur à l’application (dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) ou [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Chaque fois qu’un pilote retourne SQL_SUCCESS_WITH_INFO, le Gestionnaire de pilotes obtiendront les informations de diagnostic à partir de *hDbcInfoToken*et retourne SQL_SUCCESS_WITH_INFO, à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Applications ne doivent pas appeler cette fonction directement. Un pilote ODBC qui prend en charge le regroupement de connexions prenant en charge les pilotes doive implémenter cette fonction.  
  
 Inclure sqlspi.h pour le développement de pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Le regroupement de connexions prenant en charge de pilote](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
