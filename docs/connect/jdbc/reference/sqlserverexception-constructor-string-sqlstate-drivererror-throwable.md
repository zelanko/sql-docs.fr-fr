---
title: Constructeur SQLServerException (Java. lang. String, SQLState, DriverError, Java. lang. Throwable) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 13b0e3aea694b0cedb3594cb76650ca7c938eb55
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971095"
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>Constructeur SQLServerException (Java. lang. String, SQLState, DriverError, Java. lang. Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la classe [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) en fonction d’un objet **String** , d’un objet **SQLSTATE** , d’un objet **drivererror** et d’un objet **levant** .

## <a name="syntax"></a>Syntaxe  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState sqlState,
            DriverError driverError,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Paramètres  
 *errText*  
  
 Chaîne qui contient le texte d’erreur.
  
 *sqlState*  
  
 Objet enum qui contient l’état SQL.
 
 *driverError*  
  
 Objet enum qui contient l’erreur de pilote.
 
 *cause*  
  
 Objet pouvant être levé qui contient la cause de l’exception.
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerException, constructeurs](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException, membres](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException, classe](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
