---
title: Sqlgetpoolid, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39b3d3d1ecdc21acee8b238f56cede0a59146bd2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740057"
---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID, fonction
**Conformité**  
 Version introduite : ODBC normes 3,81 conformité : ODBC  
  
 **Résumé**  
 **SQLGetPoolID** récupère l’ID de pool.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Arguments  
 *hDbcInfoToken*  
 [Entrée] Handle de jeton qui contient toutes les informations de connexion.  
  
 *pPoolID*  
 [Sortie] L’ID du pool, qui est utilisé pour identifier un ensemble de connexions qui peuvent être utilisés indifféremment (ce qui nécessite éventuellement une réinitialisation supplémentaire).  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetPoolID** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, le Gestionnaire de pilotes utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et un **gérer** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 **SQLGetPoolID** est utilisé pour obtenir l’ID du pool reçoit un jeu d’informations de connexion (à partir de **SQLSetConnectAttrForDbcInfo**, **SQLSetDriverConnectInfo**, et  **SQLSetConnectInfo**). Ce pool d’ID est utilisé pour identifier un ensemble de connexions qui peuvent être utilisés indifféremment (ce qui nécessite éventuellement une réinitialisation supplémentaire). L’ID du pool est utilisé pour identifier le pool de connexions pour ce groupe de connexions.  
  
 Chaque fois qu’un pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le Gestionnaire de pilotes retourne l’erreur à l’application (dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) ou [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Chaque fois qu’un pilote retourne SQL_SUCCESS_WITH_INFO, le Gestionnaire de pilotes obtiendront les informations de diagnostic à partir de *hDbcInfoToken*et retourne SQL_SUCCESS_WITH_INFO, à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Applications ne doivent pas appeler cette fonction directement. Un pilote ODBC qui prend en charge le regroupement de connexions prenant en charge les pilotes doive implémenter cette fonction.  
  
 Inclure sqlspi.h pour le développement de pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Le regroupement de connexions prenant en charge de pilote](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
