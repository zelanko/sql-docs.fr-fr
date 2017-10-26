---
title: getAsciiStream (java.lang.String) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerCallableStatement.getAsciiStream(String paramName)
apilocation:
- SQLServerCallableStatement.getAsciiStream(String paramName)
apitype: Assembly
ms.assetid: 630b659f-eb36-4277-b04e-9a2e6134f795
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fbd9c5092d78134ff9fc50320e3a372eeadde874
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getasciistream-javalangstring"></a>getAsciiStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant que flux de **ASCII** caractères en fonction du nom de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.io.InputStream getAsciiStream(java.lang.String paramName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *paramName*  
  
 A **chaîne** qui indique le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getAsciiStream &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

