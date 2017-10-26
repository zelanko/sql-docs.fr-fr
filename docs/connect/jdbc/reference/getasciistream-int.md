---
title: getAsciiStream (int) | Documents Microsoft
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
- SQLServerCallableStatement.getAsciiStream(int paramIndex)
apilocation:
- SQLServerCallableStatement.getAsciiStream(int paramIndex)
apitype: Assembly
ms.assetid: 9d8b235e-4208-40ee-b5a5-bc76f73b82f8
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 125a763e6380316156fa1fb5b8b7960c7edd6b0f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getasciistream-int"></a>getAsciiStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant que flux de **ASCII** caractères en fonction de l’index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.io.InputStream getAsciiStream(int paramIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *paramIndex*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getAsciiStream &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

