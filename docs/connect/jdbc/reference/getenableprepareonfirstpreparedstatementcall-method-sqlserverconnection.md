---
title: getEnablePrepareOnFirstPreparedStatementCall, méthode (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ac1cf4dbd8c8c14b5c97dbfecbe81d397c1598ce
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67983443"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>getEnablePrepareOnFirstPreparedStatementCall, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Retourne la valeur de la propriété de connexion **enablePrepareOnFirstPreparedStatementCall**. Si la valeur est false, la première exécution appellera sp_executesql sans préparer d’instruction. À la deuxième exécution, elle appellera sp_prepexec et configurera un handle d’instruction préparée. Les exécutions suivantes appelleront sp_execute. Cela évite d’utiliser sp_unprepare lors de la fermeture de l’instruction préparée si l’instruction n’est exécutée qu’une seule fois. La valeur par défaut de cette option peut être modifiée en appelant setDefaultEnablePrepareOnFirstPreparedStatementCall().

## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>Valeur de retour
 Valeur **booléenne** qui contient la valeur de la propriété de connexion **enablePrepareOnFirstPreparedStatementCall**.

## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible dans la version 6.4 et versions ultérieures du pilote JDBC.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
