---
title: "isClosed (méthode) (SQLServerConnection) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerConnection.isClosed
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2f8c264171a4e91c4dd449f1ea8fa19830fb4ca1
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed (méthode) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si cette [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) objet a été fermé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la connexion est fermée, **false** si elle n’est pas.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isClosed est spécifiée par la méthode isClosed dans l’interface java.sql.Connection.  
  
 Vérifie l’état de l’objet SQLServerConnection appelé. Une connexion est fermée si la [fermer](../../../connect/jdbc/reference/close-method-sqlserverconnection.md) méthode a été appelée, ou si certaines erreurs irrécupérables se sont produites. Cette méthode retournera **true** uniquement lorsqu’elle est appelée une fois que la méthode close a été appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
