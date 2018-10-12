---
title: SQLServerException, constructeur (java.lang.String, SQLState, DriverError, java.lang.Throwable) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: dc7608582a5ed146b656d41714853ba4c3b21b00
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679977"
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
  
 Chaîne qui contient le texte d’erreur.
  
 *sqlState*  
  
 Un objet d’énumération qui contient l’état SQL.
 
 *driverError*  
  
 Un objet d’énumération qui contient l’erreur de pilote.
 
 *cause*  
  
 Un objet levable qui contient la cause de l’exception.
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerException, constructeurs](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException, membres](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException, classe](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
