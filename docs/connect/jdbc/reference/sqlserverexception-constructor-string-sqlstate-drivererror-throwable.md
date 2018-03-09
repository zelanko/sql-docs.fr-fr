---
title: SQLServerException, constructeur (java.lang.String, SQLState, DriverError, java.lang.Throwable) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2018
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
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 101eca8f837dcbda00b252d5dc9867dfeb754351
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>SQLServerException, constructeur (java.lang.String, SQLState, DriverError, java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) classe en fonction d’un **chaîne** objet, un **sqlstate** objet, un **drivererror** objet et un **levable** objet.

## <a name="syntax"></a>Syntaxe  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState sqlState,
            DriverError driverError,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Paramètres  
 *errText*  
  
 Chaîne qui conserve le texte d’erreur.
  
 *sqlState*  
  
 Un objet d’énumération qui contient l’état SQL.
 
 *driverError*  
  
 Un objet d’énumération qui contient l’erreur de pilote.
 
 *cause*  
  
 Un objet levable qui contient la cause de l’exception.
  
## <a name="see-also"></a>Voir aussi  
 [Constructeurs SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException Members](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException, classe](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
