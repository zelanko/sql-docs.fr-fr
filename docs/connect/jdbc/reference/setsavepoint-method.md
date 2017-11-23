---
title: "Méthode setSavepoint () | Documents Microsoft"
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
apiname: SQLServerConnection.setSavepoint ()
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 11013055-4fd3-45a9-b2da-28b2908dad52
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a3f6a99906c88241f40e94f363bbb178a464e355
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setsavepoint-method-"></a>Méthode setSavepoint ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un point de sauvegarde sans nom dans la transaction actuelle et retourne le nouvel [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) objet qui le représente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Savepoint setSavepoint()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de point d’enregistrement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setSavePoint est spécifiée par la méthode setSavePoint dans l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setSavepoint &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
