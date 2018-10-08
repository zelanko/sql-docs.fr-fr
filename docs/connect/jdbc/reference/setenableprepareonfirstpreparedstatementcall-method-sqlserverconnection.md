---
title: setenableprepareonfirstpreparedstatementcall, méthode (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e58e1a3814bd4fefda85f9ec525270923ef45dfe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729917"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>setEnablePrepareOnFirstPreparedStatementCall, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Spécifie le comportement pour une instance de connexion spécifique. Si la valeur est false, la première exécution appelle sp_executesql et n’a pas préparer une instruction, une fois que la deuxième exécution se produit, il appelle sp_prepexec et configurer réellement un descripteur d’instruction préparée. Suivant les exécutions appellera sp_execute. Cela évite la nécessité de sp_unprepare sur instruction préparée fermer si l’instruction est exécutée uniquement une fois.

## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 La nouvelle valeur de la **enablePrepareOnFirstPreparedStatementCall** propriété de connexion.  
 
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes   
 Cette méthode est disponible à partir de la version du pilote JDBC 6.4 et ultérieur.
 
## <a name="see-also"></a> Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
