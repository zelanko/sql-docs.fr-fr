---
title: "Méthode getBlob (java.lang.String) | Documents Microsoft"
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
- SQLServerCallableStatement.getBlob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3fe74b50-9ccd-4973-a93a-6da2c20a4154
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 920664ef12bbd45f312c32ce69b35cd568531240
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getblob-method-javalangstring"></a>Méthode getBlob (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre BLOB JDBC désigné en tant qu’objet Blob dans le langage de programmation Java selon le nom de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Blob getBlob(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet Blob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBlob est spécifiée par la méthode getBlob dans l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getBlob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getblob-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

