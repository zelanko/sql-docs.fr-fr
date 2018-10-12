---
title: Constructeur SQLServerException (java.lang.String, java.lang.String, int, java.lang.Throwable) | Microsoft Docs
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
ms.openlocfilehash: f596056d830ae3fa3462095e5a17a112c8f641f2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759257"
---
# <a name="sqlserverexception-constructor-javalangstring-javalangstring-int-javalangthrowable"></a>Constructeur SQLServerException (java.lang.String, java.lang.String, int, java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) classe en fonction d’un **chaîne** objet, un **chaîne** objet, un **int**et un **levable** objet.

## <a name="syntax"></a>Syntaxe  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState errState,
            int errNum,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Paramètres  
 *errText*  
  
 Chaîne contenant le texte d’erreur.
  
 *errState*  
  
 Chaîne contenant l’état de l’erreur.
 
 *errNum*  
  
 Entier qui contient le code d’erreur pour l’exception.
 
 *cause*  
  
 Un objet levable qui contient la cause de l’exception.
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerException, constructeurs](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException, membres](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException, classe](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
