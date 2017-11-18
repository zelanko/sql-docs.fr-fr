---
title: "Méthode (SQLServerConnection) getCatalog | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.getCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e87ef65f-4b5a-4e1c-8db5-7f0932390bb0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac9650ac08ac3cae7169a2f746d050ccbed7d6f6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getcatalog-method-sqlserverconnection"></a>getCatalog (méthode) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nom de catalogue actuel de ce [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getCatalog()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient le nom du catalogue.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getCatalog est spécifiée par la méthode getCatalog dans l’interface java.sql.Connection.  
  
 Retourne la propriété de catalogue actuel de l’objet SQLServerConnection, ou null s’il n’est pas défini. La propriété de catalogue est explicitement définie avec la [setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md) (méthode), soit implicitement mise à jour en lisant le changement d’environnement sur TDS pour le catalogue actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

