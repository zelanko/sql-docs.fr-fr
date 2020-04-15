---
title: Fonction SQLGetPoolID (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32cc973f4dab5bde7bcedade0365d233987dda72
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303316"
---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID, fonction
**Conformité**  
 Version introduite: ODBC 3.81 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLGetPoolID** récupère l’ID de la piscine.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Arguments  
 *hDbcInfoToken (en anglais seulement)*  
 [Entrée] Poignée de jeton qui contient toutes les informations de connexion.  
  
 *pPoolID (en)*  
 [Sortie] L’ID de la piscine, qui est utilisé pour identifier un ensemble de connexions qui peuvent être utilisées de manière interchangeable (éventuellement nécessitant une réinitialisation supplémentaire).  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetPoolID** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, le gestionnaire de conducteur utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et une **poignée** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 **SQLGetPoolID** est utilisé pour obtenir l’ID de la piscine compte tenu d’un ensemble d’informations de connexion (de **SQLSetConnectAttrForDbcInfo**, **SQLSetDriverConnectInfo**, et **SQLSetConnectInfo**). Cette pièce d’identité de piscine est utilisée pour identifier un ensemble de connexions qui peuvent être utilisées de manière interchangeable (nécessitant éventuellement une réinitialisation supplémentaire). L’ID de la piscine sera utilisé pour identifier le pool de connexion pour ce groupe de connexions.  
  
 Chaque fois qu’un pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le gestionnaire de pilote renvoie l’erreur à l’application (dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) ou [SQLDriverConnect).](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Chaque fois qu’un pilote retourne SQL_SUCCESS_WITH_INFO, le gestionnaire de conducteur obtiendra les informations diagnostiques de *hDbcInfoToken*, et retournera SQL_SUCCESS_WITH_INFO à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Les applications ne doivent pas appeler cette fonction directement. Un conducteur ODBC qui prend en charge la mise en commun des connexions consciente du conducteur doit mettre en œuvre cette fonction.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Mise en commun des connexions conscientes du conducteur](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
